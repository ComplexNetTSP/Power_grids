# Power_grids
Topologies of power networks

## Architecture

There are two folders that contains the CSV data :

- Countries
- Continents

As their names suggest, Countries contains the data for different countries and Continents the data for different continents. The architecture is the same for both folders. For each country/continent, their are 4 subfolders :

- Nodes : contains the raw nodes data
- Edges : contains the raw edges data
- gml : contains the graphs in gml format
- PNG : contains images of the graphs (Blue nodes : stations, red nodes : generators, white nodes : joints)

In the folders Nodes and Edges there are two kinds of files :

- Highvoltage CSV file : contains raw data of the highvoltage network. This does NOT contain information on generators
- Heuristic CSV file : contains raw data of the whole networks. This contains information on generators. Be carefull, as it name suggests, these data come from heuristic algorithms that tries to make sense out of incomplete Openstreet data. The networks obtain should therefore be treated as approximation of the true networks.

Therefore, there are two kinds of graphs in the gml and PNG folders : highvoltage networks and Heuristic networks.

## Nodes CSV file format

### Highvoltage files

### Heuristic files

Each row contains information relative to a single node. Fields are separated by the character '#'. The fields are the following :

- "v_id": Node identifier (type: integer)
- "lon": Node longitude (type: float)
- "lat": Node latitude (type: float)
- "typ": Node type (type: string) (example:'generator', 'substation'...)
- "voltage": Node voltage level (type: integer)
- "frequency": Node frequency (type: float)
- "name": Node name (type: string) (example: Name of the power plant). These data are mostly recorded in the language of the country.
- "operator": Operator responsible for the given node (type: string)
- "ref":
- "source": For generators only. Power source used by the generator (type: string) (example: 'biofuel', 'coal', 'solar'...)
- "n_gen": For aggregated generators only. Number of generators that were aggregated (type: integer)
- "capacity": For aggregated generators, list of aggregated generator capacities (type: List[float])
- "Net_capacity": Capacity of the generator or the aggregated generators (in this case, it is the sum of the capacities in the previous field) (type: float)
- "wkt_srid_4326": Well known text for the object geometry (type: string) 

Note that, except for the identifier, longitude, latitude, type, and wkt_srid_4326 fields, most entries contain very sparse information on the other fields.

## Edges CSV file format

TODO