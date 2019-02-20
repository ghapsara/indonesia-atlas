map: filter-map-by-province build-geo build-topo simplify-topo collect-bahasa-map clean
.PHONY: clean

filter-map-by-province:
	ndjson-filter 'd.properties.provinsi === "Lampung"' < ../data/ind-rev.ndjson > lampung.ndjson

build-geo:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < lampung.ndjson > lampung.json

build-topo:
	topojson lampung.json > lampung-topo.json -p

simplify-topo:
	mapshaper lampung-topo.json -simplify 3% -o format=topojson lampung-simplified-topo.json

collect-bahasa-map:
	cp lampung-simplified-topo.json ../All

clean:
	rm -rf lampung.ndjson lampung.json lampung-topo.json
