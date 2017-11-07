1.Default Parameters in ES6
var link = function(height = 50, color = 'red', url = 'http://azat.co') { //set default value to the parameter
  ...
}

2.Multi-line Strings in ES6	
var roadPoem = `Then took the other, as just as fair,
    And having perhaps the better claim
    Because it was grassy and wanted wear,
    Though as for that the passing there
    Had worn them really about the same,`

3.Destructuring Assignment in ES6
var { house, mouse} = $('body').data() // we'll get house and mouse variables

var {jsonMiddleware} = require('body-parser')

var {username, password} = req.body


4,Arrow Functions in ES6
var ids = ['5632953c4e345e145fdf2df8','563295464e345e145fdf2df9']
var messages = ids.map(value => `ID is ${value}`) // implicit return ${value} new features of es6 of append string 
	
var ids = ['5632953c4e345e145fdf2df8','563295464e345e145fdf2df9']
var messages = ids.map((value, index, list) => `ID of ${index} element is ${value} `) // implicit return list-orignal ids


5.Promises in ES6
var wait1000 =  ()=> new Promise((resolve, reject)=> {setTimeout(resolve, 1000)})

wait1000()
    .then(function() {
        console.log('Yay!')
        return wait1000()
    })
    .then(function() {
        console.log('Wheeyee!')
    });

6.Block-Scoped Constructs Let and Const
// Vars are function scoped, but let is limit block


7.Classes in ES6
super() is when a class is extends b class super() is point to b class constractor


8.modules in ES6
// ES 5 syntax
module.exports = {
  port: 3000,
  getAccounts: function() {
    ...
  }
}

var service = require('module.js')
console.log(service.port) // 3000


// ES6 Syntax
export var port = 3000
export function getAccounts(url) {
  ...
}
import {port, getAccounts} from 'module'
console.log(port) // 3000
//or
import * as service from 'module'
console.log(service.port) // 3000
