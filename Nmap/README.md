# Nmap

Build:

docker build -t nmap:latest .

Run:

docker run --rm nmap:latest [command]

docker run --rm nmap:latest -sP 10.0.0.0/24
