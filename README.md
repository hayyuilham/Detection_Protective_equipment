# Sistem Pengenalan Alat Pelindung Diri

Berikut merupakan penjelasan terkait develop sistem AI untuk melakukan deteksi terhadap alat pelindung pekerja.

## Dataset

- Publik Dataset berasal dari platform huggingface.co
  - Link : <https://huggingface.co/datasets/keremberke/protective-equipment-detection>
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

![img1](https://github.com/hayyuilham/Detection_Protective_equipment/blob/e217d64535417db2948fca5d3f00ec6a6d22c261/image/005341_jpg.rf.5852eef9d72488917b88a16c577ec67c.jpg)

![img2](https://github.com/hayyuilham/Detection_Protective_equipment/blob/e217d64535417db2948fca5d3f00ec6a6d22c261/image/PP02img561_jpg.rf.1f202938a336e4aa0665967070db801e.jpg)

## Model

Pengembangan model yang baik dalam proses deteksi objek tidak hanya pada aspek data, tetapi ketepatan metode yang digunakan cukup berperan.
Berdasarkan beberapa artikel/paper yang saya baca, terdapat dua metode yang cukup optimal, yaitu Faster RCNN dan YOLO. Faster RCNN cukup optimal dalam mengenali object pada jarak yang cukup jauh seperti hal nya pada rekaman cctv, dan powerful pada training dataset jumlah besar. Disisi lain, Yolo yang terus dikembangkan hingga saat ini, cukup optimal dalam hal pemrossesan, pada beberapa kasus metode Yolo memiliki akurasi yang lebih baik pada dataset yang minim.
Pada percobaan ini, saya menggunakan Yolo, dengan pertimbangan jumlah data, dan efisien waktu. Saya tidak menggunakan metode Faster RCNN karena terkendala pada processor yang tidak memadai, sehingga proses train data berjalan lama.
Dataset yang saya memiliki belum cuku bersih sehingga saya gunakan proses normalisasi terhadap data, agar data bersih dan seimbang dalam proses pembelajaran model. Berdasarkan hasil evaluasi model yang dikembankan bekerja dengan baik, terkait penjelasan dan visualisasi lebih detail tertampil pada dokumen colab paling akhir.
Evaluasi dan hasil dari percobaan saya lampirkan dalam folder runs. salah satu contoh hasil prediksi sebagai berikut:

![img3](https://github.com/hayyuilham/Detection_Protective_equipment/blob/109c22df1114b7d7634f5451cbea9f72df4cc1fe/image/result1.png)


#Requirement

- Code editor : Google colab
- Detection_protective_equipments_contruction.ipynb merupakan dokumen utama dalam proses pembuatan dan ujicoba model.
- Demo.ipynb merupakan dokumen untuk menjalankan sistem deteksi berbasis web
- Instalasi beberapa library pendukung: ultralyticsplus, ultralytics, dan streamlit
- Demo menggunakan library Streamlit. 
  Cara menjalankan streamlit web app:
	- jalankan/ run semua box code pada demo.ipynb
	- output dari script "!streamlit run app.py & npx localtunnel --port 8501" menampilkan link untuk mengakses web base dari demo. Gunakan ip external url sebagai password. Seperti berikut:
 - 
	![img3](https://github.com/hayyuilham/Detection_Protective_equipment/blob/6208a4e61f319b8479cfc6935307b081c43ac299/image/app1.JPG)

	- Aplikasi menyediakan dua option objek yang dapat di deteksi yaitu, gambar dan video. Sidebar kiri merupakan laman konfigurasi, dan sisi kanan merupakan laman display output. Contoh:
 - 
	![img3](https://github.com/hayyuilham/Detection_Protective_equipment/blob/e217d64535417db2948fca5d3f00ec6a6d22c261/image/tampilan_demo2.png)

	- Pada konfigurasi sudah disediakan default foto dan video, untuk melakukan pemrosesan deteksi secara langsung.
	- Setiap perubahan yang dilakukan pada script code, perlu dilakukan run pada localtunnel kembali.

Terima kasih.


