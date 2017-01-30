# fetch-json

A clean API for making JSON requests using the Javascript Fetch API

## Contents

- [Installation](#installation)
- [Usage](#usage)
  - [GET Requests](#get)
  - [POST Requests](#post)
  - [PUT Requests](#put)
  - [DELETE Requests](#delete)

## Installation

```sh
npm install --save fetch-json
```

## Usage

`fetch-json` provides functions for each of the HTTP verbs,
and returns promises just like the Fetch API.

All of the examples use this great fake [JSON API](https://jsonplaceholder.typicode.com/).

#### GET

```javascript
import { getJson } from 'fetch-json';

const apiRoot = 'https://jsonplaceholder.typicode.com';

// As a promise
getJson(apiRoot)
  .then(body => {
    console.log('success', body);
  })
  .catch(err => {
    console.log('error', err);
  });

// Async/Await
async function getFromApi(url) {
  try {
    const body = await getJson(apiRoot);
    console.log('success', body);
  } catch(err) {
    console.log('error', err);
  }
}
getFromApi(apiRoot);
```

#### POST

```javascript
import { postJson } from 'fetch-json';

const apiRoot = 'https://jsonplaceholder.typicode.com';
const requestBody = { foo: 'bar' };

// As a promise
postJson(apiRoot, requestBody)
  .then(responseBody => {
    console.log('success', responseBody);
  })
  .catch(err => {
    console.log('error', err);
  });

// Async/Await
async function postToApi(url, body) {
  try {
    const responseBody = await postJson(apiRoot, body);
    console.log('success', responseBody);
  } catch(err) {
    console.log('error', err);
  }
}
postToApi(apiRoot, requestBody);
```

#### PUT

```javascript
import { putJson } from 'fetch-json';

const apiRoot = 'https://jsonplaceholder.typicode.com';
const id = 1001;
const requestBody = { foo: 'baz' };

// As a promise
putJson(`${apiRoot}/${id}`, requestBody)
  .then(responseBody => {
    console.log('success', responseBody);
  })
  .catch(err => {
    console.log('error', err);
  });

// Async/Await
async function putToApi(url, body) {
  try {
    const responseBody = await putJson(apiRoot, body);
    console.log('success', responseBody);
  } catch(err) {
    console.log('error', err);
  }
}
putToApi(`${apiRoot}/${id}`, requestBody);
```

#### DELETE

```javascript
import { deleteJson } from 'fetch-json';

const apiRoot = 'https://jsonplaceholder.typicode.com';
const id = 1001;

// As a promise
deleteJson(`${apiRoot}/${id}`)
  .then(() => {
    console.log('success');
  })
  .catch(err => {
    console.log('error', err);
  });

// Async/Await
async function deleteFromApi(url) {
  try {
    await deleteJson(apiRoot);
    console.log('success');
  } catch(err) {
    console.log('error', err);
  }
}
deleteFromApi(`${apiRoot}/${id}`);
```
