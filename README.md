# Genetik Algoritma ile Güneş Paneli Optimizasyonu

Bu projede, bir belediyenin güneş enerjisi sistemi kurulumunda güneş panellerinin **eğim açısı (x1)** ve **güneye göre yön sapması (x2)** değerlerini optimize etmek amacıyla **Genetik Algoritma (GA)** kullanılmıştır. Amaç, fiziksel ve yapısal kısıtlar altında **toplam enerji verimini maksimize eden** en uygun parametreleri bulmaktır.

Proje, sürekli değişkenli ve kısıtlı bir optimizasyon problemini ele almakta olup, klasik türev tabanlı yöntemlerin zorlandığı durumlarda etkili bir sezgisel yaklaşım olan genetik algoritma ile çözülmüştür.

---

## Projenin Amacı

Bu çalışmanın temel amacı, güneş paneli kurulumunda doğru eğim ve yönlendirme parametrelerinin seçilmesinin enerji verimliliği üzerindeki etkisini incelemek ve bu parametreleri otomatik olarak optimize edebilen bir genetik algoritma modeli geliştirmektir.

Bu kapsamda:
- Fiziksel ve çevresel kısıtlar dikkate alınmış,
- Sürekli değişkenli bir problem yapısı benimsenmiş,
- Rastgeleliğe dayalı ancak yönlendirilmiş bir arama süreci uygulanmıştır.

---

## Problem Tanımı

Güneş panellerinin eğim açısı ve yönelimi, güneşten elde edilen enerji miktarını doğrudan etkilemektedir. Çok yüksek eğim açıları yapısal riskler ve rüzgâr yükü oluşturabilirken, çok düşük eğimler de güneş ışınlarından yeterince yararlanılamamasına neden olmaktadır. Ayrıca panellerin güneşe belirli bir minimum açıyla yönelmesi zorunludur.

Bu nedenle problem, belirli kısıtlar altında enerji verimini maksimize eden parametrelerin bulunması şeklinde tanımlanmıştır.

---

## Amaç Fonksiyonu

Optimizasyon probleminde kullanılan amaç fonksiyonu aşağıdaki gibidir:

\[
y = 6x_1 + 4x_2 - 0.1x_1^2
\]

Burada:
- **x1:** Güneş paneli eğim açısı (10° – 45°)
- **x2:** Güneye göre yön sapması (15° – 90°)
- **y:** Toplam enerji verimini temsil eden uygunluk (fitness) değeri

Amaç, bu fonksiyonu maksimum yapan `(x1, x2)` değerlerini bulmaktır.

---

## Kısıtlar

Problem aşağıdaki kısıtlar altında çözülmüştür:

- \( x_1 + 0.5x_2 <= 60 \)
- \( x_2 >= 15 \)

Bu kısıtlar, genetik algoritmada **ceza yöntemi (penalty method)** kullanılarak fitness fonksiyonuna entegre edilmiştir. Kısıt ihlali yapan çözümler, ihlalin büyüklüğü oranında cezalandırılmıştır.

---

## Kullanılan Genetik Algoritma Yapısı

Projede kullanılan genetik algoritma aşağıdaki bileşenlerden oluşmaktadır:

### Birey Temsili
Her birey, güneş paneli kurulumuna ait bir çözümü temsil etmekte olup `[x1, x2]` şeklinde iki sürekli gen içermektedir.

### Başlangıç Popülasyonu
Başlangıç popülasyonu, değişkenlerin tanımlı aralıkları içinde **rastgele** oluşturulmuştur. Bu yaklaşım, çözüm uzayının geniş bir şekilde keşfedilmesini sağlamaktadır.

### Uygunluk (Fitness) Fonksiyonu
Fitness fonksiyonu, amaç fonksiyonu temel alınarak tanımlanmış ve kısıt ihlalleri durumunda ceza uygulanmıştır. Böylece geçerli çözümlerin seçilme olasılığı artırılmıştır.

### Seçilim Mekanizması
Ebeveyn seçimi için **turnuva seçilimi** yöntemi kullanılmıştır. Bu yöntem, iyi çözümlerin seçilme ihtimalini artırırken genetik çeşitliliği de korumaktadır.

### Çaprazlama (Crossover)
Sürekli değişkenlere uygun olması nedeniyle **aritmetik çaprazlama** yöntemi tercih edilmiştir. Bu yöntemle ebeveyn bireylerin genleri ağırlıklı ortalama alınarak birleştirilmiştir.

### Mutasyon
Mutasyon aşamasında **Gaussian (normal dağılımlı) mutasyon** kullanılmıştır. Her gen düşük bir olasılıkla küçük miktarlarda değiştirilerek algoritmanın keşif yeteneği artırılmıştır. Mutasyon sonrası değerler, tanımlı sınırlar içinde tutulmuştur.

### Durdurma Kriteri
Algoritma, önceden belirlenen nesil sayısı boyunca çalıştırılmıştır.

---

## Sonuçlar ve Görselleştirme

Algoritmanın her nesilde elde ettiği en iyi fitness değeri kaydedilmiş ve grafik üzerinde görselleştirilmiştir. Grafik, genetik algoritmanın zamanla daha iyi çözümlere yakınsadığını ve belirli bir noktadan sonra kararlı bir çözüme ulaştığını göstermektedir.

Genetik algoritma, verilen kısıtlar altında amaç fonksiyonunu maksimize eden ve fiziksel olarak anlamlı parametre değerlerini başarıyla üretmiştir.

---

## Kurulum Yönergeleri

Bu projeyi çalıştırabilmek için aşağıdaki adımların izlenmesi gerekmektedir.

### Gerekli Yazılımlar

- **Python 3.8 veya üzeri**
- **Jupyter Notebook** veya **JupyterLab**
- Python paket yöneticisi **pip**

### Gerekli Kütüphaneler

Projede kullanılan temel Python kütüphaneleri şunlardır:

- `numpy`
- `matplotlib`

Gerekli kütüphaneleri yüklemek için aşağıdaki komutu kullanabilirsiniz:

```bash
pip install numpy matplotlib
