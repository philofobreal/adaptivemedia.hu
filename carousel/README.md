# Adaptive Media - Carousel megjelenés

Ez a reklám típus videó tartalom megjelenítésére és képek bemutatására szolgál.

## Használata

A "carousel.zip" fájlt kell felvenni az adengine-be. A benne található "index.html" 
fájl tartalmát pedig be kell másolni az "insert HTML version" részhez.

## A használathoz szükséges fájlok

2 videó fájl kell (MP4, Webm) [optionális], 
1 Háttérkép fájl (640 360),
2 (vagy több) lapozható kép fájl

* **Képek tulajdonságai**:
    * **Háttérkép:** 640x360px, max 300Kbyte
        * A "avangerbg.png" képi mintán látható szaggatott területre kell elhelyezni a logót. A többi területre csak dizájn elemeket szabad elhelyezni. Mobilon a szaggatott terület szélességén kívül eső részek nem fognak látszani.
    * **Lapozható képek:** 300x250px, max 200Kbyte

* **Videó fájlok tulajdonságai**:
    * **Képarány:** 16:9
    * **Méret:** max 10Mbyte
    * **Első videó:** MP4, amelyben H.264 a videó és MP3 a hang enkódolása. 
    * **Második videó:** Webm, Vorbis enkódolású

##### Mozilla leírása a böngésző támogatottságról és enkódolásról: https://developer.mozilla.org/en-US/docs/Web/HTML/Supported_media_formats
##### Online Webm - MP4 konverter: https://cloudconvert.com/webm-to-mp4
##### Leírás az Online Webm - MP4 konverterhez: https://github.com/philofobreal/adaptivemedia.hu/blob/master/carousel/video_converter_webm_to_mp4.fw.png

Az alábbi konfigurációs objektumban lehet beállítani kattintási kódot, előnézeti képet, statisztikai események URL kéréseit. Ez a konfiguráció az "index.html" fájlban található a "carousel.zip" fájlon belül. 

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
                
                pagination: {
                    el: ".swiper-pagination"
                },

                navigation: {
                    nextEl: ".swiper-button-next",
                    prevEl: ".swiper-button-prev"
                }
            }
        }

    </script>
```


