map: filter-map-by-province build-geo build-topo simplify-topo collect-bahasa-map clean
.PHONY: clean

filter-map-by-province:
	ndjson-filter 'd.properties.provinsi === "Kalimantan Selatan"' < ../data/ind-rev.ndjson > kalimantan-selatan.ndjson

build-geo:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < kalimantan-selatan.ndjson > kalimantan-selatan.json

build-topo:
	topojson kalimantan-selatan.json > kalimantan-selatan-topo.json -p

simplify-topo:
	mapshaper kalimantan-selatan-topo.json -simplify 3% -o format=topojson kalimantan-selatan-simplified-topo.json

collect-bahasa-map:
	cp kalimantan-selatan-simplified-topo.json ../All

clean:
	rm -rf kalimantan-selatan.ndjson kalimantan-selatan.json kalimantan-selatan-topo.json
