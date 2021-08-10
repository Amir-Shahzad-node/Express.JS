# Express.JS
this is our first project, that we are building, let hope for the best.
const express = require('express');

const app = express();

const PORT = 3000;

let accounts = [
  {
    "id": 1,
    "username": "Muneeb Shahbaz(Moon)",
    "role": "admin",
    "relation": "Brother",
    "Eduation": "BSCS",
    "status":"vaccinated",
    "Bonus":"Granted",
    age:"23",
    "material status":"unmarried"
  },
  {
    "id": 2,
    "username": "Waleed Shahbaz",
    "role": "GEN-MNGR",
    "relation": "Brother",
     "Eduation": "MPhil",
     "status":"vaccinated",
     "Bonus":"Granted",
     age:"26",
     "material status":"married"
  },
  {
    "id": 3,
    "username": "shamir Abbas",
    "role": "guest",
    "relation":"Cousin",
    " Eduation": "BSSE",
     "status":"vaccinated",
    "Bonus":"Granted",
    "age":"25",
    "material status":"unmarried"
  },
  {
    "id": 4,
    "username": "Abdullah Izmir",
    "role": "IT-MNGR",
    "relation":"Friend",
     "Eduation": "PhD",
     "status":"vaccinated",
    "Bonus":"Granted",
    "age":"28",
    "material status":"unmarried"
  },
  {
    "id": 5,
    "username": "Jalil nazir",
    "role": "HR",
    "relation":"Friend",
     "Eduation": " Bachlaor in Management Sciences",
     "Status":"vaccinated",
    "Bonus":"Pending",
    "age":"36",
    "material status":"married"
  }
];
//
//let myJsonStr = JSON.stringify(accounts);
// console.log(myJsonStr);

app.get('/accounts', (request, response) => {
   // request.json(accounts);
    response.json(accounts);
  
    console.log('Look at the browser for the desired data, being posted on the browser');
});


app.get('/accounts/:id', (request, response) => {
  
    const accountId = Number(request.params.id);
  
    const getAccount = accounts.find((account) => account.id === accountId);

  if (!getAccount) {
  
        response.status(500).send('Account not found.');
  } else {
    
        response.json(getAccount);
  }
});

/*app.delete('/accounts/:id' function(req,res){
    console.log('Got a DELETE request for /acconts/id:2');
    res.send('Hello DELETE');
    
})*/
    
    
app.use(express.json());

app.listen(PORT, () => console.log(`Express server currently running on port ${PORT}`));
