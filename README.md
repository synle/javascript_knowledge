# javascript_knowledge


## Promise Order
Understand `then`, `catch` and `catch`, `then`
```
doFetchContactsThrowError()
    .then(function(contacts){
        console.log('22 success', contacts);
        return Promise.resolve(contacts);
    })
    .catch(function(err){
        console.log('11 error', err);
        return Promise.resolve([]);
    })

// show 11 error, either do then or catch


doFetchContactsThrowError()
    .catch(function(err){
        console.log('11 error', err);
        return Promise.resolve([]);
    })
    .then(function(contacts){
        console.log('22 success', contacts);
        return Promise.resolve(contacts);
    })

// show 11 error, 22 success
// catch error and swallow it and follow through with the next then block


doFetchContacts()
    .catch(function(err){
        console.log('11 error', err);
        return Promise.resolve([]);
    })
    .then(function(contacts){
        console.log('22 success', contacts);
        return Promise.resolve(contacts);
    })
// show 22 success
// no error, go straight to the then block


function doFetchContacts(){
  return new Promise(function(resolve, reject){
    resolve([11,22]);
  });
}


function doFetchContactsThrowError(){
  return new Promise(function(resolve, reject){
    reject('bad code');
  });
}
```
