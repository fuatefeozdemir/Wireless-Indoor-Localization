Wireless Indoor Localization

Bu proje, GPS sinyallerinin yetersiz kaldığı kapalı alanlarda, ortamdaki Wi-Fi yönlendiricilerinden gelen sinyal güçlerini kullanarak bir cihazın hangi odada bulunduğunu yüksek doğrulukla tahmin eden bir makine öğrenmesi sistemidir.  

🛠️ Teknik Özellikler ve Metodoloji

Veri Sızıntısı (Data Leakage) Koruması: StandardScaler ve modeller bir Pipeline mimarisi içinde birleştirilmiştir. Bu sayede ölçeklendirme işlemi sadece eğitim setinden öğrenilir; test verisinin istatistiklerinin eğitim aşamasına sızması engellenerek metodolojik dürüstlük sağlanır.

Çok Boyutlu Analiz (t-SNE): 7 farklı router'dan gelen sinyallerin (7 boyut) 2 boyuta indirgenmesiyle, odaların sinyal uzayındaki fiziksel kümelenmesi görselleştirilmiştir.

Adil Model Yarıştırma: KNN, Random Forest, SVM, Decision Tree ve Logistic Regression modelleri, 5-katlı Çapraz Doğrulama (5-Fold CV) ile tarafsız bir şekilde kıyaslanmıştır.

Dinamik Hiperparametre Optimizasyonu: Çapraz doğrulama sonucunda lider çıkan model otomatik olarak seçilir ve GridSearchCV ile tavan performansına ulaştırılır.

📊 Veri Seti Yapısı
Kullanılan veri seti 7 adet Wi-Fi yönlendiricisi sinyali ve 1 adet hedef oda numarasından oluşur:  

Özellikler (Features): Router1, Router2, Router3, Router4, Router5, Router6, Router7 (Sinyal Gücü - dBm)  

Hedef (Target): Room (1, 2, 3, 4)  

📋 Proje Akışı
Keşifsel Veri Analizi (EDA): Sınıf dengesi ve sinyallerdeki anomali (outlier) tespiti.

Boyut İndirgeme: t-SNE algoritması ile verinin ayrılabilirliğinin kanıtlanması.

Model Değerlendirme: Farklı algoritmaların Pipeline üzerinden tarafsız testi.

Hiperparametre Ayarı: En iyi modelin (örneğin KNN veya Random Forest) iç parametrelerinin optimize edilmesi.

Performans Raporlama: Karmaşıklık Matrisi (Confusion Matrix) ve detaylı sınıflandırma raporu (Precision, Recall, F1) ile hata analizi.
