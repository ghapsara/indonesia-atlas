map: filter-map-by-province build-geo build-topo simplify-topo collect-bahasa-map clean
.PHONY: clean

filter-map-by-province:
	ndjson-filter 'd.properties.provinsi === "Maluku"' < ../data/ind-rev.ndjson > maluku.ndjson

build-geo:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < maluku.ndjson > maluku.json

build-topo:
	topojson maluku.json > maluku-topo.json -p

simplify-topo:
	mapshaper maluku-topo.json -simplify 3% -o format=topojson maluku-simplified-topo.json

collect-bahasa-map:
	cp maluku-simplified-topo.json ../All

clean:
	rm -rf maluku.ndjson maluku.json maluku-topo.json
