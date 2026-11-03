# Open climate and environmental data sources and free tools for Moldova, Romania and Türkiye (Chișinău, Galați, Tekirdağ)

Method note: every URL marked "live" was checked from a script on 2026-11-03 with curl (following redirects, browser user agent), and the final URL and HTTP status were recorded. "200" means the page loaded. "Not reachable" means the check failed: either a DNS failure (NXDOMAIN, so the domain does not exist), a timeout (often geo-blocking of non-local IPs, common for .gov.tr sites), or a 403 bot block. A failed automated check does NOT prove a site is down for a human user in the country. Re-test those URLs by hand before printing the handout.

## 1. Verification of sources already in the draft

### Takeaway
Every source in the draft is live and free, but four details need fixing. Moldova's open data portal date.gov.md has been relaunched as a landing page that sends people to a separate dataset catalogue (dataset.gov.md), which failed the automated check. Galați's "transparență decizională" page has a long Lotus-Notes-style URL. Chișinău has never submitted a Covenant of Mayors plan. Tekirdağ is the only one of the three cities with an approved SECAP (2024).

### Cited Findings
**Moldova**
- particip.gov.md is live and redirects to https://particip.gov.md/ro (HTTP 200). It is the government's public-consultation platform, and its search results include draft environmental and air-quality acts with downloadable attachments — [particip.gov.md](https://particip.gov.md/ro); see the air-quality-related attachment [particip.gov.md/ro/download_attachment/24568](https://particip.gov.md/ro/download_attachment/24568)
- date.gov.md is live (HTTP 200) but has changed. It now presents itself as the "Portalul Guvernamental de Date" with access to public datasets "centralizate prin dataset.gov.md", and links to https://dataset.gov.md/ro/dataset. The dataset counters on the landing page are filled in by JavaScript and showed "0" in the static HTML — [date.gov.md](https://date.gov.md/)
- dataset.gov.md (the catalogue that date.gov.md links to) returned HTTP 404 with a government "Resursa Inexistentă" page for /, /ro, /ro/dataset and /en/dataset, and its CKAN API path also returned 404 — [dataset.gov.md](https://dataset.gov.md/ro/dataset) (NOT confirmed live; could be geo-restriction or a migration in progress)
- The old CKAN search path date.gov.md/ckan/ro/dataset?q=… returns 404, so any old deep links into date.gov.md datasets are probably broken — [date.gov.md/ckan](https://date.gov.md/ckan/ro/dataset?q=aer) (404)
- data.gov.md is not a valid alternative (HTTP 404) — [data.gov.md](https://data.gov.md/)

**Romania**
- data.gov.ro is live (HTTP 200) — [data.gov.ro](https://data.gov.ro/)
- INS TEMPO Online is live at the exact draft URL (HTTP 200, plain http on port 8077) — [statistici.insse.ro:8077/tempo-online](http://statistici.insse.ro:8077/tempo-online/)
- The main INS site insse.ro returned HTTP 503 (service unavailable) at check time — [insse.ro](https://insse.ro/) (not confirmed live; may be temporary)
- Galați "Transparență decizională" (the generic description in the draft is correct): the city hall homepage links to https://www.primariagalati.ro/portal/galati/portal.nsf/AllByUNID/transparenta-decizionala-0001ba6a?OpenDocument, plus "Proiecte de Hotărâri", "Hotărârile Consiliului Local", "Monitorul Oficial Local" and "Anunțuri de mediu" (environmental notices) — [primariagalati.ro homepage](https://www.primariagalati.ro/)
- Note: the shorter-looking path https://www.primariagalati.ro/portal/transparenta-decizionala returns 404, and www.galati.ro returns a Cloudflare 525 error, so it is not the city hall site — [primariagalati.ro](https://www.primariagalati.ro/)

**Türkiye**
- The Tekirdağ Büyükşehir council-decision search on e-Devlet is live at the exact draft URL (HTTP 200) — [turkiye.gov.tr/tekirdag-buyuksehir-belediyesi-meclis-karari-sorgulama](https://www.turkiye.gov.tr/tekirdag-buyuksehir-belediyesi-meclis-karari-sorgulama). Searching an e-Devlet service may need an e-Devlet login (not tested).
- The municipality's own site is live — [tekirdag.bel.tr](https://www.tekirdag.bel.tr/)

**Covenant of Mayors**
- The site is live and redirects to https://eu-mayors.ec.europa.eu/en/home — [eu-mayors.ec.europa.eu](https://eu-mayors.ec.europa.eu/en/home). Each signatory has a profile at /en/signatory/{id}. The details per city are in section 5.

**Tools already listed**
- Open-Meteo Historical Weather API docs are live — [open-meteo.com/en/docs/historical-weather-api](https://open-meteo.com/en/docs/historical-weather-api)
- overpass turbo is live — [overpass-turbo.eu](https://overpass-turbo.eu/)
- Sensor.Community is live, and so is its map — [sensor.community](https://sensor.community/), [maps.sensor.community](https://maps.sensor.community/)
- Datawrapper is live — [datawrapper.de](https://www.datawrapper.de/)
- FT Visual Vocabulary is live in two places: the GitHub chart-doctor repo and the interactive version — [GitHub](https://github.com/Financial-Times/chart-doctor/tree/main/visual-vocabulary), [ft-interactive.github.io/visual-vocabulary](https://ft-interactive.github.io/visual-vocabulary/)

### Inferences
- For Moldova, the handout should say "date.gov.md (government data portal, which links to the dataset catalogue)", and the trainer should check by hand, from inside Moldova, whether dataset.gov.md loads. If it doesn't, statistica.gov.md / statbank (section 3) are the more reliable Moldovan sources.
- For Galați, give participants the full transparență decizională URL, or tell them to click "Transparență decizională" on the primariagalati.ro homepage, because the site's URLs are long and hard to guess.

### Gaps
- I could not confirm whether dataset.gov.md is broken, geo-restricted, or being migrated.
- I did not test the e-Devlet council-decision search itself (whether it needs a login).

## 2. National air-quality networks and their open data

### Takeaway
Romania's calitateaer.ro is the strongest national source. It is live, has hourly data from 100+ stations, a Reports section for historical data and a webservice, and Galați City Hall links to it. Moldova has no live online air-quality portal at the URLs in the brief. The Environment Agency (am.gov.md) publishes monthly PDF bulletins, and citizen-sensor data is best reached through global aggregators. Türkiye's havaizleme.gov.tr exists but did not load from outside the country.

### Cited Findings
**Romania**
- calitateaer.ro is live (redirects to https://www.calitateaer.ro/public/home-page/?__locale=ro). It is the public portal of the National Air Quality Monitoring Network (RNMCA), with "over 100 stations" and hourly indices and values that are still being validated and certified — [calitateaer.ro](https://www.calitateaer.ro/public/home-page/?__locale=ro)
- Historical data: the site says "Pentru a afisa toate datele istorice puteti accesa sectiunea de Rapoarte", with Reports at /public/monitoring-page/reports-reports-page/. A Webservice page (/public/webservice-page/), a station list (/public/description-page/stations-page/) and an emissions-inventory section (/public/emission-page/national-emissions-page/) also exist — [calitateaer.ro](https://www.calitateaer.ro/public/home-page/?__locale=ro)
- Galați City Hall's homepage links directly to calitateaer.ro — [primariagalati.ro](https://www.primariagalati.ro/)
- ANPM (www.anpm.ro) did not resolve in DNS at check time. A public resolver returned NOERROR with only an SOA record for anpm.ro, i.e. no web address — [anpm.ro](https://www.anpm.ro/) (NOT confirmed live)
- The Ministry of Environment, Waters and Forests is live (redirects to mmediu.ro) — [mmediu.ro](https://mmediu.ro/)

**Moldova**
- The Environment Agency is live at am.gov.md, NOT env.gov.md (env.gov.md returned NXDOMAIN). The am.gov.md menu has "Aer", "Monitorizarea mediului", "Monitoringul resurselor naturale", "Datele privind starea resurselor naturale", "Buletine lunare privind calitatea mediului" and "Planul de monitorizare a emisiilor de gaze cu efect de seră" — [am.gov.md](https://am.gov.md/ro); [Aer section](https://am.gov.md/ro/aer); [Monthly bulletins](https://am.gov.md/ro/rapoarte/buletine-lunare-privind-calitatea-mediului)
- Monthly bulletins (PDF) from the Environmental Reference Laboratory continue into 2026 (for example April 2026). They cover air, surface water, soil and radioactivity, and list exceedances of maximum admissible concentrations, including at an automatic traffic station — [Buletin lunar LRM aprilie 2026](https://am.gov.md/sites/default/files/document/attachments/BULETIN%20lunar%20LRM%2C%20aprilie%202026.pdf); [martie 2026](https://am.gov.md/sites/default/files/document/attachments/BULETIN%20lunar%20LRM%2C%20martie%202026.pdf)
- A 2019 UNDP notice said the national Atmospheric Air Quality Laboratory had 8 stationary stations (6 in Chișinău, 2 in Bălți), and that UNDP would install air-quality sensors in Chișinău — [UNDP](https://www.undp.org/node/103431); [Moldpres](https://moldpres.md/eng/society/sensors-for-measuring-air-quality-to-be-set-in-moldovan-capital-)
- The legal basis is Law LP98/2022 on atmospheric air quality and Government Decision 934/2024 on monitoring — [UNEP LEAP / FAOLEX](https://leap.unep.org/en/countries/md/national-legislation/law-no-lp982022-atmospheric-air-quality); [gov.md HG 934/2024 note](https://gov.md/sites/default/files/Filepdf/nu-934-mm-2024.pdf)
- The Ministry of Environment is live — [mediu.gov.md](https://mediu.gov.md/)
- Aer Live Moldova (citizen network, NGO Rural Revival): ten sensors in Chișinău, six more privately owned sensors not yet connected, sensors also in Rezina, plans for Bălți; "any citizen" can view the data on its website — [IPN](https://ipn.md/en/ngo-launches-citizen-driven-network-for-cleaner-air-7967_1105501.html); [Radio Moldova](https://radiomoldova.md/p/84764). The articles are undated in search results.
- aerlive.md and www.aerlive.md returned NXDOMAIN, and airq.md, aerlive.org and ruralrevival.md did not resolve. I found no working web address for the Aer Live Moldova platform — (DNS checks; NOT confirmed)
- Do not confuse it with aerlive.ro, a separate Bucharest platform launched in December 2019 — [Wall-Street.ro](https://www.wall-street.ro/articol/Social/247895/aerlive-ro-platforma-care-masoara-calitatea-aerului-din-bucuresti-s-a-lansat-miercuri.html)
- Live citizen and official sensor readings for Chișinău can be seen on aggregators: the AQICN map of Chișinău (live) and its Moldova page, sensoto.io listings of Chișinău sensors, and an OpenSenseMap archive entry from 14 May 2026 for an SDS011 PM sensor "SENZOR-PM-CHISINAU-2" — [aqicn.org/map/chisinau](https://aqicn.org/map/chisinau/); [aqicn.org/map/moldova](https://aqicn.org/map/moldova/); [sensoto.io Chișinău](https://sensoto.io/en/overview/Chișinău-e88151/); [OpenSenseMap archive](https://archive.opensensemap.org/2026-05-14/655b513ac342d500094a1e5e-SENZOR-PM-CHISINAU-2/SENZOR-PM-CHISINAU-2-2026-05-14.json)

**Türkiye**
- havaizleme.gov.tr resolves in DNS (212.175.89.52) but timed out over both http and https from the checking location. sim.csb.gov.tr and csb.gov.tr also timed out — (NOT confirmed live from outside Türkiye; probably geo-restricted)
- A third-party open-source project says national-network (UHKİA) data comes from sim.csb.gov.tr endpoints that are "resmi, dokümante edilmemiş ama halka açık" (official, undocumented, but public) — [airquality-tr-mcp listing](https://mcpservers.org/zh-TW/servers/alpbel0/airquality-tr-mcp)
- The Tekirdağ provincial directorate of the Ministry (CSB) hosts a document "thep-2025-2029" with a foreword by Mayor Candan Yüceer — [webdosya.csb.gov.tr](https://webdosya.csb.gov.tr/db/tekirdag/menu/thep-2025-2029_20250530105722.pdf) (download timed out, content not verified)

### Inferences
- "THEP" almost certainly stands for "Temiz Hava Eylem Planı" (Clean Air Action Plan), the provincial clean-air plans that Türkiye requires. If so, it is the Tekirdağ air-quality plan for 2025–2029. This is inferred from the file name and has not been verified.
- For Tekirdağ air quality, participants outside Türkiye may need aggregators (AQICN, OpenAQ, the EEA European Air Quality Index, Sensor.Community) rather than havaizleme.gov.tr. Participants inside Türkiye should test havaizleme.gov.tr directly.
- For Chișinău, the most usable no-code sources are AQICN / Sensor.Community / OpenAQ maps plus the am.gov.md monthly bulletins (PDF tables, so data has to be copied out by hand).

### Gaps
- I did not confirm whether calitateaer.ro "Rapoarte" export to CSV without login, or which Galați stations exist (codes like GL-1 were not shown in the fetched content).
- I could not confirm the current URL of the Aer Live Moldova platform, or what "AirQ" refers to in Moldova (no source found).
- Could not confirm a Tekirdağ station list or the download function on havaizleme.gov.tr.

## 3. National hydromet, water, environment and statistics agencies

### Takeaway
All the main national statistics offices and met services have working sites. One URL has changed: TÜİK's data portal data.tuik.gov.tr now redirects to veriportali.tuik.gov.tr. Moldova's hydromet service is at meteo.md, not meteo.gov.md. MGM has a Tekirdağ climate-statistics page, which is a good beginner source for heat.

### Cited Findings
**Moldova**
- The State Hydrometeorological Service site is live at meteo.md (meteo.md redirects to https://www.meteo.md/). www.meteo.gov.md does not resolve — [meteo.md](https://www.meteo.md/)
- A 2014-era EU (ENI-SEIS) document lists daily air-pollution maps and bulletins on meteo.md (may be dated) — [ENI-SEIS](https://eni-seis.eionet.europa.eu/east/governance/project-documents/RepMoldova_Country_Final_MIH_v2cleaned.pdf)
- The National Bureau of Statistics is live (statistica.gov.md redirects to /ro). Its StatBank PxWeb database is also live, at https://statbank.statistica.md/PxWeb/pxweb/ro/ — [statistica.gov.md](https://statistica.gov.md/ro); [statbank.statistica.md](https://statbank.statistica.md/PxWeb/pxweb/ro/)

**Romania**
- ANM (national meteorological administration) is live — [meteoromania.ro](https://www.meteoromania.ro/). Its /clim/ section returned 403 to the automated check — [meteoromania.ro/clim](https://www.meteoromania.ro/clim/). ANM also runs an INSPIRE GeoNetwork metadata catalogue, which is live — [inspire.meteoromania.ro](https://inspire.meteoromania.ro/geonetwork/srv/eng/catalog.search)
- Romanian Waters (ANAR) is live — [rowater.ro](https://rowater.ro/)
- INHGA (National Institute of Hydrology and Water Management) is live — [hidro.ro](https://www.hidro.ro/)
- inundatii.ro is live (www redirects to apex) — [inundatii.ro](https://inundatii.ro/) (content not inspected; likely the national flood-risk information site, unverified)
- INS: TEMPO Online is live (see section 1); insse.ro returned 503 at check time.

**Türkiye**
- MGM (Turkish State Meteorological Service) is live. Its province/district climate-statistics page for Tekirdağ is live at https://www.mgm.gov.tr/veridegerlendirme/il-ve-ilceler-istatistik.aspx?m=TEKIRDAG — [mgm.gov.tr](https://www.mgm.gov.tr/); [Tekirdağ statistics](https://www.mgm.gov.tr/veridegerlendirme/il-ve-ilceler-istatistik.aspx?m=TEKIRDAG)
- MGM's MEVBİS data-request system is live — [mevbis.mgm.gov.tr](https://mevbis.mgm.gov.tr/) (whether students can get data free or without registration was not verified)
- URL CHANGE: data.tuik.gov.tr now returns a 302 redirect to https://veriportali.tuik.gov.tr/ (live) — [veriportali.tuik.gov.tr](https://veriportali.tuik.gov.tr/tr/). The direct data.tuik.gov.tr request then timed out.
- TÜİK's MEDAS regional statistics database is live — [biruni.tuik.gov.tr/medas](https://biruni.tuik.gov.tr/medas/)
- The Climate Change Presidency (İklim Değişikliği Başkanlığı) is live — [iklim.gov.tr](https://iklim.gov.tr/)
- National open-data portal: acikveri.gov.tr did not resolve and data.gov.tr timed out. Neither was confirmed. City-level open-data portals do exist in Türkiye (for example İzmir and İstanbul's data.ibb.gov.tr, and Konya's portal with air-quality station datasets), but not for Tekirdağ (see section 5) — [Webrazzi on İBB portal](https://webrazzi.com/2020/01/19/ibb-acik-veri-portali/); [Konya açık veri air-quality stations](https://acikveri.konya.bel.tr/en/dataset/hava-kalitesi-istasyonlari-konum-bilgileri/resource/df2769be-a719-44f7-9d26-1c794fcf4b36)

### Inferences
- In the handout, replace "data.tuik.gov.tr" with "veriportali.tuik.gov.tr".
- MGM's Tekirdağ statistics page and Open-Meteo are the easiest heat and precipitation sources for Tekirdağ. For Galați and Chișinău, Open-Meteo is easier for beginners than ANM or meteo.md.

### Gaps
- I did not verify how much downloadable data (CSV) meteo.md, ANM, Romanian Waters and MGM actually provide without registration.
- No confirmed national open-data portal for Türkiye.

## 4. European and international sources covering all three countries

### Takeaway
Nearly all the pan-European and global sources are live. There are two URL changes to fix. Global Forest Watch rebranded as Global Nature Watch in September 2026, and old GFW links redirect. The EEA's air-quality viewer is at airindex.eea.europa.eu, because airquality.eea.europa.eu does not exist.

### Cited Findings
- Copernicus Climate Data Store is live — [cds.climate.copernicus.eu](https://cds.climate.copernicus.eu/)
- Copernicus Climate Change Service (C3S) is live — [climate.copernicus.eu](https://climate.copernicus.eu/)
- The Copernicus Interactive Climate Atlas is live (no-code maps of climate projections) — [atlas.climate.copernicus.eu](https://atlas.climate.copernicus.eu/). Note: atlas.copernicus.eu does not resolve.
- The CDS dataset "Climate variables for cities in Europe" (sis-urban-climate-cities, urban heat) is live — [CDS sis-urban-climate-cities](https://cds.climate.copernicus.eu/datasets/sis-urban-climate-cities?tab=overview). City coverage for Chișinău, Galați or Tekirdağ was not verified.
- Copernicus Land Monitoring: the Urban Atlas product page and the Land map viewer are live — [Urban Atlas](https://land.copernicus.eu/en/products/urban-atlas); [Land map viewer](https://land.copernicus.eu/en/map-viewer)
- EEA Datahub is live — [eea.europa.eu/en/datahub](https://www.eea.europa.eu/en/datahub)
- The EEA European City Air Quality Viewer is live — [EEA city air quality viewer](https://www.eea.europa.eu/en/topics/in-depth/air-pollution/european-city-air-quality-viewer)
- URL FIX: the European Air Quality Index (live map) is at https://airindex.eea.europa.eu/AQI/index.html (live). airquality.eea.europa.eu returned NXDOMAIN — [airindex.eea.europa.eu](https://airindex.eea.europa.eu/AQI/index.html)
- The EEA bulk air-quality download service returned 403 to the automated check — [EEA download webapp](https://eeadmz1-downloads-webapp.azurewebsites.net/) (not confirmed)
- The Climate-ADAPT European Climate Data Explorer is live. Its URL has moved to /en/eu-adaptation/assessing-climate-risks/european-climate-data-explorer — [Climate-ADAPT ECDE](https://climate-adapt.eea.europa.eu/en/eu-adaptation/assessing-climate-risks/european-climate-data-explorer)
- The EEA urban sustainability topic page is live — [EEA urban sustainability](https://www.eea.europa.eu/en/topics/in-depth/urban-sustainability)
- EDGAR emissions database (JRC) is live — [edgar.jrc.ec.europa.eu](https://edgar.jrc.ec.europa.eu/)
- RENAMED: WRI announced on 21 September 2026 that "Global Forest Watch (GFW) … is now Global Nature Watch (GNW)", covering more land ecosystems. Existing users keep access to the forest data and tools, and an AI platform "Horizon" is in preview — [WRI release](https://www.wri.org/news/release-global-forest-watch-becomes-global-nature-watch-expanding-cover-more-land-ecosystems). globalforestwatch.org and its country dashboards (for example /dashboards/country/MDA/) now redirect to globalnaturewatch.org (live) — [globalnaturewatch.org](https://globalnaturewatch.org/)
- OpenAQ Explorer is live (openaq.org/developers/ returned 404) — [explore.openaq.org](https://explore.openaq.org/); [openaq.org](https://openaq.org/)
- Climate TRACE is live (data.climatetrace.org did not resolve) — [climatetrace.org](https://climatetrace.org/)
- The World Bank Climate Change Knowledge Portal returned HTTP 403 to automated requests for the root and the /country/moldova and /country/turkiye pages — [CCKP](https://climateknowledgeportal.worldbank.org/) (probably bot protection; NOT confirmed live by script)
- The Eurostat data browser is live — [Eurostat databrowser](https://ec.europa.eu/eurostat/databrowser/). The Eurostat Cities (Urban Audit) database page is live — [Eurostat cities database](https://ec.europa.eu/eurostat/web/cities/database)
- The guessed Eurostat enlargement-countries database URL returned 404 — (ec.europa.eu/eurostat/web/enlargement-policy/data/database)
- The EU Covenant of Mayors signatory map/list covers Moldova and Türkiye as well as Romania. Its signatory data includes 156 Moldovan signatories — [eu-mayors.ec.europa.eu/en/signatories](https://eu-mayors.ec.europa.eu/en/signatories)

### Inferences
- From prior knowledge, not re-verified here: Urban Atlas covers EEA member and cooperating countries (including Romania and Türkiye) but not Moldova. Eurostat publishes some data on candidate countries (Moldova and Türkiye are both candidates) through its enlargement-countries collection. Both points should be checked before printing.
- For a no-code handout, the most beginner-friendly European tools are the EEA European Air Quality Index map, the Copernicus Interactive Climate Atlas, Climate-ADAPT's European Climate Data Explorer and Global Nature Watch. The CDS needs a free account and is harder to use.

### Gaps
- I did not verify which of the three cities appear in Urban Atlas, the CDS urban-climate dataset, or the EEA city air-quality viewer (the viewer covers EU cities; Galați is likely included, but Chișinău and Tekirdağ are uncertain).
- I did not verify Eurostat's candidate-country coverage or its current URL.
- I could not load the World Bank CCKP by script.

## 5. City-specific sources and climate plans (including Covenant of Mayors status)

### Takeaway
Tekirdağ joined the Covenant in January 2023 with a 2050 commitment, and its SECAP was approved on 10 January 2024 (baseline 2019, −80% by 2050, floods named as the main hazard). Galați joined in 2014 with a 2020 commitment, approved a SEAP in October 2016 and last reported monitoring in 2022, but has no 2030 SECAP on record. Chișinău joined in 2011 (2020 commitment) and has never submitted a plan. Chișinău and Galați publish draft decisions online. Galați has a small ArcGIS open-data pilot, and no Tekirdağ open-data portal was found.

### Cited Findings
**Covenant of Mayors (data from signatory profiles and the signatory dataset embedded in eu-mayors.ec.europa.eu/en/signatories, read 2026-11-03)**
- **Chișinău** (organisation_id 14852): committed since 2011-12-08, commitment "CoM 2020" only, profile says "No information reported". action_plan_2020/2030/2050_submitted are all 0, monitoring_reports is 0, status_id is 4 (the other two cities have 3). The mayor on the profile is still Dorin Chirtoacă, so the profile is out of date — [Chișinău signatory profile](https://eu-mayors.ec.europa.eu/en/signatory/14852); [adhesion document](http://mycovenant.eumayors.eu/docs/adhesion/3578_1322478548.pdf)
- A UNDP document says Chișinău failed to approve a SEAP within two years of joining, is a "Suspended Signatory", and showed interest in 2019 in reactivating its status with 2030 targets (document undated) — [UNDP document](https://sc.undp.md/jobget_doc/5542). Chișinău's accession news — [chisinau.md](https://www.chisinau.md/en/chisinau-will-accede-to-the-covenant-of-mayors-european-20292_244152.html)
- **Galați** (organisation_id 18130): committed since 2014-05-29. Action plan with "Target 2020", approval date 2016-10-28, titled "PLANUL DE ACTIUNE PENTRU ENERGIA DURABILA" (SEAP). Latest monitoring report 2022, "last submitted in 2022". Also takes part in the EU Green City Accord and is supported by the Romanian Municipalities Association. The site notes that Galați also reports to CDP-ICLEI Track — [Galați signatory profile](https://eu-mayors.ec.europa.eu/en/signatory/18130); [SEAP PDF](http://mycovenant.eumayors.eu/docs/seap/20863_1479214632.pdf); [other plan/monitoring document](http://mycovenant.eumayors.eu/storage/web/mc_covenant/documents/27/fT-p8yKx765X1lnphdROpctkkmTqdCuH.pdf)
- Discrepancy: the Galați profile page shows a "Commitment 2050" document under Commitments, but the signatory dataset lists commitments = "1" (CoM 2020 only) and action_plan_2030_submitted = 0 — [Galați profile](https://eu-mayors.ec.europa.eu/en/signatory/18130); [signatory list](https://eu-mayors.ec.europa.eu/en/signatories)
- **Tekirdağ** (organisation_id 31677, Büyükşehir, population 1,167,059): committed since 2023-01-11, "Signatory 2050", also in UN Race to Zero and Race to Resilience. Action plan "Target 2030, Target 2050", approval date 2024-01-10, "Tekirdağ Sustainable Energy and Climate Action Plan", last submitted 2025. Key actions listed: energy efficiency in municipal buildings (2025–2049), cleaner municipal vehicles (2026–2049), solar on municipal buildings (2025–2049) — [Tekirdağ signatory profile](https://eu-mayors.ec.europa.eu/en/signatory/31677); [SECAP PDF (103 pages, about 20 MB)](https://mycovenant.eumayors.eu/storage/web/mc_covenant/documents/31/QOyEAroJ0jU9Fb3q5Z0TNdG0roJbvqG5.pdf)
- Tekirdağ SECAP content: the title page reads "Tekirdağ Sürdürülebilir Enerji ve İklim Eylem Planı, 2023". It was prepared by the Department of Climate Change and Zero Waste with İstanbul Enerji AŞ. The baseline year is 2019, with total emissions of 12,050,617 tCO2e (stationary energy 9,696,976, transport 2,080,747, waste 272,894). Business-as-usual projection: 20,321,727 tCO2e by 2050. Target: an 80.1% cut to 4,040,315 tCO2e by 2050. Floods are the main climate hazard (floods in 1998, 2007, 2012, 2013, 2018, 2022), and the Süleymanpaşa coast and the northeast of the province have high flood risk. The plan also maps heat waves and land-surface temperature — [Tekirdağ SECAP](https://mycovenant.eumayors.eu/storage/web/mc_covenant/documents/31/QOyEAroJ0jU9Fb3q5Z0TNdG0roJbvqG5.pdf)
- Under Türkiye's local climate action plan regulation, plans in metropolitan provinces are prepared by the metropolitan municipality under the governor's coordination — [TRT Haber](https://www.trthaber.com/haber/gundem/yerel-iklim-degisikligi-eylem-planlarina-iliskin-yonetmelik-resmi-gazetede-yayimlandi-953072.html)
- An earlier EU-funded project, "Trakya Bölgesinde İklim Değişikliği ile Mücadele ve Adaptasyon" (contract signed 20 June 2016), had Tekirdağ Büyükşehir as beneficiary with Namık Kemal University and TESKİ as partners — [iklimin.org](https://www.iklimin.org/wp-content/uploads/2018/01/Bölüm0_Giriş.pdf)

**Chișinău transparency and data**
- These Primăria Chișinău pages are live and linked from the homepage: "Consultări publice" https://www.chisinau.md/ro/decision_making_process (HTTP 200), "Proiecte de decizii" https://www.chisinau.md/ro/proiecte-de-decizii-20464.html, "Decizii CMC/Acte locale" https://www.chisinau.md/ro/decizii-cmcacte-locale-20926.html, "Arhiva Decizii CMC" https://www.chisinau.md/ro/decizii-cmc-20297.html, "Rapoarte privind transparența decizională" https://www.chisinau.md/ro/rapoarte-anualetransparenta-pmc-20543.html, "Buget transparent" https://www.chisinau.md/ro/buget-transparent-20551.html — [chisinau.md](https://www.chisinau.md/ro)
- A climate-relevant consultation: "Consultarea Publică CP-04" on background studies (natural heritage, environmental protection, natural and man-made risks) for the update of Chișinău's General Urban Plan (PUG) 2040 — [chisinau.md CP-04 announcement](https://www.chisinau.md/ro/act_projects_details/anunt-privind-organizarea-consultarii-publice-cp-04-asupra-studiilor-de-fundamentare-patrimoniu-natural-protectia-mediului-riscuri-naturale-si-riscuri-antropice-si-studiu-istoric-elaborate-in-cadrul-procesului-de-reactualizare-a-planului-urbanistic-general-al-orasului-chisinau-2040/595)
- A public debate on an environmental impact assessment report is also announced — [chisinau.md EIA debate](https://www.chisinau.md/ro/act_projects_details/anunt-public-privind-desfasurarea-dezbaterii-publice-asupra-raportului-privind-evaluarea-impactului-asupra-mediului/596)
- date.chisinau.md does not exist (NXDOMAIN). No Chișinău open-data portal was found.

**Galați transparency and data**
- Galați City Hall pages are linked from the homepage: Transparență decizională, Proiecte de Hotărâri (https://www.primariagalati.ro/portal/galati/portal.nsf/AllByUNID/proiecte-de-hotarari-0001b8da?OpenDocument), Hotărârile Consiliului Local (https://www.primariagalati.ro/portal/galati/portal.nsf/AllByUNID/hotararile-consiliului-local-0001b7ba?OpenDocument), Anunțuri de mediu (https://www.primariagalati.ro/portal/galati/portal.nsf/AllByUNID/anunturi-de-mediu-0004a30e?Open), and Proiecte Europene. Council decisions are PDFs under primariagalati.ro/dm_galati/hotarari.nsf/ — [primariagalati.ro](https://www.primariagalati.ro/)
- The homepage links to "OpenData - Proiect Pilot" (https://arcg.is/bvajy), which redirects to an ArcGIS Hub at https://primaria-municipiului-galati-open-data-pmgalati.hub.arcgis.com/ (live). Its search API lists only 3 items, all about EU-funded investments ("Investitii din fonduri nerambursabile" web map, "Proiecte din FE" dashboard, "investopendata" feature service), last modified around December 2022–January 2023. No environmental datasets — [Galați Open Data hub](https://primaria-municipiului-galati-open-data-pmgalati.hub.arcgis.com/)
- Galați City Hall annual mayor's reports (2017, 2018, 2021) are online as PDFs — [Raport Primar 2021](https://www.primariagalati.ro/portal/galati/portal.nsf/AllByUNID/34673DCDCF8190AAC225889400349B55/$FILE/Raport%20Primar%202021.pdf)

**Tekirdağ data**
- No Tekirdağ Büyükşehir open-data portal was found in search. acikveri.tekirdag.bel.tr timed out — (search results: [example](https://www.sondakika.com/guncel/haber-tekirdag-buyuksehir-den-e-devlet-birinciligi-11444288/), which reports the municipality ranked first among 30 metropolitan municipalities for e-government integration)
- The Turkish Court of Accounts (Sayıştay) publishes audit reports on Tekirdağ Büyükşehir and on TESKİ (the water and sewerage utility) — [Sayıştay TBB report](https://sayistay.gov.tr/reports/download/2MgpbGMYjy-tekirdag-buyuksehir-belediyesi); [Sayıştay TESKİ report](https://www.sayistay.gov.tr/reports/download/1aYBqMAQew-tekirdag-su-ve-kanalizasyon-idaresi-genel-mudurlugu)

### Inferences
- For the handout, the Covenant line should read: Chișinău, signatory since 2011 with no plan submitted (inactive or suspended); Galați, signatory since 2014 with a 2020 SEAP approved 2016 and last monitoring in 2022, but no 2030 SECAP; Tekirdağ, signatory since 2023 with a SECAP approved 2024 (2030/2050 targets).
- The Tekirdağ SECAP is a strong workshop resource. It has a flood-risk map, heat and land-surface-temperature analysis, and an emissions inventory by sector.
- For waste, green spaces and transport in Chișinău and Galați, OpenStreetMap via overpass turbo, Urban Atlas (Galați) and national statistics will probably be more useful than the city portals.

### Gaps
- I could not find a city heat plan or 2030 climate plan for Chișinău or Galați. Galați's Green City Accord baseline or plan was not checked.
- The exact meaning of Chișinău's status_id 4 is not labelled on the site. The "suspended" label comes from an undated UNDP document.
- I could not open the Tekirdağ "thep-2025-2029" document.

## 6. Free no-code tools for beginners (and account requirements)

### Takeaway
Datawrapper's free plan needs an account but gives unlimited publishing and PNG export, with a "Created with Datawrapper" credit, and it explicitly welcomes workshops. Flourish, uMap, kepler.gl, QGIS and Looker Studio are all live. Their account rules are listed under Inferences from prior knowledge, and the trainer should spot-check them.

### Cited Findings
- Datawrapper Free: "Create and embed interactive charts, maps, and tables", "Publish and embed visualizations on the web", "Download your visualizations as PNG images", "Create an account". The free plan allows unlimited publishing and collaboration, and Datawrapper says workshop attendees' charts can be grouped into teams and shared folders. Removing the attribution needs Pro ($21/user/month) — [Datawrapper pricing](https://www.datawrapper.de/pricing)
- Flourish pricing page is live — [flourish.studio/pricing](https://flourish.studio/pricing/) (plan details not extracted)
- uMap is live — [umap.openstreetmap.fr](https://umap.openstreetmap.fr/en/)
- kepler.gl demo is live — [kepler.gl/demo](https://kepler.gl/demo)
- QGIS is live — [qgis.org](https://qgis.org/)
- Looker Studio: lookerstudio.google.com redirects to datastudio.google.com/overview (live) — [Looker Studio](https://datastudio.google.com/overview)
- The Copernicus Land map viewer, Interactive Climate Atlas, EEA Air Quality Index and Global Nature Watch are all live browser viewers (see section 4).

### Inferences
These come from prior knowledge and were NOT verified against documentation in this session:
- Flourish's free plan needs an account, and published visualisations are public.
- uMap lets you make maps without an account (you keep a secret edit link), or you can log in with an OpenStreetMap or other account.
- kepler.gl runs in the browser with no account, and data stays on your machine.
- QGIS is free desktop software with no account, but it is the hardest of these for beginners.
- Google Sheets and Looker Studio need a Google account.
- overpass turbo, Open-Meteo's web interface, Sensor.Community maps, AQICN, OpenAQ Explorer and the EEA/Copernicus viewers need no account. Copernicus CDS downloads need a free ECMWF account.
- Suggested beginner order: Google Sheets → Datawrapper → uMap/Flourish → kepler.gl → QGIS (optional, advanced).

### Gaps
- I did not verify Flourish, uMap, kepler.gl or Google account requirements against current documentation.
- I did not check whether Global Nature Watch or the CDS need logins for downloads after the 2026 changes.
