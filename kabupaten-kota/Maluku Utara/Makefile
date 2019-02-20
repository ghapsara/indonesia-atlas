map: filter-map-by-province build-geo build-topo simplify-topo collect-bahasa-map clean
.PHONY: clean

filter-map-by-province:
	ndjson-filter 'd.properties.provinsi === "Maluku Utara"' < ../data/ind-rev.ndjson > maluku-utara.ndjson

build-geo:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < maluku-utara.ndjson > maluku-utara.json

build-topo:
	topojson maluku-utara.json > maluku-utara-topo.json -p

simplify-topo:
	mapshaper maluku-utara-topo.json -simplify 3% -o format=topojson maluku-utara-simplified-topo.json

collect-bahasa-map:
	cp maluku-utara-simplified-topo.json ../All

clean:
	rm -rf maluku-utara.ndjson maluku-utara.json maluku-utara-topo.json
