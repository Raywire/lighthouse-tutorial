## Title
Lighthouse Tutorial

## Description
A basic starter pack for a GraphQL API using Lighthouse and Laravel

## Running the API
It's very simple to get the API up and running. First, create the database (and database user if necessary) and add them to the .env file.

```env
DB_DATABASE=your_db_name
DB_USERNAME=your_db_user
DB_PASSWORD=your_password
```

Then install, migrate, seed, and run the server:

```php
composer install
php artisan migrate
php artisan serve
```

## Testing Environment
Visit http://127.0.0.1:8000/graphql-playground on your browser to test the API

Alternatively you can use Postman or Insomnia

Use this url: http://localhost:8000/graphql

## Seeding the database
First run
```php
php artisan tinker
```
Then on the shell that opens up run
```shell
factory('App\User',10)->create();
factory('App\Post',50)->create();
factory('App\Comment',50)->create();
```
or simply
```php
composer seed
```
## Queries and Mutations

## Fetch a user
```
{
  user(id: 1) {
    id
    name
    email
  }
}
```

## Fetch all users with pagination
```
{
  users(count:10) {
    paginatorInfo {
      total
      hasMorePages
      currentPage
      lastPage
      perPage
      firstItem
      lastItem
      count
    }
    data {
      id
      name
      email
    }
  }
}
```

## Fetch a post
```
{
  post(id: 1) {
    id
    title
    content
    user {
      id
      name
    }
    comments {
      id
      reply
    }
  }
}
```

### Fetch posts
```
{
  posts {
    id
    title
    user {
      id
      name
    }
    comments {
      id
      reply
    }
  }
}
```

### Create a user
```
mutation {
  createUser(
    name: "Ryan Wire"
    email: "simiyuwire@gmail.com"
    password: "1234567"
  ){
    id,
    name
  }
}
```
