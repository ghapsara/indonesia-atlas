map: filter-map-by-province build-geo build-topo simplify-topo collect-bahasa-map clean
.PHONY: clean

filter-map-by-province:
	ndjson-filter 'd.properties.provinsi === "Yogyakarta"' < ../data/ind-rev.ndjson > yogyakarta.ndjson

build-geo:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < yogyakarta.ndjson > yogyakarta.json

build-topo:
	topojson yogyakarta.json > yogyakarta-topo.json -p

simplify-topo:
	mapshaper yogyakarta-topo.json -simplify 3% -o format=topojson yogyakarta-simplified-topo.json

collect-bahasa-map:
	cp yogyakarta-simplified-topo.json ../All

clean:
	rm -rf yogyakarta.ndjson yogyakarta.json yogyakarta-topo.json
