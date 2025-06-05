# # 🌾 Pirinç Yaprağı Hastalıklarının Derin Öğrenme ile Sınıflandırılması

Bu projede, pirinç yapraklarında sık görülen dört hastalığın görüntü işleme ve transfer öğrenme ile sınıflandırılması amaçlanmıştır. Önceden eğitilmiş dört farklı CNN mimarisi kullanılarak karşılaştırmalı bir analiz yapılmıştır.

---

## 📁 Veri Kümesi

Veri seti Kaggle üzerinden temin edilmiştir:  
🔗 [Rice Leaf Disease Image Dataset](https://www.kaggle.com/datasets/nirmalsankalana/rice-leaf-disease-image)

İçerdiği sınıflar:
- Bacterial Blight
- Blast
- Brown Spot
- Tungro

---

## 🧠 Kullanılan Modeller

Aşağıdaki pre-trained modeller kullanılarak transfer learning yapılmıştır:

- ✅ Xception  
- ✅ MobileNet  
- ✅ VGG16  
- ✅ DenseNet121

Her modelin son katmanları yeniden düzenlenmiş ve Softmax sınıflandırıcı ile bitirilmiştir.

---

## 🔧 Eğitim Ayarları

| Parametre          | Değer                  |
|--------------------|------------------------|
| Eğitim / Doğrulama | %80 / %20 (`validation_split=0.2`) |
| Görsel Boyutu      | 224 x 224 piksel       |
| Epoch              | 10                     |
| Batch Size         | 32                     |
| Optimizasyon       | Adam                   |
| Ortam              | Google Colab           |
| Framework          | TensorFlow / Keras     |

---

## 🧪 Veri Artırma (Augmentation)

Eğitim verileri çeşitlendirilerek overfitting riski azaltılmıştır:

```python
ImageDataGenerator(
    rescale=1./255,
    validation_split=0.2,
    rotation_range=15,
    width_shift_range=0.1,
    height_shift_range=0.1,
    horizontal_flip=True
)
```

---

## 📈 Performans Takibi

Her model için şu grafikler üretilmiştir:
- ✅ Doğruluk (Validation Accuracy)
- ✅ Eğitim Kaybı (Training Loss)
- ✅ Doğrulama Kaybı (Validation Loss)

Eğitim süreçleri `history` nesnesiyle kaydedilmiştir. Doğruluklar bar grafiklerle karşılaştırılmıştır.

---

## 📝 Sonuçlar

| Model       | En Yüksek Doğruluk (%) | Açıklama                      |
|-------------|-------------------------|-------------------------------|
| Xception    | 97.8                    | Yüksek başarı ve dengeli      |
| MobileNet   | 100.0                   | Çok iyi sonuç (aşırı uyum riski olabilir) |
| VGG16       | 80.9                    | En düşük performans           |
| DenseNet121 | 97.7                    | Kararlı ve dengeli            |

---

## 🧑‍💻 Geliştiriciler

| İsim               | Sorumluluklar |
|--------------------|----------------|
| **Haticenur Yalman** | Veri önişleme, MobileNet & DenseNet modelleri, augmentation |
| **Selcan Çelikel**   | Xception & VGG modelleri, grafikler, analiz, karşılaştırma |

---

## 🚀 Projeyi Çalıştırmak İçin

```bash
git clone https://github.com/kullanici-adi/rice-leaf-disease.git
cd rice-leaf-disease
pip install -r requirements.txt
```

Google Colab'da `Rice_Leaf_Classification.ipynb` dosyasını açarak tüm işlemleri çalıştırabilirsiniz.

---

## 📜 Lisans

Bu proje yalnızca akademik ve eğitim amaçlıdır. Ticari kullanım için izin gereklidir. Lütfen kaynak belirtiniz.

---

## 🙏 Teşekkür

Veri kümesini sağlayan Kaggle kullanıcılarına ve TensorFlow/Keras topluluğuna teşekkür ederiz.
