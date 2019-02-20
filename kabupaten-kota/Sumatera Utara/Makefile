map: filter-map-by-province build-geo build-topo simplify-topo collect-bahasa-map clean
.PHONY: clean

filter-map-by-province:
	ndjson-filter 'd.properties.provinsi === "Sumatera Utara"' < ../data/ind-rev.ndjson > sumatera-utara.ndjson

build-geo:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < sumatera-utara.ndjson > sumatera-utara.json

build-topo:
	topojson sumatera-utara.json > sumatera-utara-topo.json -p

simplify-topo:
	mapshaper sumatera-utara-topo.json -simplify 3% -o format=topojson sumatera-utara-simplified-topo.json

collect-bahasa-map:
	cp sumatera-utara-simplified-topo.json ../All

clean:
	rm -rf sumatera-utara.ndjson sumatera-utara.json sumatera-utara-topo.json
