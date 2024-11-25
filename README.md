* **Veriyi İndir ve Yapıyı İncele** 
GTSRB veri setini resmi web sitesinden veya Kaggle’dan indirebilirsiniz. Kaggle'dan https://www.kaggle.com/datasets/meowmeowmeowmeowmeow/gtsrb-german-traffic-sign/data adresinden indirebilirsiniz ya da pytorch'un içindeki datasetlerin içerisinde bulabilirsiniz.
Veriler genellikle train ve test klasörleri içinde organize edilmiştir. Klasör yapısı şu şekilde olabilir:
**GTSRB/**
* ├── Train/
* │   ├── 00000/ (Sınıf 0)
* │   ├── 00001/ (Sınıf 1)
* │   └── ...
* └── Test/ 
*    ├── 00000/ (Sınıf 0)
*    ├── 00001/ (Sınıf 1)
*    └── ...
* **PyTorch Dataset ve DataLoader Yapısı**
PyTorch’ta bir veri setini yüklemek için genellikle torch.utils.data.Dataset ve DataLoader kullanılır.
Dataset sınıfını tanımlarken:
Veri yollarını ve etiketleri (labels) okuyacak bir mantık ekle.
Görüntüleri okumak için Pillow veya benzeri kütüphaneleri kullan.
Veri setine gerekirse transform işlemleri uygula (örneğin normalizasyon, yeniden boyutlandırma).

* **Görüntü İşleme (Transforms)**
PyTorch'un torchvision.transforms modülü ile:
Görüntüleri yeniden boyutlandır (örneğin, 32x32).
Normalizasyon uygula.
Veriyi tensor haline getir.
Örnek işlem adımları:
Resize (örn. transforms.Resize((32, 32)))
ToTensor (örn. transforms.ToTensor())
Normalize (örn. transforms.Normalize(mean, std))

* **Dataset'i Özelleştir (Custom Dataset)**
PyTorch’un Dataset sınıfını miras alarak:
__init__: Veri yollarını ve etiketleri yükle.
__len__: Veri setindeki örnek sayısını döndür.
__getitem__: İstenilen indeksteki görüntüyü ve etiketini döndür.

* **DataLoader ile Veriyi Yükle**
Dataset sınıfını torch.utils.data.DataLoader ile besleyerek:
Batch boyutunu ayarla (örn. batch_size=64).
Veriyi karıştır (örn. shuffle=True).
Çoklu iş parçacığı kullanarak yükleme hızını artır (örn. num_workers=4).

* **Veri Setini Eğitim ve Test için Böl**
Eğitim ve test için ayrı Dataset nesneleri oluştur.
Eğer veri setini rastgele bölmek gerekiyorsa, PyTorch'un SubsetRandomSampler veya random_split metodunu kullan.
