#Scoped Yapısı ve  Hkk

Projemizdeki yaşam süresini sağlar, performasınızı + yönde ve - eksi yönde etkileyecektir.

***@ApplicationScoped*** yapısıda zaten bütün uygulama boyunca çalışıyor.
***@RequestScoped*** yapısıda sadece 1 istek boyunca yaşamaktadır. İlk istekte cevap verir ve bu cevap sonunda ölür.
***@SessionScoped*** 1 kullanıcı için yaşar ancak logout olunca çıkışını sağlamış oluruz.
***@Dependent*** yapısı hangi yapıdaysa onu sağlar, tıpkı bukalemun gibidir.


