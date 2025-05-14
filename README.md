# Akbank-Makine-ogrenmesi-Bootcamp-Yeni-Nesil-Proje-Kampi

# 🏠 California Housing Price Prediction

Bu proje, **Akbank Yeni Nesil Proje Kampı - Makine Öğrenmesi Bootcamp** kapsamında geliştirilmiştir. Amaç, **California'daki konut fiyatlarını tahmin etmek** için gözetimli makine öğrenmesi tekniklerini kullanmaktır. Projede regresyon modelleri test edilmiş ve en iyi sonuç veren model hiperparametre optimizasyonu ile geliştirilmiştir.

---

## 🔍 Problem Tanımı

Verilen özellikler (örneğin, evin bulunduğu konum, nüfus yoğunluğu, hane halkı geliri vs.) kullanılarak, **median_house_value** değişkeninin tahmin edilmesi hedeflenmektedir. Bu bir **sürekli değişken tahmini (regresyon)** problemidir.

---

## 📊 Veri Seti

- **Kaynak**: [Kaggle - California Housing Prices](https://www.kaggle.com/datasets/camnugent/california-housing-prices)
- **Dosya**: `/kaggle/input/california-housing-prices/housing.csv`
- **Boyut**: 20.6 MB (10 MB üzeri, kriteri karşılıyor)
- **Veri Noktası Sayısı**: 20,640 satır (10,000 üzeri, kriteri karşılıyor)
- **Hedef Değişken**: `median_house_value`

---

## 🧪 Kullanılan Adımlar

### 1. Keşifsel Veri Analizi (EDA)
- Veri setindeki eksik değerler analiz edildi (`total_bedrooms` sütununda eksikler vardı, median ile dolduruldu).
- Sayısal değişkenler arasındaki korelasyonlar `seaborn` ve `matplotlib` kullanılarak incelendi.
- `median_income` değişkeninin hedef değişkenle yüksek korelasyon taşıdığı tespit edildi.

### 2. Veri Ön İşleme
- `total_bedrooms` sütunundaki eksik veriler median ile dolduruldu.
- Kategorik `ocean_proximity` sütunu `One-Hot Encoding` ile dönüştürüldü.
- Eğitim ve test seti %80-%20 oranında ayrıldı (`train_test_split`).
- Normalizasyon uygulanmadı çünkü seçilen model olan `RandomForestRegressor` buna ihtiyaç duymaz.

### 3. Model Seçimi
- `RandomForestRegressor` seçildi çünkü:
  - Özellik mühendisliği ve ölçekleme zorunluluğu yoktur.
  - Aykırı değerlere karşı toleranslıdır.
  - Orta büyüklükte veri setlerinde başarılı sonuçlar verir.

### 4. Hiperparametre Optimizasyonu
Aşağıdaki parametre aralıklarıyla `GridSearchCV` uygulandı:

```python
param_grid = {
    'n_estimators': [50, 100, 150],
    'max_depth': [None, 10, 20],
    'min_samples_split': [2, 5]
}
```
En iyi sonuç veren parametre kombinasyonu ile model yeniden eğitildi.

5. Model Değerlendirme
Model test verisi üzerinde şu sonuçları verdi:

Metrik	Değer
MAE (Mean Absolute Error)	≈ 22,160
RMSE (Root Mean Squared Error)	≈ 33,948
R² (Determination Coefficient)	≈ 0.81

⚙️ Kullanılan Kütüphaneler
pandas, numpy

matplotlib, seaborn

scikit-learn

📎 Proje Bağlantıları

📘 Kaggle Notebook: https://www.kaggle.com/code/emrekonce/notebook8c37961ff8

💡 Gerçek Hayatta Uygulama Alanları
Bu tarz modeller:

Emlak piyasasında fiyat analizleri,

Yatırım yapılacak bölgelerin belirlenmesi,

Konut kredisi risk tahmini gibi alanlarda kullanılabilir.

🚀 Proje Nasıl Geliştirilebilir?
Derin öğrenme modelleriyle karşılaştırmalı çalışma yapılabilir.

Güncel, daha geniş çaplı konut veri setleriyle test edilebilir.

Web tabanlı kullanıcı arayüzü ile son kullanıcıya fiyat tahmini sunulabilir.

Özellik mühendisliğiyle yeni öznitelikler türetilebilir.



