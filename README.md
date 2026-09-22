# Data sources

Every dataset behind the figures in `figures/`, where it came from, its licence, where it now sits
on disk, and its documentation. **All of it is downloaded** — nothing in any figure depends on a
live service at plotting time. Accessed 2026-09-22. Total: about 2.9 GB in `data_raw/`, 29 MB in
`docs/`.

Re-fetch data with the numbered scripts (each caches and skips what it already has) and
documentation with `Rscript 90_fetch_docs.R`.

## Spatial data

| # | Dataset | Used in | Source and download link | Licence | Local path | Size |
|---|---|---|---|---|---|---|
| 1 | **Administrative boundaries VG250** (Länder, Regierungsbezirke, Kreise, 10,939 Gemeinden) | all figures | BKG, [vg250_01-01.utm32s.gpkg.ebenen.zip](https://daten.gdz.bkg.bund.de/produkte/vg/vg250_ebenen_0101/aktuell/vg250_01-01.utm32s.gpkg.ebenen.zip) ([product page](https://gdz.bkg.bund.de/index.php/default/verwaltungsgebiete-1-250-000-ebenen-stand-01-01-vg250-ebenen-01-01.html)) | dl-de/by-2.0 | `data_raw/vg250/` | 116 MB |
| 2 | **N-balance surplus per field block**, mean 2016–19, kg N/(ha·a) — the core surplus layer | Fig03, 04, 05, 06, 07, 10, 13 | LANUV NRW / GROWA+ NRW 2021 (§8 AVV GeA), [GLDN-Potenzielle-Nitrataustraege-Par-8-AVV-GeA_EPSG25832_Shape.zip](https://www.opengeodata.nrw.de/produkte/umwelt_klima/wasser/duev_hist/GLDN-Potenzielle-Nitrataustraege-Par-8-AVV-GeA_EPSG25832_Shape.zip) ([metadata](https://open.nrw/dataset/405f24c8-7d92-4681-b6e2-cbebe586f349)) | dl-de/zero-2.0 | `data_raw/gldn_pot/` | 399 MB |
| 3 | **Nitrate-polluted areas** under §13a DüV, 01/2025 | Fig03, 04, 05, 10 | LANUK NRW, [NitratbelasteteGebieteNRW-202501_EPSG25832_Shape.zip](https://www.opengeodata.nrw.de/produkte/umwelt_klima/wasser/duev_hist/NitratbelasteteGebieteNRW-202501_EPSG25832_Shape.zip) ([metadata](https://open.nrw/dataset/07afb437-8ee5-4208-92da-76a128cc268a)) | dl-de/zero-2.0 | `data_raw/nitrat_gebiete/` | 167 MB |
| 4 | **Subsidy-application parcels with crop codes** (742,503 sub-parcels; crop 115 = winter wheat) | Fig10, 11, 13 | Landwirtschaftskammer NRW, [LWK-TSCHLAG_EPSG25832_Shape.zip](https://www.opengeodata.nrw.de/produkte/umwelt_klima/bodennutzung/landwirtschaft/LWK-TSCHLAG_EPSG25832_Shape.zip) ([folder](https://www.opengeodata.nrw.de/produkte/umwelt_klima/bodennutzung/landwirtschaft/)) | dl-de/zero-2.0 | `data_raw/tschlag/` | 551 MB |
| 5 | **N₂O from agricultural soils**, 2022, 0.1° grid | Fig02, 03 | EDGAR v8.0 (JRC), [N2O/AGS 2022](https://jeodpp.jrc.ec.europa.eu/ftp/jrc-opendata/EDGAR/datasets/v80_FT2022_GHG/N2O/AGS/emi_nc/v8.0_FT2022_GHG_N2O_2022_AGS_emi_nc.zip) | CC BY 4.0 | `data_raw/edgar_n2o_ags/` | 25 MB |
| 6 | **N₂O from agricultural soils, annual 1990–2022** (33 grids) | Fig15 | EDGAR v8.0, [N2O/AGS folder](https://jeodpp.jrc.ec.europa.eu/ftp/jrc-opendata/EDGAR/datasets/v80_FT2022_GHG/N2O/AGS/emi_nc/) (one file per year) | CC BY 4.0 | `data_raw/edgar_n2o_years/` | 945 MB |
| 7 | **CH₄ enteric fermentation** (3A1) and **manure management** (3A2), 2022 — livestock proxy | Fig09 (fallback only) | EDGAR v8.0, [CH4/ENF](https://jeodpp.jrc.ec.europa.eu/ftp/jrc-opendata/EDGAR/datasets/v80_FT2022_GHG/CH4/ENF/emi_nc/v8.0_FT2022_GHG_CH4_2022_ENF_emi_nc.zip), [CH4/MNM](https://jeodpp.jrc.ec.europa.eu/ftp/jrc-opendata/EDGAR/datasets/v80_FT2022_GHG/CH4/MNM/emi_nc/v8.0_FT2022_GHG_CH4_2022_MNM_emi_nc.zip) | CC BY 4.0 | `data_raw/edgar_ch4_*/` | 50 MB |

## Tabular data extracted from reports

These are published as PDFs, not as datasets. The reports themselves are downloaded, and the scripts
parse the named tables with a reconciliation check (a row enters a figure only if it adds up).

| # | Data | Used in | Report and link | Table | Local path |
|---|---|---|---|---|---|
| 8 | **District N surplus, 2014/16 and 2022/24** | Fig14 | Nährstoffbericht NRW 2025, Landwirtschaftskammer NRW, [naehrstoffbericht-2025.pdf](https://www.landwirtschaftskammer.de/landwirtschaft/ackerbau/pdf/naehrstoffbericht-2025.pdf) | Tabelle 14 | `data_raw/naehrstoffbericht/` |
| 9 | **District livestock units, 2024 and 2020** | Fig09, 14 | Nährstoffberichte NRW [2025](https://www.landwirtschaftskammer.de/landwirtschaft/ackerbau/pdf/naehrstoffbericht-2025.pdf) and [2021](https://www.landwirtschaftskammer.de/landwirtschaft/ackerbau/pdf/naehrstoffbericht-2021.pdf) | Tabelle B 1 | `data_raw/naehrstoffbericht/` |
| 10 | **Monthly Nmin (NO₃-N + NH₄-N) at reference fields**, Aug–Dec 1990–2025 → 1,620 observations | Fig12 | Nitratdienst NRW / LUFA Münster, monthly tables `…/nitratdienst/pdf/tabelle[n]-YYYY-MM-nmin.pdf` ([archive](https://www.landwirtschaftskammer.de/landwirtschaft/ackerbau/duengung/nitratdienst/archiv/index.htm)) | whole table | `data_raw/nitratdienst/` (48 PDFs) |
| 11 | **NRW winter-wheat area** (248,800 ha, 23.3% of arable land) — validation only | Fig10, 11 | IT.NRW press release | — | `docs/ITNRW_wheat-area-2024.html` |

## Documentation (`docs/`, fetched by `90_fetch_docs.R`)

| File | What it documents |
|---|---|
| `GROWA-NRW-2021_Thuenen_N-balances-per-Gemeinde.pdf` | **How the municipal N balance surpluses in dataset 2 were derived** — the primary method reference |
| `GROWA-NRW-2021_RAUMIS-method.pdf` | The RAUMIS model behind the regional N balances |
| `GROWA-NRW-2021_measure-effect-analysis.pdf` | Effect of N-reduction measures on those balances |
| `GROWA-NRW-2021_project-overview.html` | Project page listing all report parts |
| `LWK-NRW_parcel-attributes_DE.pdf` / `_EN.pdf` | Attribute and crop-code definitions for dataset 4 |
| `ELWAS_FAQ_Ausweisung-rote-Gebiete-NRW.pdf` | How the §13a DüV areas (dataset 3) are delineated |
| `EDGAR_v8.0_dataset-page.html` | EDGAR sector definitions, units, citation, licence |
| `Nitratdienst_method-overview.html` | The Nmin monitoring network behind dataset 10 |
| `UBA_TEXTE_131-2019_N-Flaechenbilanzen.pdf` | UBA/Gießen method for district N balances 1995–2017 |
| `Haeussermann-etal-2020_district-N-budgets.pdf` + `_supplement.docx` | Peer-reviewed district N budgets 1995–2017 (CC BY) |

Documentation that shipped inside a data download and is already on disk:
`data_raw/vg250/dokumentation/*.pdf` (5 BKG PDFs) ·
`data_raw/gldn_pot/Datenbeschreibung-GLDN-*.pdf` ·
`data_raw/nitrat_gebiete/**/Metadaten_*.pdf` (2) ·
`data_raw/edgar_*/_readme.html` · the two Nährstoffberichte · 48 Nitratdienst tables.

## Not downloadable automatically

| Item | Why | What to do |
|---|---|---|
| **AGRUM-DE district N balances 2014–16** (Zinnbauer & Eysholdt 2025, [doi:10.3220/253-2025-211](https://doi.org/10.3220/253-2025-211)) | OpenAgrar sits behind a JavaScript bot check | Download the GeoPackage in a browser into `data_raw/agrum/`, re-run `01_prepare_data.R` and `02_maps_germany.R` → adds Fig02b (Germany-wide N surplus) |
| **LANUV Fachbericht 110/121** (full GROWA+ NRW 2021 report) | juser.fz-juelich.de serves a bot challenge | Optional: the project page and the three GROWA+ PDFs in `docs/` already cover the method. Fetch by hand from [juser record 891307](https://juser.fz-juelich.de/record/891307) if you want the full report |
| **Gemeinde-level livestock census** (table 41141, agricultural census 2020) | [landesdatenbank.nrw.de](https://www.landesdatenbank.nrw.de/ldbnrw/online/) only serves it through an interactive session; the federal regionalstatistik.de API has closed guest access | Optional: export a CSV into `data_raw/livestock/` (key column `AGS`, value column `GV`) and `07_livestock.R` prefers it over the district data now in use |

## Licence obligations for the manuscript

* **dl-de/by-2.0** (dataset 1) requires naming the source: "© GeoBasis-DE / BKG 2026 (dl-de/by-2.0)".
* **dl-de/zero-2.0** (datasets 2–4) imposes no conditions; the figure captions credit LANUV/LANUK
  and the Landwirtschaftskammer NRW anyway.
* **CC BY 4.0** (datasets 5–7) requires citing EDGAR: Crippa et al., *GHG emissions of all world
  countries*, JRC/IEA, EDGAR v8.0 (2023).
* The Nährstoffberichte, Nitratdienst tables and GROWA+ reports are cited as publications, not
  redistributed with the figures.
