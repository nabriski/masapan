masapan
=======

API Only At This Time
=======

successor of Ys

```javascript
var m = new require('masapan');

//generic response
m.on.all('^/koko/$').return(function(req,res){
  res.end("Hello!");  
});

//json response
m.on.all('^/koko.json$').return.json(function(req,res){
    res.end({"message" : "Hello!"});    
});

//only route to GET
m.on.get('^/loko/$').return(function(req,res){
  res.end("Hello!");  
});

//query params
m.on.get('^/loko/$').return(function(req,res){
  res.end("Hello "+req.params.name);  
});

//match groups
m.on.all('^/user/(name)/$').return(function(req,res){
  res.end("Hello "+req.$1);  
});


//only route to GET with JSON output
m.on.get('^/loko.json$').return.json(function(req,res){

    res.end({"message" : "Hello!"});    
});

//POST params
m.on.post('^/yoyo$').return(function(req,res){

    var val = parseInt(req.params.value) + 1;    
    res.end(val);
});

//html template
m.on.post('^/user/(name)/matches/$').return.template("matches.mustache").as.html(function(req,res){
    res.end({name : req.$1});    
});

//static
m.on.all("^/.*$").return.static("www/");

//rewrite
m.on.all("^/(momo)/$").return.rewrite("/query/?q=$1");

//proxy 
m.on.all("^/backend/$").return.proxy("http://localhost:8080");


m.start();

```
