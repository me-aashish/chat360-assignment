
# Quality Log Control

## Steps to run the app
 - Clone the repo: `https://github.com/me-aashish/chat360-assignment.git`
 - After cloning, first go to `client` directory and run `npm i` to install required packages and then run `npm start` to start the frontend on port `3000`.
 - Before starting backend, run start docker desktop on your system and after that run this command in your shell `docker run -d --name redis-stack -p 6379:6379 -p 8001:8001 redis/redis-stack:latest`. This will start the redis client which you can see on `localhost:8001`
 - Similarly, go to `server` directory and run `npm i` to install required packages and then run `npm start` to start the backend on port `3001`.
 - After starting the backend server, automatically 7-8 API requests will be made and their logs will be saved in the `logs` directory which can be configured from `.env` file.

## System Design of the app
![System Design](https://github.com/me-aashish/chat360-assignment/blob/master/chat360_assignment_sd.drawio.png)

## List of features
- User can search for the logs using `log_level`, `log_message`, `metadata.source`, and `timestamps` as well.
- Instead of cli, I have made a web-UI for user friendly interface
- Bonus features such as `Implement search within specific date ranges`, `Utilize regular expressions for search` have also been implemented.
- In order to increase the speed of search results, Redis as cache has been used which will do the caching of searched results.
- Proper structure of the codebase for better readibility.
- For seaching using timestamps, you have to give full timestamp such as `2024-05-14T11:03:06.187Z`.
- Also, add the `multi-filter` functionality for logs, where logs can be filtered on the basis of combination of three fields- `log_level`, `log_message` and `log_metadata`. Timestamp has not been added in the multi-filter functionality.

## List of features which could be implemented further
- For ingesting the massive volumes, we could use the `Load Balancer`s which will monitor the health of current API server and will spin up a new API server if the current one starts to get choked.
- Since, I have not used DB for storing logs, but we can use DB for the same.
- We can horizontally scale the `DB by sharding` it in order to ingest the massive volumes of log.
- Also, we can use `master-slave` design pattern for the DB where master DB will be responsible for the writes of the logs and slave DB will be responsible for the reads respectively.
- Because of time constraint, I'm not able to implement above features.
- I'll be more than happy to give the full System Design including the features to be implemented

## Few issues present in the system
- The code structure of the frontend app is not as per industry standard.
- In the backend codebase, I have written the business logic in the `controller` itself  instead of `service` layer as I have not made `service` and `repository` layer as DB is present.
- In the production/deployed app, instead of Redis client, I have used the in-memory object itself for the caching as I was facing some errors while deploying Redis client but it will be present in the cloned project.
- Also, I have not given much attention to the log_level, log_message, I have generated them randomly, focused more on implementing fucntionalities such as searching, filtering etc. 
- These issues can easily be removed in the future.




