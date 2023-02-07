# @Produces Anotasyonu nedir ve ne zaman kullanılmalıdır?

***@Produces*** bizim tüketmemiz için öncelikle üretmemiz lazım bundan dolayı, önce ***@Produces*** yapısını kullanarak veri üreteceğiz daha sonrada başka yerde bu yapıyı tüketeceğiz.

  Örnek vermek gerekirse;
  
  ```
  public List <String> getList() {
    List<String> liste=new ArrayList<>();
    liste.add("Html5");
    liste.add("css3");
    liste.add("js");
    liste.add("react");
    liste.add("angular");
    return liste;
```
_Patika Java Spring Boot Eğitiminden Alıntılanmıştır_

Normal şartlarda her bir Java sınıfı, CDI tarafından enjecte edilebilinir bir CDI nesnesidir.
Bizler metod dönüşlerindeki değerlerinde enjecte edilebilir olması için @Produces notasyonunu sunmaktadır

Örnek vermek gerekirse alltaki diyagram üzerinden 

  ![cdi-weld-4](https://user-images.githubusercontent.com/109916927/217355510-fb14b39c-4d2b-480e-b0a7-6a1ea46a9a1f.png)

şu şekilde bir kodlama yapabiliriz:

```
@Default
public class Otobus implements Arac {

    @Inject
    @Hiz // Hangi Integer?
    private Integer hiz;

    public String calis() {
        return "Otobus "+ hizSoyle() +" km. hızında çalışıyor..";
    }

    public int hizSoyle(){
        return this.hiz;
    }

}

public class Uretec {

@Hiz // Buradan üretilen Integer
@Produces
 public Integer uret() {
 return ThreadLocalRandom.current().nextInt(20, 160);
 }

/* veya

@Hiz
@Produces
private int hiz = ThreadLocalRandom.current().nextInt(20, 160);
*/

}

```

Uretec sınıfının -uret()- metodunun başındaki ***@Produces*** notasyonu vasıtasıyla -uret()- metodundan gelecek veriyi, CDI ortamı tarafından enjecte edilebilir bir veri adyı olarak işaretlenebiliyor.


_https://kodedu.com/2013/07/cdi-produces-new-ve-postconstruct-notasyonlari/  Tarafından alıntı yapılmıştır_


