map: filter-map-by-province build-geo build-topo simplify-topo collect-bahasa-map clean
.PHONY: clean

filter-map-by-province:
	ndjson-filter 'd.properties.provinsi === "Sumatera Selatan"' < ../data/ind-rev.ndjson > sumatera-selatan.ndjson

build-geo:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < sumatera-selatan.ndjson > sumatera-selatan.json

build-topo:
	topojson sumatera-selatan.json > sumatera-selatan-topo.json -p

simplify-topo:
	mapshaper sumatera-selatan-topo.json -simplify 3% -o format=topojson sumatera-selatan-simplified-topo.json

collect-bahasa-map:
	cp sumatera-selatan-simplified-topo.json ../All

clean:
	rm -rf sumatera-selatan.ndjson sumatera-selatan.json sumatera-selatan-topo.json
