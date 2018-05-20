# json-env-extract
Extract environment variables from json

```js
const inputText = `
{
  "abc": process.env.ABC,
  "abc2": process.env.ABC,
  'a1': process.env.A1,
  b1: process.env.B1,
  "bcd": 'process.env.BCD',
  'a2': "process.env.A2",
  b2: '\'process.env.B2',
  b3: "\"process.env.B3",
  b4: "\"process.env.B4\"",
  json: {
    "abc": process.env.ABC
  }
}
`;

const { text, envs } = envExtract(inputText, "$ref/envs/");

console.log(text);
/*
{
  "abc": "$ref/envs/cdd814c371eef4408bab44025c0921610d18f14bd0df827cb68bc53318dc83d1",
  "abc2": "$ref/envs/cdd814c371eef4408bab44025c0921610d18f14bd0df827cb68bc53318dc83d1",
  'a1': "$ref/envs/658d36cb102359cca4ed408df7044db86894ae1698616794ce47c917c17c7354",
  b1: "$ref/envs/db25dd79c3bcb3e417489f39b20ca768dc1e14c9b2d689e445350dc1fe886a52",
  "bcd": 'process.env.BCD',
  'a2': "process.env.A2",
  b2: ''process.env.B2',
  b3: ""process.env.B3",
  b4: ""process.env.B4"",
  json: {
    "abc": "$ref/envs/cdd814c371eef4408bab44025c0921610d18f14bd0df827cb68bc53318dc83d1"
  }
}
*/

console.log(envs);
/*
{ 
  '$ref/envs/cdd814c371eef4408bab44025c0921610d18f14bd0df827cb68bc53318dc83d1': 'process.env.ABC',
  '$ref/envs/658d36cb102359cca4ed408df7044db86894ae1698616794ce47c917c17c7354': 'process.env.A1',
  '$ref/envs/db25dd79c3bcb3e417489f39b20ca768dc1e14c9b2d689e445350dc1fe886a52': 'process.env.B1' 
}
*/
```