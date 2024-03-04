# Sistem Pengenalan Alat Pelindung Diri

Berikut merupakan penjelasan terkait develop sistem AI untuk melakukan deteksi terhadap alat pelindung pekerja.

## Dataset

- Publik Dataset berasal dari platform huggingface.co
- Berupa kumpulan file gambar dan annotasinya
- Memiliki 10 atribut deteksi objek alat pelindung diri, meliputi:'glove', 'goggles', 'helmet', 'mask', 'no_glove', 'no_goggles', 'no_helmet', 'no_mask', 'no_shoes', 'shoes'.

- Selain memiliki atribut yang lengkap sesaui dengan kebutuhan challenge, dataset ini punya variasi gambar yang banyak, seperti:
	- Objek gambar pada jarak yang dekat dan jauh.
	- Gambar meliputi gambar individu, maupun potongan dari rekaman cctv/video.
	- Annotasi gambar mendeteksi objek besar maupun kecil.
Keempat hal itu, alasan kuat data ini cocok dalam proses pembuatan model deteksi objek baik melalui foto maupun video cctv.
Berikut merupakan referensi yang digunakan:
<https://www.sciencedirect.com/science/article/pii/S0926580517304429>
<https://www.sciencedirect.com/science/article/pii/S0925753522000297?fr=RR-2&ref=pdf_download&rr=85d6475b6cff3e29>

Berikut contoh beberapa gambar data train:
- Link : <https://huggingface.co/datasets/keremberke/protective-equipment-detection>

## Model

Pengembangan model yang baik dalam proses deteksi objek tidak hanya pada aspek data, tetapi ketepatan metode yang digunakan cukup berperan.
Berdasarkan beberapa artikel/paper yang saya baca, terdapat dua metode yang cukup optimal, yaitu Faster RCNN dan YOLO. Faster RCNN cukup optimal dalam mengenali object pada jarak yang cukup jauh seperti hal nya pada rekaman cctv, dan powerful pada training dataset jumlah besar. Disisi lain, Yolo yang terus dikembangkan hingga saat ini, cukup optimal dalam hal pemrossesan, pada beberapa kasus metode Yolo memiliki akurasi yang lebih baik pada dataset yang minim.
Pada percobaan ini, saya menggunakan Yolo, dengan pertimbangan jumlah data, dan efisien waktu. Saya tidak menggunakan metode Faster RCNN karena terkendala pada processor yang tidak memadai, sehingga proses train data berjalan lama.

#Requirement

- Code editor : Google colab
- Instalasi beberapa library pendukung: ultralyticsplus, ultralytics, dan streamlit
- Demo menggunakan library Streamlit. 
  Cara menjalankan streamlit web app:
	- jalankan/ run semua box code pada demo.ipynb
	- output dari script "!streamlit run app.py & npx localtunnel --port 8501" menampilkan link untuk mengakses web base dari demo. Gunakan ip external url sebagai password. Seperti berikut:
	
	- Aplikasi menyediakan dua option objek yang dapat di deteksi yaitu, gambar dan video. Sidebar kiri merupakan laman konfigurasi, dan sisi kanan merupakan laman display output.
	- Pada konfigurasi sudah disediakan default foto dan video, untuk melakukan pemrosesan deteksi secara langsung.
	- Setiap perubahan yang dilakukan pada script code, perlu dilakukan run pada localtunnel kembali.

Terima kasih.




### Home page

<img src="https://github.com/CodingMantras/yolov8-streamlit-detection-tracking/blob/master/assets/pic1.png" >

### Page after uploading an image and object detection

