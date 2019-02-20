map: filter-map-by-province build-geo build-topo simplify-topo collect-bahasa-map clean
.PHONY: clean

filter-map-by-province:
	ndjson-filter 'd.properties.provinsi === "Sulawesi Selatan"' < ../data/ind-rev.ndjson > sulawesi-selatan.ndjson

build-geo:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < sulawesi-selatan.ndjson > sulawesi-selatan.json

build-topo:
	topojson sulawesi-selatan.json > sulawesi-selatan-topo.json -p

simplify-topo:
	mapshaper sulawesi-selatan-topo.json -simplify 3% -o format=topojson sulawesi-selatan-simplified-topo.json

collect-bahasa-map:
	cp sulawesi-selatan-simplified-topo.json ../All

clean:
	rm -rf sulawesi-selatan.ndjson sulawesi-selatan.json sulawesi-selatan-topo.json
