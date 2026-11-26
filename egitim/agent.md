# AGENT.md
# Eğitim ve Öğrenci Takip Sistemi

## 1. Proje Tanımı

Bu proje, eğitim kurumunda verilen eğitimlerin, açılan sınıfların ve öğrenci kayıtlarının dijital ortamda yönetilmesini sağlayan web tabanlı bir uygulamadır.

Projenin temel modülleri:

1. Eğitim Yönetimi
2. Sınıf Yönetimi
3. Öğrenci Yönetimi
4. Bitirme Projesi ve Değerlendirme

Uygulama yalnızca web tabanlı geliştirilecektir. Mobil uygulama geliştirilmesi proje kapsamında değildir.

## 2. Teknoloji Mimarisi

### Frontend
- React
- Vite
- TypeScript

### Backend
- Node.js
- Express.js
- TypeScript

### Veritabanı
- PostgreSQL

### ORM
- Prisma

### İletişim
- REST API

### Mimari Kurallar
- Frontend ve backend birbirinden bağımsız çalışmalıdır.
- Frontend, backend servisleriyle REST API üzerinden iletişim kurmalıdır.
- Veritabanı işlemleri yalnızca backend üzerinden Prisma kullanılarak gerçekleştirilmelidir.
- İş kuralları backend tarafında uygulanmalıdır.
- Veri doğrulama hem frontend hem backend tarafında yapılmalıdır.
- Frontend doğrudan veritabanına bağlanmamalıdır.
- API hata ve başarı yanıtları tutarlı bir yapıda olmalıdır.
- Proje TypeScript ile geliştirilmelidir.

## 3. Ana Modüller

# 3.1 Eğitim Yönetimi

Eğitim modülü, kurumda verilen eğitimlerin tanımlanmasını ve yönetilmesini sağlar.

### Eğitim Bilgileri
- Eğitim No
- Eğitim Adı
- Müfredat
- Toplam Eğitim Süresi (saat)
- Haftalık Ders Saati

### Eğitim Numarası Oluşturma

Eğitim numarası, eğitim adından otomatik olarak oluşturulmalıdır.

Örnekler:
- Python-0001
- Python-0002
- Web-Tasarim-0001
- Web-Tasarim-0002
- Veri-Analizi-0001

Kurallar:
- Her eğitim adı için ayrı bir numara serisi bulunmalıdır.
- Eğitim numarası benzersiz olmalıdır.
- Türkçe karakterler uygun şekilde normalize edilmelidir.
- Kelimeler arasındaki boşluklar tire ile değiştirilmelidir.
- Aynı eğitim adına ait yeni kayıt oluşturulduğunda sıra numarası otomatik artırılmalıdır.
- Eğitim adı sonradan değiştirildiğinde mevcut eğitim numarası değiştirilmemelidir.
- Eş zamanlı kayıt işlemlerinde aynı numaranın oluşturulması veritabanı seviyesinde engellenmelidir.

### Eğitim İşlevleri
- Eğitim ekleme
- Eğitimleri listeleme
- Eğitim detaylarını görüntüleme
- Eğitim düzenleme

### Müfredat Yönetimi

Müfredat iki yöntemle sisteme eklenebilmelidir:

1. Metin alanına manuel olarak yazılabilmelidir.
2. PDF, DOCX veya DOC dosyası yüklenebilmelidir.

Dosya yükleme kuralları:
- Yüklenen orijinal dosya saklanmalıdır.
- Dosyanın metin içeriği okunmalıdır.
- Okunan içerik müfredat metin alanına aktarılmalıdır.
- Kullanıcı aktarılan metni düzenleyebilmelidir.
- Düzenlenen müfredat kaydedilebilmelidir.
- Dosya türü ve boyutu backend tarafında doğrulanmalıdır.
- Dosya okunamadığında kullanıcıya anlaşılır hata mesajı verilmelidir.

# 3.2 Sınıf Yönetimi

Sınıf modülü, eğitimlere bağlı sınıfların oluşturulmasını ve yönetilmesini sağlar.

### Sınıf Bilgileri
- Sınıf No
- Eğitim
- Sınıfa kayıtlı öğrenciler

### Sınıf Numarası Oluşturma

Sınıf numarası sistem genelinde ortak ve sıralı olarak otomatik oluşturulmalıdır.

Örnek:
- Python 101
- Python 102
- Web Tasarım 103
- Web Tasarım 104
- Veri Analizi 105
- Veri Analizi 106

Kurallar:
- Sınıf numarası sistem genelinde benzersiz olmalıdır.
- Sınıf numarası otomatik oluşturulmalıdır.
- Silinen sınıfın numarası tekrar kullanılmamalıdır.
- Aynı eğitime birden fazla sınıf açılabilmelidir.
- Her sınıf yalnızca bir eğitime bağlı olmalıdır.
- Sınıf oluşturulurken eğitim, sistemde kayıtlı eğitimler arasından seçilmelidir.

### Sınıf İşlevleri
- Sınıf ekleme
- Sınıfları listeleme
- Sınıf detaylarını görüntüleme
- Sınıf düzenleme
- Sınıfa kayıtlı öğrencileri görüntüleme

# 3.3 Öğrenci Yönetimi

Öğrenci modülü, öğrenci kişisel bilgilerinin ve eğitim kayıtlarının yönetilmesini sağlar.

### Öğrenci Kişisel Bilgileri
- Öğrenci No
- Ad Soyad
- Telefon
- E-posta

### Öğrenci Numarası Oluşturma

Öğrenci numarası otomatik oluşturulmalıdır.

Örnek:
- OGR-0001
- OGR-0002
- OGR-0003

Kurallar:
- Öğrenci numarası benzersiz olmalıdır.
- Numara sistem tarafından otomatik oluşturulmalıdır.

### Öğrenci Eğitim Kayıtları

Öğrencinin kişisel bilgileri ile eğitim kayıtları birbirinden ayrı yönetilmelidir.

Bir öğrenci:
- Birden fazla eğitime kayıt olabilir.
- Aynı eğitime farklı zamanlarda tekrar kayıt olabilir.
- Her eğitim katılımı için ayrı bir kayıt oluşturulmalıdır.
- Önceki eğitim kayıtları korunmalıdır.

Her eğitim kaydı aşağıdaki bilgileri içermelidir:

- Öğrenci
- Eğitim
- Sınıf
- Kursa Başlama Tarihi
- Tahmini Kurs Bitiş Tarihi
- Eğitim Kayıt Durumu

### Eğitim Kayıt Durumu

Her Enrollment kaydı için ayrı bir durum alanı bulunmalıdır.

Durum seçenekleri:
- Devam Ediyor
- Tamamlandı
- İptal Edildi

Kurallar:
- Her eğitim kaydının durumu bağımsız olarak takip edilmelidir.
- Aynı öğrencinin farklı eğitim kayıtlarının durumları birbirinden bağımsız olmalıdır.
- Bir eğitim kaydının durumu değiştirildiğinde diğer kayıtlar etkilenmemelidir.

### Tahmini Kurs Bitiş Tarihi Hesaplama

Kursun tahmini bitiş tarihi, eğitim tanımındaki toplam ders saati ve haftalık ders saati bilgileri ile öğrencinin kursa başlama tarihi kullanılarak hesaplanmalıdır.

Hesaplama için kullanılacak bilgiler:
- Eğitim toplam süresi (saat)
- Haftalık ders saati
- Kursa başlama tarihi

Hesaplama yöntemi:

1. Toplam eğitim saati haftalık ders saatine bölünerek eğitim süresi hafta cinsinden hesaplanır.
2. Sonuç tam hafta değilse yukarı yuvarlanır.
3. Bulunan hafta sayısı 7 ile çarpılarak takvim günü elde edilir.
4. Kursa başlama tarihine bu gün sayısı eklenerek tahmini bitiş tarihi hesaplanır.

Formül:

`Eğitim Süresi (Hafta) = CEIL(Toplam Eğitim Saati / Haftalık Ders Saati)`

`Tahmini Bitiş Tarihi = Kursa Başlama Tarihi + (Eğitim Süresi (Hafta) × 7 gün)`

Örnek:
- Toplam eğitim süresi: 40 saat
- Haftalık ders saati: 8 saat
- Kursa başlama tarihi: 01.12.2026
- Eğitim süresi: 5 hafta
- Tahmini bitiş tarihi: 05.01.2027

Kurallar:
- Haftalık ders saati sıfırdan büyük olmalıdır.
- Toplam eğitim saati sıfırdan büyük olmalıdır.
- Tarih hesabı backend tarafında yapılmalıdır.
- Hesaplanan tahmini bitiş tarihi kullanıcı arayüzünde gösterilmelidir.
- Kursa başlama tarihi değiştirildiğinde bitiş tarihi yeniden hesaplanmalıdır.
- Eğitim süresi veya haftalık ders saati değiştiğinde hesaplama tutarlı şekilde güncellenmelidir.
- Bu tarih tahmini bitiş tarihidir; kesin ders takvimi olarak değerlendirilmemelidir.
- Ders günleri, resmî tatiller, ara tatiller ve ders yapılmayan günler bu hesaplamaya dahil değildir.

### Eğitim Kaydı Oluşturma Akışı

Öğrenci bir eğitime kaydedilirken:

1. Önce eğitim seçilmelidir.
2. Seçilen eğitime bağlı sınıflar listelenmelidir.
3. Kullanıcı ilgili sınıfı seçmelidir.
4. Kursa başlama tarihi girilmelidir.
5. Sistem tahmini kurs bitiş tarihini hesaplamalıdır.
6. Eğitim kayıt durumu belirlenmelidir.
7. Eğitim kaydı oluşturulmalıdır.

Sınıf seçiminde yalnızca seçilen eğitime bağlı sınıflar gösterilmelidir.

Backend, seçilen sınıfın gerçekten seçilen eğitime ait olduğunu doğrulamalıdır.

### Öğrenci İşlevleri
- Öğrenci kaydetme
- Öğrencileri listeleme
- Öğrenci detaylarını görüntüleme
- Öğrenci bilgilerini düzenleme
- Öğrencinin eğitim geçmişini görüntüleme
- Öğrencinin kayıtlı olduğu sınıfları görüntüleme
- Eğitim kayıtlarının durumlarını görüntüleme ve yönetme

# 3.4 Bitirme Projesi ve Değerlendirme

Her öğrenci, katıldığı eğitimin sonunda bir bitirme projesi gönderebilmelidir.

Eğitmen, öğrencinin gönderdiği bitirme projesini inceleyerek değerlendirme puanı girebilmelidir.

### Bitirme Projesi Bilgileri

Her bitirme projesi ilgili Enrollment kaydıyla ilişkilendirilmelidir.

Tutulacak bilgiler:
- İlgili öğrenci-eğitim kaydı (Enrollment)
- Proje gönderim bilgisi
- Proje gönderim tarihi
- Eğitmen değerlendirme puanı
- Değerlendirme tarihi

### İşleyiş

1. Öğrenci, katıldığı eğitimin sonunda bitirme projesini gönderir.
2. Proje, öğrencinin ilgili Enrollment kaydına bağlanır.
3. Eğitmen gönderilen projeyi inceler.
4. Eğitmen değerlendirme puanını sisteme girer.
5. Puan ilgili öğrenci-eğitim kaydına kaydedilir.
6. Öğrencinin detay sayfasında bitirme projesi ve değerlendirme puanı görüntülenir.

### Değerlendirme Kuralları
- Bitirme projesi her eğitim katılımı için ayrı tutulmalıdır.
- Aynı öğrenci aynı eğitime tekrar katıldığında önceki proje ve puan kayıtları korunmalıdır.
- Eğitmenin girdiği puan ilgili Enrollment kaydıyla ilişkilendirilmelidir.
- Puan değeri için kullanılacak minimum ve maksimum aralık teknik tasarım öncesinde ürün sahibine sorulmalıdır.
- Puanın kim tarafından verildiği ve değerlendirme tarihi takip edilebilmelidir.
- Değerlendirme bilgileri yetkisiz kullanıcılar tarafından değiştirilememelidir.

### Puan Bildirim E-postası

Eğitmen öğrencinin bitirme projesi puanını sisteme kaydettiğinde öğrencinin sistemde kayıtlı e-posta adresine bilgilendirme e-postası gönderilmelidir.

E-posta içeriğinde:
- Öğrencinin adı
- İlgili eğitim adı
- Bitirme projesinden aldığı puan
- Değerlendirme tarihi
bulunmalıdır.

Kurallar:
- E-posta, puan veritabanına başarıyla kaydedildikten sonra gönderilmelidir.
- E-posta alıcısı öğrencinin sistemde kayıtlı e-posta adresi olmalıdır.
- E-posta içeriğindeki puan ve eğitim bilgileri ilgili Enrollment kaydından alınmalıdır.
- Puan kaydı başarısız olduğunda e-posta gönderilmemelidir.
- E-posta gönderiminde hata oluşursa puan kaydı kaybolmamalı veya geri alınmamalıdır.
- E-posta gönderim hataları loglanmalı ve takip edilebilir olmalıdır.
- E-posta gönderim yöntemi ve sağlayıcısı teknik tasarım aşamasında belirlenmeli ve ürün sahibinin onayına sunulmalıdır.
- E-posta servis bilgileri güvenli ortam değişkenlerinde saklanmalıdır.
- E-posta gönderim işlemi için gerekli güvenlik ve hata yönetimi uygulanmalıdır.

# 4. Veritabanı Tasarımı

Temel veritabanı modelleri:

1. Education
2. Classroom
3. Student
4. Enrollment
5. CurriculumFile
6. CapstoneProject (Bitirme Projesi)

### Education

Eğitim bilgilerini tutar.

Temel alanlar:
- id
- educationNumber
- name
- curriculum
- totalHours
- weeklyHours
- createdAt
- updatedAt

### Classroom

Sınıf bilgilerini tutar.

Temel alanlar:
- id
- classroomNumber
- educationId
- createdAt
- updatedAt

### Student

Öğrencinin kişisel bilgilerini tutar.

Temel alanlar:
- id
- studentNumber
- fullName
- phone
- email
- createdAt
- updatedAt

### Enrollment

Öğrencinin bir eğitime katılım kaydını tutar.

Temel alanlar:
- id
- studentId
- educationId
- classroomId
- startDate
- status
- createdAt
- updatedAt

Tahmini bitiş tarihi, eğitim süresi ve haftalık ders saati üzerinden hesaplanmalıdır. Hesaplamanın hangi noktada saklanacağı veya dinamik olarak üretileceği teknik tasarım aşamasında değerlendirilerek tutarlı bir yöntem belirlenmelidir.

### CurriculumFile

Eğitime ait müfredat dosyalarını tutar.

Temel alanlar:
- id
- educationId
- originalFileName
- storedFileName
- filePath veya storageKey
- mimeType
- fileSize
- createdAt

### CapstoneProject

Öğrencinin ilgili eğitim katılımı için gönderdiği bitirme projesini ve değerlendirme bilgilerini tutar.

Temel alanlar:
- id
- enrollmentId
- projectSubmissionInfo
- submissionDate
- score
- evaluationDate
- createdAt
- updatedAt

Bitirme projesi dosya olarak gönderilecekse dosyanın saklanması için gerekli alanlar teknik tasarım aşamasında belirlenecek ve ürün sahibinin onayına sunulacaktır.

### Model İlişkileri

- Education 1:N Classroom
- Education 1:N Enrollment
- Education 1:N CurriculumFile
- Student 1:N Enrollment
- Classroom 1:N Enrollment
- Enrollment 1:N veya 1:1 CapstoneProject (proje gönderim ve yeniden değerlendirme gereksinimleri netleştirildikten sonra kesinleştirilecektir).

Bir öğrenci ile bir eğitim arasındaki ilişki Enrollment üzerinden kurulmalıdır.

Aynı öğrenci ve aynı eğitim arasında birden fazla Enrollment kaydı oluşturulmasına izin verilmelidir.

Bitirme projesi ve değerlendirme bilgileri öğrenciye doğrudan değil, ilgili Enrollment kaydına bağlanmalıdır.

## 5. Veri Bütünlüğü ve Güvenlik

- Benzersiz numaralar veritabanı seviyesinde korunmalıdır.
- Foreign key ilişkileri doğru tanımlanmalıdır.
- Sınıfın bağlı olduğu eğitim ile Enrollment kaydındaki eğitim birbiriyle tutarlı olmalıdır.
- Aynı öğrenci aynı eğitime tekrar kaydedilebilmelidir.
- Önceki Enrollment kayıtları korunmalıdır.
- Bitirme projesi ve puan ilgili Enrollment kaydıyla ilişkilendirilmelidir.
- Öğrenci e-posta adresi doğrulanmalıdır.
- E-posta gönderim hataları puan kaydını etkilememelidir.
- İlişkili verilerin silinmesi veri kaybına yol açmamalıdır.
- Silme davranışı (soft delete, restrict veya uygun başka bir yöntem) geliştirme öncesi teknik tasarımda açıklanmalı ve ürün sahibinin onayına sunulmalıdır.
- Kullanıcı girdileri backend tarafında doğrulanmalıdır.
- Veritabanı işlemlerinde Prisma kullanılmalıdır.
- Hassas bilgiler ve dosya yükleme işlemleri güvenli şekilde ele alınmalıdır.
- Hatalar kullanıcıya anlaşılır, geliştiriciye takip edilebilir şekilde raporlanmalıdır.

## 6. Geliştirme Süreci ve Sprint Yönetimi

Önerilen sprint sıralaması:

### Sprint 1 – Proje Altyapısı
- Proje klasör yapısının oluşturulması
- React + Vite + TypeScript frontend kurulumu
- Node.js + Express.js + TypeScript backend kurulumu
- PostgreSQL bağlantısı
- Prisma kurulumu
- İlk veritabanı şemasının hazırlanması
- Ortam değişkenleri ve temel yapılandırmalar

### Sprint 2 – Eğitim Yönetimi
- Eğitim ekleme
- Eğitim listeleme
- Eğitim detayları
- Eğitim düzenleme
- Otomatik eğitim numarası üretimi
- Toplam eğitim saati ve haftalık ders saati alanları

### Sprint 3 – Sınıf Yönetimi
- Sınıf ekleme
- Sınıf listeleme
- Sınıf detayları
- Sınıf düzenleme
- Otomatik ve benzersiz sınıf numarası üretimi
- Sınıfın eğitime bağlanması

### Sprint 4 – Öğrenci Yönetimi
- Öğrenci ekleme
- Öğrenci listeleme
- Öğrenci detayları
- Öğrenci düzenleme
- Otomatik öğrenci numarası üretimi
- Öğrencinin eğitime ve sınıfa kaydedilmesi
- Aynı öğrencinin aynı eğitime tekrar kaydedilebilmesi
- Eğitim kayıt durumlarının yönetilmesi
- Tahmini kurs bitiş tarihi hesaplaması ve gösterimi
- Öğrenci eğitim geçmişi

### Sprint 5 – Müfredat Yönetimi
- Müfredat metin alanı
- PDF yükleme ve okuma
- DOCX yükleme ve okuma
- DOC yükleme ve okuma
- Orijinal dosyanın saklanması
- Okunan metnin düzenlenmesi ve kaydedilmesi

### Sprint 6 – Bitirme Projesi ve Değerlendirme
- Bitirme projesi gönderim bilgilerinin kaydedilmesi
- Bitirme projesinin ilgili Enrollment kaydına bağlanması
- Eğitmen değerlendirme puanının girilmesi
- Değerlendirme tarihinin kaydedilmesi
- Öğrenci detayında proje ve puan bilgilerinin gösterilmesi
- Puan kaydedildiğinde öğrenciye e-posta bildirimi gönderilmesi
- E-posta gönderim hata yönetimi ve testleri

### Sprint 7 – Entegrasyon ve Genel Test
- Modüller arası entegrasyon
- Veri bütünlüğü testleri
- API testleri
- Form doğrulama testleri
- Hata senaryoları
- Güvenlik kontrolleri
- E-posta bildirim testleri
- Genel kullanıcı akışlarının test edilmesi

Bu sprint sıralaması başlangıç planıdır. Her sprintin ayrıntılı görevleri, kabul kriterleri ve tahmini süresi ayrıca hazırlanıp ürün sahibinin onayına sunulmalıdır.

## 7. Claude İçin Çalışma Kuralları

Claude bu projede teknik geliştirme sorumlusu olarak görev yapacaktır.

### Proje Sahibi Onayı
- Ürün sahibi kullanıcıdır.
- Kullanıcı proje gereksinimlerini ve önceliklerini belirler.
- Claude teknik analiz, mimari öneri, geliştirme ve test süreçlerini yürütür.
- Kullanıcının onayı olmadan yeni özellik eklenemez.
- Kullanıcının onayı olmadan mevcut gereksinimler değiştirilemez.
- Belirsiz gereksinimler geliştirmeye başlamadan önce kullanıcıya sorulmalıdır.

### Sprint Kuralları
1. Önce sprintin kapsamı analiz edilmelidir.
2. Sprint görevleri ve kabul kriterleri hazırlanmalıdır.
3. Sprint planı kullanıcıya sunulmalıdır.
4. Kullanıcı onayı alınmadan kodlama başlamamalıdır.
5. Yalnızca onaylanan sprint geliştirilmelidir.
6. Sprint tamamlandığında testler yapılmalıdır.
7. Test sonuçları ve yapılan çalışmalar raporlanmalıdır.
8. Sonraki sprint için kullanıcı onayı beklenmelidir.

### Kodlama Kuralları
- Mevcut çalışan kod gereksiz yere değiştirilmemelidir.
- Kod tekrarından kaçınılmalıdır.
- Modüler ve sürdürülebilir kod yazılmalıdır.
- TypeScript tip güvenliği korunmalıdır.
- Backend iş kuralları frontend'e taşınmamalıdır.
- API ve veritabanı işlemleri tutarlı şekilde tasarlanmalıdır.
- Hata yönetimi ihmal edilmemelidir.
- Kodlama sırasında kapsam dışı özellikler eklenmemelidir.
- Teknik bir engel veya gereksinim çelişkisi oluşursa kullanıcıya bilgi verilmelidir.

### Test ve Raporlama

Her sprint sonunda:
- Yapılan işlemler listelenmelidir.
- Değiştirilen ve oluşturulan dosyalar belirtilmelidir.
- Çalıştırılan testler ve sonuçları raporlanmalıdır.
- Başarısız testler açıkça belirtilmelidir.
- Bilinen eksiklikler ve teknik riskler paylaşılmalıdır.
- Kabul kriterlerinin hangilerinin karşılandığı gösterilmelidir.

## 8. Proje Kapsamı Dışında Olanlar

Kullanıcı tarafından ayrıca onaylanmadıkça aşağıdaki çalışmalar yapılmamalıdır:

- Mobil uygulama geliştirme
- Onaylanmamış yeni modüller
- Onaylanmamış raporlama ve analiz özellikleri
- Onaylanmamış otomasyonlar
- Onaylanmamış üçüncü taraf servis entegrasyonları

## 9. Temel Proje İlkesi

Bu projenin geliştirme sürecinde en önemli ilke, onaylanmış gereksinimlere bağlı kalmaktır.

Claude kendi başına kapsam genişletmemeli, ürün sahibi adına karar vermemeli ve onaylanmamış geliştirmelere başlamamalıdır.

Her geliştirme aşaması analiz, planlama, onay, geliştirme, test ve raporlama sırasıyla yürütülmelidir.