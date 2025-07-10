---
layout: default
title: "Format de données"
---

Il y a plein de format de données différents mais globalement, c'est toujours la même chose : on veut donner des caractéristiques à des objets.

Pour ça on va pouvoir les représenter sous forme de dictionnaire : on va associer une clé à une valeur / ou sous forme de tableaux : on va aussi associer des clés à des valeurs.

Finalement tableaux et dictionnaire = même combat.

tous les formats de données : csv, HTML, XML, json, excel, ... représentent des associations clés valeurs + des énumérations. On est juste plus ou moins près du langage machine et de l'interprétabilité.

### DOM

Pour Document Object Model : traite les documents XML ou HTML comme une structure arborescente.
Le DOM permet un accès programmatique à l'arbre.

### BOM

Browser Object Model

### ECMA

---

Le web est séparé en deux entre le HTML et le JSON :

le HTML est pour les humains, le json pour les machines

La représentation des informations sur HTML utilise RDFa qui permet d'utiliser des schemas. C'est le RDFa qui permet d'ajouter des informations dans le code HTML

Json

<!--
{"relation":
    "s": {"text" : "It"},
    "p": {"text": "is"},
    "o": {"text": "a replica",
        "attribute" : {"relation" :
        "p": {"text": "of"},
        "o": {"text": "the grotto"}
        },
        "attribute" : {"relation" : 
        "p": {"text": "in},
        "o": {"text": "Lourdes, France",
            "attribute": {"relation":
                "p": {"text: "where"}
                "o": {"attribute : {"relation":
                    "s": {"text": "Mary"},
                    "p": {"text": "appeared",
                        "mod" : "reputedly"
                        "attribute : 
                            "p" : {"text : "to"}
                            "o": { "text": "Saint Bernadette Soubirous"}
                        }
                    }
                }
            }
        }
    }

{@id : "it"
    "is" : {@id : replica,
            "of" : {@id : grotto
                    "where" : {@id : Mary
                                mod : reputedly
                                appeared to: {@id: Saint Bernadette Soubirous}
                                in : 1858
                            }
                    }
            }
}
Dog of Eve : Eve's Dog

    json query | jq
    Where has Mary Appreared ?
    .o


{@id: Iskandar
    "is in": "the kitchen"}
-->

