> **Not:** Bu proje, 2026 yılı bahar döneminde Gazi Üniversitesi BMT-218 Veri Bilimine Giriş dersi kapsamında geliştirilmiştir.

# Wireless Indoor Localization

![Status](https://img.shields.io/badge/Status-Completed-success.svg) ![Language](https://img.shields.io/badge/Language-Python-blue.svg) ![Library](https://img.shields.io/badge/Library-Scikit--Learn-orange.svg) ![Environment](https://img.shields.io/badge/Environment-Jupyter-F37626.svg)

Bu proje, GPS sinyallerinin yetersiz kaldığı kapalı alanlarda, ortamdaki Wi-Fi yönlendiricilerinden (router) gelen sinyal güçlerini kullanarak bir cihazın hangi odada bulunduğunu yüksek doğrulukla tahmin eden bir makine öğrenmesi sistemidir.

## Teknik Özellikler ve Metodoloji

- **Veri Sızıntısı (Data Leakage) Koruması:** StandardScaler ve makine öğrenmesi modelleri bir Pipeline mimarisi içinde birleştirilmiştir. Ölçeklendirme işlemi sadece eğitim setinden öğrenilerek test verisinin istatistiklerinin eğitim aşamasına sızması engellenmiştir.
- **Çok Boyutlu Analiz (t-SNE):** 7 farklı yönlendiriciden gelen sinyallerin (7 boyut) aralarındaki fiziksel mesafe korunarak 2 boyuta indirgenmesiyle, odaların sinyal uzayındaki kümelenmesi görselleştirilmiştir.
- **Adil Model Yarıştırma:** KNN, Random Forest, SVM, Decision Tree ve Logistic Regression modelleri, 5-katlı Çapraz Doğrulama (5-Fold CV) kullanılarak genel doğruluk (Accuracy) ve çok boyutlu metrikler (Precision, Recall, F1-Score) üzerinden karşılaştırılmıştır.
- **Dinamik Hiperparametre Optimizasyonu:** Çapraz doğrulama sonucunda lider çıkan algoritmanın (Random Forest) iç parametre kombinasyonları (ağaç derinliği, tahminci sayısı vb.) GridSearchCV ile test edilerek optimize edilmiştir.
- **Özellik Önemi (Feature Importance):** Ağaç tabanlı modelin Gini Impurity (Safsızlık Azalması) skoru kullanılarak, yönlendiricilerin önem dereceleri sıralanmış ve sisteme en çok bilgi sağlayan cihazlar tespit edilmiştir.

## Veri Seti Yapısı

Veri seti, kapalı alandaki cihazlardan alınan ölçümlere dayanmaktadır:
- **Özellikler (Features):** Router1, Router2, Router3, Router4, Router5, Router6, Router7 (Sinyal Gücü - dBm)
- **Hedef Değişken (Target):** Room (Oda numarası: 1, 2, 3, 4)

## Proje Akışı

1. **Keşifsel Veri Analizi (EDA) ve Gürültü Kontrolü:** Sınıf dengesi ve sinyallerdeki aykırı (outlier) değerlerin tespiti.
2. **Boyut İndirgeme:** t-SNE algoritması ile veri ayrılabilirliğinin kanıtlanması.
3. **Model Değerlendirme:** Farklı algoritmaların Pipeline mimarisi üzerinden çapraz doğrulama ile test edilmesi.
4. **Hiperparametre Ayarı:** Seçilen lider modelin GridSearchCV ile optimize edilmesi.
5. **Nihai Test ve Hata Analizi:** Ayrılan bağımsız test seti üzerinde modelin çalıştırılması, Karmaşıklık Matrisi (Confusion Matrix) ve detaylı sınıflandırma raporunun oluşturulması.

## Kullanılan Teknolojiler

- **Dil:** Python 3
- **Veri Manipülasyonu:** Pandas, NumPy
- **Makine Öğrenmesi:** Scikit-Learn
- **Görselleştirme:** Matplotlib, Seaborn
- **Ortam:** Jupyter Notebook
