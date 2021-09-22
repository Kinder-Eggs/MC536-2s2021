# Aluno
* Gabriel Costa Kinder - 234720

## Tarefa de Cypher sobre Marcadores e Taxonomia

## Tarefa 1

Escreva em Cypher uma consulta que retorne os marcadores da categoria `Serviços`, sem considerar as categorias subordinadas.

### Resolução
~~~cypher
MATCH (m)-[:Pertence]->(:Categoria {id:"Serviços"})
RETURN m
~~~

## Tarefa 2

Escreva em Cypher uma consulta que retorne os marcadores da categoria `Serviços`, considerando as categorias subordinadas.

### Resolução
~~~cypher
MATCH (m:Marcador)-[:Pertence]->(c:Categoria),(d:Categoria {id:"Serviços"})
WHERE (c)-[:Superior *]->(d) OR c.id = "Serviços"
RETURN m
~~~
