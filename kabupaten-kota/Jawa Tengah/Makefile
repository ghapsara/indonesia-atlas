map: filter-map-by-province build-geo build-topo simplify-topo collect-bahasa-map clean
.PHONY: clean

filter-map-by-province:
	ndjson-filter 'd.properties.provinsi === "Jawa Tengah"' < ../data/ind-rev.ndjson > jawa-tengah.ndjson

build-geo:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < jawa-tengah.ndjson > jawa-tengah.json

build-topo:
	topojson jawa-tengah.json > jawa-tengah-topo.json -p

simplify-topo:
	mapshaper jawa-tengah-topo.json -simplify 3% -o format=topojson jawa-tengah-simplified-topo.json

collect-bahasa-map:
	cp jawa-tengah-simplified-topo.json ../All

clean:
	rm -rf jawa-tengah.ndjson jawa-tengah.json jawa-tengah-topo.json
