# BeNomad-SmartChargingProvider on Islanding situation ( Microgrid )

The source of BeNomad-SmartChargingProvider on Islanding situation ( Microgrid ) web API, http://osm.procan-group.com/PvPanel

This API defines only two operations. For now, these operations  consume parameters in POST request and produce XML in GET as described below. In the next release, the operations will also be able to consume or produce RDF, in conformance with the SEAS knowledge model. SPARQL-Generate protocol will be used to describe how RDF may be generated from XML.

+ `POST`:
`curl -X POST -d "ts={ts}&device_id={device_id}&production={production}" http://osm.procan-group.com/PvPanel/rest/pvs` :  the {ts} parameter represent the timestamp of the pv production,the {device_id} parameter represent the id of the pvpanel,the {production} parameter represent the energy production value. Then the server returns a 202 Accepted.

+ `GET`:
`curl -X GET http://osm.procan-group.com/PvPanel/rest/pvs/{device_id}` :the {device_id} parameter represent the id of the pvpanel. Then if the server returns a 200 OK, the HTTP body represents the response PV Panel production  (see below)

```
     <PvPanel>
          <Device>
		<ts>1458001200</ts>
		<DeviceId>00031614</DeviceId>
		<Production>1916.85</Production>
	   </Device>
      <PvPanel>
```


`curl -X GET http://osm.procan-group.com/PvPanel/rest/pvs/` : if the server returns a 200 OK, the HTTP body represents the response all PV Panel production  (see below)

```
<PvPanel>
	<Device>
		<ts>1458001200</ts>
		<DeviceId>00031614</DeviceId>
		<Production>1916.85</Production>
	</Device>
	<Device>
		<ts>1458001800</ts>
		<DeviceId>00031614</DeviceId>
		<Production>2570.83</Production>
	</Device>
	<Device>
		<ts>1458002400</ts>
		<DeviceId>00031614</DeviceId>
		<Production>3196.07</Production>
	</Device>
	<Device>
		<ts>1458003000</ts>
		<DeviceId>00031614</DeviceId>
		<Production>3761.39</Production>
	</Device>
	<Device>
	<ts>1458003600</ts>
		<DeviceId>00031614</DeviceId>
		<Production>4300.34</Production>
	</Device>
</PvPanel>
```

