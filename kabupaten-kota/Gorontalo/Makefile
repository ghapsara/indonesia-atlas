map: filter-map-by-province build-geo build-topo simplify-topo collect-bahasa-map clean
.PHONY: clean

filter-map-by-province:
	ndjson-filter 'd.properties.provinsi === "Gorontalo"' < ../data/ind-rev.ndjson > gorontalo.ndjson

build-geo:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < gorontalo.ndjson > gorontalo.json

build-topo:
	topojson gorontalo.json > gorontalo-topo.json -p

simplify-topo:
	mapshaper gorontalo-topo.json -simplify 3% -o format=topojson gorontalo-simplified-topo.json

collect-bahasa-map:
	cp gorontalo-simplified-topo.json ../All

clean:
	rm -rf gorontalo.ndjson gorontalo.json gorontalo-topo.json
