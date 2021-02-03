# Sesion7

```R
library(mongolite)
#cargamos el archivo csv
data <- read.csv("data.csv")

#guardamos el path de acceso
urlpath <- "mongodb+srv://llamas:K9IEt8dWcALLRMeG@match.mdxrb.mongodb.net/match_games?retryWrites=true&w=majority"

#accesamos
match_collection <- mongo(collection = "match", db = "match_games", 
                          url = urlpath, 
                          verbose = TRUE)

#insertando el CVS a la BDD
match_collection$insert(data)  

# ver el Numero de registros
match_collection$count()

# Visualizar el fichero 
match_collection$find()

# busqueda juego del real madrid
match_collection$find('{"date":"2015-12-20", "home_team":"Real Madrid"}')
#se uso la base de datos obtenida del portwork 2, no tiene regristros del 2015


#Agregar otro CVS a la DDB
match_collection = mongo(collection = "match", db = "match_games") # create connection, database and collection
match_collection$insert(data)

# Cerrando la conexión
rm(match_collection)
```
