# Adaptive Media - Multiplex megjelenés

Ez a reklám típus videó tartalom megjelenítésére szolgál.

## Fejlesztése

A /multiplex/ könyvtáron belül található "multiplex.html" megnyitása a böngészőben demonstrálja a megjelenést offline módon. Itt lehet szerkeszteni a megjelenés forrását. Az alábbi sor jelöli a kezdetét a multiplex megjelenés forráskódjának:

```html
<div id="multiplex_container"...
```

## Használata

A /multiplex/ könyvtáron belül található "multiplex_code.html" tartalmát kell felvenni HTML-ként az adengine-be. Ez mindig a tömörített javascripteket és a CSS-eket, illetve azokra történő hivatkozásokat kell, hogy tartalmazza, melyeket előzetesen a "multiplex.html" fájlban dolgoztunk ki tömörítettlenül. 

## A használathoz szükséges fájlok

"adaptiveMultiplex.css"
"adaptiveMultiplex.min.js"
videó fájlok,
előnézeti kép fájl
### Előnézeti kép tulajdonságai:
1160x773px

### Videó fájlok tulajdonságai:
képarány:16:9
A két videó kiterjesztése: 
#### egyik videó: MP4, amelyben H.264 a videó és MP3 a hang enkódolása. 
#### másik videó: Webm, Vorbis enkódolású

##### Mozzila leírása a böngésző támogatottságról és enkódolásról: https://developer.mozilla.org/en-US/docs/Web/HTML/Supported_media_formats

Ezeket a fájlokat fel kell venni az adengine-be és bekötni a "multiplex_code.html" fájlon belül látható módon a megfelelő helyekre.

## "multiplex_code.html" fájl felépítése és használata

Az alábbi konfigurációs objektumban lehet beállítani kattintási kódot, előnézeti képet, statisztikai események URL kéréseit.

```html
    <script>
        adaptiveMediaMultiplexConfig = {
            clickURL: 'http://adaptivemedia.hu',
            clickTarget: '_blank',
            video: {
                url: {
                    previewImage: 'https://bbcdn.go.cz.bbelements.com/creatives/b81/847/7/b818477/extra/poster_.jpg'
                },
                events: {
                    manual_expand: 'https://go.eu.bbelements.com/please/track/adDisplay/campaign/196751/plan/769887/banner/824621/bannerType/9/?',
                    end: 'https://go.eu.bbelements.com/please/track/adDisplay/campaign/196751/plan/769890/banner/824621/bannerType/9/?',
                    proc01: {
                        percentage: 50,
                        url: 'https://go.eu.bbelements.com/please/track/adDisplay/campaign/196751/plan/769882/banner/824621/bannerType/9/?'
                    },
                    proc02: {
                        percentage: 75,
                        url: 'https://go.eu.bbelements.com/please/track/adDisplay/campaign/196751/plan/769884/banner/824621/bannerType/9/?'
                    }
                }
            }
        }
    </script>
```

A <source> HTML tagok "src" attributumaiban lehet megadni a különböző videó fájl formátumok URL-jeit.

```html
    <video id="adaptiveMultiplexVideo" class="video-js vjs-default-skin" controls preload="auto" width="100%" height="100%" data-setup='{ "inactivityTimeout": 0 }' webkit-playsinline playsinline>
        <source src="//bbcdn.go.cz.bbelements.com/creatives/b81/847/7/b818477/extra/egyenesen_at.webm" id="adaptiveMultiplexVideoWEBM" type="video/webm" />
        <source src="//bbcdn.go.cz.bbelements.com/creatives/b81/847/7/b818477/extra/egyenesen_at.mp4" id="adaptiveMultiplexVideoMP4" type="video/mp4" />
        <p class="vjs-no-js">To view this video please enable JavaScript, and consider upgrading to a web browser that <a href="http://videojs.com/html5-video-support/"
            target="_blank">supports HTML5 video</a></p>
        </video>
```
