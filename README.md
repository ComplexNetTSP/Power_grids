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

TODO

## Edges CSV file format

TODO