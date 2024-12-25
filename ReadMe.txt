- Use application-test.yml, application-dev.yml or application-prod.yml for multiple instances of
  same microsevices with different profiles access their respective configs from the config server

- Property file naming convenction based on application name
  <applicationname>.yml for individual microservice config based on its name , if multiple instances are present ,
  we also need to mention their profile like
  eg: <applicationname>-test.yml, <applicationname>-dev.yml or <applicationname>-prod.yml

- Multiple instances of services with same profile will automatically fetch same config .

- To tell the application , there is an updated version of config , go fetch it use the below actuator endpoint
  URI : http://localhost:8080/actuator/refresh
  Note : for this to work all the Config consisting classes should be annotated with @RefreshScope

- To connect with config server Client need to set the below property
  prop: spring: config: zimport: "configserver:http://localhost:8888" (this is yml format)

- Config server is looking to git source repo with the help of below property
  prop: spring.cloud.config.server.git.uri=${HOME}/ConfigServerRepo
  Note: ${Home} is a system variable and can be set in ~./bash_profile or zsh depending upon the usage

- Last but no the least we need to add Config Server and Config Client dependencies respectively in the
  application in order to access these functionalities

  HAPPY Coding!!

