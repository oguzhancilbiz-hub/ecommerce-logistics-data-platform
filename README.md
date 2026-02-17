🚀 Multi-Domain Data Platform (E-Commerce & Logistics)
Bu proje; Greenweez (E-ticaret) ve Circle Parcel (Lojistik) verilerinin, Modern Data Stack araçları kullanılarak uçtan uca taşınması, modellenmesi ve raporlanması süreçlerini kapsamaktadır.

🏗️ Veri Hattı (Data Pipeline) Mimarisi
Proje, verinin kaynağından alınarak raporlanabilir hale gelmesine kadar olan tüm Modern ELT süreçlerini içerir:
<img width="1835" height="732" alt="lineage_graph" src="https://github.com/user-attachments/assets/515c7e2b-7c33-4e94-bb36-ef49fed1292a" />


Ingestion (Veri Alımı): Google Sheets ve Cloud Storage üzerinde bulunan ham veriler, Fivetran aracılığıyla otomatik olarak BigQuery'ye aktarılmaktadır.

Warehouse: Google BigQuery

Transformation: dbt (Data Build Tool)

Version Control: GitHub

📁 Veri Modelleme Yapısı
Modeller, dbt "best-practice" prensiplerine ve Medallion Architecture (Staging -> Intermediate -> Mart) yapısına uygun olarak kurgulanmıştır:

1. Greenweez (E-Commerce)
Staging: Fivetran üzerinden gelen ham verilerin temizlendiği ve standart veri tiplerine (casting) dönüştürüldüğü ilk katman.

Intermediate: İş mantıklarının (Business Logic) uygulandığı ve tablolar arası karmaşık join işlemlerinin yapıldığı ara katman.

Mart (Finance): Finansal raporlama ve KPI analizi için optimize edilmiş, son kullanıcıya hazır tablolar.

2. Circle Parcel (Logistics)
Lojistik ve sevkiyat operasyonlarının takibi için kurgulanan staging modellerini içerir.

📂 Klasör Yapısı (Repository Structure)
Plaintext
models/
├── greenweez/
│   ├── staging/        # Veri temizleme (Fivetran sources)
│   ├── intermediate/   # İş mantığı ve join operasyonları
│   └── mart/finance/   # Raporlamaya hazır finansal tablolar
└── Circle_parcel/
    └── staging/        # Lojistik verileri ön hazırlık katmanı
🚀 Öne Çıkan Özellikler
Fivetran Automation: Veri kaynakları ile veri ambarı arasındaki senkronizasyon otomatik hale getirilmiştir.

Data Quality: schema.yml üzerinden yönetilen otomatik testler (unique, not_null) ile veri bütünlüğü sağlanmaktadır.

Modular Design: Farklı iş birimleri tek bir repo üzerinde, ölçeklenebilir ve izole şekilde yönetilmektedir.
