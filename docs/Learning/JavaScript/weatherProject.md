## weatherProject笔记

A small weather query project using OpenWeather API.

Javascript, node.js, express

# body-parser

允许查看Post请求

~~~js
npm i body-parser
~~~

# _dirname

Node.jsで`__dirname`を使用すると、現在のJavaScriptファイルが存在するフォルダーのパスを取得できる。

## index.html

~~~html
<!DOCTYPE html>
<html lang="en" dir="ltr">
    <head>
        <meta charset="utf-8">
        <title>Weather App</title>
    </head>
    <body>
        <form action="/" method="post">
            <label for="cityName">City Name</label>
            <input type="text" name="cityName" value="">
            <button type="submit">Go</button>
        </form>
       
    </body>
</html>
~~~



## app.js

~~~js
const express = require("express");
const https = require("https");
const bodyParser = require("body-parser");

const app = express();

app.use(bodyParser.urlencoded({extended: true}));

app.get("/", function(req, res){
    res.sendFile(__dirname + "/index.html");
})

app.post("/", function(req, res){
    const query = req.body.cityName;
    const apikey = "7b054e1ac706068d82a711f0969ed67a&";
    const units = "metric";
    const url = "https://api.openweathermap.org/data/2.5/weather?appid="+apikey + "&q=" + query + "&units=" + units;
   
    https.get(url, function(response){
        console.log(response.statusCode);

        response.on("data", function(data){
            const weatherData = JSON.parse(data)
            const temp = weatherData.main.temp
            const weatherDescription = weatherData.weather[0].description
            const icon = weatherData.weather[0].icon
            const imageURL = "https://openweathermap.org/img/wn/"+ icon +"@2x.png"
            
            res.write("<p> The weather is currently " + weatherDescription + ".<p>");
            res.write("<h1>The temperature in " + query + " is " + temp + ".</h1>");
            res.write("<img src = " + imageURL + ">");
            res.send;
        })
    })

})
    


app.listen(3000,function(){
    console.log("Server is running on port 30000.");
})

~~~

 

