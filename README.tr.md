# Stream-Graph: Modernleştirilmiş bir Conda Ortamı (v1.0.0)

**[Click here for English README](README.md)**

[![Travis Status](https://travis-ci.org/ysig/stream_graph.svg?branch=master)](https://travis-ci.org/ysig/stream_graph)
[![CircleCI Status](https://circleci.com/gh/ysig/stream_graph/tree/master.svg?style=shield)](https://circleci.com/gh/ysig/stream_graph/tree/master)
[![Appveyor status](https://ci.appveyor.com/api/projects/status/kqwkk8khh6btkaep?svg=true)](https://ci.appveyor.com/project/ysig/stream-graph)

> **Not:** Bu, orijinal `stream_graph` kütüphanesi için modernleştirilmiş ve yeniden üretilebilir (reproducible) bir Conda ortamı sağlayan çatallanmış (forked) bir depodur. Yukarıdaki derleme durumu rozetleri (build status badges) orijinal depoya aittir ve mevcut durumu yansıtmayabilir.

Bu proje, ilk olarak Yiannis Siglidis ve arkadaşları tarafından geliştirilen güçlü `stream_graph` kütüphanesini, modern Python ortamlarında çalışmasını engelleyen kritik bağımlılık (dependency) sorunlarını çözerek yeniden canlandırmaktadır. **v1.0.0** olarak yeniden paketlenen bu sürüm, kararlı ve kurulumu kolay bir Conda yapısı sunarak araştırmacıların ve geliştiricilerin zamansal ağ analizi (temporal network analysis) için bu kütüphaneden tekrar yararlanmasını sağlar.

---

## Stream Graph Hakkında

Bir Stream Graph, düğümlerinin (nodes) ve bağlantılarının (links) zaman içinde ortaya çıkıp kaybolduğu bir çizgedir (graph). Statik bir çizgenin zamanı da içeren bir genellemesidir ve şu makalede resmi olarak tanımlanmıştır:

*   **Stream graphs and link streams for the modeling of interactions in complex systems**  
    *Matthieu Latapy, Tiphaine Viard, Clémence Magnien.*  
    [[arXiv:1710.04177]](https://arxiv.org/abs/1710.04177)

Bu kütüphane, sosyal medyadaki iletişim dinamikleri gibi gelişen ağların (evolving networks) zamansal boyutunun analizi için tasarlanmıştır.
---

## Modernleştirme Detayları (v1.0.0)

Orijinal `stream_graph` kütüphanesi birkaç yıl önce geliştirilmiştir ve temel Python veri bilimi kütüphanelerinin eski sürümlerine dayanmaktadır. Modern bir ortamda (örneğin, Python 3.7+ ve güncel Pandas sürümleri ile) çalıştırma denemeleri, bağımlılıklarındaki API değişiklikleri nedeniyle `AttributeError` ve `ImportError` istisnalarıyla (exceptions) sonuçlanmaktadır.

Bu fork, tam uyumluluk ve yeniden üretilebilirlik (reproducibility) sağlayarak, sürümleri hassas bir şekilde sabitlenmiş (version-pinned) kütüphanelerle kendi kendine yeten bir Conda ortamı oluşturarak bu sorunları giderir.

**Ana Düzeltmeler:**
*   **`pandas` Sürümü:** `AttributeError: 'BlockManager' object has no attribute '_mgr'` ve `FutureWarning` mesajlarını çözmek için `pandas==0.24.2` sürümüne sabitlendi. Orijinal kütüphane, Pandas 1.0+ API'leri ile uyumlu değildi.
*   **`jinja2` Sürümü:** `ImportError: cannot import name 'contextfilter' from 'jinja2'` hatasını düzeltmek için `jinja2==3.0.3` sürümüne sabitlendi. `contextfilter` yeni sürümlerde kullanımdan kaldırılmış ve silinmişti.
*   **Kapsamlı Ortam:** `environment.yml` dosyası artık, dahil edilen öğreticileri (tutorials) tek bir komutla doğrudan çalıştırabilmek için gerekli tüm bağımlılıkları (`bokeh`, `networkx`, `wordcloud` vb.) içermektedir.

## Kurulum

Bu projeyi kurmanın önerilen ve en kolay yolu Anaconda veya Miniconda dağıtımını kullanmaktır.

### Ön Koşullar

*   Anaconda or Miniconda
*   `git` command-line tool
*   `git` komut satırı aracı

### Adımlar

1.  **Depoyu Klonlayın (Clone the Repository):**
    Terminalinizi veya komut isteminizi açın ve bu depoyu klonlayın.
    ```bash
    git clone https://github.com/YOUR_USERNAME/stream_graph_modernizated.git
    cd stream_graph_modernizated
    ```
    *(`YOUR_USERNAME` kısmını kendi GitHub kullanıcı adınızla değiştirin)*

2.  **Conda Ortamını Oluşturun ve Aktifleştirin:**
    Bu tek komut, `environment.yml` dosyasını okur ve tüm doğru kütüphane sürümleriyle birlikte `sg_env` adında yeni bir Conda ortamını otomatik olarak oluşturur.
    ```bash
    conda env create -f environment.yml
    ```
    Ortam oluşturulduktan sonra aktifleştirin:
    ```bash
    conda activate sg_env
    ```

3.  **Kurulumu Doğrulayın:**
    Komut satırınızın başında artık `(sg_env)` ön eki görünmelidir. Projeyi çalıştırmaya hazırsınız.

## Kullanım: Öğreticiyi (Tutorial) Çalıştırma

Depo, kütüphanenin temel işlevlerini gösteren ODYCCEUS yaz okulundan orijinal öğreticiyi içermektedir.

1.  **Jupyter Notebook'u Başlatın:**
    `sg_env` ortamı aktifken, proje dizinine gidin ve Jupyter'i başlatın:
    ```bash
    jupyter notebook
    ```

2.  **Notebook'u Açın:**
    Web tarayıcınızda yeni bir sekme açılacaktır. `tutorials/ODYCCEUS/` dizinine gidin ve `tutorial.ipynb` notebook'unu açın.
g
3.  **Analizi Çalıştırın:**
    Orijinal analizi tekrarlamak için artık notebook'taki hücreleri (cells) çalıştırabilirsiniz.

---

## Orijinal Proje Bilgileri

*   **Orijinal Kaynak:** https://github.com/ysig/stream_graph
*   **Orijinal Dokümantasyon:** https://ysig.github.io/stream_graph/doc/
*   **Laboratuvar Web Sitesi:** http://www.complexnetworks.fr/

### Atıf (Citation)

Bu kütüphaneyi araştırmalarınızda kullanırsanız, lütfen orijinal makaleye atıfta bulunun:
```bibtex
@article{latapy2018stream,
  title={Stream graphs and link streams for the modeling of interactions in complex systems},
}
```

### Orjinal Geliştiriciler

Bu paket başlangıçta Odycceus projesi için Paris 6 Bilgisayar Bilimleri Laboratuvarı (LIP6) içinde karmaşık ağlar ekibinin araştırmacıları tarafından geliştirilmiştir.

*   Yiannis Siglidis: `<Yiannis.Siglidis@lip6.fr>`
*   Robin Lamarche-Perrin: `<Robin.Lamarche-Perrin@lip6.fr>`

### Modernizasyon Yaması

Bu paketin V1.0.0 sürümü kapsamında 2025 yılı itibariyle kütüphane yeniden kullanılabilir hale getirilmiştir.

*   Talha Göktuğ Gönen `<talhagoktug.gonen@nisantasi.edu.tr>`

### Lisans

`stream_graph`, **GNU Genel Kamu Lisansı V3.0**. ücretsiz yazılımıdır.