# Overview

Test container stack to show for massive write IO problems with prometheus/grafana/promscale/timescaledb.

# How to test

1. Start docker stack "sudo docker-compose up -d"
2. Check prometheus targets http://localhost:9090/targets
3. Login Grafana http://localhost:3000 with admin/admin
4. Add Prometheus datasource with URL "http://promscale:9201"
5. Import Node_Exporter Dashboard using id 1860 with prometheus datasource
6. Check IO stats of the server in Node_Exporter dashboard under "Storage Disk"
7. Check CPU time with "sudo top -n 1 -b | tail -n +7 | sort  -k 11Vb"
8. Check Written Bytes with "sudo iotop -a -o -P"
9. Check docker volume size with "sudo docker system df -v"
