# Telco-Customer-Churn-Prediction-Project

# 📊 Telco Customer Churn Prediction

## 🎯 Proje Amacı

Bu projede, bir telekomünikasyon şirketinin müşteri kaybını (churn) tahmin etmek için veri analizi ve makine öğrenmesi teknikleri uygulandı.  
Amaç, hangi müşterilerin hizmeti bırakma eğiliminde olduğunu erken tespit ederek şirketin stratejik aksiyonlar almasına destek olmaktır.

---

## 📁 Veri Seti Bilgisi

- **Toplam Gözlem:** 7043  
- **Toplam Değişken:** 21  
- **Hedef Değişken:** `Churn` (Yes / No)  
- **Kaynak:** [IBM Telco Customer Churn Dataset on Kaggle](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)

---

## 🧼 Veri Ön İşleme

- `TotalCharges` sütunundaki boş/bozuk veriler tespit edilerek temizlendi.  
- Kategorik veriler one-hot encoding ile modele uygun hale getirildi.  
- `customerID` gibi anlamlı bilgi taşımayan sütunlar kaldırıldı.  

---

## 📊 EDA (Keşifsel Veri Analizi)

Aşağıdaki değişkenlerin churn üzerindeki etkileri görselleştirildi ve yorumlandı:

- `Contract` tipi  
- `InternetService` türü  
- `MonthlyCharges`, `Tenure`  
- `OnlineSecurity`, `PaymentMethod`, `TechSupport`

> Bu adımda verinin genel eğilimleri ve churn’e etki eden faktörler ilk kez fark edildi.

---

## 🤖 Modelleme Süreci

Veri, %80 eğitim – %20 test olarak ayrıldı. Aşağıdaki modeller kullanıldı:

### 1. Logistic Regression
- Accuracy: **0.801**
- F1 Score: **0.60**
- AUC: **0.84**

### 2. Random Forest
- Accuracy: **0.79**
- F1 Score: **0.56**
- AUC: **0.82**

### 3. XGBoost (Varsayılan Parametreler)
- Accuracy: **0.77**
- F1 Score: **0.54**
- AUC: **0.81**

### 4. XGBoost (GridSearchCV ile Optimizasyon)
- Accuracy: **0.80**
- F1 Score: **0.58**
- AUC: **0.84**
- Best Params: `{'learning_rate': 0.1, 'max_depth': 3, 'n_estimators': 100, ...}`

---

## 🔍 Feature Importance (Öznitelik Önemi)

XGBoost modeline göre en etkili değişkenler:

- `InternetService_Fiber optic`
- `Contract_Two year`
- `tenure`
- `OnlineSecurity_Yes`
- `PaymentMethod_Electronic check`

> Bu analiz, iş birimlerine rehber olacak stratejik kararların veriyle alınmasını sağlar.

---

## 📊 Model Karşılaştırma Tablosu

| Model               | Accuracy | Precision | Recall | F1 Score | AUC  |
|--------------------|----------|-----------|--------|----------|------|
| Logistic Regression| 0.801    | 0.64      | 0.57   | 0.60     | 0.84 |
| Random Forest       | 0.79     | 0.63      | 0.51   | 0.56     | 0.82 |
| XGBoost (Default)   | 0.77     | 0.57      | 0.52   | 0.54     | 0.81 |
| XGBoost (Tuned)     | 0.80     | 0.64      | 0.53   | 0.58     | 0.84 |

---

## 💡 İş Önerileri & Sonuç

- **Fiber optik kullanıcıları** churn’e daha yatkın → memnuniyet odaklı kampanyalar planlanabilir.  
- **Kısa sözleşmeli müşteriler** churn riski taşıyor → uzun vadeli sözleşme avantajları sunulmalı.  
- **OnlineSecurity hizmeti** churn’ü azaltan bir faktör → bu hizmete erişim artırılmalı.  

> Proje sonucunda geliştirilen model, churn riski yüksek müşterileri önceden belirlemek ve aksiyon almak için güvenilir bir tahmin aracı sunmaktadır.

---

## 🛠️ Kullanılan Kütüphaneler

- Python
- Pandas / NumPy  
- Seaborn / Matplotlib  
- Scikit-learn  
- XGBoost  

---

## ✍️ Kendi Gözümden

Bu proje sayesinde, gerçek bir iş problemini veriyle analiz edip çözüm üretme becerimi pekiştirdim.  
Modellerin sadece doğruluk değil; **F1, AUC, yorumlanabilirlik gibi boyutlarla** da değerlendirilmesi gerektiğini uygulamalı olarak deneyimledim.
