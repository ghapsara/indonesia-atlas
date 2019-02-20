map: filter-map-by-province build-geo build-topo simplify-topo collect-bahasa-map clean
.PHONY: clean

filter-map-by-province:
	ndjson-filter 'd.properties.provinsi === "Kepulauan Riau"' < ../data/ind-rev.ndjson > kepulauan-riau.ndjson

build-geo:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < kepulauan-riau.ndjson > kepulauan-riau.json

build-topo:
	topojson kepulauan-riau.json > kepulauan-riau-topo.json -p

simplify-topo:
	mapshaper kepulauan-riau-topo.json -simplify 3% -o format=topojson kepulauan-riau-simplified-topo.json

collect-bahasa-map:
	cp kepulauan-riau-simplified-topo.json ../All

clean:
	rm -rf kepulauan-riau.ndjson kepulauan-riau.json kepulauan-riau-topo.json
