map: filter-map-by-province build-geo build-topo simplify-topo collect-bahasa-map clean
.PHONY: clean

filter-map-by-province:
	ndjson-filter 'd.properties.provinsi === "Bengkulu"' < ../data/ind-rev.ndjson > bengkulu.ndjson

build-geo:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < bengkulu.ndjson > bengkulu.json

build-topo:
	topojson bengkulu.json > bengkulu-topo.json -p

simplify-topo:
	mapshaper bengkulu-topo.json -simplify 3% -o format=topojson bengkulu-simplified-topo.json

collect-bahasa-map:
	cp bengkulu-simplified-topo.json ../All

clean:
	rm -rf bengkulu.ndjson bengkulu.json bengkulu-topo.json
