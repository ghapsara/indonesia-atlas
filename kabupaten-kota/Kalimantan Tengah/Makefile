map: filter-map-by-province build-geo build-topo simplify-topo collect-bahasa-map clean
.PHONY: clean

filter-map-by-province:
	ndjson-filter 'd.properties.provinsi === "Kalimantan Tengah"' < ../data/ind-rev.ndjson > kalimantan-tengah.ndjson

build-geo:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < kalimantan-tengah.ndjson > kalimantan-tengah.json

build-topo:
	topojson kalimantan-tengah.json > kalimantan-tengah-topo.json -p

simplify-topo:
	mapshaper kalimantan-tengah-topo.json -simplify 3% -o format=topojson kalimantan-tengah-simplified-topo.json

collect-bahasa-map:
	cp kalimantan-tengah-simplified-topo.json ../All

clean:
	rm -rf kalimantan-tengah.ndjson kalimantan-tengah.json kalimantan-tengah-topo.json
