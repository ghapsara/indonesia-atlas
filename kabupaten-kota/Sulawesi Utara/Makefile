map: filter-map-by-province build-geo build-topo simplify-topo collect-bahasa-map clean
.PHONY: clean

filter-map-by-province:
	ndjson-filter 'd.properties.provinsi === "Sulawesi Utara"' < ../data/ind-rev.ndjson > sulawesi-utara.ndjson

build-geo:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < sulawesi-utara.ndjson > sulawesi-utara.json

build-topo:
	topojson sulawesi-utara.json > sulawesi-utara-topo.json -p

simplify-topo:
	mapshaper sulawesi-utara-topo.json -simplify 3% -o format=topojson sulawesi-utara-simplified-topo.json

collect-bahasa-map:
	cp sulawesi-utara-simplified-topo.json ../All

clean:
	rm -rf sulawesi-utara.ndjson sulawesi-utara.json sulawesi-utara-topo.json
