<!-- README.md -->
Projeto: Mapeamento de Potenciais Clientes e Busca de Estabelecimentos
Este repositório contém dois pipelines de geolocalização e visualização construídos em Python:

RoutingPipeline

Carrega dados de endereços e rotas internos (base_endereco.xlsx, rota.xlsx) e uma base externa de estabelecimentos (base_google.xlsx).

Realiza merge e pré-processamento (filtros de cidade, normalização de endereços, atribuição de cores por rota).

Aplica correspondência fuzzy entre nomes do cliente interno e estabelecimentos do Google (TF-IDF + KNN).

Unifica pontos geograficamente próximos e propaga rota a pontos “red” (sem rota).

Gera um DataFrame final com colunas:

NOME_FANTASIA, ENDERECO, LATITUDE, LONGITUDE,
ROTA_PEDIDO, DISTANCIA, CIDADE, ESTADO, CLIENTE
PlacesPipeline

Varre uma grade de coordenadas dentro de um polígono definido (ex.: limites de Santo André - SP) em pequenos passos (p. ex. 0.01°).

Para cada célula de grade, consulta o Google Places por tipos de estabelecimento (mercado, padaria, conveniência etc.), paginando resultados.

Constrói um DataFrame com:

title, address, reviews, rating, place_id, link, LATITUDE, LONGITUDE, telephone
Gera um mapa Folium marcando cada ponto, com popup e link direto ao Google Maps.

