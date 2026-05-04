<p align="center">
  <img src="skyedge_icon.png" alt="SkyEdge" width="160"/>
</p>

<h1 align="center">SkyEdge RX</h1>

<p align="center">
  <b>OFDM audio receiver for stratospheric HAB missions</b><br/>
  <i>Odbiornik audio OFDM dla misji balonów stratosferycznych</i>
</p>

<p align="center">
  <a href="https://github.com/SP5LOT/skyedge-rx/releases/latest">
    <img src="https://img.shields.io/badge/download-skyedge__rx.exe-00C8FF?style=for-the-badge" alt="Download"/>
  </a>
  &nbsp;
  <a href="https://skyedge.pl">
    <img src="https://img.shields.io/badge/web-skyedge.pl-00E8C0?style=for-the-badge" alt="skyedge.pl"/>
  </a>
</p>

---

## 🇵🇱 Polski

**SkyEdge RX** to aplikacja Windows do odbioru obrazów i plików nadawanych z balonów stratosferycznych HAB w trybie OFDM przez radio FM (np. SA828) i tor audio komputera.

Aplikacja słucha wejścia audio (mikrofon, virtual cable, line-in z radia), demoduluje sygnał OFDM mieszczący się w paśmie głosowym FM, dekoduje pakiety zabezpieczone kodem Reed-Solomon erasure (CRS) i odtwarza oryginalne pliki — zdjęcia JPG/PNG, dokumenty PDF, archiwa, logi telemetryczne.

### Obsługiwane tryby OFDM

| Tryb | Modulacja | Pasmo  | Uwagi |
|:----:|:---------:|:------:|:------|
| 6    | 8PSK      | 2700 Hz | |
| 7    | 8PSK      | 2500 Hz | |
| 8    | QPSK      | 2500 Hz | |
| 9    | QPSK      | 2250 Hz | |
| 10   | 8PSK      | 3200 Hz | szersze pasmo, większy throughput |
| 11   | 8PSK      | 2400 Hz | **default** — sprawdzony w stratosferze |
| 12   | QPSK      | 2400 Hz | bardziej odporny na słaby SNR |
| 13   | QPSK      | 1600 Hz | wąskopasmowy, najodporniejszy |

Tryb wykrywany jest automatycznie z nagłówka ramki — nadawca może zmieniać modulację bez konfiguracji odbiornika.

### Funkcje
- 🛰️ **Odbiór live** z wejścia audio (MME / DirectSound, 48 kHz mono)
- 📡 **Auto-detekcja trybu OFDM** — 8PSK i QPSK, mode 6–13
- 🔧 **CRS erasure coding** — toleruje utratę ramek przy zaniku sygnału
- 🎨 **Mission Control HUD** — wskaźnik SNR, konstelacja IQ, widmo OFDM, fala
- 💾 **Auto-zapis** dekodowanych plików z oryginalnymi nazwami
- 📂 **Plik WAV** — odtwarzanie nagranych transmisji z dysku

### Pobranie
Najnowszy build: **[Releases →](https://github.com/SP5LOT/skyedge-rx/releases/latest)**

`skyedge_rx.exe` to pojedynczy plik wykonywalny — nie wymaga instalacji. Uruchom, wybierz wejście audio i czekaj na transmisję.

### Wymagania
- Windows 10 / 11 (x64)
- Wejście audio (line-in z radia FM, virtual cable, mikrofon przy głośniku)
- ~200 MB wolnej pamięci

---

## 🇬🇧 English

**SkyEdge RX** is a Windows application for receiving images and files transmitted from stratospheric HAB balloons over FM radio (e.g. SA828) using OFDM-in-audio modulation.

The app listens to an audio input (microphone, virtual cable, line-in from a radio), demodulates an OFDM signal that fits inside FM voice bandwidth, decodes Reed-Solomon erasure-coded chunks (CRS) and reconstructs the original files — JPG/PNG images, PDFs, archives, telemetry logs.

### Supported OFDM modes

| Mode | Modulation | Bandwidth | Notes |
|:----:|:----------:|:---------:|:------|
| 6    | 8PSK       | 2700 Hz   | |
| 7    | 8PSK       | 2500 Hz   | |
| 8    | QPSK       | 2500 Hz   | |
| 9    | QPSK       | 2250 Hz   | |
| 10   | 8PSK       | 3200 Hz   | widest, highest throughput |
| 11   | 8PSK       | 2400 Hz   | **default** — flight-proven from the stratosphere |
| 12   | QPSK       | 2400 Hz   | more robust at low SNR |
| 13   | QPSK       | 1600 Hz   | narrowband, most robust |

The mode is auto-detected from the frame header — the transmitter can switch modulation without reconfiguring the receiver.

### Features
- 🛰️ **Live audio reception** (MME / DirectSound input, 48 kHz mono)
- 📡 **Auto OFDM mode detection** — 8PSK and QPSK, modes 6–13
- 🔧 **Reed-Solomon erasure coding** — recovers files even with lost frames
- 🎨 **Mission Control HUD** — SNR ring, IQ constellation, OFDM spectrum, waveform
- 💾 **Auto-save** of decoded files with original filenames
- 📂 **WAV playback** — decode recorded transmissions from disk

### Download
Latest build: **[Releases →](https://github.com/SP5LOT/skyedge-rx/releases/latest)**

`skyedge_rx.exe` is a single self-contained executable — no installation needed. Run it, pick an audio input, wait for the transmission.

### Requirements
- Windows 10 / 11 (x64)
- Audio input (line-in from FM radio, virtual cable, or just a mic next to a speaker)
- ~200 MB free RAM

---

## 🙏 Credits / Podziękowania

The OFDM modem at the heart of this receiver — and frankly the entire reason this project exists — is the brilliant work of **Ahmet Inan (DG3LV)** and the **[aicodix](https://github.com/aicodix)** team.

Their open-source [`aicodix/modem`](https://github.com/aicodix/modem) is a complete OFDM-over-audio modem optimized for narrow-band FM voice channels, supporting both 8PSK and QPSK modulations from 1.6 kHz to 3.2 kHz of bandwidth. Without it, sending images from a balloon over a Baofeng-class radio would not be feasible. They also publish the [`aicodix/android`](https://github.com/aicodix/android) Android app — *aicodix Modem* — which lets anyone receive the same signal directly on a phone held near the radio's speaker.

**SkyEdge RX is just a friendly desktop wrapper around their decoder, with a HAB-themed HUD on top.** All credit for the OFDM signal processing, FEC scheme, and modem CLI tools (`encode_old.exe`, `decode_old.exe`, `encode_crs.exe`, `decode_crs.exe`) belongs to aicodix.

If you build something similar — please credit them too.

---

Cały kunszt OFDM w tym odbiorniku — i właściwie cały powód, dla którego ten projekt w ogóle istnieje — to zasługa **Ahmeta Inana (DG3LV)** i zespołu **[aicodix](https://github.com/aicodix)**.

Ich otwartoźródłowy [`aicodix/modem`](https://github.com/aicodix/modem) to kompletny modem OFDM po audio, zoptymalizowany pod wąskopasmowe kanały FM głosowe, obsługujący zarówno modulację 8PSK jak i QPSK w paśmie od 1,6 kHz do 3,2 kHz. Bez tego wysyłanie zdjęć z balonu po radiu klasy Baofeng nie miałoby szans. Wydali też appkę na Androida [`aicodix/android`](https://github.com/aicodix/android) — *aicodix Modem* — która pozwala dowolnej osobie odebrać ten sam sygnał bezpośrednio na telefonie przyłożonym do głośnika radia.

**SkyEdge RX to po prostu przyjazna nakładka desktopowa na ich dekoder, z HUD-em w stylu Mission Control.** Cała magia OFDM, schemat FEC i narzędzia modemu (`encode_old.exe`, `decode_old.exe`, `encode_crs.exe`, `decode_crs.exe`) to ich dzieło.

Jeśli budujesz coś podobnego — proszę, też ich uznaj.

---

## 📡 About / O projekcie

Built by **Tomek Błażej, SP5LOT** — **SKYEDGE Team**, Warsaw, Poland.

Stratospheric HAB missions, software-defined radio, RF engineering.

🌐 **Web**: [skyedge.pl](https://skyedge.pl)  
📧 **Contact**: sp.five.lot@gmail.com

---

<p align="center">
  <sub>SKYEDGE Team · Warsaw, Poland · 2026</sub>
</p>
