THEIHS SNIFFER
# Sniffer

Windows üzerinde Scapy ve PyQt5 kullanarak basit bir ağ koklayıcı.

![Örnek](/sample_pic/overall_sample.gif "Örnek")

<!-- TOC -->

- [Sniffer](#sniffer)
    - [Başlarken](#başlarken)
        - [Gereksinimler](#gereksinimler)
        - [Opsiyonel](#opsiyonel)
    - [Kullanım](#kullanım)
    - [Özellikler](#özellikler)
        - [Ağ arabirimleri, Protokol, Kaynak, Hedef, Kaynak Portu ve Hedef Portu filtreleme.](#ağ-arabirimleri-protokol-kaynak-hedef-kaynak-portu-ve-hedef-portu-filtreleme)
        - [Seçili paket bilgilerini dosyalara kaydetme ve hatta panoya kopyalama.](#seçili-paket-bilgilerini-dosyalara-kaydetme-ve-hatta-panoya-kopyalama)
        - [TCP/IP yeniden birleştirme ve dosyalara kaydetme.](#tcpip-yeniden-birleştirme-ve-dosyalara-kaydetme)
        - [HTTP İstek/Cevap bilgileri](#http-istekcevap-bilgileri)
        - [Arama çubuğu işleri kolaylaştırır](#arama-çubuğu-i̇şleri-kolaylaştırır)
        - [OC Modu](#oc-modu)
        - [Ağ Hızı](#ağ-hızı)
        - [WireShark benzeri Renk Teması](#wireshark-benzeri-renk-teması)
        - [(Opsiyonel) Fare geçtiğinde kısa ve etkili bilgi.](#opsiyonel-fare-geçtiğinde-kısa-ve-etkili-bilgi)
    - [Yapılacaklar](#yapılacaklar)

<!-- /TOC -->

## Başlarken

Hepsini indirin ve main.py dosyasını çalıştırın.

### Gereksinimler

- **Windows 10**
- Python 3.6
- Çoklu işleme amacıyla kullanılan modifiye edilmiş [scapy3k](https://github.com/phaethon/scapy). Doğrudan buradan kullanın.
- ANSI ESCAPE Sekansını HTML CSS'ye parse etmek için kullanılan [ansi2html](https://github.com/ralphbean/ansi2html).
- Sistem seviyesinde alınan paket miktarını tespit etmek ve ağ hızını hesaplamak için kullanılan [psutil](https://github.com/giampaolo/psutil).
- HTTP Cevabını parse etmek için kullanılan [urllib3](https://github.com/shazow/urllib3).
- GUI için [PyQt5](https://riverbankcomputing.com/software/pyqt/download5).
- [Win10Pcap(Önerilen)](http://www.win10pcap.org/) veya bazı paketlerin eksik olmasına neden olabilecek Npcap yüklenmesi gerekiyor.
Yalnızca Windows kullanıcıları için test edilmiş ve modifiye edilmiştir.

### Opsiyonel

- Ham paketlerden kısa bilgi parse etmek için kullanılan [pyshark](https://github.com/KimiNewt/pyshark).

   - İpuçları:

      Ancak, en son sürüm Win10'da iyi çalışmıyor, bu yüzden kısa ve etkili bilgiye ihtiyaç duyuyorsanız 0.3.6.2 sürümü kullanılmalı ve önerilmektedir.

## Kullanım

THEIHS SNIFFER
# Sniffer

Simple sniffer using Scapy and PyQt5 on Windows.

![Sample](/sample_pic/overall_sample.gif "Sample")

<!-- TOC -->

- [Sniffer](#sniffer)
    - [Getting Started](#getting-started)
        - [Prerequisites](#prerequisites)
        - [Optional](#optional)
    - [Usage](#usage)
    - [Feature](#feature)
        - [Filter on Network interfaces, Protocol, Src, Dst, Sport and Dport.](#filter-on-network-interfaces-protocol-src-dst-sport-and-dport)
        - [Save selected packet(s) information to files, and even copy to clipboard.](#save-selected-packets-information-to-files-and-even-copy-to-clipboard)
        - [TCP/IP reassembly and save them to files.](#tcpip-reassembly-and-save-them-to-files)
        - [HTTP Request/Response information](#http-requestresponse-information)
        - [Search bar makes things easier](#search-bar-makes-things-easier)
        - [OC Mode](#oc-mode)
        - [Network Speed](#network-speed)
        - [Color Theme like WireShark](#color-theme-like-wireshark)
        - [(Optional) Brief efficient information when mouse passes.](#optional-brief-efficient-information-when-mouse-passes)
    - [To Do](#to-do)

<!-- /TOC -->
## Getting Started

Just download them all and run main.py

### Prerequisites

- **Windows 10**
- Python 3.6
- Modified [scapy3k](https://github.com/phaethon/scapy) Used for multiprocessing purposes. Just use directly from here.
- [ansi2html](https://github.com/ralphbean/ansi2html)  Used to parse ANSI ESCAPE Sequence to html css.
- [psutil](https://github.com/giampaolo/psutil)	Used to detect packet received amount in system level to calculate network speed.
- [urllib3](https://github.com/shazow/urllib3)  Used to parse HTTP Response
- [PyQt5](https://riverbankcomputing.com/software/pyqt/download5) GUI
- Need to install [Win10Pcap(Recommended)](http://www.win10pcap.org/), Npcap(might have slight issue of missing certain packets).
Only test and modify the lib concerning Windows users.

### Optional
-  [pyshark](https://github.com/KimiNewt/pyshark) Used to parse brief information from raw packets.

   - Tips:

      However, the latest version works not well on Win10, so version 0.3.6.2 is only used and recommended if the the brief and efficient info for packet is what you need.

## Usage
```
pip install -r requirements.txt
python main.py

#Optional lib `pyshark` for parsing brief info from packet.
#pyshark version 0.3.6.2 is the only one that works.
pip install pyshark==0.3.6.2
```

## Feature

Multiple features in this project.

### Filter on Network interfaces, Protocol, Src, Dst, Sport and Dport.

Choose the filter anytime you like and then click the start button twice to continue sniffing.(have to stop and start to take effect)

### Save selected packet(s) information to files, and even copy to clipboard.

Select one packet, or multiple packets. After using right clicks, you can save them into a txt file with readable format, or even copy
them into your clipboard(short-cut keys Ctrl-S,Ctrl-C).


### TCP/IP reassembly and save them to files.

Select one packet, and it will automatically find related packets and reassemble them.
If the total fragments number is too big, it will give you the option to reassemble and decode it or not.
Remember that all the related fragments will be displayed immediately no matter what.
After that processing, you are welcome to click the `Reassembly` button below on the status to convert them into one entire file.
Only tested in FTP Transmission, HTML reassembly and ICMP(ping), and the file size can be up to 15MB (might take certain time processing to GUI).
New feature is added to show the whole size number after reassembly to have a quick peak of the whole process.




### HTTP Request/Response information

After reassembling the TCP packet, next move is to show you the whole information in HTTP layer, espeically for HTML or image. You will be aware of how dangerous it is when the protocol is HTTP because what you have input is always transferred without any protection, or you can preview every image during the http transmission.

- sample of sniffing username and password from HTTP Request(POST):



- sample of preview images from HTTP Response:



### Search bar makes things easier

Using search bar wisely can actually save a lot of time.
Keywords are searched in whole packet's hex or decoded by UTF-8 and GB2312,which is very convenient to find http headers of filename. The new feature is the `advanced search` that enables user to search use filter. Here is the format of `advanced seach`.

```
[-p]  <protocol>
[-s]  <ipsrc>  [-d]  <ipdst>
[-sp] <sport>  [-dp] <dport>
keyword

#search keywords `image`(ordinary search)
image

#search packet of which tcp sport==80 and keyword 'image'(advanced search)
-p tcp -sp 80 image
```


### OC Mode

The default OC mode will never let you down when an additional dedicated process is used for listening and sniffing.
However, it is very CPU-consuming, but you can turn it off any time (have to stop and start to take effect)

### Network Speed

The ultimate style of Network Speed uses the API of psutil which is extremely accurate and responsive.


### Color Theme like WireShark

Every packet is sorted by the default color theme of wireshark. Default On. Using "Ctrl+F" to turn off/on.
ADD Mouse entering and leaving event for each row makes the UI more colorful and better.

### (Optional) Brief efficient information when mouse passes.

Thanks to the API of `pyshark`, the real information that contains a lot of useful details can be feeded whenever your mouse passes on. Remember it's only activated when `pyshark(version 0.3.6.2)` is installed and the current mode is `STOP`.




## To Do
-  Find a way less CPU consuming that can capture almost all packets instead of a dedicated process on it.
-  Using `WinDump` in `scapy` and `LiveRingCapture` in `pyshark` should to improve the performance.
-  Make it compatible in linux as well.


<img width="1163" alt="Ekran Resmi 2024-06-11 06 46 40" src="https://github.com/hasankilic0663/THEIHS_Sniffer-Neo4j/assets/101570706/4d05e8e5-0252-49b8-bcc6-e7a9a142dbed">
[Proje Sunumulast.pdf](https://github.com/user-attachments/files/15781878/Proje.Sunumulast.pdf)


[PROJENİN AMACI Geliştirilen program, ağ trafiğini gerçek zamanlı olarak yakalayarak analiz eder ve eld.pdf](https://github.com/user-attachments/files/15781883/PROJENIN.AMACI.Gelistirilen.program.ag.trafigini.gercek.zamanli.olarak.yakalayarak.analiz.eder.ve.eld.pdf)
<img width="493" alt="Ekran Resmi 2024-06-11 06 46 13" src="https://github.com/hasankilic0663/THEIHS_Sniffer-Neo4j/assets/101570706/479c7c65-0aa6-4506-8ad3-6e98ae0b7a60">

