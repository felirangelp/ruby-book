# Hashes

El último tipo de datos que vamos a ver son los **hashes** (no existe una buena traducción al español). Un hash no es más que una colección de datos en donde cada valor está asociado a una llave. Imagina un diccionario, en donde las palabras son las llaves y las deficiones son los valores.

Abramos IRB y creemos nuestro primer hash:

```
$ irb
2.3.1 :001 > persona = {"nombre" => "Germán", "apellido" => "Escobar", "edad" => 34, "estatura" => 1.8}
 => {"nombre"=>"Germán", "apellido"=>"Escobar", "edad"=>34, "estatura"=>1.8}
```

En este ejemplo utilizamos un hash para almacenar la información de una persona, pero podemos utilizar los hashes para almacenar cualquier tipo de información que requiera esa asociación llave-valor.

## Obteniendo valores de un hash

Para obtener el nombre de la persona en el hash que definimos previamente utilizamos la siguiente línea de código:

```
2.3.1 :002 > persona["nombre"]
 => "Germán"
```

Para obtener el valor de una llave en un hash utilizamos una notación muy similar a como lo hacemos con los arreglos, utilizando `[]`. Sin embargo, en vez de utilizar la posición como en los arreglos, utilizamos la llave. Las llaves pueden ser de cualquier tipo. En el ejemplo anterior utilizamos strings pero también podrían ser números:

```
2.3.1 :003 > statuses = {0 => "encendido", 1 => "apagado", 2 => "fundido"}
 => {0 => "encendido", 1 => "apagado", 2 => "fundido"}
```

Y para obtener el valor de la llave `1` hacemos lo siguiente:

```
2.3.1 :004 > statuses[1]
 => "apagado"
```

## Agregando nuevos elementos al hash

Podemos agregar más elementos al hash. Por ejemplo, si quisiéramos agregar una llave `peso` en el hash que definimos anteriormente, lo haríamos de la siguiente forma:

```
2.3.1 :005 > persona["peso"] = 65
 => 65
```

Si volvemos a mostrar el contenido de la variable `persona` veríamos el siguiente resultado (fíjate que ahora tiene una nueva llave `"peso"` con valor `65`):

```
2.3.1 :006 > persona
 => {"nombre"=>"Germán", "apellido"=>"Escobar", "edad"=>34, "estatura"=>1.8, "peso"=>65}
```

## Modificando elementos del hash

Es posible modificar los elementos de un hash. Por ejemplo, si queremos cambiar el valor de la llave `peso` podríamos hacer lo siguiente:

```
2.3.1 :007 > persona["peso"] = 70
 => 70
```

Ahora, si volvemos a mostrar el contenido de la variable `persona` veríamos el siguiente resultado (fíjate que ahora la llave `"peso"` tiene un valor de `70`):

```
2.3.1 :008 > persona
 => {"nombre"=>"Germán", "apellido"=>"Escobar", "edad"=>34, "estatura"=>1.8, "peso"=>70}
```

## Eliminando elementos del hash

Para eliminar una llave (con su respectivo valor) del hash podemos utilizar el método `delete`. Por ejemplo, si queremos eliminar la llave `"peso"` podemos hacer lo siguiente:

```
2.3.1 :009 > persona.delete("peso")
 => 70
```

El método `delete` devuelve el valor de la llave eliminada. Ahora, si volvemos a mostrar el contenido de la variable `person` veríamos el siguiente resultado (fíjate que no está la llave `"peso"`):

```
2.3.1 :010 > persona
 => {"nombre"=>"Germán", "apellido"=>"Escobar", "edad"=>34, "estatura"=>1.8}
```

## Recorriendo los elementos de un hash

Hay varias formas de recorrer los elementos de un hash. Primero, podemos utilizar el método `each` de la siguiente forma. Crea un archivo llamado `hashes.rb` con el siguiente código:

```ruby
persona = { "nombre" => "Germán", "apellido" => "Escobar", "edad" => 34, "estatura" => 1.8 }

persona.each do |llave, valor|
  puts "#{llave}: #{valor}"
end
```

Al ejecutarlo deberías ver el siguiente resultado:

```
$ ruby hashes.rb
nombre: Germán
apellido: Escobar
edad: 34
estatura: 1.8
```

## Usando símbolos como llaves

En los ejemplos anteriores hemos usado cadenas de texto y números como llaves de los hashes. Sin embargo, en Ruby hay un tipo de datos que es muy utilizado como llaves en los hashes: los símbolos.

```ruby
status = :encendido # nuestro primer símbolo
```

Los símbolos son muy parecidos a las cadenas de texto pero con las siguientes diferencias:

* No están envueltos en comillas.
* Empiezan con dos puntos (:).
* No contienen espacios en blanco.

Creemos nuestro primer hash con símbolos:

```
$ irb
2.3.1 :001 > persona = {:nombre => "Germán", :apellido => "Escobar", :edad => 34, :estatura => 1.8}
```

Muy parecido al ejemplo anterior. Pero entonces ¿cuál es la ventaja de usar símbolos como llaves de un hash? La respuesta es que cuando usamos símbolos podemos escribir los hashes de forma más corta:

```
2.3.1 :002 > persona = {nombre: "Germán", apellido: "Escobar", edad: 34, estatura: 1.8}
```

Los cambios que hicimos son los siguientes:

* Eliminamos el `=>` (hash rocket)
* Movimos los dos puntos (:) al final del símbolo.

Para obtener algún valor del hash utilizamos el símbolo:

```
2.3.1 :003 > persona[:nombre]
 => "Germán"
```

## Otros métodos útiles

Ya hemos visto cómo definir un hash, y cómo insertar, obtener, eliminar y recorrer elementos de un hash. Otros métodos útiles incluyen:

| Método/Operador | Descripción |
| --- | --- | --- |
| `length` | Retorna el número de elementos en el hash |
| `has_key?` | Retorna `true` si la llave existe  |
| `keys` | Retorna un arreglo con las llaves |
| `values` | Retorna un arreglo con los valres |

Prueba cada uno de los ejemplos en IRB. Puedes encontrar todos los métodos de los hashes en la [documentación de Ruby](https://ruby-doc.org/core-2.3.1/Hash.html).

## Mezclando arreglos y hashes

Es posible mezclar arreglos y hashes para crear estructuras complejas. Para probar crea un archivo llamado `products.rb` y escribe lo siguiente:

```ruby
products = [
  { id: 1, name: "Leche", price: 120, categories: ["familiar", "comida"] },
  { id: 2, name: "Arroz", price: 80, categories: ["familiar", "comida"] },
  { id: 3, name: "Lavadora", price: 7800, categories: ["electrodomésticos"] }
]
```

En este ejemplo hemos creado un arreglo de hashes. Cada hash representa un producto y una de sus llaves (`:categories`) contiene un arreglo. Modifiquemos el programa para imprimir los productos en la consola:

```ruby
products = [
  { id: 1, name: "Leche", price: 120, categories: ["familiar", "comida"] },
  { id: 2, name: "Arroz", price: 80, categories: ["familiar", "comida"] },
  { id: 3, name: "Lavadora", price: 7800, categories: ["electrodomésticos"] }
]

products.each do |product|
  puts product[:name]
  puts "  Id: #{product[:id]}"
  puts "  Precio: #{product[:price]}"
  puts "  Categorias: #{product[:categories].join(", ")}"
  puts "-" * 20
end
```

Lo primero que estamos haciendo es iterando por el arreglo de productos. Por cada uno de los productos (recuerda que esto es un hash) vamos a mostrar el nombre (la llave `:nombre`), después el identificador (la llave `:id`), el precio (la llave `:price`) y las categorías (la llave `:categories`). Como las categorías están en un arreglo debemos utilizar el método `join` para convertirlas en una cadena.

## Evalúate

1. Define un hash a partir de la siguiente tabla y almacénalo en una variable `car`:

        | Llave    | Valor     |
        | :brand   | "Renault" |
        | :year    | 2008      |
        | :price   | 12000     |
        | :color   | :negro    |
        | :sunroof | true      |

2. ¿Cómo podríamos obtener el valor de la llave `:color`?

3. ¿Cómo podemos insertar la llave `:plates` con el valor `"ABC123"`?

4. ¿Cómo podemos modificar el valor de la llave `:year` por `2007`?

5. ¿Cómo podemos eliminar la llave `:sunroof`?

6. Escribe un programa que imprima todas las llaves del hash almacenado en `car` con su respectivo valor.