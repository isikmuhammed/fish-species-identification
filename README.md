# CNN ile Balık Türü Tanıma

Bu depo, Convolutional Neural Networks (CNN) kullanarak balık türlerinin tanımlanması için bir derin öğrenme modeli içerir. Projenin amacı, balık türlerini görüntü verilerine dayanarak sınıflandırmaktır.

## Proje Genel Bakış

Balık türlerinin sınıflandırılması, ekolojik izleme, deniz biyoçeşitlilik çalışmaları ve balıkçılık yönetimi gibi çeşitli uygulamalarda kritik bir görevdir. Bu projede, balık türlerini otomatik olarak tanımak için bir CNN modeli kullanılmıştır.

## Veri Seti

Bu projede çeşitli balık türlerinin görüntülerinden oluşan bir veri seti kullanılmıştır. Veri seti üç ana bölüme ayrılmıştır:
- Eğitim seti
- Doğrulama seti
- Test seti

### Veri Artırma (Data Augmentation)
Modelin genelleme yeteneğini artırmak için şu veri artırma teknikleri uygulanmıştır:
- Yatay ve dikey çevirme
- Rastgele döndürme
- Ölçeklendirme ve yakınlaştırma

## Model Mimarisi

Model, Keras derin öğrenme çerçevesi kullanılarak aşağıdaki mimari ile oluşturulmuştur:
- **Convolutional Katmanlar**: Giriş görüntülerinden özellik çıkarımı yapmak için kullanılır.
- **Max-Pooling Katmanları**: Özellik haritalarını alt örneklemek için kullanılır.
- **Dropout Katmanları**: Aşırı uyumlamayı (overfitting) önlemek için kullanılır.
- **Yoğun (Dense) Katmanlar**: Nihai sınıflandırma için tam bağlı katmanlardır.

### Model Özeti

```python
Model: "sequential"
_________________________________________________________________
Layer (type)                 Output Shape              Param #   
=================================================================
conv2d_1 (Conv2D)            (None, 128, 128, 32)      896       
...
dense_2 (Dense)              (None, 10)                2570      
=================================================================
Toplam parametreler: 2,517,466
Eğitilebilir parametreler: 2,517,466
Eğitilemeyen parametreler: 0
_________________________________________________________________
```

Eğitim Süreci
Model, aşağıdaki ayarlarla 20 epoch boyunca eğitilmiştir:

Optimizasyon Yöntemi: Adam
Kayıp Fonksiyonu: Categorical Crossentropy
Metrikler: Eğitim ve doğrulama için doğruluk (accuracy) ve kayıp (loss).
Performans
20 epoch sonunda model şu sonuçlara ulaşmıştır:

Training Accuracy: 97.2%
Validation Accuracy: 97.4%
Training Loss: 0.0847
Validation Loss: 0.0835

Eğitim süreci boyunca eğitim ve doğrulama doğrulukları ve kayıpları izlenmiş ve görselleştirilmiştir.

Projeyi Çalıştırma
 1-Bu depoyu klonlayın:
 ```python
 git clone https://github.com/yourusername/fish-species-identification.git
cd fish-species-identification
```
 2-Jupyter Notebook'u çalıştırarak modeli eğitin ve değerlendirin.

### Sonuçlar

Son model, doğrulama setinde %97.4 doğrulukla yüksek bir performans sergilemiştir. Eğitim süreci, aşırı uyumlamanın (overfitting) minimize edilmesi ve veri artırma tekniklerinin kullanımıyla doğruluğun düzenli olarak arttığını göstermektedir.

### Kaggle Linki
https://www.kaggle.com/code/isikmuhammed/fish-species-identification
