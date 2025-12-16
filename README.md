# genetik_optimizasyonu
# genetik_optimizasyonu
# Genetik Algoritma ile Güneş Paneli Optimizasyonu

Bu projede, bir belediyenin güneş enerjisi sistemi kurulumunda güneş panellerinin **eğim açısı (x1)** ve **güneye göre yön sapması (x2)** değerlerini optimize etmek amacıyla **Genetik Algoritma (GA)** kullanılmıştır. Amaç, fiziksel ve yapısal kısıtlar altında **toplam enerji verimini maksimize eden** en uygun parametreleri bulmaktır.

Proje, sürekli değişkenli ve kısıtlı bir optimizasyon problemini ele almakta olup, klasik yöntemler yerine sezgisel bir yaklaşım olan genetik algoritma ile çözülmüştür.

---

## Problem Tanımı

Güneş panellerinin eğim açısı ve yönelimi, güneşten elde edilen enerji miktarını doğrudan etkilemektedir. Çok yüksek eğim açıları yapısal ve çevresel riskler oluştururken, çok düşük eğimler enerji verimliliğini azaltmaktadır. Ayrıca panellerin güneşe belirli bir açıyla yönelmesi zorunludur.

Bu nedenle problem, aşağıdaki amaç fonksiyonu ve kısıtlar altında tanımlanmıştır.

### Amaç Fonksiyonu

\[
y = 6x_1 + 4x_2 - 0.1x_1^2
\]

Burada:
- **x1:** Güneş paneli eğim açısı (10° – 45°)
- **x2:** Güneye göre yön sapması (15° – 90°)
- **y:** Toplam enerji verimi

---

### Kısıtlar

- \( x_1 + 0.5x_2 \le 60 \)
- \( x_2 \ge 15 \)

Kısıtlar, genetik algoritmada **ceza yöntemi** kullanılarak fitness fonksiyonuna entegre edilmiştir.

---

##  Kullanılan Genetik Algoritma Yapısı

Projede kullanılan genetik algoritma aşağıdaki temel bileşenlerden oluşmaktadır:

- **Birey Temsili:**  
  Her birey, `[x1, x2]` şeklinde iki gen içermektedir.

- **Başlangıç Popülasyonu:**  
  Belirlenen değişken aralıkları içinde rastgele oluşturulmuştur.

- **Uygunluk (Fitness) Fonksiyonu:**  
  Amaç fonksiyonu temel alınarak, kısıt ihlallerinde ceza uygulanmıştır.

- **Seçilim Mekanizması:**  
  Turnuva seçilimi yöntemi kullanılmıştır.

- **Çaprazlama (Crossover):**  
  Sürekli değişkenler için uygun olan aritmetik çaprazlama uygulanmıştır.

- **Mutasyon:**  
  Normal dağılıma dayalı küçük rastgele değişiklikler ile genetik çeşitlilik artırılmıştır.

- **Durdurma Kriteri:**  
  Algoritma belirlenen nesil sayısı boyunca çalıştırılmıştır.

---

##  Sonuçlar ve Görselleştirme

Algoritmanın her nesilde elde ettiği en iyi fitness değeri kaydedilmiş ve sonuçlar grafik üzerinde gösterilmiştir. Bu grafik, genetik algoritmanın zamanla daha iyi çözümlere yakınsadığını göstermektedir.

Çalışma sonunda, verilen kısıtları sağlayan ve amaç fonksiyonunu maksimize eden en uygun `(x1, x2)` değerleri elde edilmiştir.

---
## Kurulum Yönergeleri

Bu projede genetik algoritma kullanılarak bir optimizasyon problemi çözülmüştür. Projenin sorunsuz bir şekilde çalıştırılabilmesi için aşağıdaki adımların sırasıyla uygulanması gerekmektedir.

### Gerekli Yazılımlar

- **Python 3.8 veya üzeri**
- **Jupyter Notebook** veya **JupyterLab**
- Python paket yöneticisi **pip**

### Gerekli Kütüphaneler

Projede kullanılan temel Python kütüphaneleri aşağıda listelenmiştir:

- `numpy`
- `matplotlib`
- `random`

Bu kütüphaneler genellikle Python ile birlikte gelmektedir. Eğer sisteminizde kurulu değilse, aşağıdaki komut ile yüklenebilir:

```bash
pip install numpy matplotlib
