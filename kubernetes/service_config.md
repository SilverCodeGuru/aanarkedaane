# Service configuration

- if your microservice needs to connect to another mircoservice's api, you need to know the url. this url is somehow fixed for kubernetes as http://microservice2:80/api/microservice2
- to test your service locally, you need to replace this url with service running in the service after port forwarding.
- environment variable will be needed for configuration but not at the runtime in cluster
- ensure that **environment variable is in all upper case** in your launch.json or .env file. This is what viper expects and it is convention.
- some other configuration is also driven from the environment variables.
- those are named in all caps in config.go file
- other that are replacing the kubernetes cluster behavior are not in upper case.