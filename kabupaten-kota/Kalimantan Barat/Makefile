map: filter-map-by-province build-geo build-topo simplify-topo collect-bahasa-map clean
.PHONY: clean

filter-map-by-province:
	ndjson-filter 'd.properties.provinsi === "Kalimantan Barat"' < ../data/ind-rev.ndjson > kalimantan-barat.ndjson

build-geo:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < kalimantan-barat.ndjson > kalimantan-barat.json

build-topo:
	topojson kalimantan-barat.json > kalimantan-barat-topo.json -p

simplify-topo:
	mapshaper kalimantan-barat-topo.json -simplify 3% -o format=topojson kalimantan-barat-simplified-topo.json

collect-bahasa-map:
	cp kalimantan-barat-simplified-topo.json ../All

clean:
	rm -rf kalimantan-barat.ndjson kalimantan-barat.json kalimantan-barat-topo.json
