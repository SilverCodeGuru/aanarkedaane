# Run MongoDB locally

1. Use docker-compose to run the mongoDB locally.

```yaml
version: '3.8'
services:
  mongodb:
    image: mongo:8
    ports:
      - "27017:27017"
    volumes:
      - mongo-data:/data/db
volumes:
  mongo-data:
```

1. install mongosh on windows by downloading and running it.
1. install mongodb compass on windows by downloading and running it.
1. install mongosh on wsl 
1. from terminal connect to locally running mongodb using following command -

```bash
mongosh mongodb://localhost:27017
```
