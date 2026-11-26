# AGENT.md
# PROJE: Eğitim ve Öğrenci Takip Data Projesi

## 1. PROJENİN AMACI

Eğitim kurumunda verilen eğitimlerin, açılan sınıfların ve öğrenci kayıtlarının dijital ortamda yönetilmesini sağlayan bir veri yönetim sistemi geliştirmek.

Sistem üç ana modülden oluşacaktır:

1. Eğitim Yönetimi
2. Sınıf Yönetimi
3. Öğrenci Yönetimi

## 2. EĞİTİM YÖNETİMİ

### 2.1 Eğitim Bilgileri

- Eğitim No (Otomatik)
- Eğitim Adı
- Müfredat
- Eğitim Süresi

### 2.2 Eğitim Numaralandırma

Eğitim numarası, eğitim adından oluşturulacaktır.

Örnekler:
- Python-0001
- Python-0002
- Web-Tasarim-0001
- Veri-Analizi-0001

Kurallar:
- Eğitim adı numaralandırma için uygun formata dönüştürülecektir.
- Türkçe karakterler uygun Latin karakterlerine dönüştürülecektir.
- Boşluklar tire (-) ile değiştirilecektir.
- Her eğitim adı kendi numara serisine sahip olacaktır.
- Numara benzersiz oluşturulacaktır.

### 2.3 Müfredat Yönetimi

Müfredat iki yöntemle sisteme girilebilecektir:

1. Metin alanına doğrudan yazılması.
2. Dosya yüklenerek otomatik okunması.

Desteklenecek dosya formatları:
- PDF
- DOCX
- DOC

Dosya yükleme kuralları:
- Orijinal dosya sistemde saklanacaktır.
- Dosya içerisindeki metin otomatik olarak okunacaktır.
- Okunan metin müfredat alanına aktarılacaktır.
- Kullanıcı çıkarılan metni düzenleyebilecektir.
- Düzenlenen müfredat sistemde kaydedilecektir.

### 2.4 Eğitim İşlevleri

- Yeni eğitim ekleme.
- Eğitimleri listeleme.
- Eğitim detaylarını görüntüleme.
- Eğitim bilgilerini düzenleme.

## 3. SINIF YÖNETİMİ

### 3.1 Sınıf Bilgileri

- Sınıf No (Otomatik)
- Eğitim Adı
- Sınıfa Kayıtlı Öğrenciler

### 3.2 Sınıf Numaralandırma

Sınıf numarası sistem tarafından otomatik oluşturulacaktır.

Örnek:
- 101
- 102
- 103
- 104

### 3.3 Sınıf Oluşturma Kuralları

- Yeni Sınıf Ekle butonuyla sınıf oluşturma formu açılacaktır.
- Eğitim adı mevcut eğitim kayıtlarından seçilecektir.
- Oluşturulan sınıf seçilen eğitimle ilişkilendirilecektir.
- Aynı eğitim için birden fazla sınıf açılabilecektir.
- Bir sınıfta birden fazla öğrenci bulunabilecektir.

### 3.4 Sınıf İşlevleri

- Yeni sınıf oluşturma.
- Sınıfları listeleme.
- Sınıf detaylarını görüntüleme.
- Sınıf bilgilerini düzenleme.
- Sınıfa kayıtlı öğrencileri görüntüleme.

## 4. ÖĞRENCİ YÖNETİMİ

### 4.1 Öğrenci Bilgileri

- Öğrenci No (Otomatik)
- Ad Soyad
- Telefon Numarası
- E-Posta Adresi

### 4.2 Öğrenci Numaralandırma

Öğrenci numarası sistem tarafından otomatik oluşturulacaktır.

Örnek:
- OGR-0001
- OGR-0002
- OGR-0003

Her öğrenciye benzersiz bir öğrenci numarası atanacaktır.

### 4.3 Öğrenci Eğitim Kayıtları

Her öğrencinin katıldığı her eğitim için ayrı kayıt oluşturulacaktır.

Kayıt bilgileri:
- Öğrenci
- Eğitim
- Sınıf
- Kursa Başlama Tarihi

### 4.4 Öğrenci Kayıt Kuralları

- Bir öğrenci birden fazla eğitime kayıt olabilecektir.
- Her eğitim kaydı ayrı bir ilişki üzerinden yönetilecektir.
- Öğrenci kayıt formunda önce eğitim seçilecektir.
- Eğitim seçildikten sonra yalnızca o eğitime bağlı sınıflar listelenecektir.
- Kullanıcı ilgili sınıfı seçerek öğrenci kaydını tamamlayacaktır.
- Kursa başlama tarihi her eğitim kaydı için ayrı tutulacaktır.

### 4.5 Öğrenci İşlevleri

- Yeni öğrenci kaydetme.
- Öğrencileri listeleme.
- Öğrenci detaylarını görüntüleme.
- Öğrenci bilgilerini düzenleme.
- Öğrencinin kayıtlı olduğu eğitimleri görüntüleme.
- Öğrencinin eğitim bazında sınıf bilgilerini görüntüleme.

## 5. VERİTABANI İLİŞKİLERİ

Temel veri modelleri:

1. Education (Eğitimler)
2. Classroom (Sınıflar)
3. Student (Öğrenciler)
4. Enrollment (Öğrenci Eğitim Kayıtları)

İlişki kuralları:

- Bir eğitim birden fazla sınıfa sahip olabilir.
- Bir sınıf yalnızca bir eğitime bağlı olabilir.
- Bir öğrenci birden fazla eğitim kaydına sahip olabilir.
- Bir eğitim kaydı bir öğrenci ve bir sınıfla ilişkilendirilir.
- Bir sınıfta birden fazla öğrenci bulunabilir.
- Öğrenci kişisel bilgileri ile eğitim kayıtları birbirinden bağımsız yönetilir.

## 6. GENEL GELİŞTİRME KURALLARI

- Kullanıcı tarafından onaylanmayan hiçbir özellik geliştirmeye dahil edilmeyecektir.
- Yeni özellik önerileri öncelikle kullanıcıya sunulacaktır.
- Kullanıcı onayı olmadan proje kapsamı genişletilmeyecektir.
- Eksik veya belirsiz gereksinimler geliştirme öncesinde kullanıcıya sorulacaktır.
- İlişkili alanlarda manuel veri girişi yerine sistem kayıtları kullanılacaktır.
- Veri bütünlüğü korunacaktır.
- Otomatik numaralar benzersiz olacaktır.
- Hatalı veya eksik veri girişleri kontrol edilecektir.

## 7. GELİŞTİRME VE ONAY SÜRECİ

1. Kullanıcı gereksinimleri iletir.
2. Agent gereksinimleri analiz eder.
3. Eksik veya belirsiz konular kullanıcıya sorulur.
4. Ek özellik önerileri kullanıcıya sunulur.
5. Onaylanan gereksinimler kesinleştirilir.
6. Sprint planı hazırlanarak kullanıcıya sunulur.
7. Kullanıcı onayı olmadan geliştirme başlatılmaz.
8. Onaylanan sprint kapsamı geliştirilir.
9. Geliştirme tamamlandığında test süreci yürütülür.
10. Test sonuçları raporlanır.
11. Tespit edilen hatalar düzeltilir.
12. Sonraki sprint için kullanıcı onayı alınır.

## 8. TEMEL AGENT PRENSİBİ

Agent; analiz, mimari tasarım, planlama, kodlama ve test süreçlerinde görev alır.

Proje kapsamını tek başına değiştiremez.

Son karar ve kapsam onayı her zaman kullanıcıya aittir.