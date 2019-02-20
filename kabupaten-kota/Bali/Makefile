map: filter-map-by-province build-geo build-topo simplify-topo collect-bahasa-map clean
.PHONY: clean

filter-map-by-province:
	ndjson-filter 'd.properties.provinsi === "Bali"' < ../data/ind-rev.ndjson > bali.ndjson

build-geo:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < bali.ndjson > bali.json

build-topo:
	topojson bali.json > bali-topo.json -p

simplify-topo:
	mapshaper bali-topo.json -simplify 3% -o format=topojson bali-simplified-topo.json

collect-bahasa-map:
	cp bali-simplified-topo.json ../All

clean:
	rm -rf bali.ndjson bali.json bali-topo.json
