# ETL100 - Sakila Veritabanı Analiz Projesi

Bu proje, Sakila DVD kiralama veritabanı üzerinde kapsamlı veri analizi ve ETL (Extract, Transform, Load) işlemleri gerçekleştiren bir Jupyter Notebook projesidir. Proje, 100 farklı analitik soru üzerinden veritabanındaki ilişkileri, trendleri ve istatistikleri incelemektedir.

##  Proje Hakkında

Sakila, MySQL'in örnek veritabanı olarak sunulan bir DVD kiralama mağazası simülasyonudur. Bu proje, bu veritabanı üzerinde Python ve Pandas kullanarak çeşitli analitik sorgular gerçekleştirmektedir.

##  Özellikler

Proje aşağıdaki konularda 100 farklı analiz sorusu içermektedir:

- **Film ve Oyuncu Analizleri**: Film-oyuncu ilişkileri, oyuncu performansları
- **Kiralama İstatistikleri**: Kiralama sayıları, süreleri, iade durumları
- **Müşteri Analizleri**: Müşteri davranışları, harcama analizleri, coğrafi dağılım
- **Gelir Analizleri**: Film bazlı, kategori bazlı, müşteri bazlı gelir analizleri
- **Kategori Analizleri**: Film kategorilerine göre performans metrikleri
- **Çalışan Performansı**: Staff bazlı kiralama ve gelir analizleri
- **Envanter Yönetimi**: Stok durumu, rafta bekleyen filmler
- **Coğrafi Analizler**: Şehir bazlı kiralama ve gelir dağılımları

##  Teknolojiler

- **Python 3.x**
- **Pandas**: Veri manipülasyonu ve analizi
- **SQLite**: Veritabanı bağlantısı
- **Jupyter Notebook**: İnteraktif geliştirme ortamı

##  Kurulum

### Gereksinimler

Projeyi çalıştırmak için aşağıdaki paketlerin yüklü olması gerekir:

```bash
pip install pandas sqlite3 ipython-sql
```

Not: `sqlite3` genellikle Python ile birlikte gelir, ancak gerekirse yüklenebilir.

### Veritabanı

Proje, `sqlite-sakila.db` adlı SQLite veritabanı dosyasını kullanmaktadır. Bu dosyanın proje dizininde bulunduğundan emin olun.

##  Kullanım

1. Projeyi klonlayın veya indirin:
```bash
git clone <repository-url>
cd ETL100
```

2. Gerekli paketleri yükleyin:
```bash
pip install -r requirements.txt
```

3. Jupyter Notebook'u başlatın:
```bash
jupyter notebook ETL100.ipynb
```

4. Notebook'u hücre hücre çalıştırarak analizleri görüntüleyin.

## 📊 Analiz Kategorileri

### Temel Sorgular (1-10)
- Tüm verilerin görüntülenmesi
- Film-oyuncu ilişkileri
- Envanter durumu
- Kiralama istatistikleri

### Gelişmiş Analizler (11-30)
- Kategori bazlı analizler
- Müşteri davranış analizleri
- Çalışan performans metrikleri
- Gelir optimizasyonu analizleri

### Detaylı İncelemeler (31-50)
- Coğrafi dağılım analizleri
- Film performans karşılaştırmaları
- Müşteri segmentasyonu

### Kapsamlı Analizler (51-100)
- Aktör performans analizleri
- Kategori trend analizleri
- Kapsamlı gelir ve kiralama metrikleri

##  Proje Yapısı

```
ETL100/
│
├── ETL100.ipynb          # Ana Jupyter Notebook dosyası
├── sqlite-sakila.db      # SQLite veritabanı dosyası
├── README.md             # Bu dosya
└── requirements.txt      # Python paket gereksinimleri (opsiyonel)
```

## 🔍 Örnek Sorgular

### Film ve Oyuncu İlişkileri
```python
# Her filmdeki oyuncuları listele
film_actor_list = film_df.merge(film_actor_df, on="film_id") \
                         .merge(actor_df, on="actor_id") \
                         [["title", "first_name", "last_name"]]
```

### Gelir Analizi
```python
# En çok gelir getiren film
film_revenue = payment.merge(rental, on="rental_id") \
                      .merge(inventory, on="inventory_id") \
                      .merge(film, on="film_id") \
                      .groupby("title")["amount"].sum() \
                      .sort_values(ascending=False)
```

##  Sonuçlar

Proje, DVD kiralama işletmesi için aşağıdaki alanlarda değerli içgörüler sağlamaktadır:

- En popüler film kategorileri
- En karlı müşteri segmentleri
- Çalışan performans metrikleri
- Stok yönetimi optimizasyonu
- Coğrafi pazar analizleri


##  Kaynaklar

- [Sakila Veritabanı Dokümantasyonu](https://dev.mysql.com/doc/sakila/en/)
- [Pandas Dokümantasyonu](https://pandas.pydata.org/docs/)
- [SQLite Dokümantasyonu](https://www.sqlite.org/docs.html)

---

