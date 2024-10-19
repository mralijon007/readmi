
---

# README

## Contents

1. Synchronous
2. Asynchronous
3. New Promise
4. Async/Await
5. Try/Catch

---

### 1. Synchronous

A synchronous program is one where code is executed in a sequential order. Each command must finish before the next one starts. For example:

```javascript
console.log("Start");
console.log("Middle");
console.log("End");
```

Output:  
```
Start  
Middle  
End  
```

### 2. Asynchronous

An asynchronous program allows certain commands to run without waiting for previous ones to complete. For example, using `setTimeout`:

```javascript
console.log("Start");
setTimeout(() => {
  console.log("Middle");
}, 1000);
console.log("End");
```

Output:
```
Start  
End  
Middle (after 1 second)  
```

### 3. New Promise

A `Promise` is an object used to handle asynchronous operations. It has three states: **pending**, **fulfilled**, and **rejected**.

Example:

```javascript
let promise = new Promise((resolve, reject) => {
  setTimeout(() => resolve("Success!"), 2000);
});

promise.then((result) => {
  console.log(result); 
});
```

### 4. Async/Await

`async/await` is a simpler way to work with `Promise`s, allowing you to write asynchronous code that looks like synchronous code.

Example:

```javascript
async function example() {
  let promise = new Promise((resolve) => {
    setTimeout(() => resolve("Success!"), 2000);
  });

  let result = await promise;
  console.log(result); 
}

example();
```

### 5. Try/Catch

When using `async/await`, you can handle errors using a `try/catch` block.

Example:

```javascript
async function example() {
  try {
    let promise = new Promise((resolve, reject) => {
      setTimeout(() => reject("Error!"), 2000);
    });

    let result = await promise;
    console.log(result);
  } catch (error) {
    console.log(error); 
  }
}

example();
```

---
---
## Мазмун

1. HTTP ва HTTPS
2. API
3. REST API 

---

### 1. HTTP ва HTTPS

#### HTTP (Hypertext Transfer Protocol)

HTTP (Протоколи интиқоли гипертекст) протоколи маъмул барои ирсоли дархостҳо ва гирифтани посухҳо байни мизоҷ (client) ва сервер мебошад.

Мисоли оддӣ барои фиристодани дархости HTTP бо истифодаи JavaScript:

```javascript
fetch('http://example.com/data')
  .then(response => response.json())
  .then(data => {
    console.log('Data:', data);
  })
  .catch(error => {
    console.error('Error:', error);
  });
```

Ин мисол дархостро ба сервер мефиристад ва маълумоти гирифтшуда дар консол чоп карда мешавад.

#### HTTPS (Hypertext Transfer Protocol Secure)

HTTPS версияи бехатаршудаи HTTP мебошад, ки дар он маълумот рамзгузорӣ мешавад. Барои истифодаи HTTPS, танҳо URL-ро бо `https://` нависед.

Мисол:

```javascript
fetch('https://example.com/data')
  .then(response => response.json())
  .then(data => {
    console.log('Data:', data);
  })
  .catch(error => {
    console.error('Error:', error);
  });
```

Дар ин ҷо маълумот дар пайвасти муҳофизатшуда бо истифода аз HTTPS фиристода мешавад.

---

### 2. API (Application Programming Interface)

API роҳест, ки тавассути он барномаҳо метавонанд бо ҳамдигар бо истифодаи дархостҳо ва посухҳо муошират кунанд. API маълумотро ба мисли маълумоти ҳозиразамон дар вебсайтҳо пешниҳод мекунад.

Мисол бо истифода аз API барои гирифтани маълумоти ҳаво:

```javascript
fetch('https://api.weatherapi.com/v1/current.json?key=YOUR_API_KEY&q=London')
  .then(response => response.json())
  .then(data => {
    console.log('Weather in London:', data);
  })
  .catch(error => {
    console.error('Error:', error);
  });
```

Ин мисол бо истифода аз API-и ҳаво маълумотро дар бораи ҳавои Лондон мегирад ва онро дар консол нишон медиҳад.

---

### 3. REST API (Representational State Transfer API)

REST API як навъи маъмултарини API мебошад, ки дар он амалиётҳои HTTP ба мисли `GET`, `POST`, `PUT`, ва `DELETE` истифода мешаванд. Дар REST API, маълумотро тавассути URL ва усулҳои HTTP идора кардан мумкин аст.

#### Мисоли REST API бо JavaScript (CRUD):

##### 1. Дархости `GET` барои гирифтани маълумот:

```javascript
fetch('https://jsonplaceholder.typicode.com/posts/1')
  .then(response => response.json())
  .then(data => {
    console.log('Post Data:', data);
  })
  .catch(error => {
    console.error('Error:', error);
  });
```

Ин дархост маълумоти постро бо ID = 1 аз REST API мегирад.

##### 2. Дархости `POST` барои фиристодани маълумот:

```javascript
fetch('https://jsonplaceholder.typicode.com/posts', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    title: 'New Post',
    body: 'This is the content of the post.',
    userId: 1
  })
})
  .then(response => response.json())
  .then(data => {
    console.log('Post Created:', data);
  })
  .catch(error => {
    console.error('Error:', error);
  });
```

Ин дархост як пости навро ба сервер мефиристад.

##### 3. Дархости `PUT` барои навсозии маълумот:

```javascript
fetch('https://jsonplaceholder.typicode.com/posts/1', {
  method: 'PUT',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    title: 'Updated Post',
    body: 'This is the updated content of the post.',
    userId: 1
  })
})
  .then(response => response.json())
  .then(data => {
    console.log('Post Updated:', data);
  })
  .catch(error => {
    console.error('Error:', error);
  });
```

Ин дархост постро бо ID = 1 нав мекунад.

##### 4. Дархости `DELETE` барои пок кардани маълумот:

```javascript
fetch('https://jsonplaceholder.typicode.com/posts/1', {
  method: 'DELETE'
})
  .then(() => {
    console.log('Post Deleted');
  })
  .catch(error => {
    console.error('Error:', error);
  });
```

Ин дархост постро бо ID = 1 пок мекунад.

---
