# UAS-SIG-Emhaka-Heatmap
Nama: Emhaka, NIM: 2003040092

Link tutorial: https://www.youtube.com/watch?v=JoQhEKh7u0c&t=857s&ab_channel=GeospatialProgramming

1. Yang pertama dilakukan yaitu mengimport warnings dan pandas:
```bash
import warnings
warnings.filterwarnings('ignore')
```
```bash
import pandas as pd
```

2. Upload dataset:
Data diambil dari kagle: https://www.kaggle.com/datasets/hendratno/covid19-indonesia
```bash
df = pd.read_csv("/content/covid_19_indonesia_time_series_all.csv", encoding="ISO-8859-1")
df.head(2)
```

3. Import math dan folium:
math untuk memfilter daftar pasangan koordinat latitude dan longitude untuk membuat heatmap:

```bash
import math

coord_list = [(lat, lon) for lat, lon in zip(df.Latitude, df.Longitude) if not math.isnan(lat) and not math.isnan(lon)]
```

membuat peta heatmap:
```bash
import folium
from folium import plugins

m = folium.Map(location=(15, 30), tiles="Cartodb dark_matter", zoom_start=2)
plugins.HeatMap(coord_list, radius=20).add_to(m)
m
```



 
