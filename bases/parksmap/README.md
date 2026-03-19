# resource limits estimates
mongodb:
    cpu: 20m
    memory: 60Mi
backend:
    cpu: 10m
    memory: 800Mi
frontend:
    cpu: 10m
    memory: 800Mi

# some actions required after pod creation not in helm
## on mongo pod
mongosh -u admin -p secret --authenticationDatabase admin --eval 'use parksapp' --eval 'db.createUser({user: "parksapp", pwd: "keepsafe", roles: [{ role: "dbAdmin", db: "parksapp" },{ role: "readWrite", db: "parksapp" }]})' --quiet

## go to <nationalparks.route>ws/data/load
Items inserted in database: 2893