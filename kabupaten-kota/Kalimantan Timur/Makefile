map: filter-map-by-province build-geo build-topo simplify-topo collect-bahasa-map clean
.PHONY: clean

filter-map-by-province:
	ndjson-filter 'd.properties.provinsi === "Kalimantan Timur"' < ../data/ind-rev.ndjson > kalimantan-timur.ndjson

build-geo:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < kalimantan-timur.ndjson > kalimantan-timur.json

build-topo:
	topojson kalimantan-timur.json > kalimantan-timur-topo.json -p

simplify-topo:
	mapshaper kalimantan-timur-topo.json -simplify 3% -o format=topojson kalimantan-timur-simplified-topo.json

collect-bahasa-map:
	cp kalimantan-timur-simplified-topo.json ../All

clean:
	rm -rf kalimantan-timur.ndjson kalimantan-timur.json kalimantan-timur-topo.json
