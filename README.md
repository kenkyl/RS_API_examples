# Redis Enterprise REST API Examples

## Create Cluster
Send this request to the first node to initiate your cluster:

`curl -X POST https://<node-ip>:9443/v1/bootstrap/create_cluster -H 'Content-Type: application/json' -H 'cache-control: no-cache' -d @create-demo-cluster.json -k -I`

Example Storage Paths: 
* "persistent_path": "/mnt/disks/redis-persistent-disk-west1-1/persistent"
* "ephemeral_path": "/mnt/disks/redis-persistent-disk-west1-1/ephemeral"

## Verify Cluster Creation
`curl https://<node-ip>:9443/v1/bootstrap -H 'Content-Type: application/json' -u <email>:<password> -k`

## Join Cluster 
Send this request to join subsequent nodes to the cluster: 

`curl -X POST https://<node-ip>/v1/bootstrap/join_cluster -H 'Content-Type: application/json' -H 'cache-control: no-cache' -u <email>:<password> -d @join-demo-cluster-1.json -k -i`

## Create Database (non-CRDB)
Send this request to a node in the cluster to create a database:

`curl -X POST https://<node-ip>:9443/v1/bdbs -H 'cache-control: no-cache' -H 'Content-Type: application/json' -u <email>:<password> -d @create-db-1.json -k -i`