# Indonesia Atlas

This repo contains TopoJSON files of Indonesia maps. TopoJSON can be used in a web using [topojson-client](https://github.com/topojson/topojson-client) libary. The maps size are reduced even smaller with [mapshaper](https://github.com/mbloch/mapshaper/) simplification utility. You should also notice that some of the islands are gone and complex line border are also simplified. If you want to change the reduction size, you cand edit the makefile located on every location folder then re-run their commands.
There are some corrections on the maps data, because some of the data from the original source are outdated and there are also typos.

## Data
| source | correction |
| ----------- | ---------- |
| [provinsi](http://www.diva-gis.org/gdata) | [Notebook](kabupaten-kota/Data/map_data_correction.ipynb)
| [kabupaten-kota](http://www.gispedia.com/2016/06/download-shp-indonesia-level-kota-kabupaten.html) | [Notebook](provinsi/Data/map_data_correction.ipynb)|

If you want to modify, you should download the data sources and extract the files into maps folder under Data folder.

## Files
| Maps | File |
| -------- | ---- |
| Indonesia |[File](provinsi/provinces-simplified-topo.json)|
| Aceh | [File](kabupaten-kota/Aceh/aceh-simplified-topo.json) |
| Bali | [File](kabupaten-kota/Bali/bali-simplified-topo.json) |
| Banten | [File](kabupaten-kota/Banten/banten-simplified-topo.json) |
| Bengkulu | [File](kabupaten-kota/Bengkulu/bengkulu-simplified-topo.json) |
| Gorontalo | [File](kabupaten-kota/Gorontalo/gorontalo-simplified-topo.json) |
| Jakarta | [File](kabupaten-kota/Jakarta/jakarta-simplified-topo.json) |
| Jambi | [File](kabupaten-kota/Jambi/jambi-simplified-topo.json) |
| Jawa Barat | [File](kabupaten-kota/Jawa&#32Barat/jawa-barat-simplified-topo.json) |
| Jawa Tengah | [File](kabupaten-kota/Jawa&#32Tengah/jawa-tengah-simplified-topo.json) |
| Jawa Timur | [File](kabupaten-kota/Jawa&#32Timur/jawa-timur-simplified-topo.json) |
| Kalimantan Barat | [File](kabupaten-kota/Kalimantan&#32Barat/kalimantan-barat-simplified-topo.json) |
| Kalimantan Selatan | [File](kabupaten-kota/Kalimantan&#32Selatan/kalimantan-selatan-simplified-topo.json) |
| Kalimantan Tengah | [File](kabupaten-kota/Kalimantan&#32Tengah/kalimantan-tengah-simplified-topo.json) |
| Kalimantan Timur | [File](kabupaten-kota/Kalimantan&#32Timur/kalimantan-timur-simplified-topo.json) |
| Kalimantan Utara | [File](kabupaten-kota/Kalimantan&#32Utara/kalimantan-utara-simplified-topo.json) |
| Kepulauan Bangka Belitung | [File](kabupaten-kota/Kepulauan&#32Bangka&#32Belitung/kepulauan-bangka-belitung-simplified-topo.json) |
| Kepulauan Riau | [File](kabupaten-kota/Kepulauan&#32Riau/kepulauan-riau-simplified-topo.json) |
| Lampung | [File](kabupaten-kota/Lampung/lampung-simplified-topo.json) |
| Maluku | [File](kabupaten-kota/Maluku/maluku-simplified-topo.json) |
| Maluku Utara | [File](kabupaten-kota/Maluku&#32Utara/maluku-utara-simplified-topo.json) |
| Nusa Tenggara Barat | [File](kabupaten-kota/Nusa&#32Tenggara&#32Barat/nusa-tenggara-barat-simplified-topo.json) |
| Nusa Tenggara Timur | [File](kabupaten-kota/Nusa&#32Tenggara&#32Timur/nusa-tenggara-timur-simplified-topo.json) |
| Papua | [File](kabupaten-kota/Papua/papua-simplified-topo.json) |
| Papua Barat | [File](kabupaten-kota/Papua&#32Barat/papua-barat-simplified-topo.json) |
| Riau | [File](kabupaten-kota/Riau/riau-simplified-topo.json) |
| Sulawesi Barat | [File](kabupaten-kota/Sulawesi&#32Barat/sulawesi-barat-simplified-topo.json) |
| Sulawesi Selatan | [File](kabupaten-kota/Sulawesi&#32Selatan/sulawesi-selatan-simplified-topo.json) |
| Sulawesi Tengah | [File](kabupaten-kota/Sulawesi&#32Tengah/sulawesi-tengah-simplified-topo.json) |
| Sulawesi Tenggara | [File](kabupaten-kota/Sulawesi&#32Tenggara/sulawesi-tenggara-simplified-topo.json) |
| Sulawesi Utara | [File](kabupaten-kota/Sulawesi&#32Utara/sulawesi-utara-simplified-topo.json) |
| Sumatera Barat | [File](kabupaten-kota/Sumatera&#32Barat/sumatera-barat-simplified-topo.json) |
| Sumatera Selatan | [File](kabupaten-kota/Sumatera&#32Selatan/sumatera-selatan-simplified-topo.json) |
| Sumatera Utara | [File](kabupaten-kota/Sumatera&#32Utara/sumatera-utara-simplified-topo.json) |
| Yogyakarta | [File](kabupaten-kota/Yogyakarta/yogyakarta-simplified-topo.json) |

Dont hesitate to submit an issue, if you find typos, error, and corrections. Thank You.
