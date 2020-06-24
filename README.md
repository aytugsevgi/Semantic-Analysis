## PROBLEM TANIMI

www.kaggle.com sitesinde bulunan “Turkish Movie Sentiment Analysis” veri setini kullanarak insanların bir film sitesinde, izlediği film hakkında yaptığı yorumların hangilerinin ‘olumlu’ hangilerinin ‘olumsuz’ bir yorum olduğunu doğal dil işleme metodu aracılığıyla bulmaktır.
## ARAŞTIRMA (ÖN ÇALIŞMA)
Son yıllarda yapay zeka konusundaki gelişmelerin yanında doğal dil işleme tabanlı geliştirilen uygulamaların önemi ve sayısı artmakta. Bu konudaki gelişmeler birçok işte fayda sağlamakta ve insan gücünü ortadan kaldırmaktadır. Daha hızlı ve daha doğru sonuçlar elde etmek için kullanılan yöntemler geliştirilmeye devam etmektedir. Doğal dil işleme ile geliştirilen uygulamalar kullanım alanları bu şekilde karşımıza çıkmakta:
 
Spam Detection (İçeriklere göre sınıflandırma)
Metin içeriğinde olumlu/olumsuz söylem olup olmadığı çıkarılır. Bir
ürün/film vb. yorumların analiz edilmesinde kullanılır.
Part-Of-Speech (POS) Tagging (Metin etiketleme (Fiil, Nesne, Sıfat, Bağlaç vb.))
Named Entity Recognation (NER) (Varlık ismi tanımlama kişi, yer, zaman, tarih, sayı
tanımlamalarının yapılması)
• Coreference Resolution (Metinde aynı şeyden(kişi/nesne) birden fazla kullanılmasının tespiti)
• Word Sense Disambiguation (WDS) (Çok anlamlı, eş sesli kelimelerin, cümle içerisinde hangi
anlamda kullanıldığının anlaşılması)
• Parsing: (Metni parçalara bölme işlemi)
• Machine Translation (MT) (Bir dilden başka bir dile çevirme)
• Information Extraction (Metnin içerisinden bilgi çıkarma)
 Seçtiğimiz konu nedeniyle duygu analizi üzerine gideceğiz. Duygu analizi insanların duygularını, görüşlerini değerlendiren, bir konu hakkındaki davranışlarını yazılı dil üzerinden analiz eden çalışma alanıdır (Liu, 2012). Duygu Analizi, temel olarak bir metin işleme işlemi olup, metindeki ifade edilmek istenen duyguyu belirlemeyi amaçlar. Bir metnin ifade ettiği olumlu, olumsuz veya birden fazla duygunun belirlenmesi için kullanılır. Fikir madenciliği olarak da duyabileceğimiz duygu analizi örnek olarak bir filme gelen yorumların taşımış olduğu fikir, duygu ve düşünceyi semantik olarak ortaya çıkarmak için yapılan çalışmalardır.
Bir metindeki duygu analizi, yani o metnin duygusallığı genel olarak ikili sınıflandırmalarla gösterilir (Olumlu/Olumsuz, Pozitif/Negatif). Duygusal kutuplara (ikili sınıflandırma) ayırma işlemi ilk duygu analizi çalışmalarında sıkça görülmüştür. Daha sonra geliştirilen uygulamalarda metni duygu kategorilerine ayırarak daha detaylı sınıflandırma yapılmıştır. Biz sadece metnin olumlu/olumsuz olup olmadığına karar veren bir algoritma geliştirip ikili sınıflandırma işlemini gerçekleştireceğiz.
## KULLANILAN ORTAM, YÖNTEM, KÜTÜPHANE
Projeyi kaggle notebook ortamında geliştirdik. Deneysel olarak bazı sınıflandırıcılar denendi. Bu sınıflandırıcılar; RandomForest, LogisticRegression, KNeighborsClassifier olmak üzere 3 tanedir. TfIdfVectorizer kütüphanesi ile genel olarak metinde geçen kelimelere bağlı olarak belirlenen text verisinde bir kelimenin nadirliğinin analizi yapıldı. Train_test_split kütüphanesi ile veri seti “train” ve “test” olmak üzere parçalandı. Classification_report kütüphanesi ile en optimal modelin raporunu ekrana yazdırdık.

## GELİŞTİRİLEN/KULLANILAN YÖNTEM İzlenilen Yöntem:
• Veri seti ile dataframe oluşturuldu.
• Veri seti içerisinde ki “\n,\r,\t”, noktalama işaretleri ve gereksiz boşluklar temizlenip
daha temiz bir veri seti haline getirildi.
• TfidfVectorizer() kütüphanesi ile veri setindeki yorumlar fitlendi. Buna göre belirli bir
yorum içinde geçen kelimelerin nadiren kullanılan bir kelime olup olmadığının analizi
yapıldı.
• “Na” değer içeren satırlar veri setinden silindi.
• Veri setinde ki Score sütunu String’ten float’a dönüştürüldü.
• Score’ların grafiği çizdirildi.
• Yorumlarda en çok geçen kelimelerin grafiği çizdirildi.
• Veri seti “train” ve “test” olmak üzere ayrıldı.
• Accuracy hesabı için “accuracy_summary” fonksiyon yazıldı.
• Modeller oluşturulup feature ve model içi parametrelere göre pipeline’a parametre
olarak gönderildi. “nfeature_accuracy_checker” fonksiyonu ile bu işlem yapılırken bu fonksiyon kendi içinde “accuracy_summary” i çağırarak pipeline.fit() ile model eğitildi. Buna göre score ekrana yazıldı.
• En optimal model ve parametre değerleri için “classification_report“ ile ekrana bu modelin raporu yazdırıldı.
