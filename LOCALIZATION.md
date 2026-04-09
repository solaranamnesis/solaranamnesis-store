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
