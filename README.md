# Networking-Concepts

# Pendahuluan

Pernahkah Anda bertanya-tanya mengapa Anda membutuhkan alamat IP untuk mengakses internet? Benarkah alamat IP dapat mengidentifikasi pengguna secara unik? Apakah Anda penasaran ingin mempelajari seperti apa siklus hidup sebuah paket data? Jika jawabannya ya, mari kita mulai!

Ruangan ini adalah ruangan pertama dari serangkaian empat ruangan yang didedikasikan untuk memperkenalkan pengguna pada konsep-konsep jaringan yang penting dan protokol jaringan yang paling umum:

Konsep Jaringan (ruangan ini)
Dasar-Dasar Jaringan
Protokol Inti Jaringan
Protokol Keamanan Jaringan

Tujuan pembelajaran
Setelah menyelesaikan ruangan ini, Anda akan mempelajari hal-hal berikut:

Model jaringan ISO OSI
Alamat IP, subnet, dan perutean
TCP , UDP , dan nomor port
Cara terhubung ke port TCP yang terbuka dari baris perintah

# Osi Model / Model OSI
Sebelum kita mulai, perlu dicatat bahwa model OSI mungkin awalnya tampak rumit. Jangan khawatir jika Anda menemukan akronim yang membingungkan, karena kami memberikan contoh lapisan model OSI. Kami jamin bahwa setelah Anda menyelesaikan modul ini, tugas ini akan terasa sangat mudah.

Model OSI (Open Systems Interconnection) adalah model konseptual yang dikembangkan oleh Organisasi Internasional untuk Standardisasi (ISO) yang menjelaskan bagaimana komunikasi seharusnya terjadi dalam jaringan komputer. Dengan kata lain, model OSI mendefinisikan kerangka kerja untuk komunikasi jaringan komputer. Meskipun model ini bersifat teoritis, penting untuk mempelajari dan memahaminya karena membantu memahami konsep jaringan pada tingkat yang lebih dalam. Model OSI terdiri dari tujuh lapisan:

Lapisan Fisik
Lapisan Tautan Data
Lapisan Jaringan
Lapisan Transportasi
Lapisan Sesi
Lapisan Presentasi
Lapisan Aplikasi
Penomoran dimulai dengan lapisan fisik sebagai lapisan 1, sedangkan lapisan teratas, lapisan aplikasi, adalah lapisan 7. Untuk membantu Anda mengingat lapisan dari bawah ke atas, Anda dapat menggunakan mnemonik seperti “Please Do Not Throw Spinach Pizza Away” (Jangan Buang Pizza Bayam). Anda dapat mencari di internet untuk akronim lain yang mudah diingat jika ini membantu Anda menghafalnya. Mengingat lapisan model OSI beserta nomor lapisannya sangat penting; jika tidak, Anda akan kesulitan memahami istilah seperti “saklar lapisan 3” atau “ firewall lapisan 7 ”.

<img width="1077" height="800" alt="image" src="https://github.com/user-attachments/assets/ffeaeaea-cef8-4cf3-a590-9a46a082cb82" />

# Lapisan 1: Lapisan Fisik
Lapisan fisik, yang juga disebut lapisan 1, berkaitan dengan koneksi fisik antar perangkat; ini termasuk media, seperti kabel, dan definisi angka biner 0 dan 1. Transmisi data dapat dilakukan melalui sinyal listrik, optik, atau nirkabel. Oleh karena itu, kita membutuhkan kabel data atau antena, tergantung pada media fisik yang kita gunakan.

Selain kabel Ethernet, seperti yang ditunjukkan pada ilustrasi di bawah ini, dan kabel serat optik, contoh media lapisan fisik lainnya meliputi pita frekuensi radio WiFi, yaitu pita 2,4 GHz, pita 5 GHz, dan pita 6 GHz.

<img width="1140" height="800" alt="image" src="https://github.com/user-attachments/assets/a8710f19-5ab0-46af-a33f-5d44926d8f7d" />

# Lapisan 2: Lapisan Tautan Data
Lapisan fisik mendefinisikan media untuk mengirimkan sinyal kita. Lapisan tautan data, yaitu lapisan 2, mewakili protokol yang memungkinkan transfer data antar node pada segmen jaringan yang sama. Mari kita sederhanakan. Lapisan tautan data menjelaskan kesepakatan antara berbagai sistem pada segmen jaringan yang sama tentang cara berkomunikasi. Segmen jaringan mengacu pada sekelompok perangkat jaringan yang menggunakan media atau saluran bersama untuk transfer informasi. Misalnya, pertimbangkan kantor perusahaan dengan sepuluh komputer yang terhubung ke switch jaringan; itu adalah segmen jaringan.

Contoh lapisan 2 meliputi Ethernet, yaitu 802.3, dan WiFi, yaitu 802.11. Alamat Ethernet dan WiFi terdiri dari enam byte. Alamat tersebut disebut alamat MAC, di mana MAC merupakan singkatan dari Media Access Control. Alamat tersebut biasanya dinyatakan dalam format heksadesimal dengan titik dua yang memisahkan setiap dua digit heksadesimal (satu byte). Tiga byte paling kiri mengidentifikasi vendor.

<img width="1051" height="517" alt="image" src="https://github.com/user-attachments/assets/2adffde2-3e36-4ece-bc57-d8df8a4cad5a" />

Dalam komunikasi jaringan nyata melalui Ethernet atau WiFi, kita mengharapkan untuk melihat dua alamat MAC di setiap frame. Paket pada tangkapan layar di bawah ini menunjukkan:

Alamat tautan data tujuan (alamat MAC) disorot dengan warna kuning.
Alamat tautan data sumber (alamat MAC) disorot dengan warna biru.
Bagian yang tersisa menunjukkan data yang sedang dikirim.

<img width="1640" height="760" alt="image" src="https://github.com/user-attachments/assets/73261c5c-3c66-488c-82a1-87b514c88e02" />

# Lapisan 3: Lapisan Jaringan
Lapisan tautan data berfokus pada pengiriman data antara dua node pada segmen jaringan yang sama. Lapisan jaringan, yaitu lapisan 3, berkaitan dengan pengiriman data antara jaringan yang berbeda. Dalam istilah yang lebih teknis, lapisan jaringan menangani pengalamatan logis dan perutean, yaitu menemukan jalur untuk mentransfer paket jaringan antara jaringan yang beragam.

Pada lapisan tautan data, kita telah memberikan contoh sebuah kantor perusahaan dengan sepuluh komputer, di mana lapisan tautan data bertanggung jawab untuk menyediakan koneksi antar komputer tersebut. Katakanlah perusahaan ini memiliki banyak kantor yang tersebar di berbagai kota, negara, atau bahkan benua. Lapisan jaringan bertanggung jawab untuk menghubungkan berbagai kantor tersebut.

Diagram jaringan di bawah menunjukkan bahwa komputer A dan B terhubung, meskipun berada di jaringan yang berbeda. Anda juga dapat melihat dua jalur yang menghubungkan kedua komputer; lapisan jaringan akan mengarahkan paket jaringan melalui jalur yang dianggap lebih baik.


<img width="1920" height="649" alt="image" src="https://github.com/user-attachments/assets/9bd8d03f-f6c4-4f9c-8b1a-ce14009d66f9" />

Contoh lapisan jaringan meliputi Protokol Internet (IP), Protokol Pesan Kontrol Internet (ICMP), dan protokol Jaringan Pribadi Virtual ( VPN ) seperti IPSec dan SSL/ TLS VPN .

# Lapisan 4: Lapisan Transportasi
Lapisan 4, lapisan transport, memungkinkan komunikasi ujung-ke-ujung antara aplikasi yang berjalan di host yang berbeda. Peramban web Anda terhubung ke server web TryHackMe melalui lapisan transport, yang dapat mendukung berbagai fungsi seperti kontrol aliran, segmentasi, dan koreksi kesalahan.

Contoh lapisan 4 adalah Transmission Control Protocol ( TCP ) dan User Datagram Protocol ( UDP ).

# Lapisan 5: Lapisan Sesi
Lapisan sesi bertanggung jawab untuk membangun, memelihara, dan menyinkronkan komunikasi antara aplikasi yang berjalan di host yang berbeda. Membangun sesi berarti memulai komunikasi antara aplikasi dan menegosiasikan parameter yang diperlukan untuk sesi tersebut. Sinkronisasi data memastikan bahwa data ditransmisikan dalam urutan yang benar dan menyediakan mekanisme pemulihan jika terjadi kegagalan transmisi.

Contoh lapisan sesi adalah Network File System (NFS) dan Remote Procedure Call (RPC).

# Lapisan 6: Lapisan Presentasi
Lapisan presentasi memastikan data dikirim dalam bentuk yang dapat dipahami oleh lapisan aplikasi. Lapisan 6 menangani pengkodean, kompresi, dan enkripsi data. Contoh pengkodean adalah pengkodean karakter, seperti ASCII atau Unicode.

Berbagai standar digunakan pada lapisan presentasi. Pertimbangkan skenario di mana kita ingin mengirim gambar melalui email. Pertama, kita menggunakan JPEG, GIF, dan PNG untuk menyimpan gambar kita; selanjutnya, meskipun disembunyikan dari pengguna oleh klien email, kita menggunakan MIME (Multipurpose Internet Mail Extensions) untuk melampirkan file ke email kita. MIME mengkodekan file biner menggunakan karakter ASCII 7-bit.

# Lapisan 7: Lapisan Aplikasi
Lapisan aplikasi menyediakan layanan jaringan langsung ke aplikasi pengguna akhir. Peramban web Anda akan menggunakan protokol HTTP untuk meminta file, mengirimkan formulir, atau mengunggah file.

Lapisan aplikasi adalah lapisan teratas, dan Anda mungkin telah menjumpai banyak protokolnya saat menggunakan berbagai aplikasi. Contoh protokol Lapisan 7 adalah HTTP , FTP , DNS , POP3 , SMTP , dan IMAP . Jangan khawatir jika Anda tidak familiar dengan semuanya.

Ringkasan
Membaca tentang model ISO OSI untuk pertama kalinya bisa terasa menakutkan; namun, hal itu akan menjadi lebih mudah seiring kemajuan Anda dalam mempelajari protokol jaringan. Untuk membantu studi Anda, kami telah merangkum lapisan ISO OSI dalam tabel di bawah ini.

Nomor Lapisan	Nama Lapisan	Fungsi Utama	Contoh Protokol dan Standar
Lapisan 7	Lapisan aplikasi	Menyediakan layanan dan antarmuka untuk aplikasi.	HTTP , FTP , DNS , POP3 , SMTP , IMAP
Lapisan 6	Lapisan presentasi	Pengkodean, enkripsi, dan kompresi data.	Unicode, MIME , JPEG, PNG, MPEG
Lapisan 5	Lapisan sesi	Membangun, memelihara, dan menyinkronkan sesi.	NFS, RPC
Lapisan 4	Lapisan transport	Komunikasi ujung-ke-ujung dan segmentasi data	UDP , TCP
Lapisan 3	Lapisan jaringan	Pengalamatan logis dan perutean antar jaringan	IP, ICMP, IPSec
Lapisan 2	Lapisan tautan data	Transfer data yang andal antara node yang berdekatan	Ethernet (802.3), WiFi (802.11)
Lapisan 1	Lapisan fisik	Media transmisi data fisik	Sinyal listrik, optik, dan nirkabel
Jawablah pertanyaan-pertanyaan di bawah ini.
Lapisan manakah yang bertanggung jawab atas  komunikasi ujung-ke-ujung antara aplikasi yang sedang berjalan?

4

Jawaban yang Benar

Lapisan manakah yang bertanggung jawab untuk mengarahkan paket ke jaringan yang tepat?
3

Jawaban yang Benar

Dalam model OSI, lapisan manakah yang bertanggung jawab untuk mengkodekan data aplikasi?

6

Jawaban yang Benar

Lapisan manakah yang bertanggung jawab untuk mentransfer data antar host pada segmen jaringan yang sama?

2

Jawaban yan


Model TCP/IP
Setelah membahas model konseptual ISO OSI, sekarang saatnya mempelajari model yang telah diimplementasikan, yaitu model TCP /IP. TCP /IP adalah singkatan dari Transmission Control Protocol/Internet Protocol dan dikembangkan pada tahun 1970-an oleh Departemen Pertahanan (DoD). Mungkin Anda bertanya mengapa DoD membuat model seperti itu. Salah satu keunggulan model ini adalah memungkinkan jaringan untuk terus berfungsi meskipun sebagian jaringannya tidak beroperasi, misalnya, karena serangan militer. Kemampuan ini dimungkinkan sebagian karena desain protokol routing yang mampu beradaptasi seiring perubahan topologi jaringan.

Dalam presentasi kita tentang model ISO OSI, kita membahasnya dari bawah ke atas, dari lapisan 1 hingga lapisan 7. Dalam tugas ini, mari kita lihat dari perspektif yang berbeda, dari atas ke bawah. Dari atas ke bawah, kita memiliki:

Lapisan Aplikasi : Dalam model OSI, lapisan aplikasi, presentasi, dan sesi, yaitu lapisan 5, 6, dan 7, dikelompokkan ke dalam lapisan aplikasi dalam model TCP /IP.
Lapisan Transportasi : Ini adalah lapisan 4.
Lapisan Internet : Ini adalah lapisan 3. Lapisan jaringan pada model OSI disebut lapisan Internet dalam model TCP /IP.
Lapisan Tautan : Ini adalah lapisan 2.
Tabel di bawah ini menunjukkan bagaimana lapisan model TCP /IP dipetakan ke lapisan model ISO/OSI.

Nomor Lapisan	Model ISO OSI	Model TCP /IP ( RFC 1122)	Protokol
7	Lapisan Aplikasi	Lapisan Aplikasi	HTTP , HTTPS, FTP , POP3 , SMTP , IMAP , Telnet , SSH
6	Lapisan Presentasi
5	Lapisan Sesi
4	Lapisan Transportasi	Lapisan Transportasi	TCP , UDP
3	Lapisan Jaringan	Lapisan Internet	IP, ICMP, IPSec
2	Lapisan Tautan Data	Lapisan Tautan	Ethernet 802.3, WiFi 802.11
1	Lapisan Fisik		
Banyak buku teks jaringan modern menunjukkan model TCP /IP sebagai lima lapisan, bukan empat. Misalnya, dalam buku Computer Networking: A Top-Down Approach Edisi ke-8, Kurose dan Ross menjelaskan tumpukan protokol Internet lima lapisan berikut dengan memasukkan lapisan fisik:

Aplikasi
Mengangkut
Jaringan
Link
Fisik
Pada tugas-tugas berikut, kita akan membahas protokol IP dari lapisan Internet dan protokol UDP serta TCP dari lapisan transport.

Jawablah pertanyaan-pertanyaan di bawah ini.
HTTP termasuk dalam lapisan manakah dalam model TCP/IP?

Application Layer


Berapa banyak lapisan model OSI yang dicakup oleh lapisan aplikasi dalam model TCP/IP?

3

# IP addresses and subnets
Ketika Anda mendengar kata alamat IP, Anda mungkin berpikir tentang alamat seperti 192.168.0.1atau sesuatu yang kurang umum, seperti 172.16.159.243. Dalam kedua kasus tersebut, Anda benar. Keduanya adalah alamat IP; lebih tepatnya, alamat IPv4 (IP versi 4).

Setiap host di jaringan membutuhkan pengidentifikasi unik agar host lain dapat berkomunikasi dengannya. Tanpa pengidentifikasi unik, host tidak dapat ditemukan tanpa ambiguitas. Saat menggunakan rangkaian protokol TCP/IP, kita perlu menetapkan alamat IP untuk setiap perangkat yang terhubung ke jaringan.

Salah satu analogi alamat IP adalah alamat pos rumah Anda. Alamat pos memungkinkan Anda menerima surat dan paket dari seluruh dunia. Selain itu, alamat pos dapat mengidentifikasi rumah Anda tanpa ambiguitas; jika tidak, Anda tidak dapat berbelanja online!

Seperti yang mungkin sudah Anda ketahui, kita memiliki IPv4 dan IPv6 (IP versi 6). IPv4 masih yang paling umum, dan setiap kali Anda menemukan teks yang menyebutkan IP tanpa menyebutkan versinya, kita mengharapkan mereka merujuk pada IPv4.

Jadi, apa yang membentuk alamat IP? Alamat IP terdiri dari empat oktet, yaitu 32 bit. Dengan 8 bit, satu oktet memungkinkan kita untuk merepresentasikan angka desimal antara 0 dan 255. Alamat IP ditunjukkan pada gambar di bawah ini.

<img width="1140" height="487" alt="image" src="https://github.com/user-attachments/assets/6ca2a964-1476-4a75-9e28-f28719ee419f" />


Dengan risiko menyederhanakan masalah secara berlebihan, angka 0 dan 255 masing-masing dicadangkan untuk alamat jaringan dan alamat siaran. Dengan kata lain, 192.168.1.0adalah alamat jaringan, sedangkan 192.168.1.255adalah alamat siaran. Mengirim ke alamat siaran menargetkan semua host di jaringan. Dengan perhitungan sederhana, Anda dapat menyimpulkan bahwa kita tidak mungkin memiliki lebih dari 4 miliar alamat IPv4 unik. Jika Anda penasaran dengan perhitungannya, angkanya kira-kira 2³² karena kita memiliki 32 bit. Angka ini merupakan perkiraan karena kita tidak mempertimbangkan alamat jaringan dan alamat siaran.

Memeriksa Konfigurasi Jaringan Anda
Anda dapat mencari alamat IP Anda di baris perintah MS Windows menggunakan perintah ` ipconfig.`. Pada sistem berbasis Linux dan UNIX, Anda dapat menjalankan perintah `.` ifconfigatau ip address show`.`, yang dapat diketik sebagai ip a s`.`. Di jendela terminal di bawah ini, kami menampilkan ifconfig`.`.

Terminal
user@TryHackMe$ ifconfig
[...]
wlo1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.66.89  netmask 255.255.255.0  broadcast 192.168.66.255
        inet6 fe80::73e1:ca5e:3f93:b1b3  prefixlen 64  scopeid 0x20<link>
        ether cc:5e:f8:02:21:a7  txqueuelen 1000  (Ethernet)
        RX packets 19684680  bytes 18865072842 (17.5 GiB)
        RX errors 0  dropped 364  overruns 0  frame 0
        TX packets 14439678  bytes 8773200951 (8.1 GiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
Output terminal di atas menunjukkan hal berikut:

Alamat IP host (laptop) adalah192.168.66.89
Subnet mask adalah255.255.255.0
Alamat siaran adalah192.168.66.255
Mari kita gunakan ip a suntuk membandingkan bagaimana alamat IP kartu jaringan ditampilkan.

Terminal
user@TryHackMe$ ip a s
[...]
4: wlo1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether cc:5e:f8:02:21:a7 brd ff:ff:ff:ff:ff:ff
    altname wlp3s0
    inet 192.168.66.89/24 brd 192.168.66.255 scope global dynamic noprefixroute wlo1
       valid_lft 36795sec preferred_lft 36795sec
    inet6 fe80::73e1:ca5e:3f93:b1b3/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
Output terminal di atas menunjukkan hal berikut:

Alamat IP host (laptop) adalah192.168.66.89/24
Alamat siaran adalah192.168.66.255
Jika Anda bertanya-tanya, subnet mask 255.255.255.0juga dapat ditulis sebagai /24. Artinya /24, 24 bit paling kiri dalam alamat IP tidak berubah di seluruh jaringan, yaitu subnet. Dengan kata lain, tiga oktet paling kiri sama di seluruh subnet; oleh karena itu, kita dapat mengharapkan untuk menemukan alamat yang berkisar dari 192.168.66.1hingga 192.168.66.254. Mirip dengan yang disebutkan sebelumnya, 192.168.66.0dan 192.168.66.255masing-masing adalah alamat jaringan dan alamat broadcast.

Alamat Pribadi
Sembari menjelaskan alamat IP, perlu disebutkan bahwa untuk sebagian besar keperluan praktis, terdapat dua jenis alamat IP:

Alamat IP publik
Alamat IP pribadi
RFC 1918 mendefinisikan tiga rentang alamat IP pribadi berikut:

10.0.0.0- 10.255.255.255( 10/8)
172.16.0.0- 172.31.255.255( 172.16/12)
192.168.0.0- 192.168.255.255( 192.168/16)
Sebelumnya kita telah menyajikan analogi yang menyatakan bahwa alamat IP publik seperti alamat pos rumah Anda. Alamat IP pribadi berbeda; ide awalnya adalah bahwa alamat tersebut tidak dapat dijangkau atau diakses dari dunia luar. Ini seperti kota atau kompleks terisolasi, di mana semua rumah dan apartemen diberi nomor secara sistematis dan dapat dengan mudah bertukar surat satu sama lain, tetapi tidak dengan dunia luar. Agar alamat IP pribadi dapat mengakses Internet, router harus memiliki alamat IP publik dan harus mendukung Network Address Translation (NAT). Pada tahap ini, mari kita tidak perlu khawatir tentang memahami cara kerja NAT, karena kita akan membahasnya kembali nanti di modul ini.

Sebelum melanjutkan, saya sarankan untuk menghafal rentang alamat IP pribadi. Jika tidak, Anda mungkin melihat alamat IP seperti 10.1.33.7atau 172.31.33.7dan mencoba mengaksesnya dari alamat IP publik.

Rute
Router itu seperti kantor pos setempat; Anda menyerahkan paket pos kepada mereka, dan mereka akan tahu cara mengirimkannya. Jika kita telusuri lebih dalam, Anda mungkin mengirimkan sesuatu ke alamat di kota atau negara lain. Kantor pos akan memeriksa alamat tersebut dan memutuskan ke mana harus mengirimkannya selanjutnya. Misalnya, jika paket tersebut akan dikirim ke luar negeri, kita mengharapkan satu kantor pusat untuk menangani semua pengiriman ke luar negeri.

Secara teknis, router meneruskan paket data ke jaringan yang tepat. Biasanya, sebuah paket data melewati beberapa router sebelum mencapai tujuan akhirnya. Router berfungsi pada lapisan 3, memeriksa alamat IP dan meneruskan paket ke jaringan (router) terbaik sehingga paket tersebut semakin dekat dengan tujuannya.

<img width="1520" height="1360" alt="image" src="https://github.com/user-attachments/assets/eb400258-c57a-48ca-9500-27d30a4f071a" />

Jawablah pertanyaan-pertanyaan di bawah ini.
Manakah dari alamat IP berikut yang bukan merupakan alamat IP pribadi?

192.168.250.125
10.20.141.132
49.69.147.197
172.23.182.251
49.69.147.197

Jawaban yang Benar
Manakah dari alamat IP berikut yang bukan merupakan alamat IP yang valid?

192.168.250.15
192.168.254.17
192.168.305.19
192.168.199.13
192.168.305.19

Jawaban yang Benar

# UDP dan TCP
Protokol IP memungkinkan kita untuk mencapai host tujuan di jaringan; host tersebut diidentifikasi oleh alamat IP-nya. Kita membutuhkan protokol yang memungkinkan proses pada host yang terhubung ke jaringan untuk berkomunikasi satu sama lain. Ada dua protokol transport untuk mencapai hal tersebut: UDP dan TCP .

UDP
UDP (User Datagram Protocol) memungkinkan kita untuk mencapai proses tertentu pada host target ini. UDP adalah protokol tanpa koneksi sederhana yang beroperasi pada lapisan transport, yaitu lapisan 4. Tanpa koneksi berarti tidak perlu membangun koneksi. UDP bahkan tidak menyediakan mekanisme untuk mengetahui bahwa paket telah terkirim.

Alamat IP mengidentifikasi host; kita membutuhkan mekanisme untuk menentukan proses pengiriman dan penerimaan. Hal ini dapat dicapai dengan menggunakan nomor port. Nomor port menggunakan dua oktet; akibatnya, nilainya berkisar antara 1 dan 65535; port 0 dicadangkan. (Angka 65535 dihitung dengan rumus 2¹⁶ −  1. )

Contoh nyata yang mirip dengan UDP adalah layanan pos standar, tanpa konfirmasi pengiriman. Dengan kata lain, tidak ada jaminan bahwa paket UDP telah diterima dengan sukses, mirip dengan kasus pengiriman paket menggunakan pos standar tanpa konfirmasi pengiriman. Dalam kasus pos standar, ini berarti biaya yang lebih murah daripada opsi pengiriman pos dengan konfirmasi. Dalam kasus UDP , ini berarti kecepatan yang lebih baik daripada protokol transport yang menyediakan "konfirmasi".

Namun bagaimana jika kita menginginkan protokol transport yang memberikan pengakuan terhadap paket yang diterima? Jawabannya terletak pada penggunaan TCP sebagai pengganti UDP .

TCP
TCP (Transmission Control Protocol) adalah protokol transport berorientasi koneksi. Protokol ini menggunakan berbagai mekanisme untuk memastikan pengiriman data yang andal yang dikirim oleh berbagai proses pada host yang terhubung ke jaringan. Seperti UDP , TCP merupakan protokol lapisan 4. Karena berorientasi koneksi, TCP memerlukan pembentukan koneksi TCP sebelum data apa pun dapat dikirim.

Dalam TCP , setiap oktet data memiliki nomor urutan; ini memudahkan penerima untuk mengidentifikasi paket yang hilang atau duplikat. Di sisi lain, penerima memberikan pengakuan atas penerimaan data dengan nomor pengakuan yang menentukan oktet terakhir yang diterima.

Koneksi TCP dibangun menggunakan apa yang disebut jabat tangan tiga arah. Dua flag digunakan: SYN (Sinkronisasi) dan ACK (Pengakuan). Paket dikirim sebagai berikut:

Paket SYN: Klien memulai koneksi dengan mengirimkan paket SYN ke server. Paket ini berisi nomor urutan awal yang dipilih secara acak oleh klien.
Paket SYN-ACK: Server merespons paket SYN dengan paket SYN-ACK, yang menambahkan nomor urutan awal yang dipilih secara acak oleh server.
Paket ACK: Proses jabat tangan tiga arah selesai ketika klien mengirimkan paket ACK untuk mengakui penerimaan paket SYN-ACK.

<img width="1280" height="640" alt="image" src="https://github.com/user-attachments/assets/f1c882d6-00e4-46f2-9ce6-7e2473080cf9" />

Mirip dengan UDP , TCP mengidentifikasi proses memulai atau menunggu (mendengarkan) koneksi menggunakan nomor port. Seperti yang dinyatakan, nomor port yang valid berkisar antara 1 dan 65535 karena menggunakan dua oktet dan port 0 dicadangkan.

Jawablah pertanyaan-pertanyaan di bawah ini.
Protokol mana yang memerlukan jabat tangan tiga arah?

TCP

Jawaban yang Benar
Berapakah perkiraan jumlah nomor port (dalam ribuan)?

65

Jawaban yang Benar

# Enkapsulation /Enkapsulasi
Sebelum mengakhiri pembahasan, penting untuk menjelaskan konsep kunci lainnya: enkapsulasi . Dalam konteks ini, enkapsulasi mengacu pada proses di mana setiap lapisan menambahkan header (dan terkadang trailer) ke unit data yang diterima dan mengirimkan unit yang "terenkapsulasi" tersebut ke lapisan di bawahnya.

Enkapsulasi adalah konsep penting karena memungkinkan setiap lapisan untuk fokus pada fungsi yang dimaksudkan. Pada gambar di bawah ini, kita memiliki empat langkah berikut:

Data aplikasi : Semuanya dimulai ketika pengguna memasukkan data yang ingin mereka kirim ke dalam aplikasi. Misalnya, Anda menulis email atau pesan instan dan menekan tombol kirim. Aplikasi memformat data ini dan mulai mengirimkannya sesuai dengan protokol aplikasi yang digunakan, menggunakan lapisan di bawahnya, yaitu lapisan transport.
Segmen protokol transport atau datagram : Lapisan transport, seperti TCP atau UDP , menambahkan informasi header yang sesuai dan membuat segmen TCP (atau datagram UDP ). Segmen ini dikirim ke lapisan di bawahnya, yaitu lapisan jaringan.
Paket jaringan : Lapisan jaringan, yaitu lapisan Internet, menambahkan header IP ke segmen TCP atau datagram UDP yang diterima. Kemudian, paket IP ini dikirim ke lapisan di bawahnya, yaitu lapisan tautan data.
Frame tautan data : Ethernet atau WiFi menerima paket IP dan menambahkan header dan trailer yang sesuai, sehingga menciptakan sebuah frame .
Kita mulai dengan data aplikasi. Pada lapisan transport, kita menambahkan header TCP atau UDP untuk membuat segmen TCP atau datagram UDP . Kemudian, pada lapisan jaringan, kita menambahkan header IP yang tepat untuk mendapatkan paket IP yang dapat dirutekan melalui Internet. Terakhir, kita menambahkan header dan trailer yang sesuai untuk mendapatkan frame WiFi atau Ethernet pada lapisan tautan.

<img width="1603" height="602" alt="image" src="https://github.com/user-attachments/assets/ec3432b4-2221-4360-b122-0871542e2232" />

Proses tersebut harus dibalik di sisi penerima hingga data aplikasi diekstrak.

Kehidupan Sebuah Paket
Berdasarkan apa yang telah kita pelajari sejauh ini, kita dapat menjelaskan versi sederhana dari siklus hidup paket. Mari kita pertimbangkan skenario di mana Anda mencari ruangan di TryHackMe.

Di halaman pencarian TryHackMe, Anda memasukkan kata kunci pencarian dan tekan enter.
Browser web Anda, menggunakan HTTPS, menyiapkan permintaan HTTP dan mengirimkannya ke lapisan di bawahnya, yaitu lapisan transport.
Lapisan TCP perlu membangun koneksi melalui jabat tangan tiga arah antara browser Anda dan server web TryHackMe. Setelah koneksi TCP terjalin , ia dapat mengirimkan permintaan HTTP yang berisi kueri pencarian. Setiap segmen TCP yang dibuat dikirim ke lapisan di bawahnya, yaitu lapisan Internet.
Lapisan IP menambahkan alamat IP sumber, yaitu komputer Anda, dan alamat IP tujuan, yaitu alamat IP server web TryHackMe. Agar paket ini mencapai router, laptop Anda mengirimkannya ke lapisan di bawahnya, yaitu lapisan tautan.
Tergantung pada protokolnya, lapisan tautan menambahkan header dan trailer lapisan tautan yang sesuai, dan paket dikirim ke router.
Router menghapus header dan trailer lapisan tautan, memeriksa IP tujuan, di antara bidang-bidang lainnya, dan mengarahkan paket ke tautan yang tepat. Setiap router mengulangi proses ini hingga mencapai router server target.
Langkah-langkah tersebut kemudian akan dibalik saat paket mencapai router jaringan tujuan. Seiring kita membahas protokol tambahan, kita akan meninjau kembali latihan ini dan membuat versi yang lebih mendalam.

Jawablah pertanyaan-pertanyaan di bawah ini.
Pada jaringan WiFi, di dalam apa paket IP akan dienkapsulasi?

Frame

Jawaban yang Benar
Apa sebutan untuk unit data UDP yang membungkus data aplikasi?

Datagram

Jawaban yang Benar
Apa sebutan untuk unit data yang membungkus data aplikasi yang dikirim melalui TCP?

Segment

Jawaban yang Benar


# Telnet
Mulai AttackBox dengan menekan tombol Mulai AttackBox di bagian atas halaman ini. Mesin AttackBox akan dimulai dalam tampilan Layar Terpisah. Jika tidak terlihat, gunakan tombol biru Tampilkan Tampilan Terpisah di bagian atas halaman.

Beri mereka waktu sekitar 2 menit untuk melakukan booting dengan benar. Setelah kedua mesin siap, kita perlu memulai terminal di AttackBox untuk melakukan eksperimen telnet.

Protokol TELNET (Teletype Network) adalah protokol jaringan untuk koneksi terminal jarak jauh. Sederhananya, telnetTELNET, sebagai klien, memungkinkan Anda untuk terhubung dan berkomunikasi dengan sistem jarak jauh serta mengeluarkan perintah teks. Meskipun awalnya digunakan untuk administrasi jarak jauh, kita dapat menggunakannya telnetuntuk terhubung ke server mana pun yang mendengarkan pada nomor port TCP.

Pada mesin virtual target, berbagai layanan berjalan. Kita akan bereksperimen dengan tiga di antaranya:

Server gema: Server ini menggemakan semua yang Anda kirimkan. Secara default, server ini mendengarkan pada port 7.
Server siang hari: Server ini secara default mendengarkan pada port 13 dan membalas dengan hari dan waktu saat ini.
Server web (HTTP): Server ini secara default mendengarkan pada port TCP 80 dan menyajikan halaman web.
Sebelum melanjutkan, perlu kami sebutkan bahwa server echo dan daytime dianggap sebagai risiko keamanan dan sebaiknya tidak dijalankan; namun, kami secara eksplisit menjalankannya untuk mendemonstrasikan komunikasi dengan server menggunakan . Pada terminal di bawah ini, kami terhubung ke VM target pada port TCPtelnet nomor 7 server echo. Untuk menutup koneksi, tekan tombol + secara bersamaan.CTRL]

Terminal
user@TryHackMe$ telnet MACHINE_IP 7
telnet MACHINE_IP 7
Trying MACHINE_IP...
Connected to MACHINE_IP.
Escape character is '^]'.
Hi
Hi
How are you?
How are you?
Bye
Bye
^]

telnet> quit
Connection closed.
Pada terminal di bawah ini, kita menggunakannya telnetuntuk terhubung ke server siang hari yang mendengarkan di port 13. Kami memperhatikan bahwa koneksi terputus setelah tanggal dan waktu saat ini dikembalikan.

Terminal
user@TryHackMe$ telnet MACHINE_IP 13
Trying MACHINE_IP...
Connected to MACHINE_IP.
Escape character is '^]'.
Thu Jun 20 12:36:32 PM UTC 2024
Connection closed by foreign host.
Terakhir, mari kita minta halaman web menggunakan telnet. Setelah terhubung ke port 80, Anda perlu mengeluarkan perintah GET / HTTP/1.1dan mengidentifikasi host tempat semua hal akan masuk, misalnya Host: telnet.thm. Selanjutnya, Anda perlu menekan Enterdua kali sehingga baris input terakhir Anda menjadi baris kosong. Output di bawah ini menunjukkan pertukaran tersebut. (Halaman telah disunting.)

Catatan : Anda mungkin perlu menekan tombol lagi Entersetelah mengirim informasi jika Anda tidak mendapatkan respons.

Terminal
user@TryHackMe$ telnet MACHINE_IP 80
Trying MACHINE_IP...
Connected to MACHINE_IP.
Escape character is '^]'.
GET / HTTP/1.1
Host: telnet.thm

HTTP/1.1 200 OK
Content-Type: text/html
[...]

Connection closed by foreign host.
Jawablah pertanyaan-pertanyaan di bawah ini.
Gunakan telnetuntuk terhubung ke server web di MACHINE_IP. Apa nama dan versi server HTTP tersebut?

lighttpd/1.4.63

Jawaban yang Benar

# Kesimpulan
Di ruangan ini, kami membahas model ISO, OSI, dan TCP /IP, membandingkan dan membedakan keduanya. Kami juga membahas alamat IP dan subnet, serta menjelaskan secara singkat tentang routing. Selanjutnya, setelah mempelajari TCP dan UDP , kami menjelaskan enkapsulasi. Untuk tujuan demonstrasi, kami menggunakan TCPtelnet untuk "berkomunikasi" dengan berbagai server .
