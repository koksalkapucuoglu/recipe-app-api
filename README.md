
# Recipe App API

Recipe App is an API service that developers can use to manage recipes.



## Tech Stack

**Core Tech:** Python

**Backend Service:** Django, Django Rest Framework

**Code Format:** PEP8 Standart

**Test:** unittest, Flake8

**Database:** Postgresql

**Container:** Docker

**CI:** Github Actions


## Features

- Test Driven Development
- User Authentication and Management
- Recipe Management using tags and ingredients
- Continuous Integration
- Dockerize System


## API Reference

#### Create a new user

```http
  POST /api/user/create
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `email` | `string` | **Required**.  |
| `password` | `string` | **Required**.|
| `name` | `string` | **Required**.|

#### Create authentication token

```http
  POST /api/user/token
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `email` | `string` | **Required**.  |
| `password` | `string` | **Required**.|

#### Get own information

```http
  GET /api/user/me
```

| Header | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `Authorization` | `string` | **Required**. Token <token>|

#### Create a new tag

```http
  POST /api/recipe/tags
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `name` | `string` | **Required**.  |

| Header | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `Authorization` | `string` | **Required**. Token <token>|

#### Get own tag list

```http
  GET /api/recipe/tags/?assigned_only={assigned_only}
```
| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `assigned_only` | `boolean` | |

| Header | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `Authorization` | `string` | **Required**. Token <token>|


#### Create a new ingredient

```http
  POST /api/recipe/ingredients
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `name` | `string` | **Required**.  |

| Header | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `Authorization` | `string` | **Required**. Token <token>|

#### Get own ingredient list

```http
  GET /api/recipe/ingredients/?assigned_only={assigned_only}
```
| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `assigned_only` | `boolean` | |

| Header | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `Authorization` | `string` | **Required**. Token <token>|


#### Create a new recipe

```http
  POST /api/recipe/recipes
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `user` | `user model` | **Required**.  |
| `title` | `string` | **Required**.  |
| `ingredient` | `ingredient model` | support multiple choice  |
| `tag` | `tag model` |  support multiple choice  |
| `time_minutes` | `integer` | **Required**.|
| `price` | `float` | **Required**. |
| `link` | `string` |  |
| `image` | `file` | |

| Header | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `Authorization` | `string` | **Required**. Token <token>|

#### Get own recipe list

```http
  GET /api/recipe/recipes
```

| Header | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `Authorization` | `string` | **Required**. Token <token>|

#### Get own recipe by id

```http
  GET /api/recipe/recipes/${id}
```
| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `id`      | `string` | **Required**. Id of item to fetch |

| Header | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `Authorization` | `string` | **Required**. Token <token>|

#### Update own recipe by id

```http
  PUT /api/recipe/recipes/${id}
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `id`      | `string` | **Required**. Id of item to update |
| `user` | `user model` | **Required**.  |
| `title` | `string` | **Required**.  |
| `ingredient` | `ingredient model` |  support multiple choice |
| `tag` | `tag model` | support multiple choice  |
| `time_minutes` | `integer` | **Required**.|
| `price` | `float` | **Required**. |
| `link` | `string` |  |
| `image` | `file` | |

| Header | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `Authorization` | `string` | **Required**. Token <token>|

#### Delete own recipe by id

```http
  DELETE /api/recipe/recipes/${id}
```

| Parameter | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `id`      | `string` | **Required**. Id of item to update |

| Header | Type     | Description                |
| :-------- | :------- | :------------------------- |
| `Authorization` | `string` | **Required**. Token <token>|


## Run Locally

Clone the project

```bash
  git clone https://github.com/koksalkapucuoglu/recipe-app-api.git
```

Go to the project directory

```bash
  cd recipe-app-api
```

Build docker

```bash
  docker-compose build
```

Start the server

```bash
  docker-compose up
```


## Create Django Superuser 


Go to the project directory

```bash
  cd recipe-app-api
```

Run following command for create a new super user
```bash
  docker-compose run app sh -c "python manage.py createsuperuser"
```


## Running Tests

Go to the project directory

```bash
  cd recipe-app-api
```

Run following command for unit test and coding style(PEP8) test

```bash
  docker-compose run app sh -c "python manage.py test && flake8"
```

