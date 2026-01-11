# 🕸️ Scraping / Ráscao!

![scraping](images/scraper/scraper.png#derecha "Scraping web")

Scraping significa arañar en inglés. Cando falamos de scrapear, web scraping, arañado de datos ou raspado de datos estamos a falar da extracción dos mesmos dunha páxina web de xeito habitualmente automatizado.

O xeito máis simple é mediante [**🤖 API REST**](scraping-requests-api.md). Normalmente é información preparada para ser extraída automáticamente.

Tamén podemos extraer esta información directamente de HTML, PDF e outros formatos descargando as páxinas.

No caso de páxinas estáticas (que non requiran javascript para cargar os datos) unha boa alternativa é [**🥫 Beautiful Soup**](scraping-bs.md).

Pola conta [**✅ Selenium**](scraping-selenium.md) é unha suite que sirve tanto para probar páxinas como para extraer información que requira carga de javascript, interactuar con formularios e carga dinámica.

Ademáis, nos últimos anos tense posto de moda o framework de extracción de datos [**🕷️ Scrapy**](scraping-scrapy.md)  permitindo ter de forma ordeada configuracións comúns tales como: cookies, cabeceiras, proxies, etc. Permite engadir de xeito simple cabeceiras, limitación de peticións e consultas (rate limits) e esperas (delays). Ademáis Scrapy é compatible con Beautiful Soup.

## Máis información

- <https://es.wikipedia.org/wiki/Web_scraping>
- <https://es.wikipedia.org/wiki/Transferencia_de_Estado_Representacional>
