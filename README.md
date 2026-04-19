# Makine Öğrenmesi — Ara Sınav Ödevi

**Breast Cancer Wisconsin** veri seti üzerinde klasik makine öğrenmesi algoritmaları, boyut indirgeme (PCA & LDA) ve açıklanabilir yapay zeka (SHAP) analizi.

> **Üsküdar Üniversitesi** — Yapay Zeka Mühendisliği Yüksek Lisans Programı
> Makine Öğrenmesi Dersi Ara Sınav Ödevi

---

## 📋 Proje Özeti

Bu çalışmada **569 örnek** ve **30 özellik** içeren *Breast Cancer Wisconsin* veri seti üzerinde:

- ✅ Veri kalite kontrolleri (eksik değer, aykırı değer, dtype)
- ✅ Keşifsel veri analizi (istatistikler, Pearson korelasyon, boxplot)
- ✅ `StandardScaler` ile ölçeklendirme (leakage-safe)
- ✅ Stratified split (%70 train / %10 validation / %20 test)
- ✅ **PCA** (6 bileşen, %89.19 varyans) ve **LDA** (1 bileşen) ile boyut indirgeme
- ✅ **5 algoritma × 3 veri temsili = 15 model** eğitimi
- ✅ Validation & test metrikleri (Accuracy, Precision, Recall, F1, ROC-AUC)
- ✅ Confusion matrix + ROC eğrisi
- ✅ **SHAP** ile açıklanabilirlik analizi (klinik yorum)

---

## 🏆 Sonuçlar

### En İyi Model: `Logistic Regression / raw`

| Metrik | Validation | Test |
|--------|:---:|:---:|
| **Accuracy** | 0.9649 | **0.9737** |
| **Precision** | 0.9722 | **0.9726** |
| **Recall** | 0.9722 | **0.9861** |
| **F1-score** | 0.9722 | **0.9793** |
| **ROC-AUC** | 0.9960 | **0.9947** |

**Confusion Matrix (Test Seti — 114 örnek):**
- TN = 40, FP = 2, FN = 1, TP = 71
- **Sadece 3 yanlış sınıflandırma** 🎯

### SHAP — En Önemli 5 Özellik

1. `worst texture` (|SHAP| = 0.868)
2. `worst radius` (|SHAP| = 0.845)
3. `worst area` (|SHAP| = 0.827)
4. `worst concave points` (|SHAP| = 0.773)
5. `worst perimeter` (|SHAP| = 0.712)

> Modelin ağırlıklı olarak **"worst" (en kötü)** ölçümlere odaklanması, kötü huylu tümörlerin tipik olarak düzensiz, büyük ve içbükey yapıya sahip olmasıyla **klinik açıdan tutarlıdır**.

---

## 📁 Dosya Yapısı

```
.
├── MakineOgrenmesiVize.ipynb                        # Ana Colab notebook (10 bölüm)
├── MakineOgrenmesi_Rapor_IbrahimKeremGUMUS.docx    # Word raporu
└── README.md                                         # Bu dosya
```

---

## 🧪 Kullanılan Kütüphaneler

| Kütüphane | Kullanım |
|-----------|----------|
| `pandas`, `numpy` | Veri manipülasyonu |
| `matplotlib`, `seaborn` | Görselleştirme |
| `scikit-learn` | Ön işleme, PCA, LDA, modeller, metrikler |
| `xgboost` | XGBoost sınıflandırıcısı |
| `shap` | Açıklanabilir yapay zeka (XAI) |

---

## 🚀 Notebook'u Çalıştırmak

### Google Colab ile (önerilen)

1. `MakineOgrenmesiVize.ipynb` dosyasına tıkla
2. Sağ üstteki **"Open in Colab"** butonuna bas
3. `Runtime → Run all` ile tüm hücreleri çalıştır

### Yerel ortam

```bash
pip install numpy pandas matplotlib seaborn scikit-learn xgboost shap
jupyter notebook MakineOgrenmesiVize.ipynb
```

---

## 📊 Notebook İçeriği (10 Bölüm)

| # | Bölüm |
|---|-------|
| 1 | Veri setinin yüklenmesi |
| 2 | Veri kalite kontrolleri (missing value, IQR outlier, dtype) |
| 3 | Keşifsel veri analizi (EDA) |
| 4 | Veri ölçeklendirme (StandardScaler) |
| 5 | Stratified train/validation/test split |
| 6 | PCA & LDA boyut indirgeme |
| 7 | 15 modelin eğitimi (5 algoritma × 3 temsil) |
| 8 | Validation performans karşılaştırması |
| 9 | En iyi modelin test değerlendirmesi + Confusion Matrix + ROC |
| 10 | SHAP ile açıklanabilirlik analizi (Zorunlu) |

---

## 🔑 Anahtar Bulgular

- 🎯 **Doğrusal model üstünlüğü**: Logistic Regression, XGBoost ve Random Forest gibi karmaşık modelleri geride bıraktı (verinin doğrusal ayrılabilirlik özelliği yüksek).
- 📉 **PCA neredeyse kayıpsız**: 30D → 6D indirgemede ROC-AUC sadece **-0.0013** düştü.
- 🧬 **LDA tek bileşenle güçlü**: İkili sınıflandırma kısıtı nedeniyle sadece 1 bileşen üretilebilse de 0.95+ ROC-AUC korundu.
- ✅ **Overfitting yok**: Test metrikleri validation'a çok yakın (hatta çoğunda daha iyi).
- 🩺 **Klinik uyum**: SHAP, modelin tıbbi olarak anlamlı özelliklere odaklandığını doğruladı.

---

## 📄 Lisans

Bu ödev akademik amaçlıdır.
