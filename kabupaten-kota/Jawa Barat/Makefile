map: filter-map-by-province build-geo build-topo simplify-topo collect-bahasa-map clean
.PHONY: clean

filter-map-by-province:
	ndjson-filter 'd.properties.provinsi === "Jawa Barat"' < ../data/ind-rev.ndjson > jawa-barat.ndjson

build-geo:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < jawa-barat.ndjson > jawa-barat.json

build-topo:
	topojson jawa-barat.json > jawa-barat-topo.json -p

simplify-topo:
	mapshaper jawa-barat-topo.json -simplify 3% -o format=topojson jawa-barat-simplified-topo.json

collect-bahasa-map:
	cp jawa-barat-simplified-topo.json ../All

clean:
	rm -rf jawa-barat.ndjson jawa-barat.json jawa-barat-topo.json
