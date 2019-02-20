map: filter-map-by-province build-geo build-topo simplify-topo collect-bahasa-map clean
.PHONY: clean

filter-map-by-province:
	ndjson-filter 'd.properties.provinsi === "Papua Barat"' < ../data/ind-rev.ndjson > papua-barat.ndjson

build-geo:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < papua-barat.ndjson > papua-barat.json

build-topo:
	topojson papua-barat.json > papua-barat-topo.json -p

simplify-topo:
	mapshaper papua-barat-topo.json -simplify 3% -o format=topojson papua-barat-simplified-topo.json

collect-bahasa-map:
	cp papua-barat-simplified-topo.json ../All

clean:
	rm -rf papua-barat.ndjson papua-barat.json papua-barat-topo.json
