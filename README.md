masapan
=======

API Only At This Time
=======

successor of Ys

```javascript
var ma = require('masapan');

//generic response
ma('^/koko/$').returns = function(req,res){
  res.end("Hello!");  
};

//json response
ma('^/koko.json$').returns.json = function(req,res){
    res.writeObject({"message" : "Hello!"});    
    res.end();
};

//only route to GET
ma.get('^/loko/$').returns = function(req,res){
  res.end("Hello!");  
};

//query params
ma.get('^/loko/$').returns= function(req,res){
  res.end("Hello "+req.params.name);  
};

//match groups
ma('^/user/(name)/$').returns = function(req,res){
  res.end("Hello "+req.$1);  
};


//only route to GET with JSON output
ma.get('^/loko.json$').returns.json = function(req,res){

    res.writeObject({"message" : "Hello!"});    
    res.end();
};

//POST params
ma.post('^/yoyo$').returns = function(req,res){

    var val = parseInt(req.params.value) + 1;    
    res.end(val);
};

//html template
ma.post('^/user/(name)/matches/$').returns.template("matches.mustache").as.html = function(req,res){
    res.writeObject({name : req.$1});    
    res.end(val);
};

ma.start();

```
