map: filter-map-by-province build-geo build-topo simplify-topo collect-bahasa-map clean
.PHONY: clean

filter-map-by-province:
	ndjson-filter 'd.properties.provinsi === "Jambi"' < ../data/ind-rev.ndjson > jambi.ndjson

build-geo:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < jambi.ndjson > jambi.json

build-topo:
	topojson jambi.json > jambi-topo.json -p

simplify-topo:
	mapshaper jambi-topo.json -simplify 3% -o format=topojson jambi-simplified-topo.json

collect-bahasa-map:
	cp jambi-simplified-topo.json ../All

clean:
	rm -rf jambi.ndjson jambi.json jambi-topo.json
