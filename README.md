# Hendri-Capstone-Project-modul-3

**Context**

Syarah adalah sebuah platform online yang khusus menjual mobil bekas dan baru, platform ini memberikan pengalaman pembelian online yang lancar dan nyaman bagi pelanggan. Melalui platform itu, pelanggan dapat menelusuri dan membeli mobil dari ponsel mereka tanpa kesulitan dan perusahaan mengirimkan mobil ke rumah mereka. Aplikasi ini menawarkan manfaat garansi komprehensif untuk mobil bekas. Mobil bekas diperiksa lebih dari 200 poin, dengan garansi satu tahun, dan yang terpenting adalah jaminan pengembalian dalam 10 hari sehingga pelanggan dapat mencoba mobil tersebut. dan jika pelanggan tidak menyukainya, mereka dapat mengembalikannya tanpa alasan apa pun. Kantor pusat kami berada di ibu kota Saudi - Riyadh, dan layanan kami mencakup seluruh wilayah Kerajaan. 

Syarah menjual mobil bekasnya ke pelanggan dengan harga yang beragam, dan ini tentu menyulitkan untuk menentukan harga jual yang wajar bagi pelanggan dan di sisi lain menguntungkan juga bagi perusahaan. Banyak faktor yang mempengaruhi harga dari mobil bekas, sehingga hal ini perlu dipahami oleh perusahaan karena berhubungan dengan profit yang didapatkan.    

 **Problem Statement**

Salah satu tantangan terbesar bagi perusahaan seperti Syarah adalah pemecahan masalah untuk dapat memiliki model bisnis yang menguntungkan bagi perusahaan, tetapi di sisi lain juga memberikan pengalaman yang menyenangkan bagi pelanggan saat membeli mobil.

Mengingat Syarah memegang kendali penuh untuk menentukan harga jual, maka cara untuk menentukan harga jual berdasarkan berbagai faktor agar tetap kompetitif dengan kompetitor sangatlah penting.  
**Goals**

Berdasarkan permasalahan tersebut, Syarah tentu perlu memiliki alat yang dapat memprediksi serta membantu perusahaan untuk dapat menentukan harga jual mobil yang tepat untuk ditawarkan ke pelanggan. Adanya  berbagai fitur yang terdapat pada suatu mobil bekas, seperti type mobil, produsen mobil, type transmisi, tahun dan kilometer/jarak tempuh mobil dapat menambah keakuratan prediksi harga jual, yang mana dapat mendatangkan profit perusahaan, dan juga tentunya masih wajar bagi pelanggan.

Bagi Syarah, prediction tool yang dapat memberikan prediksi harga jual secara wajar tentu dapat meningkatkan jumlah pelanggan yang tertarik membeli mobil bekas. Dengan kata lain, semakin banyak pelanggan yang tertarik untuk membeli mobil maka dapat meningkatkan laba dari perusahaan 

**Analytic Approach**

Kita akan membangun suatu model regresi yang akan membantu perusahaan untuk dapat menyediakan 'tool' prediksi harga jual mobil bekas, yang mana akan berguna bagi perusahaan dalam menentukan harga jual mobil bekas.

**Metric Evaluation**

Evaluasi metrik yang akan digunakan adalah MAE dan MAPE. Dimana MAE adalah rataan nilai absolut dari error, sedangkan MAPE adalah rataan persentase error yang dihasilkan oleh model regresi. Semakin kecil nilai MAE dan MAPE yang dihasilkan, berarti model semakin akurat dalam memprediksi harga jual mobil sesuai dengan limitasi fitur yang digunakan. 

- Dataset merupakan data harga jual mobil bekas di Syarah.
- Setiap baris data merepresentasikan informasi terkait detail dari mobil yang akan dijual beserta harganya.


**Attributes Information**

| **Atribut** | **Tipe Data** | **Deskripsi** |
| --- | --- | --- |
| Type | Object | Type dari mobil bekas |
| Region | Object | Wilayah dari mobil bekas |
| Make | Object | Produsen Mobil |
| Gear_Type | Object | Tipe Transmisi |
| Origin | Object | Asal dari mobil bekas |
| Options | Object | Opsi aksesoris dari mobil bekas |
| Year | Integer | Tahun produksi |
| Engine Size | Float | Ukuran mesin dari mobil bekas |
| Mileage | Integer | Kilometer tempuh dari mobil bekas |
| Negotiable | Bool | True jika harga jualnya 0, artinya dapat nego |
| Price | Integer | Harga jual mobil bekas |

### **Conclusion** 

- Metrik evaluasi yang digunakan pada model adalah nilai MAE & MAPE. Jika ditinjau dari nilai MAPE yang dihasilkan oleh model setelah dilakukan hyperparameter tuning, yaitu sebesar 15.97%, kita dapat menyimpulkan bahwa bila nanti model yang kita buat ini digunakan untuk memperkirakan harga jual mobil bekas pada rentang nilai seperti yang dilatih terhadap model (maksimal harga 182.500 SAR), maka perkiraan harganya rata-rata akan meleset kurang lebih sebesar 15.97% dari harga seharusnya. 

- Model XGBoost adalah model terbaik dimana nilai MAE dan MAPE sebelum tuning di sekitar 11.574 dan 16.29 %, setelah melalui proses hyperparameter tuning, dapat ditingkatkan ke sekitar 11.119 dan 15.97 %

- Best Parameters:
colsample_bytree: 0.9,
gamma: 0, 
learning_rate': 0.1,
max_depth': 5,
n_estimators': 300, 
subsample': 0.8
 
 - Tetapi, tidak menutup kemungkinan juga ada prediksi yang meleset karena masih adanya sedikit bias yang dihasilkan model bila dilihat antara harga aktual dan prediksi. Bias yang dihasilkan oleh model ini dikarenakan oleh terbatasnya fitur pada dataset yang bisa merepresentasikan mobil seperti tipe body mobil(hatchback,SUV,Sedan dll) dan fitur mobil(parking sensor, camera, hill start assist dll).

 ### **Recommendation**

 Berikut poin-poin yang dapat dilakukan untuk mengembangkan model agar lebih baik lagi, seperti:
- Jika memungkinkan, penambahan fitur yang lebih korelatif dengan target ('price'), seperti tipe body mobil dan fitur mobil. Selain itu, adanya penambahan data terbaru untuk Syarah tentu akan dapat mengimprovisasi kapasitas prediksi dari model.
- Mendiskusikan dengan user / stakeholders sehingga dapat lebih terarah untuk proses pengembangan modelnya. 
-  Lakukan A/B testing untuk menguji tingkat efektivitas dan ketepatan model terhadap harga mobil bekas jika dibandingkan dengan user yang menentukan harga jual mobil bekas.
- Kumpulkan data yang lebih banyak untuk melatih model
