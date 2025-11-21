# VARIABILIDAD DE LA FRECUENCIA CARDIACA (HRV) Y BALANCE AUTONOMICO  LABORATORIO-5
## DESCRIPCIÓN 
Este laboratorio tiene como propósito analizar la variabilidad de la frecuencia cardíaca (HRV) como un indicador del balance entre la actividad simpática y parasimpática del sistema nervioso autónomo. Para ello, se adquiere una señal ECG real en dos condiciones fisiológicas diferentes (reposo y lectura en voz alta), se procesa digitalmente mediante filtrado, detección de picos R y cálculo de intervalos R-R, y finalmente se estudia la HRV tanto en el dominio del tiempo como mediante el diagrama de Poincaré, permitiendo obtener índices cuantitativos de actividad simpática y vagal. La práctica integra conceptos de fisiología, adquisición de señales y procesamiento digital. <br>
## OBJETIVOS
- Identificar cambios en el balance autonómico mediante análisis temporal de la variabilidad de la frecuencia cardíaca (HRV).<br>
- Analizar la variabilidad de la frecuencia cardíaca (HRV) como herramienta para evaluar el balance autonómico. <br>
- Adquirir y procesar correctamente una señal ECG utilizando métodos de filtrado y detección de picos R. <br>
- Comparar la respuesta autonómica del sujeto entre reposo y lectura en voz alta. <br>
- Aplicar herramientas de análisis temporal y no lineal (diagrama de Poincaré) para caracterizar la HRV.<br>
- Interpretar resultados fisiológicos relacionados con actividad simpática y parasimpática. <br> 
## PROCEDIMIENTO 
<img width="327" height="883" alt="image" src="https://github.com/user-attachments/assets/d07f50e0-a005-4168-b820-c8ecad102284" />

# PARTE A - Fundamento teórico y adquisición de señal
## Descripción 
En esta parte se realiza la investigación teórica necesaria para comprender la variabilidad de la frecuencia cardiaca (HRV) y su relación con el sistema nervioso autónomo. Luego, se adquiere la señal ECG de un sujeto en dos condiciones distintas: reposo y lectura en voz alta, con el fin de analizar cómo cambia el balance simpático-parasimpático. <br> 

# PARTE B - Preprocesamiento, filtrado, detección de picos R y HRV en dominio del tiempo
## Descripción
En esta sección se implementan las etapas de procesamiento digital necesarias para limpiar la señal ECG, extraer los picos R y calcular los intervalos R-R. La señal es filtrada utilizando un filtro IIR diseñado por el estudiante, posteriormente se divide según las dos condiciones experimentales y se obtiene la serie temporal de HRV para cada segmento. <br> 
## Diseño Filtro

<img width="327" height="883" alt="image" src="[https://github.com/user-attachments/assets/d07f50e0-a005-4168-b820-c8ecad102284](https://github.com/Maria-Alejandra-Luque/LABORATORIO-5/blob/main/imagen_2025-11-20_214947303.png)" />
<img width="327" height="883" alt="image" src="https://github.com/Maria-Alejandra-Luque/LABORATORIO-5/blob/main/imagen_2025-11-20_215036048.png" />


## CODIGO 
```
# ============================================
#   PARTE B - PRE-PROCESAMIENTO + GRÁFICAS
# ============================================
import numpy as np
import pandas as pd
from scipy import signal
import matplotlib.pyplot as plt
from scipy.io import wavfile

# ============================================
# 1. MONTAR GOOGLE DRIVE
# ============================================
from google.colab import drive
drive.mount('/content/drive')

# ============================================
# 2. PARÁMETROS
# ============================================
Fs = 500.0
seg_duration_s = 2*60  # 2 minutos

# Filtro IIR diseñado (orden 4)
b = np.array([0.04514067, 0.0, -0.09028134, 0.0, 0.04514067])
a = np.array([1.0, -3.31025739, 4.11831107, -2.30421103, 0.49616466])
```
Este fragmento del código inicia la Parte B del laboratorio, correspondiente al pre-procesamiento de la señal ECG. Primero importa las librerías necesarias para análisis digital y visualización de señales, y luego monta Google Drive para acceder a los archivos del experimento. Después define los parámetros principales del procesamiento: la frecuencia de muestreo del ECG (Fs = 500 Hz) y la duración de cada segmento del análisis (2 minutos). Finalmente, se especifican los coeficientes b y a de un filtro digital IIR de orden 4, previamente diseñado para eliminar ruido de la señal ECG y permitir una detección más precisa de los picos R. <br>

```
# ============================================
# 3. FUNCIONES
# ============================================

def load_ecg(path, assumed_fs=Fs):
    """Carga CSV con encabezado o sin encabezado, TXT, WAV, MAT."""
    if path.endswith('.csv') or path.endswith('.txt'):
        df = pd.read_csv(path)

        # 1 columna → solo señal
        if df.shape[1] == 1:
            x = df.iloc[:, 0].astype(float).values
            t = np.arange(len(x))/assumed_fs
            return t, x, assumed_fs

        # 2 columnas → tiempo y señal
        elif df.shape[1] == 2:
            t = df.iloc[:, 0].astype(float).values
            x = df.iloc[:, 1].astype(float).values
            Fs_est = 1.0/np.mean(np.diff(t))
            return t, x, Fs_est
        else:
            raise ValueError("El CSV tiene más de 2 columnas.")

    elif path.endswith('.wav'):
        fs, data = wavfile.read(path)
        if data.ndim > 1:
            data = data[:,0]
        t = np.arange(len(data))/fs
        return t, data.astype(float), fs

    elif path.endswith('.mat'):
        from scipy.io import loadmat
        m = loadmat(path)
        for k in ['ecg','ECG','signal','sig','data','x']:
            if k in m:
                x = np.squeeze(m[k]).astype(float)
                t = np.arange(len(x))/assumed_fs
                return t, x, assumed_fs
        raise ValueError("No se encontró señal válida en .mat")
    else:
        raise ValueError("Formato no soportado")
def apply_iir(x, zero_phase=True):
    if zero_phase:
        return signal.filtfilt(b, a, x)
    else:
        return signal.lfilter(b, a, x)
def detect_r_peaks(ecg_segment, fs, integrator_ms=150, min_rr_ms=250):
    diff = np.diff(ecg_segment, prepend=ecg_segment[0])
    sq = diff**2
    win = max(1, int(integrator_ms * fs / 1000))
    integ = np.convolve(sq, np.ones(win)/win, mode='same')

    dist = int(min_rr_ms * fs / 1000)
    thresh = np.mean(integ) + 0.5*np.std(integ)

    peaks, _ = signal.find_peaks(integ, distance=dist, height=thresh)

    refined = []
    radius = int(0.05*fs)
    for p in peaks:
        L = max(0, p-radius)
        R = min(len(ecg_segment)-1, p+radius)
        local = L + np.argmax(ecg_segment[L:R+1])
        refined.append(local)
    return np.unique(refined), integ

def compute_rr_from_peaks(peaks_idx, fs):
    if len(peaks_idx) < 2:
        return np.array([])
    return np.diff(peaks_idx)/fs

def clean_rr(rr_s, min_rr=0.25, max_rr=2.0):
    mask = (rr_s >= min_rr) & (rr_s <= max_rr)
    return rr_s[mask]
```
Se definió el conjunto de funciones utilizadas para el procesamiento de la señal ECG. Se creó load_ecg() para cargar archivos en diferentes formatos y obtener tiempo, señal y frecuencia de muestreo. Se implementó apply_iir() para aplicar el filtro IIR diseñado previamente. Se definió detect_r_peaks() para detectar y refinar los picos R en cada segmento. Se creó compute_rr_from_peaks() para calcular los intervalos R-R y se añadió clean_rr() para depurar los intervalos no válidos. Estas funciones apoyan las etapas posteriores del análisis de HRV.<br> 

```
# ============================================
# 4. PROCESAR TODO
# ============================================

def process_ecg_file(path):

    print(f"\nCargando archivo: {path}")
    t, x, fs = load_ecg(path)
    print(f"Señal cargada: {len(x)} muestras — Fs={fs} Hz — dur={len(x)/fs:.1f} s")

    # 1. Filtrado
    x_f = apply_iir(x, zero_phase=True)

    # --------------------------------------------
    # GRÁFICA: Señal original vs filtrada (FUCSIA)
    # --------------------------------------------
    plt.figure(figsize=(18,6))
    plt.plot(t, x, label="Señal Original", alpha=0.6)
    plt.plot(t, x_f, color="#FF00FF", label="Filtrada (fucsia)", linewidth=1.5)
    plt.title("Comparación: Señal Original vs Señal Filtrada")
    plt.xlabel("Tiempo (s)")
    plt.ylabel("Amplitud")
    plt.legend()
    plt.grid()
    plt.show()

    # 2. Segmentos
    seg_len = int(seg_duration_s * fs)
    if len(x_f) < 2*seg_len:
        raise ValueError("La señal NO tiene mínimo 4 minutos.")

    seg1 = x_f[:seg_len]
    seg2 = x_f[seg_len:2*seg_len]

    # 3. R-peaks
    p1, integ1 = detect_r_peaks(seg1, fs)
    p2, integ2 = detect_r_peaks(seg2, fs)

    # 4. RR intervals
    rr1 = clean_rr(compute_rr_from_peaks(p1, fs))
    rr2 = clean_rr(compute_rr_from_peaks(p2, fs))

    # 5. Estadísticas
    mean1 = np.mean(rr1)*1000 if len(rr1)>0 else np.nan
    sdnn1 = np.std(rr1, ddof=1)*1000 if len(rr1)>1 else np.nan

    mean2 = np.mean(rr2)*1000 if len(rr2)>0 else np.nan
    sdnn2 = np.std(rr2, ddof=1)*1000 if len(rr2)>1 else np.nan

    print("\n=== SEGMENTO 1 ===")
    print("Picos detectados:", len(p1))
    print("RR válidos:", len(rr1))
    print(f"Mean RR = {mean1:.2f} ms")
    print(f"SDNN = {sdnn1:.2f} ms")

    print("\n=== SEGMENTO 2 ===")
    print("Picos detectados:", len(p2))
    print("RR válidos:", len(rr2))
    print(f"Mean RR = {mean2:.2f} ms")
    print(f"SDNN = {sdnn2:.2f} ms")

```
Se implementó la función process_ecg_file() para ejecutar todo el flujo de procesamiento de la señal ECG. Esta función carga el archivo seleccionado, aplica el filtro IIR para obtener la señal limpia y genera una gráfica comparativa entre la señal original y la filtrada. Posteriormente, la señal filtrada se segmenta en dos intervalos de dos minutos. Para cada segmento se detectan los picos R, se calculan los intervalos R-R y se depuran los valores no válidos. Finalmente, se obtienen las estadísticas principales de HRV en el dominio del tiempo (Mean RR y SDNN) para cada segmento y se imprimen los resultados correspondientes. <br>

# PARTE C - Diagrama de Poincaré y análisis del balance autonómico
## Descripción
Esta parte consiste en construir el diagrama de Poincaré para cada segmento de ECG y analizar la dispersión de los puntos para determinar cambios en la actividad simpática y vagal. Se calculan los índices CSI (simpático) y CVI (vagal) y se comparan entre reposo y lectura.<br>

## CODIGO 
```
    # ============================================
    # 6. GRÁFICAS — TODAS EN FUCSIA
    # ============================================

    # --- ECG filtrada completa ---
    plt.figure(figsize=(18,5))
    plt.plot(t, x_f, color="#FF00FF")
    plt.title("ECG Filtrada (IIR) — Fucsia")
    plt.xlabel("Tiempo (s)")
    plt.ylabel("Amplitud (a.u.)")
    plt.grid()
    plt.show()

    # ---------------------------
    # SEGMENTO 1 — TODAS LAS GRÁFICAS
    # ---------------------------

    plt.figure(figsize=(18,6))
    plt.plot(seg1, color="#FF00FF")
    plt.plot(p1, seg1[p1], 'ro')
    plt.title("Segmento 1 — Señal Filtrada + R-peaks (Fucsia)")
    plt.grid()
    plt.show()

    plt.figure(figsize=(18,5))
    plt.plot(integ1, color="#FF00FF")
    plt.title("Integración Pan-Tompkins — Segmento 1")
    plt.grid()
    plt.show()

    plt.figure(figsize=(7,5))
    plt.hist(rr1*1000, bins=30, color="#FF00FF", alpha=0.8)
    plt.title("Histograma RR — Segmento 1")
    plt.grid()
    plt.show()

    if len(rr1)>=2:
        plt.figure(figsize=(6,6))
        plt.scatter(rr1[:-1]*1000, rr1[1:]*1000, color="#FF00FF", alpha=0.7)
        plt.title("Poincaré — Segmento 1")
        plt.grid()
        plt.show()

```
Se generaron las gráficas correspondientes a la visualización del procesamiento de la señal ECG. Primero se creó la gráfica de la señal filtrada completa utilizando el filtro IIR. Posteriormente se graficó el Segmento 1, mostrando tanto la señal filtrada como los picos R detectados. También se incluyó la gráfica de la señal integrada utilizada en la detección de picos bajo el esquema Pan-Tompkins. Se construyó el histograma de los intervalos R-R del Segmento 1 y, cuando fue posible, se generó el diagrama de Poincaré para este mismo segmento. Todas las gráficas fueron representadas en color fucsia para mantener consistencia visual en el análisis.<br> 

```
    # ---------------------------
    # SEGMENTO 2 — MISMAS GRÁFICAS
    # ---------------------------

    plt.figure(figsize=(18,6))
    plt.plot(seg2, color="#FF00FF")
    plt.plot(p2, seg2[p2], 'ro')
    plt.title("Segmento 2 — Señal Filtrada + R-peaks (Fucsia)")
    plt.grid()
    plt.show()

    plt.figure(figsize=(18,5))
    plt.plot(integ2, color="#FF00FF")
    plt.title("Integración Pan-Tompkins — Segmento 2")
    plt.grid()
    plt.show()

    plt.figure(figsize=(7,5))
    plt.hist(rr2*1000, bins=30, color="#FF00FF", alpha=0.8)
    plt.title("Histograma RR — Segmento 2")
    plt.grid()
    plt.show()

    if len(rr2)>=2:
        plt.figure(figsize=(6,6))
        plt.scatter(rr2[:-1]*1000, rr2[1:]*1000, color="#FF00FF", alpha=0.7)
        plt.title("Poincaré — Segmento 2")
        plt.grid()
        plt.show()

    return {
        "t": t, "x": x, "x_f": x_f,
        "seg1": seg1, "seg2": seg2,
        "p1": p1, "p2": p2,
        "rr1": rr1, "rr2": rr2,
        "mean1_ms": mean1, "sdnn1_ms": sdnn1,
        "mean2_ms": mean2, "sdnn2_ms": sdnn2
    }
 
```
Se generaron las gráficas correspondientes al segundo segmento de la señal ECG. Se visualizó la señal filtrada junto con los picos R detectados, la señal integrada del método Pan-Tompkins, el histograma de los intervalos R-R y el diagrama de Poincaré para este segmento. Finalmente, se retornaron las variables principales del procesamiento, incluyendo el tiempo, la señal original y filtrada, los dos segmentos, los picos detectados, los intervalos R-R y las métricas de HRV (media y SDNN) para ambos segmentos.<br>

```
# ============================================
# 7. EJECUTAR
# ============================================
results = process_ecg_file('/content/drive/MyDrive/SEÑAL.csv')

```
Se generaron todas las gráficas correspondientes al Segmento 2 utilizando la señal filtrada. Se visualizó la señal junto con los picos R detectados, la señal integrada tipo Pan-Tompkins, el histograma de los intervalos R-R y el diagrama de Poincaré para este segmento. Finalmente, se organizó y retornó un diccionario con todas las variables procesadas, incluyendo los segmentos, picos R, intervalos R-R y los valores de media y SDNN para ambos segmentos. <br>
