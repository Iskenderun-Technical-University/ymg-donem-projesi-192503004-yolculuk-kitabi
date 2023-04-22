                                  Yolculuk Kitabı Uygulaması

Yolculuk kitabı, yolculuk yapanlar ve gezginler için oluşturulmuş, iOS platformu üzerinde çalışan, Swift dilinde ve Xcode kullanılarak geliştirilmiş bir uygulamadır. Uygulama, kullanıcıların gezdikleri veya gitmeyi planladıkları yerlerin adlarını ve bu yerlere ait yorumlarını ekleyip, daha sonra bu bilgilere kolayca ulaşabilecekleri şekilde kaydetmelerine olanak tanır.

                                   Özellikler

Navigasyon: Uygulama içinde yer alan iki ekran arasında, kullanıcı dostu bir navigasyon sunar. Kullanıcılar, yerlerin listelendiği ana ekrandan, yeni yer ekleme ekranına kolaylıkla geçiş yapabilirler.

Yer Ekleme: Kullanıcılar, uygulama sayesinde yeni yerler ekleyebilir ve bu yerlere ait yorumlar yazabilirler. Yeni yerler eklemek için basit ve kullanıcı dostu arayüz sunar.

Harita Entegrasyonu: Kullanıcılar, eklemek istedikleri yerin konumunu, harita üzerinde basılı tutarak belirleyebilirler. Harita üzerinde belirlenen konumlar, eklenen yerlerle birlikte saklanır.

CoreData Entegrasyonu: Uygulama, eklenen yerlerin ve yorumların güvenli bir şekilde saklanması için CoreData entegrasyonu kullanır. Bu sayede kullanıcılar, uygulamayı kapatıp açtıklarında bile ekledikleri yerlere ve yorumlara erişebilirler.

Mekan Listesi: Uygulama ana ekranında, kullanıcıların eklediği mekanların listesini görüntüleyebilirsiniz. Bu liste, kullanıcıların daha önce eklediği yerlere kolaylıkla erişebilmelerini sağlar.




                                   Ekranlar ve İçerikleri

ListViewController: Bu ekran, kullanıcıların eklediği yerlerin listelendiği bir TableView içerir. Her satır, kullanıcı tarafından eklenen ve CoreData'da saklanan bir mekanı temsil eder. Her satırın sol tarafında mekanın adı ve sağ tarafında bir ok simgesi bulunur. Ok simgesine tıklayarak mekanın detaylarını görebilirsiniz. Sağ üst köşede bulunan "+" butonu ile yeni yer ekleme ekranına geçiş yapılır.

ViewContoller: Bu ekran, kullanıcıların yeni yerler eklemeleri için tasarlanmıştır. Aşağıdaki öğeleri içerir:
Mekan Adı TextField: Bu TextField, gidilmek istenen yerin adı için kullanılır. Kullanıcı buraya gidilecek mekanın adını yazmalıdır.
Yorumlar TextField: Bu TextField, gidilmek istenen yere ait yorumlar için kullanılır. Kullanıcı buraya mekanla ilgili düşüncelerini, ipuçlarını veya deneyimlerini yazabilir.
Harita: Bu harita, kullanıcıların gidilmek istenen yerin konumunu belirlemelerine olanak tanır. Harita üzerinde gidilmek istenen yeri belirlemek için kullanıcının basılı tutması gerekmektedir. Belirtilen konum, harita üzerinde bir pin ile işaretlenir.
Save Butonu: Bu buton, kullanıcının mekan adı, yorumlar ve harita üzerinde belirlenen konumu kaydetmesini sağlar. "Save" butonuna tıklandığında, girilen bilgiler CoreData'ya kaydedilir ve ListViewController'daki TableView'a eklenir. Kaydetme işlemi tamamlandıktan sonra, uygulama otomatik olarak ListViewController ekranına geri döner ve eklenen mekanın adı listeye eklenir.
Kullanıcılar, yeni yerler eklemek için sağ üst köşedeki "+" düğmesine tıklayarak açılan ViewController ekranında yer ve yorum bilgilerini girebilir. Gidilmek istenen yerin üzerine basılı tutarak yerin konumunu harita üzerinde işaretleyin. "Save" butonuna tıklayarak eklediğiniz yerin ve yorumun kaydedilmesini sağlayın.


<img width="1680" alt="VC Ekranları" src="https://user-images.githubusercontent.com/104498895/233783438-e199cd43-fc81-4ed2-bfd3-e90e32283197.png"> 









                                     ListViewController 
        
- baslikArray: [String]
- idArray: [UUID]
- secilmisBaslik: String 
- secilmisBaslikID: UUID?
- tableView: UITableView

----------------------------------------------------------------
+ viewDidLoad()
+ viewWillAppear(_ animated: Bool)
+ getData()
+ addButtonClicked()
+ tableView(_:numberOfRowsInSection:) -> Int
+ tableView(_:cellForRowAt:) -> UITableViewCell
+ tableView(_:didSelectRowAt:)
+ prepare(for segue: UIStoryboardSegue, sender: Any?)


İlk diyagram, "ListViewController" adlı sınıfın özelliklerini ve işlevlerini gösterir. Bu sınıf, kullanıcıların gitmek istedikleri yerleri listelemelerine ve kaydetmelerine olanak tanır. Sınıfın içinde, "baslikArray" ve "idArray" adında iki adet dizi vardır, bunlar yerlerin adlarını ve ID'lerini tutarlar. Bunun yanı sıra, "secilmisBaslik" ve "secilmisBaslikID" adında iki değişken, seçilen yerin adını ve ID'sini tutar. Sınıf, ayrıca Core Data kullanarak kaydedilmiş yerlerin listesini tableView'da görüntüler. Ek olarak, kullanıcıların yeni bir yer eklemelerine olanak tanıyan bir "+" butonu da vardır. Aşağıda Xcode platformu ile Iphone simulasyonu oluşturularak "ListViewController" adlı sınıfın UI karşığı vardır

<img width="474" alt="ListViewController" src="https://user-images.githubusercontent.com/104498895/233783755-31279161-3eaa-4d05-8746-194b703401da.png">





                                  ViewController                    
        
- nameText: UITextField
- commentText: UITextField
- mapView: MKMapView
- locationManager: CLLocationManager
- secilenEnlem: Double
- secilenBoylam: Double
- secilenBaslik: String
- secilenBaslikID: UUID?
- annotationBaslik: String
- annotationAltBaslik: String
- annotationEnlem: Double
- annotationBoylam: Double
----------------------------------------------------------------                             
+ viewDidLoad()
+ chooseLocation(gestureRecognizer: UILongPressGestureRecognizer)
+ locationManager(_ manager: CLLocationManager, didUpdateLocations locations: [CLLocation])
+ mapView(_:viewFor:) -> MKAnnotationView?
+ mapView(_:annotationView:calloutAccessoryControlTapped:)
+ saveButtonClicked(_ sender: Any)

İkinci diyagram, "ViewController" adlı sınıfın özelliklerini ve işlevlerini gösterir. Bu sınıf, kullanıcıların harita üzerinde bir yere tıklayarak o yeri kaydetmelerine olanak tanır. Kullanıcıların kaydettikleri yerler, "ListViewController" sınıfında listelenir. Sınıfın içinde "nameText" ve "commentText" adında iki adet textfield, kullanıcının eklediği yere ait isim ve yorum bilgisini alır. Ayrıca, "mapView" adında bir harita da bulunur. Sınıfın işlevleri arasında, kullanıcının dokunma hareketi ile harita üzerinde bir noktaya bir pin yerleştirmesi ve yerin adı ve yorumu ile birlikte kaydetmesi vardır. Sınıf ayrıca, kullanıcının kaydedilen yere tıkladığında yön bulma özelliği de sunar. Aşağıda ise yine Xcode platformu ile Iphone simüle edilmiş "ViewController" adlı sınıfın ekran UI karşılığı vardır

<img width="474" alt="ViewController" src="https://user-images.githubusercontent.com/104498895/233783860-cc85e35e-9b66-4049-b021-c2b3cd48d6c6.png">



