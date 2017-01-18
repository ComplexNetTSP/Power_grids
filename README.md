# Power grids datasets

## Origin of the data

The power grid topologies listed in the present repository were obtained from the crowdsourcing project OpenStreetMap (OSM) (https://www.openstreetmap.org). These data are fed in by users of the app and may be incomplete or even wrong. For this reason, topologies presented here should not be considered as exact representations of the real topologies, but rather as approximations. Results clearly depends on the data entered by the users. 

There is a large gap between OSM data and a graphical representation of the power grid. Please refer to the SCIGRID project (http://scigrid.de [1]) for more information.

[1] C. Matke, W. Medjroubi, D. Kleinhans, SciGRID - An Open Source Model of the European Power Transmission Network. Mathematics and Physics of Multilayer Complex Networks, 2015.

## Architecture

There are two folders that contains the CSV data :

- *Countries*
- *Continents*

As their names suggest, *Countries* contains the data for different countries and *Continents* the data for different continents. The architecture is the same for both folders. For each country/continent, there are 4 subfolders :

- *Nodes* : contains the raw nodes data
- *Edges* : contains the raw edges data
- *graphml* : contains the graphs in graphml format
- *PNG* : contains images of the graphs (Blue nodes : stations, red nodes : generators, white nodes : joints)

In the folders Nodes and Edges there are two kinds of files :

- Highvoltage CSV file : contains raw data of the highvoltage network.
- Heuristic CSV file : contains raw data of the whole networks. As its name suggests, these data come from heuristic algorithms that try to make sense out of incomplete OpenStreetMap data. The networks obtained should therefore be treated as approximations of the true networks.

Therefore, there are two kinds of graphs in the *graphml* and *PNG* folders : highvoltage networks and heuristic networks.

## Nodes CSV file format

Each row contains information relative to a single node. Fields are separated by the character '#'. The fields are the following :

- *v_id*: Node identifier (type: integer)
- *lon*: Node longitude (type: float)
- *lat*: Node latitude (type: float)
- *typ*: Node type (type: string) (example:'generator', 'substation'...)
- *voltage*: Node voltage level (type: integer)
- *frequency*: Node frequency (type: float)
- *name*: Node name (type: string) (example: Name of the power plant). These data are mostly recorded in the language of the country.
- *operator*: Operator responsible for the given node (type: string)
- *source*: For generators only. Power source used by the generator (type: string) (example: 'biofuel', 'coal', 'solar'...)
- *n_gen*: For aggregated generators only. Number of generators that were aggregated (type: integer)
- *capacity*: For aggregated generators, list of aggregated generator capacities (type: List[float])
- *Net_capacity*: Capacity of the generator or the aggregated generators (in this case, it is the sum of the capacities in the previous field) (type: float)
- *wkt_srid_4326*: Well known text for the object geometry (type: string) 

Note that, except for the identifier, longitude, latitude, type, and wkt_srid_4326 fields, most entries contain very sparse information on the other fields.

## Edges CSV file format

Each row contains information relative to a single electrical line. Fields are separated by the character '#'. The fields are the following :

- *l_id*: Line identifier (type: integer)
- *v_id_1*: End node 1 identifier (type: integer)
- *v_id_2*: End node 2 identifier (type: integer)
- *voltage*: Line voltage level (type: integer)
- *cables*: Number of cables for the line (type: integer)
- *wires*: Number of wires (type: integer)
- *frequency*: Line frequency (type: float)
- *name*: Line name (type: string)
- *operator*: Name of the line operator (type: string)
- *length_m*: Line length in meters (type: float)
- *r_ohmkm*: Resistance of the line (type: float)
- *x_ohmkm*: Reactance of the line (type: float)
- *c_nfkm*: Capacitance of the line (type: float)
- *i_th_max_a*: Maximum current thermal limit (type: float)
- *from_relation*: Relation the line was obtained from
- *wkt_srid_4326*: Well known text for the object geometry (type: string) 
- *type*: Geometry type (typr: string)

Note that, except for the identifiers and wkt_srid_4326 fields, most entries contain very sparse information on the other fields.


## Loading the data in a graph

There are two main ways for building a graph. Both methods are explained in details in the Ipython Notebook *Loading the data, an example.ipynb*. 

The easiest way consists in using the graphml files directly :

```python
import networkx as nx
nx.read_graphml('path_to_graphml_file')
```

The harder way consists in loading nodes and edges data from the CSV files. Please refer to the Ipython Notebook mentioned above for more information.

