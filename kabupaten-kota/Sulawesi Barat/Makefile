map: filter-map-by-province build-geo build-topo simplify-topo collect-bahasa-map clean
.PHONY: clean

filter-map-by-province:
	ndjson-filter 'd.properties.provinsi === "Sulawesi Barat"' < ../data/ind-rev.ndjson > sulawesi-barat.ndjson

build-geo:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < sulawesi-barat.ndjson > sulawesi-barat.json

build-topo:
	topojson sulawesi-barat.json > sulawesi-barat-topo.json -p

simplify-topo:
	mapshaper sulawesi-barat-topo.json -simplify 3% -o format=topojson sulawesi-barat-simplified-topo.json

collect-bahasa-map:
	cp sulawesi-barat-simplified-topo.json ../All

clean:
	rm -rf sulawesi-barat.ndjson sulawesi-barat.json sulawesi-barat-topo.json
