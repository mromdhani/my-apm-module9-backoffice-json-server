1- Installer globally json-server
   $ npm install -g json-server
2- Creer la base de données products.json 
   sous la forme {"products" : [{ "productId": 1, ...},{...}, ... ]}
3- JSOn-Server réclame un id nommé "id", mais si l'on veuille utiliser comme id "productId", il faut ajouter 
   le fichier ids.json   
3- Démarrer json-server en indiquant le fichier ids
   $ json-server --watch products.json --id ids.json
4- Exploiter votre ressources rest sous la route http://localhost:3000/products

======================
L'étape 3 semble ne pas fonctionner avec 0.12.1 (12/2017), la solution serait de programmer le js 
du serveur 
1 - Faire d'abord un npm init sur le dossier 
2 - Y Installer localement json-server avec $ npm install --save-dev json-server
3-  Ecrire le server.js selon le modèle suivant 

			// server.js
			const jsonServer = require('json-server')
			const server = jsonServer.create()
			const router = jsonServer.router('products.json')
			router.db._.id = "productId";
			const middlewares = jsonServer.defaults()

			server.use(middlewares)
			server.use(router)
			server.listen(3000, () => {
			  console.log('JSON Server is running')
			})
4- Démarrer le server avec $ node server.js
    ceci doit rouler !
