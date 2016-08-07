# Nommage

## Règle générale

Tous les noms de **méthodes** et de **classes** sont en anglais dans le kit dans un soucis de partage et d'accessibilité. 

**Notez qu'il est important qu'en cas de traduction du kit, aucune méthode, classe ou variable ne doive être renommée.**

## Localisation des symbol

En cas d'utilisation de `symbol`, veillez à garder un nom anglais: la localisation doit apparaît sous forme de `string` modifiable indépendament du code.

## Fonctions du kit

Dans la `class Interpreter`, les noms de méthodes sont en anglais également: la localisation intervient sous forme d'`alias_method`, de la manière suivante:

	def my_function
		print "Some text"
	end
	alias_method :ma_fonction, :my_function

Ainsi, nous conservons la clareté du code. 

# Philosophie

## Une approche purement objet

Nous tenons à utiliser une approche orientée objet. Préfèrez toujours l'héritage plutôt qu'une nouvelle définition ou et une classe qu'un système de tableau ou d'array. C'est bien plus flexible et extensible pour quiconque souhaite ajouter des fonctionnalités au kit.

De la même manière, utilisez les `attr_accessor`, `attr_reader` et `attr_writer` de manière quasiment systématique.

### Exemple

	# Classe

	def initialize()
		@var = 0
	end

	def get_var
		@var
	end

	def set_var(i)
		@var = i
	end

	# Accès

	objet.set_var(12)

Devra être remplacé par

	# Classe

	attr_accessor :var

	def initialize()
		@var = 0
	end

	# Objet

	objet.var = 12

Ce qui est bien plus pratique et plus efficace. Cependant, en cas de génération sur la valeur des variables, n'oubliez pas de remplacer `attr_accessor` par `attr_reader` et d'ajouter une méthode pour définir la variable:

	# Classe

	attr_reader :var

	def initialize()
		@var = 0
	end

	def set_var(i)
		@var = i + 16
	end

	# Accès

	objet.set_var(12)
	objet.var # Renvoie 28

## Utilisation des Array

Nous banissons quasiment systématiquement l'utilisation des `array` pour des `hash` pour tout ce qui est accès aux données. N'oubliez pas d'utiliser, sauf raison particulière, des `symbol` à la place des `string` pour les clés des `hash`.