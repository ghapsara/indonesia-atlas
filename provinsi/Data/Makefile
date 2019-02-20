step-1: build-geojson build-ndjson add-id generate-data-ndjson generate-data-json

step-2: build-ind-data-rev-ndjson join-with-data-rev apply-new-properties remove-id rebuild-geojson build-topojson simplify-topojson

.PHONY: clean

build-geojson:
	shp2json ./maps/IDN_adm1.shp -o ind-prov.json

build-ndjson:
	ndjson-split 'd.features' < ind-prov.json > ind-prov.ndjson

add-id:
	ndjson-map 'd.id = d.properties.NAME_1, d' < ind-prov.ndjson > ind-id.ndjson

generate-data-ndjson:
	ndjson-map 'd = {id: d.id, provinsi: d.id}, d' < ind-id.ndjson > ind-data.ndjson

generate-data-json:
	ndjson-reduce 'p.push(d), p' '[]' < ind-data.ndjson > ind-data.json

build-ind-data-rev-ndjson:
	ndjson-split 'd' < ind-data-prov-rev.json > ind-data-prov.ndjson

join-with-data-rev:
	ndjson-join 'd.id' ind-id.ndjson ind-data-prov.ndjson > ind-join.ndjson

apply-new-properties:
	ndjson-map 'd[0].properties = {provinsi: d[1].provinsi}, d[0]' < ind-join.ndjson > ind-new-prop.ndjson

remove-id:
	ndjson-map 'delete d.id, d' < ind-new-prop.ndjson > ind-map.ndjson

rebuild-geojson:
	ndjson-reduce 'p.features.push(d), p' '{type: "FeatureCollection", features: []}' < ind-map.ndjson > provinces.json

build-topojson:
	topojson provinces.json > provinces-topo.json -p

simplify-topojson:
	mapshaper provinces-topo.json -simplify 3% -o format=topojson ../provinces-simplified-topo.json

clean:
	rm -rf ind-prov.json ind-prov.ndjson ind-id.ndjson ind-data.ndjson ind-data.json ind-data-prov.ndjson ind-join.ndjson ind-new-prop.ndjson ind-map.ndjson provinces.json provinces-topo.json
