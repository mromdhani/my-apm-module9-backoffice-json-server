1- Installer globally json-server
   $ npm install -g json-server
   
2- Creer la base de données products.json 
   sous la forme {"products" : [{ "productId": 1, ...},{...}, ... ]} 
   
3- Démarrer json-server en indiquant le fichier ids
   $ json-server --watch products.json --id productId
   
4- Exploiter votre ressources rest sous la route http://localhost:3000/products
   (Cette ressource offre les primitives CRUD usuels via les verbes GET, POST, PUT, DELETE)
