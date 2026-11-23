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

Dentro de cada carreira aparecen as categorías dispoñibles para consultar as clasificacións.

Ao seleccionar a categoría «Absoluta» accédese á táboa cos resultados dos participantes desa carreira e categoría.

Esta navegación permite establecer a seguinte estrutura xerárquica para a extracción dos datos:

**Edición → Carreira → Categoría → Resultados.**

## 4. Exclusións

O proceso automatizado deberá identificar a categoría Absoluta e as súas subcategorías adultas, evitando extraer as clasificacións correspondentes ás categorías infantís e xuvenís.

Para iso, a identificación das categorías deberá realizarse mediante a súa denominación ou texto, evitando depender da posición que ocupen na páxina ou dun número fixo de ligazóns.

## 5. Última carreira

## 6. Elementos indispensables para scrapping