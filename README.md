# Motoko Hesap Makinesi Projesi

Bu proje, **Motoko** dilini kullanarak oluşturulmuş bir hesap makinesini içerir. Proje, toplama, çıkarma, çarpma ve bölme gibi temel matematiksel işlemleri gerçekleştirir. **Motoko Playground IDE** üzerinden projeyi inceleyebilir ve test edebilirsiniz.

## Proje Özeti

Bu hesap makinesi, asenkron fonksiyonlarla toplama, çıkarma, çarpma ve bölme işlemlerini gerçekleştirir. Ayrıca sonuç sıfırlama fonksiyonu da mevcuttur. Motoko'nun `actor` yapısı ve asenkron fonksiyonları kullanılarak modern bir hesap makinesi işlevselliği sağlanmıştır.

## Kullanılan Teknolojiler

- **Motoko**: İnternet Bilgisayarı (Internet Computer) için özel olarak geliştirilmiş bir dil.
- **Motoko Playground IDE**: Motoko projelerini online olarak yazıp test edebileceğiniz bir platform.

## Projeyi İncelemek için Bağlantı

Projenin canlı bir versiyonunu Motoko Playground'da inceleyebilirsiniz:

[Proje URL'si](https://play.motoko.org/?tag=3418880261)

## Kod Parçaları

### Hesap Makinesi Aktörü

Aşağıda hesap makinesi için oluşturulmuş `actor` yapısına ait fonksiyonlar yer almaktadır.

```motoko
actor hesap_makinesi {
  
  var sonuc: Int = 0;

  // Toplama işlemini gerçekleştiren fonksiyon
  public func toplama_islemi(sayi: Int) : async Int {
    sonuc += sayi;
    sonuc;
  };

  // Çıkarma işlemini gerçekleştiren fonksiyon
  public func cikarma_islemi(sayi: Int) : async Int {
    sonuc -= sayi;
    sonuc;
  };

  // Çarpma işlemini gerçekleştiren fonksiyon
  public func carpma_islemi(sayi: Int) : async Int {
    sonuc *= sayi;
    sonuc;
  };

  // Bölme işlemini gerçekleştiren fonksiyon
  public func bolme_islemi(sayi: Int) : async ?Int {
    if (sayi == 0) {
      null;  // Sıfıra bölme kontrolü
    } else {
      sonuc /= sayi;
      ?sonuc;
    }
  };

  // Sonucu sıfırlayan fonksiyon
  public func temizle(): async () {
    sonuc := 0;
  };
};
