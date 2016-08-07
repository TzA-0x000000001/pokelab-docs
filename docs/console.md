# Classe

La class Console est une classe dédiée au Debug. Elle affiche une console au démarrage du jeu. La classe sert également à y afficher des informations de différentes manières.

### Utilisation basique

	Console.init
	Console.log("Log")
	e = 12
	Console.var("e", binding)

Pour l'usage, merci de vous référer au manuel.

# Constantes

### CHANGE_FONT

Si `true`, tente de modifier la police de la console pour Lucida Console au démarrage de celle-ci. Il est conseillé de laisser à true sauf si la commande ne fonctionne pas (cela peut arriver sur certaines versions de Windows, notamment d'anciennes versions).

### USE_UNICODE

Si `true`, active le support unicode de la console (encodage UTF-8). 

*(Pour rappel, l'UTF-8 est obligatoire pour afficher des caractères spéciaux, dont nos chers accents français.)*

### NO_WARNINGS

Si `true`, désactive l'affichage des warning et des log. Déconseillé lors du développement.

### FORCE_DEBUG

Si `true`, la console sera affichée également si le jeu est lancé en dehors de l'éditeur.

# Méthodes

### self.color(c)

Modifie la couleur du texte et du fond.

`int` c → code couleur (hexadécimal)

	0x0000 # noir
	0x0001 # bleu foncé
	0x0002 # vert foncé
	0x0003 # cyan foncé
	0x0004 # rouge foncé
	0x0005 # rose foncé
	0x0006 # jaune foncé
	0x0007 # gris clair
	0x0008 # gris
	0x0009 # bleu
	0x000a # vert
	0x000b # cyan
	0x000c # rouge
	0x000d # rose
	0x000e # jaune
	0x000f # blanc

### self.debug(msg, line, custom_caller)

Affiche un message de debug (coloration syntaxique).

`string` msg → message à afficher

`bool` line (`true` par défaut) → affiche la ligne où se situe le debug

`caller` custom_caller (`nil` par défaut) → caller spécifique pour la ligne du debug si jamais le debug se situe dans une autre fonction (laisser à nil pour automatique)

### self.debug_a(msg, line, custom_caller)

Affiche un message de debug (coloration syntaxique).
Version ASCII. N'utiliser que dans des cas très spécifiques.

`string` msg → message à afficher

`bool` line (`true` par défaut) → affiche la ligne où se situe le debug

`caller` custom_caller (`nil` par défaut) → caller spécifique pour la ligne du debug si jamais le debug se situe dans une autre fonction (laisser à nil pour automatique)

### self.debug_u(msg, line, custom_caller)

Affiche un message de debug (coloration syntaxique).
Version Unicode. N'utiliser que dans des cas très spécifiques.

`string` msg → message à afficher

`bool` line (`true` par défaut) → affiche la ligne où se situe le debug

`caller` custom_caller (`nil` par défaut) → caller spécifique pour la ligne du debug si jamais le debug se situe dans une autre fonction (laisser à nil pour automatique)

### self.done

Termine l'action en cours.

### self.error(msg, line, custom_caller)

Affiche une erreur.

`string` msg → message à afficher

`bool` line (`true` par défaut) → affiche la ligne où se situe l'erreur

`caller` custom_caller (`nil` par défaut) → caller spécifique pour la ligne de l'erreur si jamais l'erreur se situe dans une autre fonction (laisser à nil pour automatique)

	def afficher_erreur
		Console.error("ceci est une erreur", true, caller.first.split(":""))
	end

	afficher_erreur() # C'est cette ligne qui sera affichée grâce à l'argument custom_caller.

### self.init

Initialise la console. Il est fortement déconseillé de lancer plusieurs consoles.
La console doit être lancée avant tout le reste.

### self.log(msg)

Affiche un log. (console en mode test ou popup en mode jeu)

`string` msg → message à afficher

### self.step(msg)

Affiche une action en cours.

`string` msg → message à afficher

### self.title(msg)

Affiche un titre important.

`string` msg → message à afficher

### self.unicode(msg)

Affiche une chaîne de caractères unicode.

`string` msg → message à afficher

### self.unicode_c(c)

Affiche un caractère unicode

`string` c → caractère à afficher

### self.var(v,b)

Affiche les informations d'une variable.

`string` v → variable entre guillemets
`binding` b → contexte de la variable

	e = 12

	Console.var("e", binding) # Affiche le debug de la variable

### self.warning(msg, line, custom_caller)

Affiche un avertissement.

`string` msg → message à afficher

`bool` line (`true` par défaut) → affiche la ligne où se situe l'avertissement

`caller` custom_caller (`nil` par défaut) → caller spécifique pour la ligne de l'avertissement si jamais l'avertissement se situe dans une autre fonction (laisser à nil pour automatique)

	def afficher_avertissement
		Console.warning("ceci est un avertissement", true, caller.first.split(":""))
	end

	afficher_avertissement() # C'est cette ligne qui sera affichée grâce à l'argument custom_caller.