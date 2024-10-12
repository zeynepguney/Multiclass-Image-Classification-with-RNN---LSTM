# Multiclass-Image-Classification-with-RNN---LSTM

Bu proje, TensorFlow ve Keras kullanarak MNIST el yazısı rakam veri seti üzerinde LSTM (Uzun Kısa Süreli Bellek) modelini eğitmek ve test etmek üzerine kurulmuştur. MNIST veri seti, el yazısı ile yazılmış rakamların 28x28 piksel boyutunda görüntülerini içerir ve her görüntü 0'dan 9'a kadar bir rakamı temsil eder.

## Proje İçeriği
TensorFlow ve Keras kullanılarak LSTM modeli oluşturulmuştur.
Model, el yazısı ile yazılmış rakamları tanımak üzere eğitilmiş ve test edilmiştir.
Model eğitimi sırasında eğitim ve doğrulama verilerinin doğruluk ve kayıp değerleri izlenmiştir.
Sonuçlar doğruluk ve kayıp grafiklerinde görselleştirilmiş, ayrıca bir karışıklık matrisi ile modelin performansı değerlendirilmiştir.

### Projeyi çalıştırabilmek için aşağıdaki kütüphanelere ihtiyaç vardır:

* TensorFlow 2.x
* NumPy
* Pandas
* Matplotlib
* Scikit-learn

Gerekli kütüphaneleri yüklemek için şu komutu kullanabilirsiniz:

```pip install tensorflow numpy pandas matplotlib scikit-learn```

### Veri Seti
MNIST veri seti, TensorFlow Keras kütüphanesi içinde hazır olarak gelmektedir. Bu veri seti, eğitim ve test için iki ayrı kısımdan oluşur:
60.000 eğitim görüntüsü
10.000 test görüntüsü
Her bir görüntü 28x28 piksel boyutundadır ve gri tonlamalıdır.

#### Model Mimarisi

##### LSTM Katmanları:

İlk LSTM katmanı 128 birime sahip ve giriş şekli (28, 28) olan dizileri alır. Aktivasyon fonksiyonu relu olarak belirlenmiştir ve return_sequences=True ile sonraki LSTM katmanına diziler aktarılır.
İkinci LSTM katmanı da 128 birimlidir ve dizileri tek bir çıktı vektörüne dönüştürür.
##### Dropout Katmanları:
Overfitting'i önlemek amacıyla her LSTM katmanından sonra %20 dropout uygulanmıştır.
##### Yoğun Katman (Dense):
İlk yoğun katman, 32 birime sahip ve relu aktivasyon fonksiyonu kullanır.
İkinci yoğun katman, 10 sınıf için softmax aktivasyon fonksiyonu ile nihai çıktı verir.

## Modelin Derlenmesi

* Optimizasyon: Adam
* Öğrenme Oranı: 0.001
* Kayıp Fonksiyonu: sparse_categorical_crossentropy
* Değerlendirme Metrikleri: Doğruluk (accuracy)

## Modelin Eğitimi
Model, eğitim verisi üzerinde 10 epoch boyunca eğitilmiştir. Eğitim sırasında doğrulama verisi (test verisi) kullanılarak her epoch'tan sonra modelin doğruluğu ve kaybı izlenmiştir.

## Sonuçlar
Modelin performansı, eğitim ve test verileri üzerinde değerlendirildi. Eğitim süreci sonunda modelin doğruluğu yaklaşık %98.89'a ulaştı. Ayrıca modelin performansı karışıklık matrisi ile de incelenmiştir.

### Grafikler
Eğitim ve doğrulama doğruluğu ile kayıp değerleri grafik olarak görselleştirilmiştir. Bu grafikler, modelin nasıl öğrendiğini ve doğrulama verisi üzerinde ne kadar başarılı olduğunu gösterir.
confusion_matrix
Modelin sonuçları, sklearn.metrics.confusion_matrix ile hesaplanmıştır. Bu matris, her sınıf için doğru ve yanlış tahmin edilen değerleri gösterir.

## Sonuçlar
Eğitim Doğruluğu: %98.97
Test Doğruluğu: %98.89
