--
layout: default
title: "NEO4j"
---

Dans une VM avec neo4j d'installer, on peut relancer une nouvelle base de données avec la commande :
`docker run -d --publish=7475:7474 --publish=7688:7687 --volume=./data:/data neo4j`

En changeant le port public (premier numéro) des publish pour éviter d'utiliser les mêmes.