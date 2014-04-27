masapan
=======

API Only At This Time
=======

successor of Ys

```javascript
var ma = require('masapan');

//generic response
ma['^/koko/$'] = function(req,res){
  res.end("Hello!");  
};

//json response
ma['^/koko.json$'].json = function(req,res){

    res.writeObject({"message" : "Hello!"});    
    res.end();

};

//only route to GET
ma['^/loko/$'].get = function(req,res){
  res.end("Hello!");  
};

//query params
ma['^/loko/$'].get = function(req,res){
  res.end("Hello "+req.params.name);  
};

//match groups
ma['^/user/(name)/$'] = function(req,res){
  res.end("Hello "+req.$1);  
};


//only route to GET with JSON output
ma['^/loko.json$'].json.get = //or
ma['^/loko.json$'].get.json = function(req,res){

    res.writeObject({"message" : "Hello!"});    
    res.end();
};

//POST params
ma['^/yoyo$'].post = function(req,res){
    var val = parseInt(req.params.value) + 1;    
    res.end(val);
};

ma.start();

```
