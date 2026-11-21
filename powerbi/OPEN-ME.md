# Opening the Power BI report

`SACountryBuses.pbip` is a Power BI Project: the report (`SACountryBuses.Report`, PBIR format) and the semantic model (`SACountryBuses.SemanticModel`, TMDL) saved as text, so the repo can show every change. Power BI Desktop opens it like a `.pbix`.

## What you need

- Power BI Desktop for Windows, a recent version (2026). Projects and the PBIR report format are standard in current versions. If Desktop is older than about mid 2025, turn on **File, Options and settings, Options, Preview features, Power BI Project (.pbip) save option** and **Store reports using enhanced metadata format (PBIR)**, then restart Desktop.
- The repo folder on the Windows machine. In Parallels the Mac home folder is usually shared as `\\Mac\Home`.

## Open it

1. In Windows, go to the repo's `powerbi` folder and double-click `SACountryBuses.pbip`, or in Desktop use **File, Open report, Browse reports** with the file type set to *Power BI project files (\*.pbip)*.
2. The visuals are empty the first time. Select **Refresh** on the Home ribbon.
   - By default the data is read from the repo's public copy on GitHub (`DataFolder` is `https://raw.githubusercontent.com/cjmuldoon/plotlay-sa-country-buses/main/data/`). If Desktop asks how to connect, choose **Anonymous** and then **Connect**.
   - To read the files from disk instead, go to **Home, Transform data, Edit parameters** and set `DataFolder` to the full path of the repo's `data` folder, **ending with a backslash** (for example `\\Mac\Home\plotlay-sa-country-buses\data`). Then select **OK** and **Apply changes**.
   - If Desktop warns about privacy levels, choose **Ignore privacy levels** (all the sources are public open data).
3. Check the numbers (below).

If the report was updated while open, close Power BI and reopen the .pbip rather than using Apply external changes.

## Check the numbers after Refresh

After **Refresh**, on **Towns** (as the report opens):

| Card | Should read |
|---|---|
| Towns with a bus on 4 days or fewer | 12 |
| Their residents | 21,380 |

On **The week**: share of residents with a bus on 4 days or fewer 8.8%, trips in the week 2,428.

## The model

- **Towns**: one row per town (`data/tables/towns.csv`): residents in 2021, the bus service class, trips in the week, days with a bus, trips on to Greater Adelaide, school trips left out, operators, latitude and longitude. Measures: `Towns counted`, `Residents`, `Trips in the week`, `Towns with a bus on 4 days or fewer`, `Residents with a bus on 4 days or fewer`, `Share of residents with a bus on 4 days or fewer`.
- **Days**: one row per day of the week (`days.csv`): the trips leaving the 52 towns. Measure: `Trips`.

## The map

- **Azure Maps** (page 1): every town by latitude and longitude, sized by residents and coloured by its bus service. If it asks, allow Azure Maps in **File, Options and settings, Options, Security**.

## Save a .pbix too

After the refresh, use **File, Save as** with the type **Power BI file (\*.pbix)** to save `powerbi\SACountryBuses.pbix`. It includes the data, so it opens without a refresh.

## Publish (only if you choose to)

Use **Home, Publish**. In the Power BI service, set the semantic model's **Data source credentials** for the GitHub address to **Anonymous**. Scheduled refresh then works with no gateway. **Publish to web** makes a public link, so only use it if you mean the report to be public.

## Shot list for the website and the video

| # | Shot | How | Length |
|---|---|---|---|
| 1 | Towns | As it opens | still |
| 2 | The week | As it opens | still |

Save page images into `powerbi/Screenshots/`.
