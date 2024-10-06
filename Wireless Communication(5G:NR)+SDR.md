# Notes on 5G (Coursera Course)

## Index
1. [Introduction to Wireless Communication](#introduction-to-wireless-communication)
2. [Modulation and Demodulation](#modulation-and-demodulation)
3. [Signal Processing Steps](#signal-processing-steps)
4. [Transmission Issues](#transmission-issues)
5. [Radio Channels and Bandwidth](#radio-channels-and-bandwidth)
6. [5G Overview](#5g-overview)
7. [5G Network Architecture](#5g-network-architecture)
8. [5G Techniques and Technologies](#5g-techniques-and-technologies)
9. [5G Cloud Compatibility](#5g-cloud-compatibility)
10. [mmWave Spectrum](#mmwave-spectrum)

## Introduction to Wireless Communication
- **Wireless Communication** does not need a physical medium like internet cables, etc.
- Requires a **Transmitter** and **Receiver** (both with antennas).
- **RF (Radio Frequencies)**: Frequencies of wireless signals lie within the radio range.

## Modulation and Demodulation
- **Modulation**: The process by which the transmitter encodes information into a signal to be carried to the receiver.
- **Modulator + Demodulator = MODEM**: 
  - **Modulation** happens at the transmitter.
  - **Demodulation** happens at the receiver to decode the information from the signal.

## Signal Processing Steps
- **Upconversion**: Occurs at the transmitter; it shifts the signal to a higher frequency for transmission.
- **Downconversion**: Happens at the receiver; it shifts the signal back to a lower frequency for processing.

## Transmission Issues
- **Pathloss**: Energy lost during transmission.
- **Noise**: Random signals that affect the intended signal.
- **Interference**: When multiple transmitters on the same frequency emit signals that can overlap.

## Radio Channels and Bandwidth
- **Radio Channel**: A slice of the radio spectrum; bandwidth is a precious resource managed by entities like the **FCC**.
- **Multiple Access**: When many users attempt to access the same channel simultaneously, an algorithm allocates resources to each user based on their needs.
- **Spectral Efficiency**: A measure of how efficiently the spectrum allocated to a specific channel is being used.

## 5G Overview
- **5G New Radio (NR)**: The latest generation of mobile communication technology.
  - Aims to provide much higher bit rates and data speeds than previous generations (4G LTE).
  - Higher bandwidth is used to support increased demand (e.g., virtual reality, cloud computing, high-speed travel up to 500 km/h).
  - **Lower latency** (faster response times) and better spectral efficiency.
  - Cost is lower compared to previous systems.

## 5G Network Architecture
- **gNodeB Towers**: New towers deployed for 5G, based on 4G towers.
- **Core Network**:
  - **Control messages**: Background processes ensuring content delivery.
  - **User plane**: Content visible on your device.
  - Includes components like **AMF**, **SMF**, and **UPF**.
- **NSA (Non-Standalone) 5G Deployment**: 
  - Uses gNodeB towers in high-demand areas (e.g., airports, stadiums).
  - Relies on a 4G core network, so no end-to-end 5G connectivity.
  - Requires newer phones that support both 5G and 4G.
- **Data Network**: Provides operator services to users.

## 5G Techniques and Technologies
- **OFDM (Orthogonal Frequency Division Multiplexing)**: Divides a wideband channel into multiple smaller narrowbands.
- **Flexible Slot-Based Framework**: Adjusts channel size based on incoming traffic.
- **Channel Coding**: Reduces the impact of noise, interference, and pathloss.
- **Massive MIMO (Multiple Input, Multiple Output)**: 
  - Utilizes multiple transmitters and receivers using the same frequency channel.
  - Signals are encoded differently to prevent interference.
  - **Massive MIMO** is a larger-scale implementation of MIMO, allowing more simultaneous data streams.

## 5G Cloud Compatibility
- 5G aims to be more **cloud-compatible**:
  - Data can be stored and managed on the cloud.
  - In case of hardware issues, the data remains safe.

## mmWave Spectrum
- **39 GHz Band**: Part of the **mmWave spectrum** used by 5G.
  - **mmWave** improves data rates and reduces latency.
  - However, it compromises on **range of coverage** and **penetration** in low coverage areas.
  - **mm** refers to the millimeter wavelength of the signals.
