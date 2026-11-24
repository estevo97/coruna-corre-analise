# Estrutura da web *corunacorre.com*

Neste informe explícase en detalle a estrutura da web *corunacorre.com*: edicións do circuito, carreiras realizadas e categorías. Determñinase como identificar a categoría Absoluta e como excluír as demáis categorías, así como a identificar a última carreira realizada e comprobar se de veras xa se disputou. 

Documéntase os elementos necesarios para scraping.

## 1. Organización xeral da web.

A páxina web oficial do circuíto é corunacorre.com.

No menú principal aparecen diferentes seccións: Eventos, Información, Galerías, Inscrición, Percorridos e Resultados.

### Regulamento do circuito (PDF)

Dentro de Información atópase o apartado «Reglamento del circuito», desde o que se pode descargar o regulamento oficial en formato PDF. Este documento describe o funcionamento do circuíto e establece que cada edición está composta por sete carreiras populares, a saber: 

- 1. Carreira Popular Torre de Hércules.

- 2. Carreira Popular Matogrande-Xuxán.

- 3. Baixada Popular de Cross San Pedro de Visma.

- 4. Carreira Popular Os Rosales.

- 5. Carreira Popular Volta a Oza.

- 6. Carreira Popular Ventorrillo.

- 7. Carreira Popular Novo Mesoiro.

## 2. Navegación

A sección «Resultados» permite consultar as clasificacións do circuíto. Dentro desta sección aparecen dúas opcións principais:

- Edición actual: permite consultar os resultados da edición máis recente.

- Histórico: permite acceder a edicións anteriores.

Ao seleccionar «Edición actual» aparece a posibilidade de escoller entre diferentes edicións. Durante a exploración identificáronse a edición actual, a de 2025 e a de 2024.

Unha vez seleccionada a edición que se quere consultar, aparecen dúas modalidades de consulta:

- Circuito: permite consultar información relacionada coa clasificación xeral do circuíto.

- Por evento: permite acceder aos resultados individuais de cada unha das carreiras que forman a edición.

Para extraer os resultados de cada carreira deberase seleccionar a opción «Por evento».

Nesta vista aparecen as sete carreiras do circuíto. Ao seleccionar unha delas accédese á páxina correspondente, na que se presentan as diferentes categorías nas que se publican os resultados.

## 3. Categorías

Dentro de cada carreira aparece un selector que permite escoller entre as diferentes categorías dispoñibles para consultar as clasificacións.

Para este proxecto interesa a categoría «ABSOLUTA (2008 e anteriores)», que agrupa os participantes adultos.

Ao seleccionala accédese a unha única táboa clasificatoria que permite consultar os resultados filtrados por diferentes subcategorías de idade (Máster 1 Masculino, Máster 2 Masculino, Máster 2 Feminino, etc.).

## 4. Exclusións

Para o scraping extraerase a táboa completa da categoría Absoluta, sen aplicar filtros adicionais, excluíndo así as restantes categorías infantís e xuvenís.

A estrutura de extracción será:

Edición → Carreira → Categoría → Resultados.

## 5. Última carreira

Para identificar a última carreira da edición, consultarase a sección «Eventos», onde aparecen as probas programadas para o circuíto.

Seleccionarase a última carreira da lista e accederase á súa ficha individual, na que se pode consultar a data de celebración.

## 5. Última carreira

Para identificar a última carreira da edición, accederase á sección «Eventos» e percorreranse as ligazóns de todas as carreiras dispoñibles.

Accederase á ficha individual de cada evento para obter a súa data de celebración. Unha vez recollidas todas as datas, compararanse para identificar a carreira máis recente.

Para comprobar se xa se celebrou, verificarase que a súa data sexa anterior ou igual á data actual e que os resultados da categoría Absoluta estean publicados en «Resultados → Edición actual → Por evento».

## 6. Elementos indispensables para scraping

Para implementar o scraper será necesario identificar os elementos que permiten navegar polas diferentes seccións da web e localizar os resultados das carreiras.

Os elementos principais que se deberán identificar son:

- **Eventos:** ligazóns ás carreiras e datas de celebración das súas fichas individuais.
- **Resultados:** ligazóns ás edicións dispoñibles.
- **Edición:** acceso á modalidade «Por evento».
- **Por evento:** ligazóns ás carreiras que forman parte da edición.
- **Carreira:** selector de categorías e identificación da opción «ABSOLUTA (2008 e anteriores)».
- **Resultados:** táboa clasificatoria correspondente á categoría Absoluta e, se existen, controis para navegar entre as distintas páxinas de resultados.

A categoría Absoluta agrupa os participantes adultos nunha única táboa clasificatoria. Dentro dela existen subcategorías por idade e sexo, que funcionan como filtros da mesma táboa. Polo tanto, para este proxecto extraerase a clasificación completa da categoría Absoluta, sen aplicar filtros adicionais, excluíndo así as categorías infantís e xuvenís.

Da táboa clasificatoria identificáronse os seguintes campos:

- Posto xeral.
- Dorsal.
- Nome e apelidos.
- Posto por sexo.
- Posto por categoría.
- Tempo.

Será necesario identificar as ligazóns, os elementos HTML correspondentes e os seus atributos (por exemplo, `href`, `id` ou `class`) para facilitar a navegación automatizada e a posterior extracción dos datos.

### 6.1. Legalidade e protección de datos

**Robots.txt**

A web `corunacorre.com` non dispón dun ficheiro `robots.txt`. Ao acceder a `https://corunacorre.com/robots.txt`, o servidor devolve un erro HTTP 404 (Not Found).

Isto significa que non hai instrucións específicas para robots automatizados publicadas neste ficheiro. Porén, a súa ausencia non implica que a extracción automatizada estea automaticamente autorizada nin exime de respectar as condicións de uso da web e a normativa de protección de datos.

**Aviso legal e protección de datos**

O aviso legal de corunacorre.com identifica a Multisports Galicia, S.L. como titular da web. Nel establécese que o uso da información persoal obtida da plataforma está limitado á xestión deportiva do evento correspondente e que non se permite a cesión destes datos para outras finalidades non contempladas na política de protección de datos.

A política de privacidade identifica a Multisports Galicia, S.L.U. como responsable do tratamento dos datos na plataforma. Entre as finalidades indicadas figura a publicación dos resultados das actividades deportivas. Tamén contempla a comunicación dos datos ás entidades organizadoras dos eventos.

Pola súa parte, o artigo 13 do regulamento do Circuíto Coruña Corre identifica o Concello da Coruña como responsable do tratamento dos datos necesarios para a inscrición, o rexistro e o desenvolvemento das actividades deportivas. Tamén contempla a publicación de nomes e imaxes das persoas participantes co seu consentimento.

**Datos persoais e medidas de protección**

Os resultados deportivos poden conter datos persoais como nome e apelidos, dorsal, sexo, categoría, posición e tempo. Estes datos utilizaranse exclusivamente para a análise deportiva prevista neste proxecto.

Para protexer a privacidade dos participantes:

- Non se mostrarán nomes nin apelidos nas saídas dos notebooks.
- Eliminaranse as columnas que conteñan nomes antes de visualizar ou imprimir os datos.
- Non se publicarán nin compartirán datos persoais innecesarios.
- Limitarase o acceso aos ficheiros descargados e evitarase incluír datos persoais no repositorio.

**Acceso responsable á web**
    
As descargas realizaranse identificando o cliente mediante un `User-Agent` propio e respectando unha pausa mínima dun segundo entre peticións, evitando solicitudes innecesarias ao servidor.