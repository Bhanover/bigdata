# 🕸️ Scraping / Ráscao! &mdash; 🕷️ Scrapy

![Logo Scrapy](images/scraper/scrapy.svg#derecha "Scrapy")

## Instalación

``` bash
conda install scrapy
```

## Compoñentes

### Proxecto

``` bash
scrapy startproject rascador
```

### Spiders

Tamén chamados arañas ou rastreadores web son programas que de xeito automático percorren unha ou varias páxinas webs. Poden navegar por (case) tódalas ligazóns e recopilar, indexar, *interactuar* ou analizar a información presente.

Creación dun spider:

``` bash
cd rascador
scrapy genspider rascoSpider jfsanchez.es
```

Execución do spider dentro dun proxecto

``` bash
scrapy crawl rascoSpider
```

Execución solta dun spider (sen facer caso de axustes e resto de proxecto)

``` bash
scrapy runspider rascador/spiders/rascoSpider.py
```

### Axustes

**settings.py**:

É un arquivo que nos permite configurar axustes para o proxecto (os diferentes spiders empregados).

Por exemplo, obviar o arquivo **robots.txt**, que permite indicar, entre outros axustes, que partes da nosa páxina non queremos facer dispoñibles aos robots de busca:

O seguinte exemplo:

1. Simula a navegación dende Microsoft Windows e Google Chrome (USER_AGENT e DEFAULT_REQUEST_HEADERS).
2. Ignora o arquivo robots.txt.
3. Activa as cookies (xa é a opción por defecto).

``` python
USER_AGENT = "Mozilla/5.0 (Windows NT 11.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/134.0.6998.166 Safari/537.36"

ROBOTSTXT_OBEY = False

COOKIES_ENABLED = True

DEFAULT_REQUEST_HEADERS = {
    "Accept": "text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8",
    "Accept-Language": "es-ES,es;q=0.8",
    "Accept-Encoding": "gzip, deflate, br, zstd",
}
```

### Funcións asíncronas




## Exemplos

### Exemplo para a páxina OpenBSD

Lembra mudar no arquivo ```settings.py``` o axuste:

``` python
ROBOTSTXT_OBEY = True
```

``` python title='OpenBSDSpider.py'
import scrapy
from urllib.parse import urljoin

class OpenBSDSpider(scrapy.Spider):
    name = "openbsd"
    allowed_domains = ["openbsd.org"]
    start_urls = ["https://www.openbsd.org/"]
    seen = set()

    def parse(self, response):
        self.seen.add(response.url)
        text = " ".join(t.strip() for t in response.xpath("//text()").getall() if t.strip())
        yield {"url": response.url, "text": text}

        for href in response.xpath("//a/@href").getall():
            url = urljoin(response.url, href)
            if url.startswith("https://www.openbsd.org/") and url not in self.seen:
                yield scrapy.Request(url, callback=self.parse)
```


## Máis información

- Web oficial:
    - <https://www.scrapy.org>
    - <https://docs.scrapy.org/en/latest/intro/tutorial.html#creating-a-project>
    - Exemplo: <https://github.com/scrapy/quotesbot>
    - Carga de contido dinámico (headless browser) <https://docs.scrapy.org/en/latest/topics/dynamic-content.html#topics-headless-browsing>
    - <https://docs.scrapy.org/en/latest/topics/dynamic-content.html#topics-inspecting-source>

- Estándares:
    - <https://www.robotstxt.org/>

- Para os User agents (identificador do navegador):
    - <https://www.whatismybrowser.com/guides/the-latest-user-agent/chrome>
    - <https://www.useragentstring.com/pages/Chrome/>

- Tamén pode interesarte (relacionado):
    - <https://administraciondesistemas.com/scrapy-la-herramienta-de-scraping-mas-poderosa-y-tambien-la-mas-temida-por-millones-de-sitios-web/>
