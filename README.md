
# Quality Log Control

## Steps to run the app
 - Clone the repo: `https://github.com/me-aashish/chat360-assignment.git`
 - After cloning, first go to `client` directory and run `npm i` to install required packages and then run `npm start` to start the frontend on port `3000`
 - Similarly, go to `server` directory and run `npm i` to install required packages and then run `npm start` to start the backend on port `3001`
 - After starting the backend server, automatically 7-8 API requests will be made and their logs will be saved in the `logs` directory which can be configured from `.env` file.

## System Design of the app
![System Design](https://github.com/me-aashish/chat360-assignment/blob/master/chat360_assignment_sd.drawio.png)

## List of features
- User can search for the logs using `log_level`, `log_message`, `metadata.source`, and `timestamps` as well.
- Instead of cli, I have made a web-UI for user friendly interface
- Bonus features such as `Implement search within specific date ranges`, `Utilize regular expressions for search` have also been implemented.
- In order to increase the speed of serach results, Redis as cache has been used which will do the caching of searched results.
- Proper structure of the codebase for better readibility

## List of features which could be implemented further
- For ingesting the massive volumes, we could use the `Load Balancer`s which will monitor the health of current API server and will spin up a new API server if the current one starts to get choked.
- Since, I have not used DB for storing logs, but we can use DB for the same.
- We can horizontally scale the `DB by sharding` it in order to ingest the massive volumes of log.
- Also, we can use `master-slave` design pattern for the DB where master DB will be responsible for the writes of the logs and slave DB will be responsible for the reads respectively.
- Because of time constraint, I'm not able to implement above features.

## Few issues present in the system
- The code structure of the frontend app is not as per industry standard.
- In the backend codebase, I have written the business logic in the `controller` itself  instead of `service` layer as I have not made `service` and `repository` layer as DB is present.
- In the production/deployed app, instead of Redis client, I have used the in-memory object itself for the caching as I was facing some errors while deploying Redis client.
- Also, I have not given much attention to the log_level, log_message, I have generated them randomly, focused more on implementing fucntionalities such as searching, filtering etc. 




