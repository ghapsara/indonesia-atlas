map: filter-map-by-province build-geo build-topo simplify-topo collect-bahasa-map clean
.PHONY: clean

filter-map-by-province:
	ndjson-filter 'd.properties.provinsi === "Nusa Tenggara Timur"' < ../data/ind-rev.ndjson > nusa-tenggara-timur.ndjson

build-geo:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < nusa-tenggara-timur.ndjson > nusa-tenggara-timur.json

build-topo:
	topojson nusa-tenggara-timur.json > nusa-tenggara-timur-topo.json -p

simplify-topo:
	mapshaper nusa-tenggara-timur-topo.json -simplify 3% -o format=topojson nusa-tenggara-timur-simplified-topo.json

collect-bahasa-map:
	cp nusa-tenggara-timur-simplified-topo.json ../All

clean:
	rm -rf nusa-tenggara-timur.ndjson nusa-tenggara-timur.json nusa-tenggara-timur-topo.json
