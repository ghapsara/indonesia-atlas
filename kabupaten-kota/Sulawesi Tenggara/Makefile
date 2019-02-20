map: filter-map-by-province build-geo build-topo simplify-topo collect-bahasa-map clean
.PHONY: clean

filter-map-by-province:
	ndjson-filter 'd.properties.provinsi === "Sulawesi Tenggara"' < ../data/ind-rev.ndjson > sulawesi-tenggara.ndjson

build-geo:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < sulawesi-tenggara.ndjson > sulawesi-tenggara.json

build-topo:
	topojson sulawesi-tenggara.json > sulawesi-tenggara-topo.json -p

simplify-topo:
	mapshaper sulawesi-tenggara-topo.json -simplify 3% -o format=topojson sulawesi-tenggara-simplified-topo.json

collect-bahasa-map:
	cp sulawesi-tenggara-simplified-topo.json ../All

clean:
	rm -rf sulawesi-tenggara.ndjson sulawesi-tenggara.json sulawesi-tenggara-topo.json
