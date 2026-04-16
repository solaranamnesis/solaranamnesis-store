# Localization Documentation

This document describes how language index pages are structured, how to add new languages, and provides a reference for all translations used in the Solar Anamnesis Store.

---

## Overview

Each language version of the store's index page is a standalone HTML file named `index-{lang}.html`, where `{lang}` is the [ISO 639-1](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) (or relevant BCP 47) language tag.

**Current language files:**

| File | Language |
|------|----------|
| `index.html` | English (original) |
| `index-am.html` | Amharic (አማርኛ) |
| `index-ar.html` | Arabic (العربية) |
| `index-az.html` | Azerbaijani (Azərbaycan dili) |
| `index-bn.html` | Bengali (বাংলা) |
| `index-bo.html` | Lhasa Tibetan (ལྷ་སའི་སྐད་) |
| `index-de.html` | German |
| `index-el.html` | Greek (Ελληνικά) |
| `index-es.html` | Spanish |
| `index-eu.html` | Basque (Euskara) |
| `index-fa.html` | Persian (فارسی) |
| `index-fi.html` | Finnish (Suomi) |
| `index-fr.html` | French |
| `index-gu.html` | Gujarati (ગુજરાતી) |
| `index-ha.html` | Hausa |
| `index-he.html` | Hebrew (עברית) |
| `index-hi.html` | Hindi (हिन्दी) |
| `index-hu.html` | Hungarian (Magyar) |
| `index-hy.html` | Armenian (Հայերեն) |
| `index-id.html` | Bahasa Indonesia |
| `index-it.html` | Italian |
| `index-ja.html` | Japanese (日本語) |
| `index-jv.html` | Javanese (Basa Jawa) |
| `index-ka.html` | Georgian (ქართული) |
| `index-kn.html` | Kannada (ಕನ್ನಡ) |
| `index-ko.html` | Korean (한국어) |
| `index-la.html` | Latin (Latina) |
| `index-mg.html` | Malagasy |
| `index-mn.html` | Mongolian Latin Script (Mongol) |
| `index-mr.html` | Marathi (मराठी) |
| `index-new.html` | Nepal Bhasa (𑐣𑐾𑐥𑐵𑐮 𑐨𑐵𑐲𑐵) |
| `index-nl.html` | Dutch (Nederlands) |
| `index-or.html` | Odia (ଓଡ଼ିଆ) |
| `index-pa.html` | Punjabi (ਪੰਜਾਬੀ) |
| `index-pl.html` | Polish (Język Polski) |
| `index-pt.html` | Portuguese |
| `index-ru.html` | Russian (Русский) |
| `index-si.html` | Sinhala (සිංහල) |
| `index-sv.html` | Swedish (Svenska) |
| `index-sw.html` | Kiswahili |
| `index-ta.html` | Tamil (தமிழ்) |
| `index-te.html` | Telugu (తెలుగు) |
| `index-th.html` | Thai (ไทย) |
| `index-tl.html` | Tagalog (Filipino) |
| `index-tr.html` | Turkish (Türkçe) |
| `index-tt.html` | Tatar (Tatarça) |
| `index-ur.html` | Urdu (اردو) |
| `index-vi.html` | Vietnamese (Tiếng Việt) |
| `index-yo.html` | Yoruba (Yorùbá) |
| `index-zh.html` | Chinese (中文) |
| `index-kk.html` | Kazakh (Қазақша) |
| `index-ky.html` | Kyrgyz (Кыргызча) |
| `index-cs.html` | Czech (Česky) |
| `index-uk.html` | Ukrainian (Українська) |
| `index-ro.html` | Romanian (Română) |
| `index-ku.html` | Kurdish Kurmanji (Kurdî / Kurmancî) |
| `index-bg.html` | Bulgarian (Български) |
| `index-my.html` | Burmese (မြန်မာ) |
| `index-so.html` | Somali (Af Soomaali) |
| `index-zu.html` | Zulu (isiZulu) |
| `index-ht.html` | Haitian Creole (Kreyòl ayisyen) |
| `index-da.html` | Danish (Dansk) |
| `index-no.html` | Norwegian Bokmål (Norsk Bokmål) |
| `index-qu.html` | Quechua (Runa Simi) |

---

## Page Structure

Each `index-{lang}.html` file follows the same HTML template. Key elements to localize are:

1. **`<html lang="...">`** — Set to the appropriate language tag (e.g., `lang="fi"` for Finnish).
2. **`<title>`** — The page title in the target language.
3. **`<h1>` heading** — The word for "Collections" in the target language.
4. **Each `<a>` link text** — The translated name of each meteorite collection.

All links (`href` attributes) point to the same English-path URLs and must **not** be translated.

### Template Skeleton

```html
<!doctype html>
<html lang="{LANG_CODE}">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1" />
    <title>{PAGE_TITLE}</title>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bulma@1.0.2/css/bulma.min.css" />
    <style>
      body {
        background: linear-gradient(to bottom, #013, #036);
        color: #fff;
      }
      .card { background-color: rgba(0, 51, 102, 0.9); border: 1px solid #fff; }
      .card a { color: #fff; }
      .card a:hover { color: gold; }
    </style>
  </head>
  <body>
    <section class="section">
      <div class="container">
        <h1 class="title has-text-centered">{COLLECTIONS_HEADING}</h1>
        <div class="columns is-multiline">
          <!-- One .column.is-one-third block per collection -->
          <div class="column is-one-third">
            <div class="card">
              <div class="card-content">
                <p class="title">
                  <a href="https://store.solaranamnesis.com/{CollectionPath}">{TRANSLATED_NAME}</a>
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </body>
</html>
```

---

## Adding a New Language

1. **Copy** any existing `index-{lang}.html` as a starting point.
2. **Rename** the file to `index-{new_lang}.html` using the correct ISO 639-1 code.
3. **Update** the `<html lang="...">` attribute.
4. **Update** the `<title>` to the store name in the new language.
5. **Translate** the `<h1>` heading ("Collections") and each link's display text.
6. **Do not change** any `href` URL values — they must remain as-is.
7. **Add an entry** to `README.md` with a link to the new file.
8. **Add the language** to the translations reference table below.

---

## Collections — URL Path Reference

| English Name | URL Path |
|---|---|
| Acapulcoite Meteorites | `/AcapulcoiteMeteorites` |
| Angrite Meteorites | `/AngriteMeteorites` |
| Aubrite Meteorites | `/AubriteMeteorites` |
| Brachinite Meteorites | `/BrachiniteMeteorites` |
| Enstatite Chondrites | `/EnstatiteChondrites` |
| Gigapixel Gallery | `/GigapixelGallery` |
| HED Meteorites | `/HEDMeteorites` |
| High Metal Group | `/HighMetalGroup` |
| Individual MicroShots | `/IndividualMicroShots` |
| Iron Meteorites | `/IronMeteorites` |
| Karoonda Group | `/KaroondaGroup` |
| Lodranite Meteorites | `/LodraniteMeteorites` |
| Lunar Meteorites | `/LunarMeteorites` |
| Martian Meteorites | `/MartianMeteorites` |
| Mesosiderite Meteorites | `/MesosideriteMeteorites` |
| Mighei Group | `/MigheiGroup` |
| Miscellaneous | `/Misc` |
| Ordinary Chondrites | `/OrdinaryChondrites` |
| Ornans Group | `/OrnansGroup` |
| Pallasite Meteorites | `/PallasiteMeteorites` |
| Renazzo Group | `/RenazzoGroup` |
| Rumuruti Chondrites | `/RumurutiChondrites` |
| STRESS Style Thin Sections | `/STRESSStyleThinSections` |
| Unclassified Meteorites | `/UnclassifiedMeteorites` |
| Ungrouped Achondrite Meteorites | `/UngroupedAchondriteMeteorites` |
| Ureilite Meteorites | `/UreiliteMeteorites` |
| Vigarano Group | `/VigaranoGroup` |

---

## Translations Reference

The table below records all translations for collections across languages. Scientific terms often retain their Latin/international form. Group names that are proper nouns are frequently left unchanged. "STRESS Style Thin Sections" is a specific product name and is kept in English.

> **Note:** Translations should be verified with native speakers before use in production.

### Collections Heading

| Language | Code | Translation |
|---|---|---|
| English | en | Collections |
| Latin | la | Collectiones |
| Basque | eu | Bilduma |
| Finnish | fi | Kokoelmat |
| Mongolian (Latin) | mn | Kholboloo |
| Tatar | tt | Cıyın |
| Kazakh | kk | Жинақтар |
| Kyrgyz | ky | Жыйнактар |
| Czech | cs | Sbírky |
| Ukrainian | uk | Колекції |
| Romanian | ro | Colecții |
| Kurdish Kurmanji | ku | Kom |
| Malayalam | ml | ശേഖരങ്ങൾ |
| Serbian | sr | Колекције |
| Bosnian | bs | Kolekcije |
| Croatian | hr | Kolekcije |
| Pashto | ps | ټولګې |
| Igbo | ig | Nchịkọta |
| Afrikaans | af | Versamelings |
| Catalan | ca | Col·leccions |
| Bulgarian | bg | Колекции |
| Burmese | my | စုစည်းမှုများ |
| Somali | so | Kooxaha |
| Zulu | zu | Iqoqo |
| Haitian Creole | ht | Koleksyon |
| Danish | da | Samlinger |
| Norwegian Bokmål | no | Samlinger |
| Azerbaijani | az | Kolleksiyalar |
| Malagasy | mg | Fitambarana |
| Quechua | qu | Tantanakuykuna |

### Acapulcoite Meteorites

| Language | Code | Translation |
|---|---|---|
| English | en | Acapulcoite Meteorites |
| Latin | la | Acapulcoitae Meteoritae |
| Basque | eu | Acapulcoita Meteoritoak |
| Finnish | fi | Acapulcoittimetriitit |
| Mongolian (Latin) | mn | Acapulcoite Meteoritnuud |
| Tatar | tt | Acapulcoite Meteoritlar |
| Kazakh | kk | Акапулькоит метеориттері |
| Kyrgyz | ky | Акапулькоит метеориттери |
| Czech | cs | Akapulkoitové meteority |
| Ukrainian | uk | Акапулькоїтові метеорити |
| Romanian | ro | Meteorite acapulcoite |
| Kurdish Kurmanji | ku | Meteorîtên akapulkoîtî |
| Malayalam | ml | അകാപുൾക്കോയിറ്റ് മെറ്റിയറൈറ്റുകൾ |
| Serbian | sr | Акапулкоит метеорити |
| Bosnian | bs | Akapulkoidni meteoriti |
| Croatian | hr | Akapulkoidni meteoriti |
| Pashto | ps | اکاپولکویټ میټیورایټونه |
| Igbo | ig | Acapulcoite meteorites |
| Afrikaans | af | Acapulcoïet-meteoriete |
| Catalan | ca | Meteorits acapulcoïtics |
| Bulgarian | bg | Акапулкоитови метеорити |
| Burmese | my | အကပ်ပူလ်ကိုက် မီတီယိုရိုက်များ |
| Somali | so | Acapulcoite meteorites |
| Zulu | zu | Izinkanyezi ze-Acapulcoite |
| Haitian Creole | ht | Meteorit Acapulcoite |
| Danish | da | Acapulcoit-meteoritter |
| Norwegian Bokmål | no | Acapulcoitt-meteoritter |
| Azerbaijani | az | Akapulkoit Meteorları |
| Malagasy | mg | Vatoandro Acapulcoite |
| Quechua | qu | Acapulkoita Meteoro Rumikuna |

### Angrite Meteorites

| Language | Code | Translation |
|---|---|---|
| English | en | Angrite Meteorites |
| Latin | la | Angritae Meteoritae |
| Basque | eu | Angrita Meteoritoak |
| Finnish | fi | Angrittimetriitit |
| Mongolian (Latin) | mn | Angrite Meteoritnuud |
| Tatar | tt | Angrite Meteoritlar |
| Kazakh | kk | Ангрит метеориттері |
| Kyrgyz | ky | Ангрит метеориттери |
| Czech | cs | Angritové meteority |
| Ukrainian | uk | Ангритові метеорити |
| Romanian | ro | Meteorite angrite |
| Kurdish Kurmanji | ku | Meteorîtên angrîtî |
| Malayalam | ml | അംഗ്രൈറ്റ് മെറ്റിയറൈറ്റുകൾ |
| Serbian | sr | Ангрит метеорити |
| Bosnian | bs | Angritski meteoriti |
| Croatian | hr | Angritski meteoriti |
| Pashto | ps | انګرایټ میټیورایټونه |
| Igbo | ig | Angrite meteorites |
| Afrikaans | af | Angriet-meteoriete |
| Catalan | ca | Meteorits angrítics |
| Bulgarian | bg | Ангритови метеорити |
| Burmese | my | အင်ဂရိုက် မီတီယိုရိုက်များ |
| Somali | so | Angrite meteorites |
| Zulu | zu | Izinkanyezi ze-Angrite |
| Haitian Creole | ht | Meteorit Angrite |
| Danish | da | Angrit-meteoritter |
| Norwegian Bokmål | no | Angritt-meteoritter |
| Azerbaijani | az | Angrit Meteorları |
| Malagasy | mg | Vatoandro Angrite |
| Quechua | qu | Angrita Meteoro Rumikuna |

### Aubrite Meteorites

| Language | Code | Translation |
|---|---|---|
| English | en | Aubrite Meteorites |
| Latin | la | Aubritae Meteoritae |
| Basque | eu | Aubrita Meteoritoak |
| Finnish | fi | Aubrittimetriitit |
| Mongolian (Latin) | mn | Aubrite Meteoritnuud |
| Tatar | tt | Aubrite Meteoritlar |
| Kazakh | kk | Обрит метеориттері |
| Kyrgyz | ky | Обрит метеориттери |
| Czech | cs | Aubritové meteority |
| Ukrainian | uk | Обритові метеорити |
| Romanian | ro | Meteorite aubrite |
| Kurdish Kurmanji | ku | Meteorîtên obrîtî |
| Malayalam | ml | ഓബ്രൈറ്റ് മെറ്റിയറൈറ്റുകൾ |
| Serbian | sr | Обрит метеорити |
| Bosnian | bs | Abritski meteoriti |
| Croatian | hr | Aubritski meteoriti |
| Pashto | ps | اوبرایټ میټیورایټونه |
| Igbo | ig | Aubrite meteorites |
| Afrikaans | af | Aubriet-meteoriete |
| Catalan | ca | Meteorits aubrítics |
| Bulgarian | bg | Обритови метеорити |
| Burmese | my | အော်ဘရိုက် မီတီယိုရိုက်များ |
| Somali | so | Aubrite meteorites |
| Zulu | zu | Izinkanyezi ze-Aubrite |
| Haitian Creole | ht | Meteorit Aubrite |
| Danish | da | Aubrit-meteoritter |
| Norwegian Bokmål | no | Aubritt-meteoritter |
| Azerbaijani | az | Aubrit Meteorları |
| Malagasy | mg | Vatoandro Aubrite |
| Quechua | qu | Awbrita Meteoro Rumikuna |

### Brachinite Meteorites

| Language | Code | Translation |
|---|---|---|
| English | en | Brachinite Meteorites |
| Latin | la | Brachinitae Meteoritae |
| Basque | eu | Brachinita Meteoritoak |
| Finnish | fi | Brachiniittimetriitit |
| Mongolian (Latin) | mn | Brachinite Meteoritnuud |
| Tatar | tt | Brachinite Meteoritlar |
| Kazakh | kk | Брахинит метеориттері |
| Kyrgyz | ky | Брахинит метеориттери |
| Czech | cs | Brachinitové meteority |
| Ukrainian | uk | Брахінітові метеорити |
| Romanian | ro | Meteorite brachinite |
| Kurdish Kurmanji | ku | Meteorîtên brahînîtî |
| Malayalam | ml | ബ്രാചിനൈറ്റ് മെറ്റിയറൈറ്റുകൾ |
| Serbian | sr | Брахинит метеорити |
| Bosnian | bs | Brahinitni meteoriti |
| Croatian | hr | Brahinitni meteoriti |
| Pashto | ps | براخینایټ میټیورایټونه |
| Igbo | ig | Brachinite meteorites |
| Afrikaans | af | Brachyniet-meteoriete |
| Catalan | ca | Meteorits braxinítics |
| Bulgarian | bg | Брахинитови метеорити |
| Burmese | my | ဘရာချီနိုက် မီတီယိုရိုက်များ |
| Somali | so | Brachinite meteorites |
| Zulu | zu | Izinkanyezi ze-Brachinite |
| Haitian Creole | ht | Meteorit Brachinite |
| Danish | da | Brachinit-meteoritter |
| Norwegian Bokmål | no | Brachinitt-meteoritter |
| Azerbaijani | az | Brakinit Meteorları |
| Malagasy | mg | Vatoandro Brachinite |
| Quechua | qu | Brachinita Meteoro Rumikuna |

### Enstatite Chondrites

| Language | Code | Translation |
|---|---|---|
| English | en | Enstatite Chondrites |
| Latin | la | Enstatitae Chondritae |
| Basque | eu | Enstatita Kondritoak |
| Finnish | fi | Enstatiittikondriitit |
| Mongolian (Latin) | mn | Enstatite Chondritnuud |
| Tatar | tt | Enstatite Chondritlar |
| Kazakh | kk | Энстатит хондриттері |
| Kyrgyz | ky | Энстатит хондриттери |
| Czech | cs | Enstatitové chondrity |
| Ukrainian | uk | Енстатитові хондрити |
| Romanian | ro | Condrite enstatitice |
| Kurdish Kurmanji | ku | Kondrîtên enstatîtî |
| Malayalam | ml | എൻസ്റ്റാറ്റൈറ്റ് കോൺഡ്രൈറ്റുകൾ |
| Serbian | sr | Енстатит хондрити |
| Bosnian | bs | Enstatski hondriti |
| Croatian | hr | Enstatski hondriti |
| Pashto | ps | انسټاټایټ کانډرایټونه |
| Igbo | ig | Enstatite chondrites |
| Afrikaans | af | Enstatiet-chondriete |
| Catalan | ca | Condrites enstatítiques |
| Bulgarian | bg | Енстатитови хондрити |
| Burmese | my | အင်စတေတိုက် ကွန်ဒရိုက်များ |
| Somali | so | Enstatite chondrites |
| Zulu | zu | Izinkanyezi ze-Enstatite chondrites |
| Haitian Creole | ht | Chondrit Enstatite |
| Danish | da | Enstatit-chondritter |
| Norwegian Bokmål | no | Enstatitt-kondritter |
| Azerbaijani | az | Enstatit Xondritləri |
| Malagasy | mg | Kondrita Enstatite |
| Quechua | qu | Enstatita Kondritakuna |

### Gigapixel Gallery

| Language | Code | Translation |
|---|---|---|
| English | en | Gigapixel Gallery |
| Latin | la | Gigapixel Gallery |
| Basque | eu | Gigapixel Galeria |
| Finnish | fi | Gigapixel Galleria |
| Mongolian (Latin) | mn | Gigapixel Gallery |
| Tatar | tt | Gigapixel Galereya |
| Kazakh | kk | Гигапиксель галереясы |
| Kyrgyz | ky | Гигапиксель галереясы |
| Czech | cs | Gigapixelová galerie |
| Ukrainian | uk | Гігапіксельна галерея |
| Romanian | ro | Galerie Gigapixel |
| Kurdish Kurmanji | ku | Galeriya Gîgapîksel |
| Malayalam | ml | ഗിഗാപിക്സൽ ഗാലറി |
| Serbian | sr | Гигапиксел галерија |
| Bosnian | bs | Gigapiksel galerija |
| Croatian | hr | Gigapiksel galerija |
| Pashto | ps | ګیګاپیکسل ګالري |
| Igbo | ig | Gigapixel gallery |
| Afrikaans | af | Gigapiksel-galery |
| Catalan | ca | Galeria Gigapíxel |
| Bulgarian | bg | Гигапикселна галерия |
| Burmese | my | ဂီဂါပစ်ဆယ် ဂလက်ရီ |
| Somali | so | Giga-piksel galeriya |
| Zulu | zu | Igalari ye-Gigapixel |
| Haitian Creole | ht | Galri Gigapiksel |
| Danish | da | Gigapixel-galleri |
| Norwegian Bokmål | no | Gigapixel-galleri |
| Azerbaijani | az | Giqapiksel Qalereyası |
| Malagasy | mg | Galeria Gigapixel |
| Quechua | qu | Gigapixel Qawana |

### HED Meteorites

| Language | Code | Translation |
|---|---|---|
| English | en | HED Meteorites |
| Latin | la | HED Meteoritae |
| Basque | eu | HED Meteoritoak |
| Finnish | fi | HED-metriitit |
| Mongolian (Latin) | mn | HED Meteoritnuud |
| Tatar | tt | HED Meteoritlar |
| Kazakh | kk | HED метеориттері |
| Kyrgyz | ky | HED метеориттери |
| Czech | cs | HED meteority |
| Ukrainian | uk | HED метеорити |
| Romanian | ro | Meteorite HED |
| Kurdish Kurmanji | ku | Meteorîtên HED |
| Malayalam | ml | HED മെറ്റിയറൈറ്റുകൾ |
| Serbian | sr | HED метеорити |
| Bosnian | bs | HED meteoriti |
| Croatian | hr | HED meteoriti |
| Pashto | ps | HED میټیورایټونه |
| Igbo | ig | HED meteorites |
| Afrikaans | af | HED-meteoriete |
| Catalan | ca | Meteorits HED |
| Bulgarian | bg | HED метеорити |
| Burmese | my | HED မီတီယိုရိုက်များ |
| Somali | so | HED meteorites |
| Zulu | zu | Izinkanyezi ze-HED |
| Haitian Creole | ht | Meteorit HED |
| Danish | da | HED-meteoritter |
| Norwegian Bokmål | no | HED-meteoritter |
| Azerbaijani | az | HED Meteorları |
| Malagasy | mg | Vatoandro HED |
| Quechua | qu | HED Meteoro Rumikuna |

### High Metal Group

| Language | Code | Translation |
|---|---|---|
| English | en | High Metal Group |
| Latin | la | High Metal Group |
| Basque | eu | High Metal Group |
| Finnish | fi | High Metal Group |
| Mongolian (Latin) | mn | High Metal Group |
| Tatar | tt | High Metal Group |
| Kazakh | kk | Жоғары металл тобы |
| Kyrgyz | ky | Жогору металл тобу |
| Czech | cs | Skupina s vysokým obsahem kovu |
| Ukrainian | uk | Група з високим вмістом металу |
| Romanian | ro | Grup cu conținut ridicat de metal |
| Kurdish Kurmanji | ku | Koma metalê bilind |
| Malayalam | ml | ഹൈ മെറ്റൽ ഗ്രൂപ്പ് |
| Serbian | sr | Група високог садржаја метала |
| Bosnian | bs | Grupa visokog sadržaja metala |
| Croatian | hr | Grupa visokog udjela metala |
| Pashto | ps | لوړ فلزي ډله |
| Igbo | ig | High metal group |
| Afrikaans | af | Hoë-metaalgroep |
| Catalan | ca | Grup d'alt contingut metàl·lic |
| Bulgarian | bg | Група с високо съдържание на метал |
| Burmese | my | အမြင့်သတ္တုအုပ်စု |
| Somali | so | Kooxda birta sare |
| Zulu | zu | Iqembu eliphezulu le-metal |
| Haitian Creole | ht | Gwoup metal ki wo |
| Danish | da | Gruppe med højt metalindhold |
| Norwegian Bokmål | no | Gruppe med høyt metallinnhold |
| Azerbaijani | az | Yüksək Metal Qrupu |
| Malagasy | mg | High Metal Group |
| Quechua | qu | High Metal Group |

### Individual MicroShots

| Language | Code | Translation |
|---|---|---|
| English | en | Individual MicroShots |
| Latin | la | Individual MicroShots |
| Basque | eu | Indibidual MicroShots |
| Finnish | fi | Yksittäiset MicroShots |
| Mongolian (Latin) | mn | Individual MicroShots |
| Tatar | tt | Individual MicroShots |
| Kazakh | kk | Жеке MicroShots |
| Kyrgyz | ky | Жеке MicroShots |
| Czech | cs | Jednotlivé MicroShots |
| Ukrainian | uk | Індивідуальні MicroShots |
| Romanian | ro | MicroShots individuale |
| Kurdish Kurmanji | ku | MicroShotsên takekesî |
| Malayalam | ml | ഇൻഡിവിജ്വൽ മൈക്രോഷോട്ടുകൾ |
| Serbian | sr | Појединачни MicroShots |
| Bosnian | bs | Pojedinačni MicroShots |
| Croatian | hr | Pojedinačni MicroShots |
| Pashto | ps | فردي مایکرو شاټونه |
| Igbo | ig | Individual microshots |
| Afrikaans | af | Individuele MicroShots |
| Catalan | ca | MicroShots individuals |
| Bulgarian | bg | Индивидуални MicroShots |
| Burmese | my | တစ်ခုချင်းစီ MicroShots |
| Somali | so | MicroShots gaar ah |
| Zulu | zu | I-MicroShots ngayinye |
| Haitian Creole | ht | MicroShots endividyèl |
| Danish | da | Enkelte MicroShots |
| Norwegian Bokmål | no | Enkelte MicroShots |
| Azerbaijani | az | Fərdi MikroŞotlar |
| Malagasy | mg | Individual MicroShots |
| Quechua | qu | Individual MicroShots |

### Iron Meteorites

| Language | Code | Translation |
|---|---|---|
| English | en | Iron Meteorites |
| Latin | la | Ferrum Meteoritae |
| Basque | eu | Burdinazko Meteoritoak |
| Finnish | fi | Rautametriitit |
| Mongolian (Latin) | mn | Töömör Meteoritnuud |
| Tatar | tt | Temir Meteoritlar |
| Kazakh | kk | Темір метеориттері |
| Kyrgyz | ky | Темир метеориттери |
| Czech | cs | Železné meteority |
| Ukrainian | uk | Залізні метеорити |
| Romanian | ro | Meteorite de fier |
| Kurdish Kurmanji | ku | Meteorîtên hesinî |
| Malayalam | ml | ഐറൺ മെറ്റിയറൈറ്റുകൾ |
| Serbian | sr | Гвоздени метеорити |
| Bosnian | bs | Gvožđeni meteoriti |
| Croatian | hr | Željezni meteoriti |
| Pashto | ps | آهن میټیورایټونه |
| Igbo | ig | Iron meteorites |
| Afrikaans | af | Ystermeteoriete |
| Catalan | ca | Meteorits de ferro |
| Bulgarian | bg | Железни метеорити |
| Burmese | my | သံမီတီယိုရိုက်များ |
| Somali | so | Meteorites bir ah |
| Zulu | zu | Izinkanyezi zensimbi |
| Haitian Creole | ht | Meteorit fè |
| Danish | da | Jernmeteoritter |
| Norwegian Bokmål | no | Jernmeteoritter |
| Azerbaijani | az | Dəmir Meteorları |
| Malagasy | mg | Vatoandro Vy |
| Quechua | qu | Fierro Meteoro Rumikuna |

### Karoonda Group

| Language | Code | Translation |
|---|---|---|
| English | en | Karoonda Group |
| Latin | la | Karoonda Group |
| Basque | eu | Karoonda Taldea |
| Finnish | fi | Karoonda-ryhmä |
| Mongolian (Latin) | mn | Karoonda Group |
| Tatar | tt | Karoonda Gruppası |
| Kazakh | kk | Карунда тобы |
| Kyrgyz | ky | Карунда тобу |
| Czech | cs | Skupina Karoonda |
| Ukrainian | uk | Група Карунда |
| Romanian | ro | Grupul Karoonda |
| Kurdish Kurmanji | ku | Koma Karoonda |
| Malayalam | ml | കാരൂണ്ട ഗ്രൂപ്പ് |
| Serbian | sr | Карунда група |
| Bosnian | bs | Karoonda grupa |
| Croatian | hr | Karoonda skupina |
| Pashto | ps | کارونډا ډله |
| Igbo | ig | Karoonda group |
| Afrikaans | af | Karoondagroep |
| Catalan | ca | Grup Karoonda |
| Bulgarian | bg | Група Карунда |
| Burmese | my | ကာရုန်းဒါ အုပ်စု |
| Somali | so | Kooxda Karoonda |
| Zulu | zu | Iqembu le-Karoonda |
| Haitian Creole | ht | Gwoup Karoonda |
| Danish | da | Karoonda-gruppen |
| Norwegian Bokmål | no | Karoonda-gruppen |
| Azerbaijani | az | Karoonda Qrupu |
| Malagasy | mg | Vondrona Karoonda |
| Quechua | qu | Karoonda Ayllukuna |

### Lodranite Meteorites

| Language | Code | Translation |
|---|---|---|
| English | en | Lodranite Meteorites |
| Latin | la | Lodranitae Meteoritae |
| Basque | eu | Lodranita Meteoritoak |
| Finnish | fi | Lodraniittimetriitit |
| Mongolian (Latin) | mn | Lodranite Meteoritnuud |
| Tatar | tt | Lodranite Meteoritlar |
| Kazakh | kk | Лодранит метеориттері |
| Kyrgyz | ky | Лодранит метеориттери |
| Czech | cs | Lodranitové meteority |
| Ukrainian | uk | Лодранітові метеорити |
| Romanian | ro | Meteorite lodranite |
| Kurdish Kurmanji | ku | Meteorîtên lodranîtî |
| Malayalam | ml | ലോഡ്രാനൈറ്റ് മെറ്റിയറൈറ്റുകൾ |
| Serbian | sr | Лодранит метеорити |
| Bosnian | bs | Lodranitski meteoriti |
| Croatian | hr | Lodranitski meteoriti |
| Pashto | ps | لورانایټ میټیورایټونه |
| Igbo | ig | Lodranite meteorites |
| Afrikaans | af | Lodraniet-meteoriete |
| Catalan | ca | Meteorits lodranítics |
| Bulgarian | bg | Лодранитови метеорити |
| Burmese | my | လောဒရန်ိုက် မီတီယိုရိုက်များ |
| Somali | so | Lodranite meteorites |
| Zulu | zu | Izinkanyezi ze-Lodranite |
| Haitian Creole | ht | Meteorit Lodranite |
| Danish | da | Lodranit-meteoritter |
| Norwegian Bokmål | no | Lodranitt-meteoritter |
| Azerbaijani | az | Lodranit Meteorları |
| Malagasy | mg | Vatoandro Lodranite |
| Quechua | qu | Lodranita Meteoro Rumikuna |

### Lunar Meteorites

| Language | Code | Translation |
|---|---|---|
| English | en | Lunar Meteorites |
| Latin | la | Lunares Meteoritae |
| Basque | eu | Ilargiko Meteoritoak |
| Finnish | fi | Kuun metriitit |
| Mongolian (Latin) | mn | Saran Meteoritnuud |
| Tatar | tt | Ay Meteoritlar |
| Kazakh | kk | Ай метеориттері |
| Kyrgyz | ky | Ай метеориттери |
| Czech | cs | Lunární meteority |
| Ukrainian | uk | Місячні метеорити |
| Romanian | ro | Meteorite lunare |
| Kurdish Kurmanji | ku | Meteorîtên heyvê |
| Malayalam | ml | ലൂണാർ മെറ്റിയറൈറ്റുകൾ |
| Serbian | sr | Лундарни метеорити |
| Bosnian | bs | Lunarni meteoriti |
| Croatian | hr | Lunarni meteoriti |
| Pashto | ps | لومري میټیورایټونه |
| Igbo | ig | Lunar meteorites |
| Afrikaans | af | Maanmeteoriete |
| Catalan | ca | Meteorits lunars |
| Bulgarian | bg | Лунни метеорити |
| Burmese | my | လune မီတီယိုရိုက်များ |
| Somali | so | Meteorites dayaxa |
| Zulu | zu | Izinkanyezi zenyanga |
| Haitian Creole | ht | Meteorit Lalin |
| Danish | da | Måne-meteoritter |
| Norwegian Bokmål | no | Måne-meteoritter |
| Azerbaijani | az | Ay Meteorları |
| Malagasy | mg | Vatoandro Volana |
| Quechua | qu | Killa Meteoro Rumikuna |

### Martian Meteorites

| Language | Code | Translation |
|---|---|---|
| English | en | Martian Meteorites |
| Latin | la | Martiales Meteoritae |
| Basque | eu | Martearen Meteoritoak |
| Finnish | fi | Marsin metriitit |
| Mongolian (Latin) | mn | Angara Meteoritnuud |
| Tatar | tt | Marss Meteoritlar |
| Kazakh | kk | Марс метеориттері |
| Kyrgyz | ky | Марс метеориттери |
| Czech | cs | Marťanské meteority |
| Ukrainian | uk | Марсіанські метеорити |
| Romanian | ro | Meteorite marțiene |
| Kurdish Kurmanji | ku | Meteorîtên Marsê |
| Malayalam | ml | മാർഷ്യൽ മെറ്റിയറൈറ്റുകൾ |
| Serbian | sr | Марсови метеорити |
| Bosnian | bs | Marsijanski meteoriti |
| Croatian | hr | Marsovci meteoriti |
| Pashto | ps | مریخي میټیورایټونه |
| Igbo | ig | Martian meteorites |
| Afrikaans | af | Marsmeteoriete |
| Catalan | ca | Meteorits marcians |
| Bulgarian | bg | Марсиански метеорити |
| Burmese | my | မာ့ခ် မီတီယိုရိုက်များ |
| Somali | so | Meteorites Mars |
| Zulu | zu | Izinkanyezi zikaMars |
| Haitian Creole | ht | Meteorit Mès |
| Danish | da | Mars-meteoritter |
| Norwegian Bokmål | no | Mars-meteoritter |
| Azerbaijani | az | Mars Meteorları |
| Malagasy | mg | Vatoandro Mars |
| Quechua | qu | Marte Meteoro Rumikuna |

### Mesosiderite Meteorites

| Language | Code | Translation |
|---|---|---|
| English | en | Mesosiderite Meteorites |
| Latin | la | Mesosideritae Meteoritae |
| Basque | eu | Mesosiderita Meteoritoak |
| Finnish | fi | Mesosideriittimetriitit |
| Mongolian (Latin) | mn | Mesosiderite Meteoritnuud |
| Tatar | tt | Mesosiderite Meteoritlar |
| Kazakh | kk | Мезосидерит метеориттері |
| Kyrgyz | ky | Мезосидерит метеориттери |
| Czech | cs | Mesosideritové meteority |
| Ukrainian | uk | Мезосидеритові метеорити |
| Romanian | ro | Meteorite mezosiderite |
| Kurdish Kurmanji | ku | Meteorîtên mezosîderîtî |
| Malayalam | ml | മെസോസൈഡറൈറ്റ് മെറ്റിയറൈറ്റുകൾ |
| Serbian | sr | Мезосидерит метеорити |
| Bosnian | bs | Mezosideritski meteoriti |
| Croatian | hr | Mezosideritski meteoriti |
| Pashto | ps | میوسایډرایټ میټیورایټونه |
| Igbo | ig | Mesosiderite meteorites |
| Afrikaans | af | Mesosideriet-meteoriete |
| Catalan | ca | Meteorits mesosiderítics |
| Bulgarian | bg | Мезосидеритови метеорити |
| Burmese | my | မီဆိုဆိုက်ဒရိုက် မီတီယိုရိုက်များ |
| Somali | so | Mesosiderite meteorites |
| Zulu | zu | Izinkanyezi ze-Mesosiderite |
| Haitian Creole | ht | Meteorit Mezosiderit |
| Danish | da | Mesosiderit-meteoritter |
| Norwegian Bokmål | no | Mesosideritt-meteoritter |
| Azerbaijani | az | Mezosiderit Meteorları |
| Malagasy | mg | Vatoandro Mesosiderite |
| Quechua | qu | Mesosiderita Meteoro Rumikuna |

### Mighei Group

| Language | Code | Translation |
|---|---|---|
| English | en | Mighei Group |
| Latin | la | Mighei Group |
| Basque | eu | Mighei Taldea |
| Finnish | fi | Mighei-ryhmä |
| Mongolian (Latin) | mn | Mighei Group |
| Tatar | tt | Mighei Gruppası |
| Kazakh | kk | Мигей тобы |
| Kyrgyz | ky | Мигей тобу |
| Czech | cs | Skupina Mighei |
| Ukrainian | uk | Група Мігей |
| Romanian | ro | Grupul Mighei |
| Kurdish Kurmanji | ku | Koma Mighei |
| Malayalam | ml | മിഗ്ഹെ ഗ്രൂപ്പ് |
| Serbian | sr | Мигеј група |
| Bosnian | bs | Mighejeva grupa |
| Croatian | hr | Mighejeva skupina |
| Pashto | ps | مګهي ډله |
| Igbo | ig | Mighei group |
| Afrikaans | af | Migheegroep |
| Catalan | ca | Grup Mighei |
| Bulgarian | bg | Група Мигей |
| Burmese | my | မီဂဟေ အုပ်စု |
| Somali | so | Kooxda Mighei |
| Zulu | zu | Iqembu le-Mighei |
| Haitian Creole | ht | Gwoup Mighei |
| Danish | da | Mighei-gruppen |
| Norwegian Bokmål | no | Mighei-gruppen |
| Azerbaijani | az | Mighei Qrupu |
| Malagasy | mg | Vondrona Mighei |
| Quechua | qu | Mighei Ayllukuna |

### Miscellaneous

| Language | Code | Translation |
|---|---|---|
| English | en | Miscellaneous |
| Latin | la | Miscellanea |
| Basque | eu | Hainbat |
| Finnish | fi | Sekalaista |
| Mongolian (Latin) | mn | Olni |
| Tatar | tt | Törle |
| Kazakh | kk | Әртүрлі |
| Kyrgyz | ky | Ар кандай |
| Czech | cs | Různé |
| Ukrainian | uk | Різне |
| Romanian | ro | Diverse |
| Kurdish Kurmanji | ku | Curbeş |
| Malayalam | ml | വ്യത്യസ്തം |
| Serbian | sr | Разно |
| Bosnian | bs | Razno |
| Croatian | hr | Razno |
| Pashto | ps | بېلابېل |
| Igbo | ig | Ihe dị iche iche |
| Afrikaans | af | Divers |
| Catalan | ca | Varis |
| Bulgarian | bg | Разни |
| Burmese | my | အမျိုးမျိုး |
| Somali | so | Kala duwan |
| Zulu | zu | Okuhlukene |
| Haitian Creole | ht | Divers |
| Danish | da | Diverse |
| Norwegian Bokmål | no | Diverse |
| Azerbaijani | az | Müxtəlif |
| Malagasy | mg | Samy hafa |
| Quechua | qu | Hukniray Kaykuna |

### Ordinary Chondrites

| Language | Code | Translation |
|---|---|---|
| English | en | Ordinary Chondrites |
| Latin | la | Ordinariae Chondritae |
| Basque | eu | Ohiko Kondritoak |
| Finnish | fi | Tavalliset kondriitit |
| Mongolian (Latin) | mn | Ordinary Chondritnuud |
| Tatar | tt | Ordinary Chondritlar |
| Kazakh | kk | Қарапайым хондриттері |
| Kyrgyz | ky | Жөнөкөй хондриттер |
| Czech | cs | Běžné chondrity |
| Ukrainian | uk | Звичайні хондрити |
| Romanian | ro | Condrite obișnuite |
| Kurdish Kurmanji | ku | Kondrîtên asayî |
| Malayalam | ml | ഓർഡിനറി കോൺഡ്രൈറ്റുകൾ |
| Serbian | sr | Обични хондрити |
| Bosnian | bs | Obični hondriti |
| Croatian | hr | Obični hondriti |
| Pashto | ps | عادي کانډرایټونه |
| Igbo | ig | Ordinary chondrites |
| Afrikaans | af | Gewone chondriete |
| Catalan | ca | Condrites ordinàries |
| Bulgarian | bg | Обикновени хондрити |
| Burmese | my | ပုံမှန် ကွန်ဒရိုက်များ |
| Somali | so | Chondrites caadi ah |
| Zulu | zu | Izinkanyezi ze-chondrites ejwayelekile |
| Haitian Creole | ht | Chondrit òdinè |
| Danish | da | Almindelige chondritter |
| Norwegian Bokmål | no | Vanlige kondritter |
| Azerbaijani | az | Adi Xondritlər |
| Malagasy | mg | Kondrita Mahazatra |
| Quechua | qu | Sapan Kondritakuna |

### Ornans Group

| Language | Code | Translation |
|---|---|---|
| English | en | Ornans Group |
| Latin | la | Ornans Group |
| Basque | eu | Ornans Taldea |
| Finnish | fi | Ornans-ryhmä |
| Mongolian (Latin) | mn | Ornans Group |
| Tatar | tt | Ornans Gruppası |
| Kazakh | kk | Орнан тобы |
| Kyrgyz | ky | Орнан тобу |
| Czech | cs | Skupina Ornans |
| Ukrainian | uk | Група Орнан |
| Romanian | ro | Grupul Ornans |
| Kurdish Kurmanji | ku | Koma Ornans |
| Malayalam | ml | ഓർണാൻസ് ഗ്രൂപ്പ് |
| Serbian | sr | Орнанс група |
| Bosnian | bs | Ornanska grupa |
| Croatian | hr | Ornanska skupina |
| Pashto | ps | اورنانس ډله |
| Igbo | ig | Ornans group |
| Afrikaans | af | Ornansgroep |
| Catalan | ca | Grup Ornans |
| Bulgarian | bg | Група Орнан |
| Burmese | my | အော်နန် အုပ်စု |
| Somali | so | Kooxda Ornans |
| Zulu | zu | Iqembu le-Ornans |
| Haitian Creole | ht | Gwoup Ornans |
| Danish | da | Ornans-gruppen |
| Norwegian Bokmål | no | Ornans-gruppen |
| Azerbaijani | az | Ornans Qrupu |
| Malagasy | mg | Vondrona Ornans |
| Quechua | qu | Ornans Ayllukuna |

### Pallasite Meteorites

| Language | Code | Translation |
|---|---|---|
| English | en | Pallasite Meteorites |
| Latin | la | Pallasitae Meteoritae |
| Basque | eu | Pallasita Meteoritoak |
| Finnish | fi | Pallasitiittimetriitit |
| Mongolian (Latin) | mn | Pallasite Meteoritnuud |
| Tatar | tt | Pallasite Meteoritlar |
| Kazakh | kk | Палласит метеориттері |
| Kyrgyz | ky | Палласит метеориттери |
| Czech | cs | Palazitové meteority |
| Ukrainian | uk | Паласитові метеорити |
| Romanian | ro | Meteorite palazite |
| Kurdish Kurmanji | ku | Meteorîtên pallasîtî |
| Malayalam | ml | പല്ലസൈറ്റ് മെറ്റിയറൈറ്റുകൾ |
| Serbian | sr | Паласит метеорити |
| Bosnian | bs | Pallasitski meteoriti |
| Croatian | hr | Pallasitski meteoriti |
| Pashto | ps | پالاسایټ میټیورایټونه |
| Igbo | ig | Pallasite meteorites |
| Afrikaans | af | Pallasiet-meteoriete |
| Catalan | ca | Meteorits pal·làsics |
| Bulgarian | bg | Паласитови метеорити |
| Burmese | my | ပလာဆိုက် မီတီယိုရိုက်များ |
| Somali | so | Pallasite meteorites |
| Zulu | zu | Izinkanyezi ze-Pallasite |
| Haitian Creole | ht | Meteorit Palasit |
| Danish | da | Pallasit-meteoritter |
| Norwegian Bokmål | no | Pallasitt-meteoritter |
| Azerbaijani | az | Pallasit Meteorları |
| Malagasy | mg | Vatoandro Pallasite |
| Quechua | qu | Pallasita Meteoro Rumikuna |

### Renazzo Group

| Language | Code | Translation |
|---|---|---|
| English | en | Renazzo Group |
| Latin | la | Renazzo Group |
| Basque | eu | Renazzo Taldea |
| Finnish | fi | Renazzo-ryhmä |
| Mongolian (Latin) | mn | Renazzo Group |
| Tatar | tt | Renazzo Gruppası |
| Kazakh | kk | Ренаццо тобы |
| Kyrgyz | ky | Ренаццо тобу |
| Czech | cs | Skupina Renazzo |
| Ukrainian | uk | Група Ренаццо |
| Romanian | ro | Grupul Renazzo |
| Kurdish Kurmanji | ku | Koma Renazzo |
| Malayalam | ml | റെനാറ്റ്സോ ഗ്രൂപ്പ് |
| Serbian | sr | Ренацо група |
| Bosnian | bs | Renacco grupa |
| Croatian | hr | Renacco skupina |
| Pashto | ps | رناتسو ډله |
| Igbo | ig | Renazzo group |
| Afrikaans | af | Renazzogroep |
| Catalan | ca | Grup Renazzo |
| Bulgarian | bg | Група Ренацо |
| Burmese | my | ရီနာဇို အုပ်စု |
| Somali | so | Kooxda Renazzo |
| Zulu | zu | Iqembu le-Renazzo |
| Haitian Creole | ht | Gwoup Renazzo |
| Danish | da | Renazzo-gruppen |
| Norwegian Bokmål | no | Renazzo-gruppen |
| Azerbaijani | az | Renazzo Qrupu |
| Malagasy | mg | Vondrona Renazzo |
| Quechua | qu | Renazzo Ayllukuna |

### Rumuruti Chondrites

| Language | Code | Translation |
|---|---|---|
| English | en | Rumuruti Chondrites |
| Latin | la | Rumuruti Chondritae |
| Basque | eu | Rumuruti Kondritoak |
| Finnish | fi | Rumuruti-kondriitit |
| Mongolian (Latin) | mn | Rumuruti Chondritnuud |
| Tatar | tt | Rumuruti Chondritlar |
| Kazakh | kk | Румурути хондриттері |
| Kyrgyz | ky | Румурути хондриттери |
| Czech | cs | Rumurutické chondrity |
| Ukrainian | uk | Румурутські хондрити |
| Romanian | ro | Condrite rumuruti |
| Kurdish Kurmanji | ku | Kondrîtên rumurutî |
| Malayalam | ml | റുമുരുതി കോൺഡ്രൈറ്റുകൾ |
| Serbian | sr | Румуроти хондрити |
| Bosnian | bs | Rumuruti hondriti |
| Croatian | hr | Rumuruti hondriti |
| Pashto | ps | روموروټي کانډرایټونه |
| Igbo | ig | Rumuruti chondrites |
| Afrikaans | af | Rumuruti-chondriete |
| Catalan | ca | Condrites rumurutianes |
| Bulgarian | bg | Румурутски хондрити |
| Burmese | my | ရူးမူရူတီ ကွန်ဒရိုက်များ |
| Somali | so | Chondrites Rumuruti |
| Zulu | zu | Izinkanyezi ze-Rumuruti chondrites |
| Haitian Creole | ht | Chondrit Rumuruti |
| Danish | da | Rumuruti-chondritter |
| Norwegian Bokmål | no | Rumuruti-kondritter |
| Azerbaijani | az | Rumuruti Xondritləri |
| Malagasy | mg | Kondrita Rumuruti |
| Quechua | qu | Rumuruti Kondritakuna |

### STRESS Style Thin Sections

| Language | Code | Translation |
|---|---|---|
| All languages | — | STRESS Style Thin Sections *(kept in English as a specific product name)* |
| Kazakh | kk | STRESS стиліндегі жұқа кесінділер |
| Kyrgyz | ky | STRESS стилиндеги жука кесиндилер |
| Czech | cs | Tenké výbrusy ve stylu STRESS |
| Ukrainian | uk | Тонкі шліфи у стилі STRESS |
| Romanian | ro | Secțiuni subțiri în stil STRESS |
| Kurdish Kurmanji | ku | Birînên zirav ên şêweya STRESS |
| Malayalam | ml | STRESS സ്റ്റൈൽ തിൻ സെക്ഷനുകൾ |
| Serbian | sr | СТРЕСС стил танких пресека |
| Bosnian | bs | STRESS stil tankih presjeka |
| Croatian | hr | STRESS stil tankih presjeka |
| Pashto | ps | STRESS سبک نری برخې |
| Igbo | ig | STRESS style thin sections |
| Afrikaans | af | STRESS-styl dun snitte |
| Catalan | ca | Seccions primes estil STRESS |
| Bulgarian | bg | Тънки срезове в стил STRESS |
| Burmese | my | STRESS ပုံစံပါးလွှာ အပိုင်းများ |
| Somali | so | Qaybaha dhuuban ee qaabka STRESS |
| Zulu | zu | Izingcezu ezincane zohlobo lwe-STRESS |
| Haitian Creole | ht | Seksyon mens stil STRESS |
| Danish | da | Tynde snit i STRESS-stil |
| Norwegian Bokmål | no | Tynne snitt i STRESS-stil |
| Azerbaijani | az | STRESS Üslublu Nazik Kəsimlər |
| Malagasy | mg | STRESS Style Thin Sections |
| Quechua | qu | STRESS Style Thin Sections |

### Unclassified Meteorites

| Language | Code | Translation |
|---|---|---|
| English | en | Unclassified Meteorites |
| Latin | la | Inclassificatae Meteoritae |
| Basque | eu | Klasifikatu Gabeko Meteoritoak |
| Finnish | fi | Luokittelemattomat metriitit |
| Mongolian (Latin) | mn | Angiildeg Meteoritnuud |
| Tatar | tt | Törkänmägän Meteoritlar |
| Kazakh | kk | Жіктелмеген метеориттер |
| Kyrgyz | ky | Классификацияланбаган метеориттер |
| Czech | cs | Neklasifikované meteority |
| Ukrainian | uk | Некласифіковані метеорити |
| Romanian | ro | Meteorite neclasificate |
| Kurdish Kurmanji | ku | Meteorîtên nehatine sinorkirin |
| Malayalam | ml | വർഗ്ഗീകരിക്കപ്പെടാത്ത മെറ്റിയറൈറ്റുകൾ |
| Serbian | sr | Нераспоређени метеорити |
| Bosnian | bs | Neklasificirani meteoriti |
| Croatian | hr | Neklasificirani meteoriti |
| Pashto | ps | غیر طبقه بندي شوي میټیورایټونه |
| Igbo | ig | Meteorites na-enweghị nkewa |
| Afrikaans | af | Ongeklassifiseerde meteoriete |
| Catalan | ca | Meteorits no classificats |
| Bulgarian | bg | Некласифицирани метеорити |
| Burmese | my | အမျိုးအစားခွဲခြားမထားသော မီတီယိုရိုက်များ |
| Somali | so | Meteorites aan la sifeyn |
| Zulu | zu | Izinkanyezi ezingahlelwanga |
| Haitian Creole | ht | Meteorit ki pa klase |
| Danish | da | Ikke-klassificerede meteoritter |
| Norwegian Bokmål | no | Ikke-klassifiserte meteoritter |
| Azerbaijani | az | Təsnif Edilməmiş Meteorlar |
| Malagasy | mg | Vatoandro Tsy Voakajy |
| Quechua | qu | Manam Rakisqa Meteoro Rumikuna |

### Ungrouped Achondrite Meteorites

| Language | Code | Translation |
|---|---|---|
| English | en | Ungrouped Achondrite Meteorites |
| Latin | la | Ungrouped Achondritae Meteoritae |
| Basque | eu | Talderik gabeko Akondritoak |
| Finnish | fi | Järjestämättömät akondriitimetriitit |
| Mongolian (Latin) | mn | Ungrouped Achondrite Meteoritnuud |
| Tatar | tt | Ungrouped Achondrite Meteoritlar |
| Kazakh | kk | Топтастырылмаған ахондрит метеориттері |
| Kyrgyz | ky | Топтоштурулбаган ахондрит метеориттери |
| Czech | cs | Nezařazené achondritové meteority |
| Ukrainian | uk | Негруповані ахондритові метеорити |
| Romanian | ro | Meteorite achondrite negrupate |
| Kurdish Kurmanji | ku | Meteorîtên axondrîtî yên bêkom |
| Malayalam | ml | അൺഗ്രൂപ്പ്ഡ് അകോൺഡ്രൈറ്റ് മെറ്റിയറൈറ്റുകൾ |
| Serbian | sr | Негруписани ахондрит метеорити |
| Bosnian | bs | Negrupisani ahondritni meteoriti |
| Croatian | hr | Negrupirani ahondritni meteoriti |
| Pashto | ps | غیر ډله ایز اکونډرایټ میټیورایټونه |
| Igbo | ig | Achondrite meteorites na-enweghị otu |
| Afrikaans | af | Ongroepeerde achondriet-meteoriete |
| Catalan | ca | Meteorits acòndrits no agrupats |
| Bulgarian | bg | Негрупирани ахондритови метеорити |
| Burmese | my | အုပ်စုဖွဲ့မထားသော အာကွန်ဒရိုက် မီတီယိုရိုက်များ |
| Somali | so | Achondrite meteorites aan la kooxeeyn |
| Zulu | zu | Izinkanyezi ze-achondrite ezingaqoqwanga |
| Haitian Creole | ht | Meteorit achondrit ki pa gwoupe |
| Danish | da | Ikke-grupperede achondrit-meteoritter |
| Norwegian Bokmål | no | Ikke-grupperte achondritt-meteoritter |
| Azerbaijani | az | Qruplaşdırılmamış Akondrit Meteorları |
| Malagasy | mg | Vatoandro Akondrita Tsy Voavondrona |
| Quechua | qu | Aylluniyuq Akondrita Meteoro Rumikuna |

### Ureilite Meteorites

| Language | Code | Translation |
|---|---|---|
| English | en | Ureilite Meteorites |
| Latin | la | Ureilitae Meteoritae |
| Basque | eu | Ureilita Meteoritoak |
| Finnish | fi | Ureiliittimetriitit |
| Mongolian (Latin) | mn | Ureilite Meteoritnuud |
| Tatar | tt | Ureilite Meteoritlar |
| Kazakh | kk | Урейлит метеориттері |
| Kyrgyz | ky | Урейлит метеориттери |
| Czech | cs | Ureilitové meteority |
| Ukrainian | uk | Уреїлітові метеорити |
| Romanian | ro | Meteorite ureilitice |
| Kurdish Kurmanji | ku | Meteorîtên ureylîtî |
| Malayalam | ml | യൂറിലൈറ്റ് മെറ്റിയറൈറ്റുകൾ |
| Serbian | sr | Уреилит метеорити |
| Bosnian | bs | Ureilitni meteoriti |
| Croatian | hr | Ureilitni meteoriti |
| Pashto | ps | یوریلایټ میټیورایټونه |
| Igbo | ig | Ureilite meteorites |
| Afrikaans | af | Ureiliet-meteoriete |
| Catalan | ca | Meteorits ureilítics |
| Bulgarian | bg | Урейлитови метеорити |
| Burmese | my | ယူရီလိုက် မီတီယိုရိုက်များ |
| Somali | so | Ureilite meteorites |
| Zulu | zu | Izinkanyezi ze-Ureilite |
| Haitian Creole | ht | Meteorit Ureilit |
| Danish | da | Ureilit-meteoritter |
| Norwegian Bokmål | no | Ureilitt-meteoritter |
| Azerbaijani | az | Ureilit Meteorları |
| Malagasy | mg | Vatoandro Ureilite |
| Quechua | qu | Ureilita Meteoro Rumikuna |

### Vigarano Group

| Language | Code | Translation |
|---|---|---|
| English | en | Vigarano Group |
| Latin | la | Vigarano Group |
| Basque | eu | Vigarano Taldea |
| Finnish | fi | Vigarano-ryhmä |
| Mongolian (Latin) | mn | Vigarano Group |
| Tatar | tt | Vigarano Gruppası |
| Kazakh | kk | Вигарано тобы |
| Kyrgyz | ky | Вигарано тобу |
| Czech | cs | Skupina Vigarano |
| Ukrainian | uk | Група Вігарано |
| Romanian | ro | Grupul Vigarano |
| Kurdish Kurmanji | ku | Koma Vigarano |
| Malayalam | ml | വിഗാരാനോ ഗ്രൂപ്പ് |
| Serbian | sr | Вигарано група |
| Bosnian | bs | Vigaranova grupa |
| Croatian | hr | Vigaranova skupina |
| Pashto | ps | ویګارانو ډله |
| Igbo | ig | Vigarano group |
| Afrikaans | af | Vigaranogroep |
| Catalan | ca | Grup Vigarano |
| Bulgarian | bg | Група Вигарано |
| Burmese | my | ဗီဂါရနို အုပ်စု |
| Somali | so | Kooxda Vigarano |
| Zulu | zu | Iqembu le-Vigarano |
| Haitian Creole | ht | Gwoup Vigarano |
| Danish | da | Vigarano-gruppen |
| Norwegian Bokmål | no | Vigarano-gruppen |
| Azerbaijani | az | Vigarano Qrupu |
| Malagasy | mg | Vondrona Vigarano |
| Quechua | qu | Vigarano Ayllukuna |

---

## Notes

- Scientific meteorite type names (e.g., Acapulcoite, Angrite, Ureilite) often retain their Latin/international form across languages.
- Group names (e.g., Karoonda Group, Mighei Group) may remain as proper nouns in languages where a direct translation is not natural.
- "STRESS Style Thin Sections" is a specific product name and is kept in English across all languages.
- "High Metal Group" and "Individual MicroShots" are product-specific terms and are generally kept in English.
- All translations should be verified with native speakers before use in production.
- The Mongolian file uses Latin script (`mn`); the standard Cyrillic-script Mongolian would also use the `mn` code but would differ in content.
- The Finnish ISO 639-1 code is `fi`.
- The Tatar ISO 639-1 code is `tt`.
