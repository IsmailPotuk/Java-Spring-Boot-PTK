# @New Anotasyonu Çalışma Mantığı

***@New*** Anotasyonu aslen javax.enterprise.inject paket yapısı altında bulunan özel bir seçici notasyondur.

Allta verilen kod üzerinden sizlere gerekli açıklamaları yapalim.

```
public class Galeri {

    @Inject
    @New(value=Araba.class) // new Araba(); gibi
    private Arac arac;

    @Inject
    @New(Otobus.class) // new Otobus(); gibi
    private Arac tasit;

    @Inject
    @New // new Arac(); gibi. Hata!!
    private Arac motorlu;

    public static void main(String[] args) {

    Weld weld = new Weld();
    WeldContainer konteyner = weld.initialize();
    Galeri galeri = konteyner.instance().select(Galeri.class).get();

    String aracMesaj = galeri.arac.calis();
    System.out.println("> " + aracMesaj);

    String tasitMesaj = galeri.tasit.calis();
    System.out.println("> " + tasitMesaj);

    }
}
```
Galeri sınıfı içerisinde @Inject notasyonu kullanan üç global alan vardır. Bunların hemen hemen hepsi Arac arayüzütüründendir. CDI konteyner ortamında Arac arayüzü türünden iki adet enjecte edilebilir tip vardır, bunlar Araba ve Otobüs'tür.

Bundan dolayı bir biçimde Araba mı yoksa Otobüs mü hangi nesnesinin mi hangisinin enjecte edileceği seçilmelidir.

Tıpkı diğer klasik seçiciler gibi gömülü seçici olan ***@New***'de kullanılabilinir.

***@New*** notasyonu hangi türden nesnenin seçileceğini tayin etmektedir.

_https://kodedu.com/2013/07/cdi-produces-new-ve-postconstruct-notasyonlari/ sitesinden alıntı yapılmıştır_


