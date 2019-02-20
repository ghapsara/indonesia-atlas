map: filter-map-by-province build-geo build-topo simplify-topo collect-bahasa-map clean
.PHONY: clean

filter-map-by-province:
	ndjson-filter 'd.properties.provinsi === "Banten"' < ../data/ind-rev.ndjson > banten.ndjson

build-geo:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < banten.ndjson > banten.json

build-topo:
	topojson banten.json > banten-topo.json -p

simplify-topo:
	mapshaper banten-topo.json -simplify 3% -o format=topojson banten-simplified-topo.json

collect-bahasa-map:
	cp banten-simplified-topo.json ../All

clean:
	rm -rf banten.ndjson banten.json banten-topo.json
