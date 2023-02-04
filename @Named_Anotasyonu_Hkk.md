# @Named Anotasyonu @Provides Anotasyonu Varken Ne İşe Yarar?

***@Provides*** anotasyonu aynı tipte olan nesneler için yalnızca bir kere işlem yapabilir. Alttaki örnek üzerinden açıklamasını yapabiliriz.

```
 data class Car(val type: String)

 class MainActivity : AppCompatActivity() {
    @Inject
    lateinit var sedan: Car
 
    @Inject
    lateinit var sports: Car
 
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(...)
 
    }
}
```  

***CarModule.kt*** dosyasında da alttaki gibi provide ettiğimizi düşünün

```
@Module

class CarModule {
 
    @Provides
    fun provideSedan(): Car = Car("Sedan")
 
    @Provides
    fun provideSports(): Car = Car("Sports")
}
```
Bu şekildeki bir kod bloğunu çalıştırdığınızda hata alacaksınız çünkü  ***@Provides*** anotasyonu sadece ***TEK BİR NESNEYİ PROVİDE EDEBİLİR***.

Çözüm için ***@Name*** anotasyonunu kullanacağız.

***CarModule.kt*** dosyasını tekrar yazalım fakat bu sefer @Name anotasyonunu kullanarak deneyelim.

```
@Module
class CarModule {
 
    @Provides
    @Named("sedan")
    fun provideSedan(): Car = Car("Sedan")
 
    @Provides
    @Named("sports")
    fun provideSports(): Car = Car("Sports")
}
```

Daha sonra gene MainActivity üzerinde inject ettiğimiz değerlere yine ***@Named*** ile hangisini istediğimizi söylüyoruz.

```
class MainActivity : AppCompatActivity() {
    @Inject
    @field:Named("sedan")
    lateinit var sedan: Car
 
    @Inject
    @field:Named("sports")
    lateinit var sports: Car
 
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(...)
 
    }
}
```


Şimdi sistem bunların birbirlerinden farklı 2 nesne olduğunu anlayacak ve inject işlemlerinde herhangi bir hata ile karşılaşmayacaksınız.

***ÖNEMLİ BİR NOT***

***@Named*** Anotasyonuun kaynak kodlatına bakıldığında aslında bunun bir niteleme anotaysonu ***@Qualifier*** anotasyonu olduğunu görüyoruz.

Yani bizlerde aslında kendi Custon Anotasyonumuzu oluşturabiliriz.




_http://emre-kose.net/dagger2-qualifier-ve-named-annotation/_ _Sitesinden Alıntılanmıştır_


