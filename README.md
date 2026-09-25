# TEST
**PMT25 - Bejelentés a pénzmosás és a terrorizmus finanszírozása megelőzéséről és megakadályozásáról**

Automatikusan generált új generációs űrlap repository.


## Repository célja

Ez a repository a(z) `TEST` űrlaptípushoz tartozó **XML/XSD alapú űrlapleíró és a kapcsolódó metaállományokat** tartalmazza.


---

## Kontextus

Az ÁNYK kivezetéséhez kapcsolódó NAV M2M 4.0 fejlesztések célja, hogy az ügyviteli szoftverek számára szabványosabb, automatizálhatóbb és könnyebben feldolgozható űrlapkezelési megoldás álljon rendelkezésre.

Az új NAV M2M bizonylat API-ban az űrlapok adatszerkezete XML alapon, űrlaponként saját XSD állományban kerülnek leírásra. Ezek az űrlapspecifikus XSD-k egységes szerkezeti elveket követnek, és közös elemekre, típusokra, enumerációkra, valamint metaséma-elemekre támaszkodhatnak.

Ez a repository ehhez a közös alapréteghez tartozik.

---

### A(z) `TEST` repository szerepe az architektúrában

Az új generációs űrlapkezelési architektúra három fő repository-típusra épül:

| Repository | Szerep |
| --- | --- |
| `common` | közös sémák, metasémák, enumerációk |
| űrlapspecifikus repository-k | konkrét űrlapleírók |
| `catalog` | verzió- és érvényességi katalógus |

Ez a repository egy konkrét űrlaptípus technikai leíróit tartalmazza.


### Kapcsolat a common repository-val

A repository a `common` repository-ban található:
- közös típusokra,
- enumerációkra,
- metasémákra,
- valamint validációs alapelemekre

épül.


### Kapcsolat a catalog repository-val

A repository-ban található verziók önmagukban nem jelentik azt, hogy az adott űrlapverzió beadásra elfogadott.

Az aktuálisan használható és beadásra elfogadott verziók a `catalog` repository-ban található katalógusállományok segítségével állapíthatók meg.

A `catalog` repository tartalmazza:
- az egyes űrlaptípusok verzióit,
- azok érvényességi időszakát (érvényesség kezdete/érvényesség vége),
- valamint az esetleges verzió tiltási (`disabled`) állapotot.

Az űrlap benyújthatóságának meghatározása során a `catalog` repository validitási és tiltási szabályai az irányadók.

---

## Űrlaptípus verziókezelése

A repository tartalmát képező űrlaptípus verziókövetése git release tag segítségével történik.

A(z) `TEST` űrlaptípus egy-egy verzióját egy [tag](../../tags) reprezentálja.

Emellett a repository két branch-et használ:
- `main`: technikai branch, a generálási/szinkronizálási folyamatok alapértelmezett munkabranch-e.
- `actual`: **nézeti branch**, amely mindig az aktuális verziót jelölő tagre mutat.


### Mi az aktuális verzió?

Az aktuális verzió az a legmagasabb verziószámú verzió, amelyhez a `catalog` repository-ban tárolt metaadatok alapján az alábbi feltételek egyszerre teljesülnek:
- az érvényesség kezdete nem a jövőben van,
- az érvényesség vége üres vagy még nem járt le,
- a verzió nincs tiltva (`disabled=false`).

Megjegyzés: a beadási/érvényességi döntés forrása továbbra is a `catalog` repository.


---

## Repository felépítése, állományai

A repository fő tartalmai a `content/` könyvtárban találhatók. Példa tartalom:

```text
content/
├── TEST.xsd
├── TEST_nyomtatvanyinfo.xml
├── TEST_xpath.xml
└── ...
```


---

## Kapcsolódó dokumentációk

Az új M2M bizonylatkezelési modellhez és az ÁNYK kivezetéséhez kapcsolódó háttéranyagok:

- [ÁNYK kivezetéshez kapcsolódó M2M fejlesztések](https://github.com/nav-gov-hu/M2M/wiki/%C3%81NYK-kivezet%C3%A9shez-kapcsol%C3%B3d%C3%B3-M2M-fejleszt%C3%A9sek)
- [Új bizonylat API](https://github.com/nav-gov-hu/M2M/wiki/%C3%9Aj-bizonylat-API)
- [Új bizonylat API: XML formátum](https://github.com/nav-gov-hu/M2M/wiki/%C3%9Aj-bizonylat-API:-XML-form%C3%A1tum)
- [Új bizonylat API: XML validáció](https://github.com/nav-gov-hu/M2M/wiki/%C3%9Aj-bizonylat-API:-XML-valid%C3%A1ci%C3%B3)
- [Tech Tips: Új bizonylat API használata](https://github.com/nav-gov-hu/M2M/wiki/Tech-Tips:-%C3%9Aj-bizonylat-API-haszn%C3%A1lata)




## Technikai jelleg

A repository gépi feldolgozásra optimalizált űrlapleíró és metaállományokat tartalmaz.



