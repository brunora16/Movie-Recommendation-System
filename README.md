# Sistema de Recomendação de Filmes

## Sobre o Projeto
Este projeto foi desenvolvido por mim e um companheiro de classe como projeto final para a disciplina de Álgebra Linear Algorítmica.

O objetivo é criar um sistema simples de recomendação de filmes. O usuário fornece os IDs e suas avaliações (notas de 1 a 5) para até 5 filmes que já assistiu. Com base nessas preferências, o sistema utiliza técnicas de análise de características (como gêneros e tags) e similaridade para sugerir 5 novos filmes. Adicionalmente, gera um gráfico 2D que visualiza a posição dos filmes avaliados e recomendados em relação aos demais do banco de dados.





## Funcionalidades
Entrada do Usuário: Permite que o usuário insira o ID e a nota (1 a 5) para até 5 filmes.


Processamento de Características: Utiliza gêneros e tags  dos filmes para criar um vetor de características para cada um. Tags recebem um peso maior por serem mais específicas.



Cálculo de Similaridade: Mede quão parecidos os filmes são entre si com base em suas características (usando similaridade de cosseno).



Redução de Dimensionalidade (PCA): Aplica a Análise de Componentes Principais (PCA) para reduzir a dimensionalidade dos vetores de características, permitindo a visualização em 2D e auxiliando no cálculo de diversidade.



Recomendação Balanceada: Combina a similaridade entre os filmes (baseada em características) com a distância no espaço 2D reduzido (para promover diversidade) ao gerar as recomendações.


Visualização Gráfica: Gera um gráfico de dispersão 2D mostrando todos os filmes, destacando os filmes avaliados pelo usuário e os filmes recomendados pelo sistema.


### Defesas Implementadas:

Não recomenda filmes que o usuário já avaliou.



Remove filmes duplicados da lista final de recomendações.



Limita o número de recomendações a 5 filmes.

## Banco de Dados Utilizado
O sistema utiliza o dataset MovieLens Latest (small) fornecido pelo GroupLens. Ele é composto por três arquivos principais:



movies.csv: Contém informações sobre os filmes, como ID (movieId), título e gêneros.


ratings.csv: Contém avaliações de usuários para os filmes (não usado diretamente para a recomendação baseada em conteúdo, mas parte do dataset original).


tags.csv: Contém tags aplicadas por usuários aos filmes, usadas como características adicionais.

Nota: O dataset completo pode ser baixado do site do GroupLens.

## Como Funciona (Visão Geral)

Carregamento e Preparação: Os dados dos arquivos movies.csv, tags.csv e ratings.csv são carregados.



Matriz de Características: Uma matriz é criada onde cada linha representa um filme e as colunas representam suas características (presença de gêneros específicos e tags).


Entrada do Usuário: O sistema solicita ao usuário que digite os IDs dos filmes e suas notas.


Cálculo de Similaridade e PCA: A similaridade de cosseno é calculada entre todos os filmes. O PCA é aplicado para reduzir as características a 2 dimensões.



Geração de Score: Para cada filme avaliado positivamente pelo usuário, um score combinado é calculado para os outros filmes, ponderando a similaridade de características e a distância no espaço 2D (diversidade). Filmes avaliados negativamente podem influenciar negativamente o score de filmes similares.


Classificação e Filtragem: Os filmes são classificados com base nesse score. Filmes já avaliados e duplicatas são removidos.



Saída: Os 5 melhores filmes recomendados são exibidos, junto com um gráfico 2D mostrando a relação espacial entre os filmes.
