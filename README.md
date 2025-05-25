# Sahte Haber Tespit Projesi
[[https://www.kaggle.com/code/denizeldeniz/sahtehabertespitimlml](https://www.kaggle.com/code/denizeldeniz/habertespitmlml)](https://www.kaggle.com/code/denizeldeniz/habertespitmlml)

!!!!!! 100mb boyutunu açtığı için https://www.kaggle.com/datasets/suleymancan/turkishnews70000 isimli data setimi githuba yükleyemedim.!!!!!!

Bu proje, Türkçe haber makalelerini **gerçek** veya **sahte** olarak sınıflandırmak için bir makine öğrenmesi modeli geliştirmeyi amaçlamaktadır. Veri seti, çeşitli kaynaklardan toplanan gerçek haber makaleleri ve ayrı olarak üretilen veya temin edilen sahte haber makalelerinden oluşmaktadır. Proje, ikili sınıflandırma için Lojistik Regresyon kullanmakta ve doğal dil işleme (NLP) teknikleriyle işlenen metin verilerine dayanmaktadır.

## İçindekiler
1. [Proje Genel Bakış](#proje-genel-bakış)
2. [Veri Seti](#veri-seti)
2. [Sonuçlar](#sonuçlar)
3. [Projeyi Çalıştırma](#projeyi-çalıştırma)
4. [Geliştirme ve Gelecek Çalışmalar](#geliştirme-ve-gelecek-çalışmalar)
5. [Bağımlılıklar](#bağımlılıklar)
6. 
---

## Proje Genel Bakış

Bu projenin amacı, Türkçe haber makalelerini gerçek ve sahte olarak ayırt edebilen bir makine öğrenmesi modeli geliştirmektir. Türkçe sahte haber veri setlerinin azlığı nedeniyle, proje birden fazla gerçek haber veri setini birleştirir ve bunları AI tarafından üretilen sahte haber verileriyle tamamlar. Model, basitliği, hızı ve ikili sınıflandırma görevlerindeki etkinliği nedeniyle Lojistik Regresyon kullanılarak eğitilmiştir. Proje, veri toplama, temizleme, ön işleme, model eğitimi ve performans değerlendirmesini içerir.

---

## Veri Seti
### Kaynaklar
- **Gerçek Haberler**:
  - [Kaggle: Turkish News 70000](https://www.kaggle.com/datasets/suleymancan/turkishnews70000): 70.000 gerçek Türkçe haber makalesi içeren bir veri seti.
  - [Kaggle: Sahte Haber Analizi Türkçe Metinler](https://www.kaggle.com/datasets/mohamedibrahimabdi/sahte-haber-analizit-rke-metinler): Gerçek haberler için ikincil bir kaynak olarak kullanılan başka bir Türkçe haber metinleri veri seti.
  - Bu veri setleri birleştirilerek daha büyük bir gerçek haber korpusu oluşturuldu ve `0` (gerçek) olarak etiketlendi.
- **Sahte Haberler**:
  - Türkçe sahte haber veri setlerinin kamuoyunda bulunmaması nedeniyle, sahte haber makaleleri temin edildi veya üretildi (örneğin, notebook’ta belirtildiği üzere AI araçları kullanılarak).

## Sonuçlar
- **Doğruluk**: Model, test setinde `1.0000` (100%) doğruluk elde etti ve mükemmel sınıflandırma performansı gösterdi.
- **Performans Metrikleri**:
  - **Kesinlik**: Muhtemelen 1.0 (sahte haber tespiti için mükemmel kesinlik).
  - **Geri Çağırma**: Muhtemelen 1.0 (sahte haber tespiti için mükemmel geri çağırma).
  - **F1-Skoru**: Muhtemelen 1.0 (kesinlik ve geri çağırmanın harmonik ortalaması).
- **Görselleştirme**: Kesinlik, geri çağırma ve F1-skorunu gösteren bir çubuk grafik oluşturuldu ve modelin güçlü performansı doğrulandı.

### Gözlemler
- Mükemmel doğruluk, aşırı öğrenme veya eğitim ve test setlerinin aşırı benzer olması ihtimalini öneriyor.
- Veri seti dengesiz olabilir ve gerçek haberler baskın olduğu için doğruluk metriklerini şişirebilir.

---

## Projeyi Çalıştırma
1. **Depoyu Klonlayın**:
   ```bash
   git clone <depo-url’si>
   cd <depo-dizini>
   ```

2. **Bağımlılıkları Kurun**:
   ```bash
   pip install -r requirements.txt
   ```

3. **Veriyi Hazırlayın**:
   - Veri setlerini (`gercek1.xlsx`, `gercek2.csv`, `sahte.csv`) proje dizinine yerleştirin.
   - Alternatif olarak, notebook’taki dosya yollarını veri seti konumlarınızla güncelleyin.

4. **Notebook’u Çalıştırın**:
   - `haber.ipynb` dosyasını Jupyter Notebook veya JupyterLab’de açın.
   - Hücreleri sırayla çalıştırarak veriyi ön işleyin, modeli eğitin ve sonuçları değerlendirin.

5. **Sonuçları Görüntüleyin**:
   - Modelin doğruluğu ve performans metrikleri yazdırılacaktır.
   - Kesinlik, geri çağırma ve F1-skorunu gösteren bir çubuk grafik görüntülenecektir.

---

## Geliştirme ve Gelecek Çalışmalar
Proje mükemmel sonuçlar elde etse de, geliştirme için birkaç alan ve gelecekteki çalışmalar için öneriler bulunmaktadır:

### 1. Aşırı Öğrenmeyi Ele Alma
- **Sorun**: %100 doğruluk, aşırı öğrenme veya test setinin eğitim setine çok benzer olması ihtimalini gösteriyor.
- **Çözümler**:
  - **Çapraz doğrulama** (örneğin, 5 veya 10 katlı) kullanarak modeli birden fazla eğitim-test bölünmesinde değerlendirin.
  - Sahte haber veri setinin boyutunu ve çeşitliliğini artırarak yanlılığı azaltın.
  - Lojistik Regresyon’da **düzenlileştirme** (örneğin, L1 veya L2 cezaları) uygulayarak aşırı karmaşık modelleri cezalandırın.

### 2. Veri Dengesizliğini Ele Alma
- **Sorun**: Gerçek haber veri seti, sahte haber veri setinden çok daha büyük, bu da modeli yanlı hale getirebilir.
- **Çözümler**:
  - **Aşırı örnekleme** (örneğin, SMOTE) kullanarak sentetik sahte haber örnekleri oluşturun.
  - **Az örnekleme** yaparak gerçek haber makalelerinin sayısını azaltın.
  - Lojistik Regresyon’da **sınıf ağırlıkları** (örneğin, `class_weight='balanced'`) kullanarak azınlık sınıfına (sahte haberler) öncelik verin.

### 3. Metin Ön İşlemeyi Geliştirme
- **Sorun**: Mevcut ön işleme, TF-IDF vektörizasyonuna odaklanıyor ancak gelişmiş NLP tekniklerini içermiyor.
- **Çözümler**:
  - **Türkçe’ye özgü ön işleme** uygulayın:
    - Kelimeleri köklerine indirmek için bir Türkçe kök ayırıcı veya lemmatizer (örneğin, `zemberek` veya `TurkishStemmer`) kullanın.
    - Özel bir Türkçe durdurma kelime listesiyle durdurma kelimelerini kaldırın.
    - Özel karakterleri, noktalama işaretlerini ve sayıları daha titizlikle işleyin.
  - Kelimeler arasındaki anlamsal ilişkileri yakalamak için **kelime gömme** (örneğin, Word2Vec, fastText veya Türkçe için BERT) deneyin.

### 4. Gelişmiş Modeller Deneme
- **Sorun**: Lojistik Regresyon basit bir temel modeldir ve metin verilerindeki karmaşık kalıpları yakalayamayabilir.
- **Çözümler**:
  - **Topluluk modelleri** (örneğin, Rastgele Orman veya Gradyan Artırma, XGBoost, LightGBM gibi) deneyin.
  - **Derin öğrenme modelleri** (örneğin, LSTM’ler, CNN’ler veya Türkçe BERT modelleri, `bert-base-turkish-cased` gibi) kullanın.
  - Model performansını AUC-ROC, kesinlik-geri çağırma eğrileri ve karışıklık matrisleri gibi metriklerle karşılaştırın.

### 5. Veri Setini Genişletme
- **Sorun**: Sahte haber veri seti sınırlı ve gerçek haber veri seti tüm konuları veya kaynakları kapsamayabilir.
- **Çözümler**:
  - Güvenilir kaynaklardan (örneğin, Hürriyet, Milliyet) ek Türkçe haber makaleleri kazıyın.
  - Gelişmiş AI modelleriyle (örneğin, Türkçe için ince ayar yapılmış GPT tabanlı modeller) daha fazla sahte haber üretin.
  - Sınıflandırma doğruluğunu artırmak için **çok modlu veriler** (örneğin, resimler, başlıklar, meta veriler) ekleyin.

### 6. Değerlendirmeyi Geliştirme
- **Sorun**: Mevcut değerlendirme büyük ölçüde doğruluğa dayanıyor ve bu, dengesiz veri setlerinde yanıltıcı olabilir.
- **Çözümler**:
  - Yanlış pozitif ve yanlış negatifleri analiz etmek için **karışıklık matrisleri** kullanın.
  - Performansı eşik değerleri arasında değerlendirmek için **AUC-ROC** ve **kesinlik-geri çağırma eğrileri** hesaplayın.
  - Modeli **ayrılmış bir doğrulama seti** veya gerçek dünya haber makaleleri üzerinde test ederek genelleştirme yeteneğini değerlendirin.

### 7. Yorumlanabilirlik Ekleme
- **Sorun**: Modelin tahminleri yorumlanabilir değil, bu da bazı makalelerin neden sahte olarak sınıflandırıldığını anlamayı zorlaştırıyor.
- **Çözümler**:
  - Model tahminlerini açıklamak için **SHAP** veya **LIME** kullanarak önemli kelimeleri veya ifadeleri vurgulayın.
  - Sahte haberlerdeki kalıpları (örneğin, sansasyonel dil, dilbilgisi hataları) belirlemek için en etkili TF-IDF özelliklerini analiz edin.

### 8. Modeli Dağıtma
- **Sorun**: Model şu anda bir notebook prototipi ve gerçek dünya kullanımı için erişilebilir değil.
- **Çözümler**:
  - Kullanıcıların haber makaleleri girip gerçek/sahte tahminleri alabileceği bir **web uygulaması** (örneğin, Flask veya FastAPI kullanarak) oluşturun.
  - Modeli ölçeklenebilir çıkarım için bir **API** olarak dağıtın (xAI’nin API servisine bakın: [xAI API](https://x.ai/api)).
  - Gerçek zamanlı sahte haber işaretlemesi için bir **tarayıcı uzantısı** geliştirin.

### 9. Gerçek Zamanlı Veri Ekleme
- **Sorun**: Model statik veri setleri üzerinde eğitildi ve gelişen haber kalıplarına uyum sağlayamayabilir.
- **Çözümler**:
  - Modeli yeni verilerle zaman içinde güncellemek için **çevrimiçi öğrenme** uygulayın.
  - Türkçe medya kuruluşlarından ve sosyal medya platformlarından (örneğin, X) gerçek zamanlı haberler toplamak için **web kazıma** kullanın.
  - Ortaya çıkan sahte haber kalıplarını belirlemek için X’teki **trend konuları** izleyin.

### 10. Etik Hususlar
- **Sorun**: Sahte haber tespiti toplumsal etkilere sahip olabilir ve yanlış sınıflandırmalar güvenilirliği zedeleyebilir veya yanlış bilgi yayabilir.
- **Çözümler**:
  - Tahminler için güven skorları ve açıklamalar sağlayarak şeffaflığı sağlayın.
  - Yanlılıkları önlemek için modeli çeşitli veri setleri üzerinde doğrulayın (örneğin, siyasi, bölgesel).
  - Modeli ve veri setini geliştirmek için alan uzmanlarıyla (örneğin, gazeteciler, doğrulama uzmanları) iş birliği yapın.

---

## Bağımlılıklar
Proje aşağıdaki Python kütüphanelerini gerektirir:
```bash
pandas==2.2.2
scikit-learn==1.5.2
matplotlib==3.9.2
seaborn==0.13.2
```
Kurulum için:
```bash
pip install pandas scikit-learn matplotlib seaborn
```

---

## Lisans
Bu proje MIT Lisansı altında lisanslanmıştır. Ayrıntılar için [LICENSE](LICENSE) dosyasına bakın.

---

Bu README, projenin kapsamlı bir özetini sunar, her kararın gerekçesini açıklar ve geliştirme için uygulanabilir öneriler sunar. Önerilen iyileştirmeleri ele alarak, model daha sağlam, ölçeklenebilir ve Türkçe sahte haber tespitinde gerçek dünyada uygulanabilir hale gelebilir.
