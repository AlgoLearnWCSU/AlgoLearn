# AlgoLearn Architecure

![AlgoLearn Architecture](./img/CS360_Architecture_Transparent.png)

---

## Front End

Anyone may access the front end server via web browser,
where they may view/search posted problems, users, and
visuals. Any user may read, create, delete, and modify content via api calls to the back end.

<br>

## Back End

The backend provides an [api](https://redocly.github.io/redoc/?url=https://raw.githubusercontent.com/AlgoLearnWCSU/AlgoLearnApi/dev/docs/swagger.yml) for
users to manipulate the database. The api for creating,
updating, and deleting is restricted to authorized
users. Solutions from users are passed to a code
running service before it is submitted to the database.

<br>

## Code Runner

The code runner server is a microservice that responds to calls from the backend. This service will run JavaScript code provided by the user in a secure runtime environemnt. The result and metadata of the execution of the code is returned to the backend.

<br>

## User Authorization

The authorization flow for this application starts on the frontend. The user will be directed to the OAuth2.0 link for either Microsoft or GitHub. The user will then sign into the given service and be returned to the frontend with a code. That code is passed to the backend, which can now access user's data and verify that the user is validated. The backend will generate and return an access token and will also return a refresh token to the user from the sign in provider. The user can now access our api routes via their access token. If their access token becomes invalid, they may refresh their access token via sending the refresh token to our backend, which will in turn generate a new refresh token for the user.

<br>
