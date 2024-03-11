## Datasets

This folder contains the datasets made available for the _Hackathon SMARTNESS / 5G Dataset Challenge_.

For the Hackathon, data on 5G network usage in Brazil was collected. The data collection methodology was based on field tests. The experiments were conducted on a _Samsung S21 5G_.

Below, we list the two datasets produced and an auxiliary one. Each dataset has a Jupyter Notebook demonstrating an initial data exploration for participants to get to know the data structure.

# 🎬 Traffic Monitoring
YouTube has integrated in its various clients (Web, Web Mobile, IFrame, and iOS and Android applications) a tool for collecting user experience metrics. To identify the monitored metrics (which are the same in the other clients), we analyzed the YouTube Web code and the HAR request collections by Chrome DevTools.

To generate traffic data on the _Samsung S21 5G_, we played a playlist of high-resolution videos on YouTube Web Mobile, and the traffic metrics were intercepted by `PCAPdroid`: [https://github.com/emanuele-f/PCAPdroid](https://github.com/emanuele-f/PCAPdroid) and the `PCAPdroid-mitm`: [https://github.com/emanuele-f/PCAPdroid-mitm](https://github.com/emanuele-f/PCAPdroid-mitm) plugin to decrypt TLS packets.

> 🛠️ In the future, the experiment will use the YouTube application to represent a situation closer to the reality of mobile customers. For now, this has not been done yet because the YouTube application uses the QUIC protocol, which is not supported by the current version of the plugin, but will be supported in the next version: [https://github.com/mitmproxy/mitmproxy/blob/main/CHANGELOG.md#unreleased-mitmproxy-next](https://github.com/mitmproxy/mitmproxy/blob/main/CHANGELOG.md#unreleased-mitmproxy-next).

- Dados `youtube-qoe`: ./youtube-qoe (PCAPdroid collections)
- Data exploration / Jupyter Notebook: ./youtube-qoe.ipynb

<details>
<summary><b>How to collect data using PCAPdroid</b></summary>

## Configuring TLS decryption
- In the *Traffic inspection* section of the PCAPdroid settings (⚙️ icon in the upper right corner), enable *TLS decryption*
- The first time decryption is enabled, the menu for configuring the plugin will open. The steps include:
    1. Download and install the `PCAPdroid-mitm` addon
    2. Authorize PCAPdroid to control the addon
    3. Install the PCAPdroid Certificate Authority (CA)

## Initial Setup
- In the _Traffic inspection_ section of the PCAPdroid settings (⚙️ icon in the upper right corner), disable the _Full payload_ option
- In the _Capture_ section of the PCAPdroid settings, enable the _PCAPdroid trailer_ option
- Set the traffic capture format (_traffic dump format_) to _PCAP file_
- Select the application that will capture the traffic (in this case, the browser that will open YouTube Web Mobile. Example: Google Chrome, Firefox, Samsung Internet)

## Capture and export
- Enter the PCAPdroid application
- Select _Ready_
- Start generating traffic. At this point, you can leave the application
- ...
- To finish capturing traffic, enter PCAPdroid again
- Press the stop button (⬜ icon in the upper right corner)
- Press _OK_ in the dialog informing that the traffic has been saved
- If an SSL key file `sslkeylogfile.txt` is generated, a dialog will open to save it:
    - Go to the folder where the file should be saved, such as in `~/Download/PCAPdroid` (the same location where PCAP captures are saved)
    - Select the most recent PCAP capture file to copy its name (for easy identification later)
    - Edit the `.pcap` extension to `.txt` of the file to be saved
    - Save

## Merging `sslkeylogfile.txt` and `.pcap` into a single `.pcapng` file

To merge the two files `sslkeylogfile.txt` and `.pcap` into a single `.pcapng` file, we can use the command line program `editcap` (which can be obtained by installing `tshark`).

If the SSL key file and PCAP have the same name, simply use a variable with the capture name:
```bash
filename=PCAPdroid_17_Feb_02_19_56
editcap --inject-secrets tls,${filename}.txt ${filename}.pcap ${filename}.pcapng
```

Alternatively, we can specify the different names individually:
```bash
editcap --inject-secrets tls,sslkeylogfile_abc.txt captura_abc.pcap captura_e_sslkeys_abc.pcapng
```

Once we have the `.pcapng` files, we pre-process them into a more usable format. To do this, we run the _scripts_: ../scripts/ below:
```bash
# transforms .pcapng files to .json
./scripts/extract_youtube_qoe_urls.py -g '*.pcapng'

# transforms .json files to pandas Dataframes in .pickle format
./scripts/youtube_qoe_urls_preprocessing.py -g '*.json'
```

</details>

# 📶 Mobile Network Monitoring

The network metrics were collected by the G-NetTrack Pro tool (manual: [https://gyokovsolutions.com/manual-g-nettrack/#:~:text=Here%20is%20description%20of%20logfile%20columns](https://gyokovsolutions.com/manual-g-nettrack/#:~:text=Here%20is%20description%20of%20logfile%20columns)) on a route with Claro 5G coverage, such as downtown São Paulo, Paulista Avenue, Butantã, and surroundings.

- Dados `g-nettrack`: ./g-nettrack-pro
- Data exploration / Jupyter Notebook: ./g-nettrack-pro.ipynb

# 📡 ERBs Mosaico/Anatel (auxiliary)

In conjunction with traffic and mobile network data, we can also perform **data enrichment** with other datasets, such as using Anatel's Mosaico, which contains information on all telecommunications stations (ERBs) registered in Brazil. Among the data made available by Mosaico, include: the technologies and equipment used, the transmission and reception frequencies, the geographical location of the stations, the licensing and validity dates, information on the owners of the stations, among others.

- Dados `mosaico`: ./mosaico
- Data exploration / Jupyter Notebook: ./mosaico.ipynb