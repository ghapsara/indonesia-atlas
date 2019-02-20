map: filter-map-by-province build-geo build-topo simplify-topo collect-bahasa-map clean
.PHONY: clean

filter-map-by-province:
	ndjson-filter 'd.properties.provinsi === "Kepulauan Bangka Belitung"' < ../data/ind-rev.ndjson > kepulauan-bangka-belitung.ndjson

build-geo:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < kepulauan-bangka-belitung.ndjson > kepulauan-bangka-belitung.json

build-topo:
	topojson kepulauan-bangka-belitung.json > kepulauan-bangka-belitung-topo.json -p

simplify-topo:
	mapshaper kepulauan-bangka-belitung-topo.json -simplify 3% -o format=topojson kepulauan-bangka-belitung-simplified-topo.json

collect-bahasa-map:
	cp kepulauan-bangka-belitung-simplified-topo.json ../All

clean:
	rm -rf kepulauan-bangka-belitung.ndjson kepulauan-bangka-belitung.json kepulauan-bangka-belitung-topo.json
