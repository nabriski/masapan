masapan
=======

API Only At This Time
=======

successor of Ys

```javascript
var m = new require('masapan');

//generic response
m.every('^/koko/$').returns = function(req,res){
  res.end("Hello!");  
};

//json response
m.every('^/koko.json$').returns.json = function(req,res){
    res.end({"message" : "Hello!"});    
};

//only route to GET
m.get('^/loko/$').returns = function(req,res){
  res.end("Hello!");  
};

//query params
m.get('^/loko/$').returns= function(req,res){
  res.end("Hello "+req.params.name);  
};

//match groups
m.every('^/user/(name)/$').returns = function(req,res){
  res.end("Hello "+req.$1);  
};


//only route to GET with JSON output
m.get('^/loko.json$').returns.json = function(req,res){

    res.end({"message" : "Hello!"});    
};

//POST params
m.post('^/yoyo$').returns = function(req,res){

    var val = parseInt(req.params.value) + 1;    
    res.end(val);
};

//html template
m.post('^/user/(name)/matches/$').returns.template("matches.mustache").as.html = function(req,res){
    res.end({name : req.$1});    
};

//static
m.static("^/.*$").returns = "www/";

//rewrite
m.rewrite("^/(momo)/$").returns = "/query/?q=$1";

//proxy 
m.proxy("^/backend/$").returns = "http://localhost:8080";


m.start();

```
