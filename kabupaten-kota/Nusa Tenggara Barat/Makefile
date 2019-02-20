map: filter-map-by-province build-geo build-topo simplify-topo collect-bahasa-map clean
.PHONY: clean

filter-map-by-province:
	ndjson-filter 'd.properties.provinsi === "Nusa Tenggara Barat"' < ../data/ind-rev.ndjson > nusa-tenggara-barat.ndjson

build-geo:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < nusa-tenggara-barat.ndjson > nusa-tenggara-barat.json

build-topo:
	topojson nusa-tenggara-barat.json > nusa-tenggara-barat-topo.json -p

simplify-topo:
	mapshaper nusa-tenggara-barat-topo.json -simplify 3% -o format=topojson nusa-tenggara-barat-simplified-topo.json

collect-bahasa-map:
	cp nusa-tenggara-barat-simplified-topo.json ../All

clean:
	rm -rf nusa-tenggara-barat.ndjson nusa-tenggara-barat.json nusa-tenggara-barat-topo.json
