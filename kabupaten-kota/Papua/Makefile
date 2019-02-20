map: filter-map-by-province build-geo build-topo simplify-topo collect-bahasa-map clean
.PHONY: clean

filter-map-by-province:
	ndjson-filter 'd.properties.provinsi === "Papua"' < ../data/ind-rev.ndjson > papua.ndjson

build-geo:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < papua.ndjson > papua.json

build-topo:
	topojson papua.json > papua-topo.json -p

simplify-topo:
	mapshaper papua-topo.json -simplify 3% -o format=topojson papua-simplified-topo.json

collect-bahasa-map:
	cp papua-simplified-topo.json ../All

clean:
	rm -rf papua.ndjson papua.json papua-topo.json
