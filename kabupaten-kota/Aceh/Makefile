map: filter-map-by-province build-geo build-topo simplify-topo collect-bahasa-map clean
.PHONY: clean

filter-map-by-province:
	ndjson-filter 'd.properties.provinsi === "Aceh"' < ../data/ind-rev.ndjson > aceh.ndjson

build-geo:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < aceh.ndjson > aceh.json

build-topo:
	topojson aceh.json > aceh-topo.json -p

simplify-topo:
	mapshaper aceh-topo.json -simplify 3% -o format=topojson aceh-simplified-topo.json

collect-bahasa-map:
	cp aceh-simplified-topo.json ../All

clean:
	rm -rf aceh.ndjson aceh.json aceh-topo.json
