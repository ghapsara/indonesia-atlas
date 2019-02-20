map: filter-map-by-province build-geo build-topo simplify-topo collect-bahasa-map clean
.PHONY: clean

filter-map-by-province:
	ndjson-filter 'd.properties.provinsi === "Riau"' < ../data/ind-rev.ndjson > riau.ndjson

build-geo:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < riau.ndjson > riau.json

build-topo:
	topojson riau.json > riau-topo.json -p

simplify-topo:
	mapshaper riau-topo.json -simplify 3% -o format=topojson riau-simplified-topo.json

collect-bahasa-map:
	cp riau-simplified-topo.json ../All

clean:
	rm -rf riau.ndjson riau.json riau-topo.json
