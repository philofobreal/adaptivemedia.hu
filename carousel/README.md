# Adaptive Media - Carousel megjelenés

Ez a reklám típus videó tartalom megjelenítésére szolgál.

## Használata

A "carousel.zip" fájlt kell felvenni az adengine-be.

## A használathoz szükséges fájlok

"adaptiveMultiplex.css"
"adaptiveMultiplex.min.js"
2 videó fájl kell (MP4, Webm), [optionális]
1 Háttérkép fájl
2 lapozható kép fájl

### Előnézeti kép tulajdonságai:
#### Méret: 1160x773px, max 500Kbyte,

### Videó fájlok tulajdonságai:
#### Képarány:16:9
#### Méret: max 10Mbyte
#### -Első videó: MP4, amelyben H.264 a videó és MP3 a hang enkódolása. 
#### -Második videó: Webm, Vorbis enkódolású

##### Mozilla leírása a böngésző támogatottságról és enkódolásról: https://developer.mozilla.org/en-US/docs/Web/HTML/Supported_media_formats
##### Online Webm - MP4 konverter: https://cloudconvert.com/webm-to-mp4

Ezeket a fájlokat fel kell venni az adengine-be és bekötni a "multiplex_code.html" fájlon belül látható módon a megfelelő helyekre.

## "multiplex_code.html" fájl felépítése és használata

Az alábbi konfigurációs objektumban lehet beállítani kattintási kódot, előnézeti képet, statisztikai események URL kéréseit.

```html
    <script>
        window.adaptiveMediaCarousel = {
        clickURL: "http://adaptivemedia.hu",
        clickTarget: "_blank",
        hasVideo: true,
        backgroundImage: 'https://bbcdn.go.cz.bbelements.com/creatives/cdn12653/b88/359/5/b883595/extra/avangerbg_minta_03.fw.png',
        images: [
            'https://bbcdn.go.cz.bbelements.com/creatives/cdn12653/b88/359/5/b883595/extra/avangers2_05.fw.png',
            'https://bbcdn.go.cz.bbelements.com/creatives/cdn12653/b88/359/5/b883595/extra/avangers_tanos_06.fw.png'
        ],
        multiplex: {
            clickURL: "http://adaptivemedia.hu",
            clickTarget: "_blank",
            video: {
            url: {
                WEBM: "https://bbcdn.go.cz.bbelements.com/creatives/cdn12653/b88/359/5/b883595/extra/infinitywar.webm",
                MP4: "https://bbcdn.go.cz.bbelements.com/creatives/cdn12653/b88/359/5/b883595/extra/infinitywar.mp4",
                previewImage: "https://bbcdn.go.cz.bbelements.com/creatives/cdn12653/b88/359/5/b883595/extra/maxresdefault1.jpg"
            },
            events: {
                manual_expand: "https://go.eu.bbelements.com/please/track/adDisplay/campaign/196751/plan/769887/banner/824621/bannerType/9/?",
                end: "https://go.eu.bbelements.com/please/track/adDisplay/campaign/196751/plan/769890/banner/824621/bannerType/9/?",
                proc01: {
                percentage: 50,
                url: "https://go.eu.bbelements.com/please/track/adDisplay/campaign/196751/plan/769882/banner/824621/bannerType/9/?"
                },
                proc02: {
                percentage: 75,
                url: "https://go.eu.bbelements.com/please/track/adDisplay/campaign/196751/plan/769884/banner/824621/bannerType/9/?"
                }
            }
            }
        },
        swiperConfig: {
            // Optional parameters
            allowTouchMove: false,        
            direction: "horizontal",
            loop: false,
            simulateTouch: false,

            keyboard: {
            enabled: true,
            onlyInViewport: false,
            },

            autoplay: {
            delay: 2500,
            disableOnInteraction: false,
            },
            // If we need pagination
            pagination: {
            el: ".swiper-pagination"
            },

            // Navigation arrows
            navigation: {
            nextEl: ".swiper-button-next",
            prevEl: ".swiper-button-prev"
            }

        }
        }

    </script>
```

A <source> HTML tagok "src" attributumaiban lehet megadni a különböző videó fájl formátumok URL-jeit. Az első a Webm kiterjesztés, a második az MP4 kiterjesztés.

```html
    <video id="adaptiveMultiplexVideo" class="video-js vjs-default-skin" controls preload="auto" width="100%" height="100%" data-setup='{ "inactivityTimeout": 0 }' webkit-playsinline playsinline>
        <source src="//bbcdn.go.cz.bbelements.com/creatives/b81/847/7/b818477/extra/egyenesen_at.webm" id="adaptiveMultiplexVideoWEBM" type="video/webm" />
        <source src="//bbcdn.go.cz.bbelements.com/creatives/b81/847/7/b818477/extra/egyenesen_at.mp4" id="adaptiveMultiplexVideoMP4" type="video/mp4" />
        <p class="vjs-no-js">To view this video please enable JavaScript, and consider upgrading to a web browser that <a href="http://videojs.com/html5-video-support/"
            target="_blank">supports HTML5 video</a></p>
        </video>
```
