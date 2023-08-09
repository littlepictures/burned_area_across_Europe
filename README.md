# little picture - little picture - global mean sea level

## Background on this little picture
_burned area across Europe 2001-2020 – a streamgraph_

Monitoring wildfires from space is crucial for understanding their impact on climate, including the release of greenhouse gases &amp; aerosols that
influence the Earth system. This data driven Little Picture illustrates satellite Burned Area data for European countries between 2001-2020. Each country has its own
stream. The width of each stream represents the burned area for that year.

https://climate.esa.int/en/little-pictures-gallery/Burned-area-across-Europe/


## Data Sources

The CLIP uses the following datasets:

- [ESA Fire CCI: MODIS Fire_cci Burned Area Pixel product, version 5.1](https://catalogue.ceda.ac.uk/uuid/58f00d8814064b79a0c49662ad3af537), 
  Cate dataset identifier: `esacci.FIRE.mon.L4.BA.MODIS.Terra.MODIS_TERRA.v5-1.grid`.
- [cate.ds.data.countries/countries-110m.geojson](https://github.com/CCI-Tools/cate/blob/master/cate/ds/data/countries/countries-110m.geojson) 
  country polygons provided as public domain from [Natural Earth](https://www.naturalearthdata.com/).

## Data Preparation
### Description

Data preparation comprises the following steps:

* Opening the Fire CCI dataset `esacci.FIRE.mon.L4.BA.MODIS.Terra.MODIS_TERRA.v5-1.grid`.
* Opening the countries GeoJSON dataset `cate.ds.data.countries/countries-110m.geojson` 
* Select European countries Features from countries dataset.
* Use European countries to spatially subset the Fire dataset.
* Generate annual sums of burned areas of the Fire dataset.
* Group the annual Fire dataset by country codes.
* Generate the sums of burned areas for each country.
* Put burned area sums in a data frame and save a CSV files 
  `data/ba-europe-countries.csv` and the cumulative sums in 
  `data/ba-europe-countries-cumsums.csv`. The units are square meters.

### One-time script setup

If you do not have a Cate account yet, please visit [Cate App](https://cate.climate.esa.int/), select **Cate Cloud Service** and register. 
Using the Cate credentials, login to the [Cate JupyterLab](https://cate-lab.brockmann-consult.de/). 
From the JupyterLab's **Launcher**, open a **Terminal** window and type

```bash
cd ~/work
git clone https://github.com/littlepictures/pytrevalabs.git
git clone https://github.com/littlepictures/clip_05_burning_lands.git
```

Note you can also use the JupyterLab's **Git** extension (left side bar) to clone the repos.

### Running the script

In JupyterLab's **File Browser** navigate to `/clip_05_burning_lands/scripts/dataprep` and open
the Notebook [extract-burned-areas.ipynb](scripts/dataprep/extract-burned-areas.ipynb) and run it.

To stay in sync with the repos, open a **Terminal** window and

```bash
cd ~/work/pytrevalabs
git pull --rebase
cd ~/work/clip_05_burning_lands
git pull --rebase
```

Note you can also use the JupyterLab's **Git** extension (left side bar) to update the repos.

## Data Visualization
- The data is loaded from a CSV file, 'ba-europe-countries.csv', into a pandas DataFrame.
- The DataFrame is then preprocessed by "melting" it, transforming it from a wide format to a long format. This is done to make the data suitable for creating a streamgraph.
- Further, certain countries (Europe, Ukraine, and Belarus) are filtered out from the DataFrame.

- The processed data is visualized using Altair, a declarative statistical visualization library for Python.
- A color scale is defined for all the countries included in the analysis.
- The streamgraph is created, where the x-axis represents the burned area, the y-axis represents the years, and the color represents the different countries.
- The streamgraph is then configured and displayed, showing the trend of burned areas in various European countries over the years.
- A Bauhaus-style poster is created by adding title, logo, and detail texts to the streamgraph. The poster is then configured and displayed.


## CREDITS & LICENSE
- Idea by: [ESA Climate Office](https://climate.esa.int/)
- Processing Scripts by: [Brockmann Consult](https://www.brockmann-consult.de/)
- Visualization by: [Ubilabs](https://www.ubilabs.com/)

The code in this repository is published under [CC BY-SA 4.0 license](https://creativecommons.org/licenses/by-sa/4.0/)
