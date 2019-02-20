map: filter-map-by-province build-geo build-topo simplify-topo collect-bahasa-map clean
.PHONY: clean

filter-map-by-province:
	ndjson-filter 'd.properties.provinsi === "Kalimantan Utara"' < ../data/ind-rev.ndjson > kalimantan-utara.ndjson

build-geo:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < kalimantan-utara.ndjson > kalimantan-utara.json

build-topo:
	topojson kalimantan-utara.json > kalimantan-utara-topo.json -p

simplify-topo:
	mapshaper kalimantan-utara-topo.json -simplify 3% -o format=topojson kalimantan-utara-simplified-topo.json

collect-bahasa-map:
	cp kalimantan-utara-simplified-topo.json ../All

clean:
	rm -rf kalimantan-utara.ndjson kalimantan-utara.json kalimantan-utara-topo.json
