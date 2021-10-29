# API Monitor
 A program that monitors the performance of multiple APIs and visualizes them with graphs.
 ![samplegraph](https://puu.sh/IlAEs/630efbacaf.jpg)
## Installation
1. Install docker
2. For each API (api1, api2) go into its folder and run the corresponding command:
 
     - For api1 in api1 folder:
     > docker build -f Dockerfile -t api1 .

     - For api2 in api2 folder:
     >docker build -f Dockerfile2 -t api2 .
3. Then in main folder where `docker-compose.yml` is, run:
> docker-compose up -d

4. You can stop the program with:
> docker-compose down

## Usage
- Send requests to
`http://localhost:8082`or `http://localhost:8084`
- If you want to replicate bad requests such as "404", you can send requests to URLs such as <br /> `http://localhost:8082/badrequest` and `http://localhost:8084/badrequest`
- Now you can check the metrics by going directly to Prometheus. ` http://localhost:9090/`
- If you want to visualize the metrics better with graphs, check the [Setting Up Grafana](#setting-up-grafana)
## Setting Up Grafana
- First start by going to the URL `http://localhost:3000/ `
- Login with __admin__ on both username and password.
- Click to the __Add your first data source__ . Choose __Prometheus__ and fill the URL part with `http://prometheus:9090/`. Rest can stay at the default settings.
- Click to the save and test button at the bottom. If it says data source is working, you can continue.
- From the left menu, choose `+` icon and import.( You can create your own dashboard if you want)
- Use the ID `10427` , load and choose Prometheus as data source. Then import.
- Do the same with ID `10915`. This dashboard has error rate while the previos one has response times etc.
- Now you can see the metrics in graphs by changing dashboards.
