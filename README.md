# Web Crawler

Պարզ և արդյունավետ web crawler Python-ով իրականացված:

## Հնարավորություններ

- 🔍 Web էջերի crawling/ցիրույց
- 📊 Տվյալների հավաքագրում և պահպանում
- 🚦 Rate limiting և respect robots.txt
- 📁 JSON և CSV ֆորմատներով արտահանում
- 📈 Վիճակագրություն և logging
- 🌐 Same-domain և cross-domain crawling
- ⚙️ Կարգավորվող պարամետրեր

## Կախությունները

Անհրաժեշտ Python packages:

```bash
pip install requests beautifulsoup4 lxml
```

## Տեղադրում

1. Clone repository:
```bash
git clone https://github.com/yourusername/web-crawler.git
cd web-crawler
```

2. Տեղադրեք կախությունները:
```bash
pip install -r requirements.txt
```

## Օգտագործում

### Command Line Interface

Հիմնական օգտագործում:
```bash
python crawler.py https://example.com
```

Ընդլայնված օպցիաներ:
```bash
python crawler.py https://example.com \
  --max-pages 100 \
  --delay 2 \
  --timeout 15 \
  --output my_crawl \
  --format json \
  --cross-domain
```

### Python API

```python
from crawler import WebCrawler

# Ստեղծել crawler instance
crawler = WebCrawler(max_pages=50, delay=1)

# Սկսել crawling
crawler.crawl('https://example.com')

# Պահպանել տվյալները
crawler.save_to_json('results.json')
crawler.save_to_csv('results.csv')

# Ստանալ վիճակագրություն
stats = crawler.get_statistics()
print(stats)
```

## Պարամետրեր

| Պարամետր | Նկարագրություն | Default արժեք |
|-----------|----------------|---------------|
| `max_pages` | Առավելագույն crawl արվող էջերի քանակ | 50 |
| `delay` | Delay requests-ների միջև (վրկ) | 1 |
| `timeout` | Request timeout (վրկ) | 10 |
| `same_domain_only` | Crawl միայն նույն domain-ից | True |

## Ֆայլային կառուցվածք

```
web-crawler/
├── crawler.py          # Հիմնական crawler implementation
├── requirements.txt    # Python dependencies
├── README.md          # Նախագծի նկարագրություն
├── .gitignore         # Git ignore rules
├── examples/          # Օրինակներ
│   ├── basic_usage.py
│   └── advanced_usage.py
└── tests/             # Unit tests
    ├── __init__.py
    ├── test_crawler.py
    └── test_utils.py
```

## Արտահանման ֆորմատներ

### JSON Output
```json
{
  "url": "https://example.com",
  "title": "Example Domain",
  "description": "Example website",
  "headings": [
    {"tag": "h1", "text": "Example Domain"}
  ],
  "text_preview": "This domain is for use in illustrative examples...",
  "images": [
    {"url": "https://example.com/image.jpg", "alt": "Example image"}
  ],
  "crawl_timestamp": "2024-01-15T10:30:45",
  "links_count": 15
}
```

### CSV Output
CSV ֆայլը պարունակում է հետևյալ columns:
- url
- title
- description
- text_preview
- links_count
- crawl_timestamp

## Օրինակներ

### Հիմնական օգտագործում
```python
crawler = WebCrawler(max_pages=10)
crawler.crawl('https://news.am')
crawler.save_to_json('news_crawl.json')
```

### Բազմաթիվ domains
```python
crawler = WebCrawler(max_pages=50, delay=2)
crawler.crawl('https://example.com', same_domain_only=False)
```

### Կարգավորված headers
```python
crawler = WebCrawler()
crawler.headers['Accept-Language'] = 'hy,en;q=0.9'
crawler.crawl('https://example.com')
```

## Logging

Crawler-ը ապահովում է մանրամասն logging:
- Console output real-time progress-ի համար
- `crawler.log` ֆայլ մանրամասն logs-ի համար

## Սահմանափակումներ

- Հարգում է robots.txt (ապագա ամսություն)
- Չի աջակցում JavaScript-rendered content
- Չի աջակցում session management
- Կախված է content-type headers-ից

## Զարգացում

### Tests գործարկում
```bash
python -m pytest tests/
```

### Code formatting
```bash
black crawler.py
```

## Լիցենզիա

MIT License - տես LICENSE ֆայլը մանրամասների համար:

## Ներդրում

Pull requests-ը ողջունվում են! Խնդիրների կամ բարելավումների համար:

1. Fork repository
2. Ստեղծեք feature branch (`git checkout -b feature/amazing-feature`)
3. Commit փոփոխությունները (`git commit -m 'Add amazing feature'`)
4. Push branch-ը (`git push origin feature/amazing-feature`)
5. Բացեք Pull Request


