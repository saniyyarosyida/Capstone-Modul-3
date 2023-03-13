## Business Problem Understanding
#### Context
Travel insurance / asuransi perjalanan adalah jenis asuransi yang memberikan perlindungan selama kita melakukan perjalanan baik ke dalam negeri maupun ke luar negeri. Beberapa perusahaan yang menyediakan jasa asuransi perjalanan diantaranya adalah Allianz, Lippo, Zurich, Simasnet, MNC, dan masih banyak lagi. Tidak sedikit orang yang menjadikan asuransi perjalanan sebagai teman perjalanan mereka, sebab manfaatnya yang dapat melindungi penggunanya (pemegang polis) dari berbagai risiko yang mungkin terjadi selama perjalanan. Mulai dari perlindungan dan evakuasi medis, penggantian atas kerusakan / kehilangan bagasi, perlindungan atas pembatalan perjalanan, hingga santunan kecelakaan, cacat permanen, dan kunjungan kematian.

Kesepakatan bahwa Penyedia Asuransi bersedia menanggung risiko yang dimiliki oleh tertanggung dalam jangka waktu tertentu yang tertulis dalam polis asuransi. Untuk mendapatkan manfaat asuransi dari pihak penyedia, pemegang polis wajib membayar sejumlah biaya premi yang telah disepakati. Besarnya premi tergantung dari pertanggungan yang diinginkan, lama perjalanan, dan tujuan perjalanan.

Dalam dunia usaha asuransi, beberapa perusahaan asuransi memiliki agen asuransi (berbentuk perseorangan atau agensi berbadan hukum) sebagai perantara untuk menjual produk asuransinya kepada seseorang yang ingin melakukan perjalanan. Misalnya traveloka yang menyedikan jasa untuk pemesanan tiket penerbangan dan perjalanan kereta api, yang juga menyediakan produk asuransi perjalanan sebagai opsi tambahan yang dapat dibeli oleh calon traveler. Disini, traveloka berperan sebagai agen asuransi yang bekerja sama dengan berbagai perusahaan asuransi.

Perusahaan asuransi mendapatkan keuntungan melalui :

Pembatalan polis, yang berarti risiko klaim akan hilang dan perusahaan dapat menyimpan semua premi yang telah dibayarkan
Investasi premi di pasar finansial
Tidak ada klaim hingga kontrak asuransi berakhir. Klaim adalah tuntutan yang diajukan oleh pemegang polis kepada perusahaan Asuransi untuk memenuhi haknya sesuai yang tertera dalam Polis dan hanya dapat dilakukan dalam jangka waktu tertentu tergantung dengan jenis produk asuransi yang dibeli atau ketentuan perusahaan. Contohnya asuransi perjalanan Zurich yang memberikan waktu untuk melakukan klaim maksimal 5x24 jam setelah terjadinya kerugian.
Problem Statement & Goals
Suatu perusahaan yang bergerak di bidang asuransi perjalanan ingin dapat melakukan perencanaan penyiapan dana untuk pertanggungan asuransi secara lebih terukur dengan memprediksi kemungkinan seorang pemegang polis akan mengajukan klaim asuransi atau tidak. Jika dana asuransi disiapkan dengan besaran yang tepat, perusahaan berharap kredibilitas perusahaan akan tetap terjaga karena lancarnya proses pertanggungan klaim dan resiko idle money akibat tidak ada/sedikitnya pemegang polis yang mengajukan klaim berkurang.

Selain itu, perusahaan juga ingin mengetahui karakter pemegang polis berdasarkan status klaimnya dan jenis produk asuransi yang memiliki kemungkinan kecil untuk diklaim. Kedua hal ini akan bermanfaat dalam penentuan syarat dan ketentuan diterimanya polis seseorang / proses underwriting serta perencanaan penjualan produk yang lebih baik. Tim penjualan akan lebih mudah mencari pelanggan sesuai target dan karakteristik calon yang diinginkan dan keuntungan yang diperoleh perusahaan meningkat karena terminimalisirnya kemungkinan pemegang polis yang mengajukan klaim.

Analytic Approach (Model & Metric Evaluation)
Analisis data akan dilakukan untuk menemukan perbedaan pola antara pemegang polis yang mengajukan klaim dan tidak mengajukan klaim, serta memperoleh insight tentang peluang klaim berdasarkan jenis produk asuransi yang dijual. Selanjutnya, kita akan membangun model yang diharapkan dapat membantu perusahaan memprediksi kemungkinan seorang calon pemegang polis akan mengajukan klaim atau tidak. Oleh karena itu, model yang akan dibuat adalah model klasifikasi. Pemodelan akan dilakukan menggunakan beberapa algoritma model klasifikasi seperti Logistic Regression, Desicion Tree, KNN, Random Forest, XGBoost dan LightGBM.

Berikut beberapa kemungkinan yang dapat terjadi saat model mendefinisian status klaim pemegang polis :

Metric

TP : Jumlah pemegang polis yang memang benar melakukan klaim

TN : Jumlah pemegang polis yang memang benar tidak melakukan klaim

Type 1 error (FP) : Jumlah pemegang polis yang dinyatakan melakukan klaim padahal tidak melakukan klaim.

Konsekuensi : Dana asuransi dari hasil pencairan menjadi idle money (uang menganggur / tidak digunakan untuk apa pun dan tersimpan begitu saja tanpa tujuan yang jelas). Hal ini dapat menghambat pelaksanaan kegiatan lain dalam perusahaan yang juga membutuhkan dana serta terjadinya opportunity loss bagi perusahaan.

Type 2 error (FN) : Jumlah pemegang polis yang dinyatakan tidak melakukan klaim padahal melakukan klaim
Konsekuensi : Kurangnya persiapan dana asuransi sehingga dapat menghambat proses klaim pemegang polis, akibatnya kualitas dan kapabilitas perusahaan akan dipertanyakan dan akan berdampak buruk pada penjualan produk di masa depan karena hilangnya kepercayaan masyarakat.

Melihat resiko akibat kesalahan pendefinisian kelas positif dan negatif, maka model yang akan dibuat harus memperhatikan kedua kelas. Oleh karena itu, metric evaluation yang akan digunakan adalah ROC/AUC (Receiver Operating Characteristic) sebagai metric utama. Metric Accuracy tidak dipilih karena setelah diteliti, data merupakan data imbalance. Sebagai gantinya kita akan menggunakan metric balanced accuracy. Beberapa model akan diseleksi berdasarkan hasil evaluasi metriknya dan model dengan performa terbaik akan dipilih untuk dilanjutkan pada proses hyperparameter tuning dengan harapan dapat meningkatkan performa model.
