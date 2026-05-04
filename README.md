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
</p>

---

## 🇵🇱 Polski

**SkyEdge RX** to aplikacja Windows do odbioru obrazów i plików nadawanych z balonów stratosferycznych HAB w trybie OFDM przez radio FM (np. SA828) i tor audio komputera.

Aplikacja słucha wejścia audio (mikrofon, virtual cable, line-in z radia), demoduluje sygnał OFDM 8PSK 2400 Hz w paśmie głosowym FM, dekoduje pakiety zabezpieczone kodem Reed-Solomon erasure (CRS) i odtwarza oryginalne pliki — zdjęcia JPG/PNG, dokumenty PDF, archiwa, logi telemetryczne.

### Funkcje
- 🛰️ **Odbiór live** z wejścia audio (MME / DirectSound, 48 kHz mono)
- 📡 **Dekoder OFDM** w trybach 8PSK i QPSK (mode 6–13, default 8PSK 2400 Hz — sprawdzony w stratosferze)
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

### Test bez radia
Można odtworzyć przykładowy WAV z innego komputera/telefonu przez kabel audio i sprawdzić odbiór. Aplikacja `SkyEdge WAV Generator` (osobne repo) generuje takie WAV-y do testów.

---

## 🇬🇧 English

**SkyEdge RX** is a Windows application for receiving images and files transmitted from stratospheric HAB balloons over FM radio (e.g. SA828) using OFDM-in-audio modulation.

The app listens to an audio input (microphone, virtual cable, line-in from a radio), demodulates the OFDM 8PSK 2400 Hz signal that fits inside FM voice bandwidth, decodes Reed-Solomon erasure-coded chunks (CRS) and reconstructs the original files — JPG/PNG images, PDFs, archives, telemetry logs.

### Features
- 🛰️ **Live audio reception** (MME / DirectSound input, 48 kHz mono)
- 📡 **OFDM decoder** for 8PSK and QPSK modes (6–13, default 8PSK 2400 Hz — flight-proven from the stratosphere)
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

### Test without a radio
Play a generated WAV from another computer/phone over an audio cable. The companion `SkyEdge WAV Generator` app produces such WAV files for testing.

---

## 🙏 Credits / Podziękowania

The OFDM modem at the heart of this receiver — and frankly the entire reason this project exists — is the brilliant work of **Ahmet Inan (DG3LV)** and the **[aicodix](https://github.com/aicodix)** team.

Their open-source [`aicodix/modem`](https://github.com/aicodix/modem) is a complete OFDM-over-audio modem optimized for narrow-band FM voice channels. Without it, sending images from a balloon over a Baofeng-class radio would not be feasible. They also publish the [`aicodix/android`](https://github.com/aicodix/android) Android app — *aicodix Modem* — which lets anyone receive the same signal directly on a phone held near the radio's speaker.

**SkyEdge RX is just a friendly desktop wrapper around their decoder, with a HAB-themed HUD on top.** All credit for the OFDM signal processing, FEC scheme, and modem CLI tools (`encode_old.exe`, `decode_old.exe`, `encode_crs.exe`, `decode_crs.exe`) belongs to aicodix.

If you build something similar — please credit them too.

---

Cały kunszt OFDM w tym odbiorniku — i właściwie cały powód, dla którego ten projekt w ogóle istnieje — to zasługa **Ahmeta Inana (DG3LV)** i zespołu **[aicodix](https://github.com/aicodix)**.

Ich otwartoźródłowy [`aicodix/modem`](https://github.com/aicodix/modem) to kompletny modem OFDM po audio, zoptymalizowany pod wąskopasmowe kanały FM głosowe. Bez tego wysyłanie zdjęć z balonu po radiu klasy Baofeng nie miałoby szans. Wydali też appkę na Androida [`aicodix/android`](https://github.com/aicodix/android) — *aicodix Modem* — która pozwala dowolnej osobie odebrać ten sam sygnał bezpośrednio na telefonie przyłożonym do głośnika radia.

**SkyEdge RX to po prostu przyjazna nakładka desktopowa na ich dekoder, z HUD-em w stylu Mission Control.** Cała magia OFDM, schemat FEC i narzędzia modemu (`encode_old.exe`, `decode_old.exe`, `encode_crs.exe`, `decode_crs.exe`) to ich dzieło.

Jeśli budujesz coś podobnego — proszę, też ich uznaj.

---

## 📡 About / O projekcie

Built by **Tomek Błażej, SP5LOT** for [Fundacja SkyEdge](https://skyedge.foundation) — a Polish foundation running stratospheric HAB missions.

Project website: TBD &nbsp;·&nbsp; Contact: tomaszblazej@gmail.com

---

<p align="center">
  <sub>SkyEdge Foundation · Warsaw, Poland · 2026</sub>
</p>
