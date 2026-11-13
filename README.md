# Coruña Corre

Proxecto de análise de datos de carreiras populares de Coruña, centrado na extracción automatizada, limpeza, integración e análise de resultados e participantes.

## 1. Obxectivos

- Extraer de forma automática e responsable os resultados de varias carreiras desde unha web pública, minimizando a carga sobre o sitio e respectando as súas condicións de uso.
- Avaliar a calidade dos datos con pandas, documentar os problemas detectados e aplicar procesos de limpeza e validación para mellorar a súa fiabilidade.
- Integrar a información de resultados e participantes nun mesmo fluxo de traballo, permitindo relacionar as persoas entre distintas carreiras.
- Responder preguntas sobre participación, rendemento e evolución dos corredores mediante análise con pandas e visualizacións gráficas.
- Protexer os datos persoais do proxecto aplicando medidas de pseudonimización, xeneralización e agregación para evitar a identificación directa de individuos.
- Traballar de forma colaborativa con GitHub, usando issues, ramas, pull requests e revisións para manter un fluxo de traballo ordenado e reproducible.

## 2. Descrición do proxecto

Este proxecto combina tres etapas principais:

1. Adquisición de datos mediante scraping de fontes públicas.
2. Preparación e limpeza dos datos para garantir a súa calidade e consistencia.
3. Análise de participación e rendemento, coa xeración de gráficos e informes.

A idea final é construír un pipeline reproducible que transforme datos brutos en información útil para a investigación, a prensa ou a organización de eventos deportivos.

A selección do contido debe centrarse na categoría Absoluta e nas súas subcategorías adultas, excluíndo infantís e xuvenís. Ademais, a última carreira do circuíto non se debe incluir se aínda non se correu.

## 3. Fontes de datos

### 3.1. Resultados de carreiras

- Fonte: `corunacorre.com`
- Contido: para cada carreira dispónse de información sobre categoría, posto, dorsal, nome, sexo, tempo e clasificación.
- Obtención: scraping automatizado das páxinas de resultados de cada proba.

### 3.2. Inscritos no circuíto

- Fonte: `corunacorre.com`
- Contido: lista de persoas inscritas no circuíto completo, con datos de identificación e participación.
- Obtención: scraping da lista de inscritos publicada na web.

### 3.3. Regulamento do circuíto

- Fonte: PDF publicado na web do circuíto.
- Contido: categorías, distancias e normas do circuíto.
- Obtención: lectura do documento PDF e extracción da información relevante, con tratamento manual ou automatizado segundo o formato.

## 4. Tarefas da parte base

Traballaremos nun repositorio chamado `p2-coruna-corre/`, seguindo a estrutura do P1 e ampliándoa coas carpetas necesarias para o tratamento dos datos. A estrutura debe incluír, como mínimo, os directorios:

- `data/raw/`: datos brutos descargados da web
- `data/interim/`: táboas extraídas que aínda conservan nomes, formatos ou campos non normalizados
- `data/clean/`: datos limpos e listos para análise
- `data/externos/`: ficheiros creados polo equipo ou provenientes de fontes externas relevantes
- `src/` ou notebooks: código e análise
- `output/`: gráficos, informes e resultados finais

O obxectivo desta parte é construír a base do pipeline de datos desde a web ata as análises. Para iso, o traballo pode repartirse en varios notebooks numerados, cada un dedicado a unha fase concreta do proceso, por exemplo:

- Notebook 1: adquisición e exploración inicial dos datos
- Notebook 2: extracción de resultados das carreiras
- Notebook 3: extracción da lista de inscritos
- Notebook 4: limpeza e normalización de campos
- Notebook 5: integración das fontes de datos
- Notebook 6: preparación de táboas intermedias e análise inicial
- Notebook 7: elaboración de gráficos e resumo de resultados

A tarefa principal consiste en:

- extraer automaticamente os resultados das carreiras da web;
- gardar os datos en `data/raw/` e `data/interim/`;
- limpar e transformar os ficheiros para preparar unha base de datos consistente;
- integrar a información de carreiras, participantes e regras do circuíto;
- documentar o proceso e os problemas de calidade dos datos;
- preparar a base para responder preguntas sobre participación, rendemento e evolución no circuíto;
- traballar só coa categoría Absoluta e as súas subcategorías adultas, excluíndo infantís e xuvenís;
- ignorar a última carreira do circuíto se aínda non se correu;
- navegar por edición → carreira → categoría e seleccionar as categorías relevantes polo texto da ligazón, non pola posición nin por un número fixo.

Ademais, os datos persoais deben tratarse de forma responsable: aplicar pseudonimización, agregación ou xeneralización sempre que sexa posible, evitando a exposición de información sensible en informes públicos.

A figura 2 resume o recorrido dos datos desde a web ata as análises e as entregas, mostrando como os ficheiros brutos se transforman en táboas intermedias, datos limpos e, finalmente, resultados analíticos listos para presentar.

### 4.1. Organizade o traballo en GitHub

- Creade un repositorio do grupo e protexed a rama `main`: ningunha persoa pode facer push directo, e todo o cambio debe entrar mediante pull request.
- Rexistrade cada tarefa como unha issue, con persoal responsable asignado.
- Traballade cada issue nunha rama propia e abride unha pull request que a peche mediante a referencia `Closes #n`.
- Cada pull request debe ser revisado por outra persoa do grupo antes de integralo: debe haber comentarios sobre o código, cambios pedidos se fai falla e aprobación final.
- Repartide o traballo de maneira equilibrada: todas as persoas do grupo deben ter issues, commits, pull requests e revisións propias.
- Mantede un fluxo de traballo claro e reproducible, garantindo que cada cambio teña un responsable, unha revisión e unha validación previa á fusión.

### 4.2. Antes de descargar

- Comprobade se a web ten `robots.txt` e que di. Se non o ten, explicade que significa iso e que outras normas seguen aplicándose.
- Lede o aviso legal da web e o apartado de protección de datos do regulamento.
- No README, nunha sección de `Legalidade e protección de datos`, explicade: que datos persoais hai, para que os ides usar e que medidas aplicades.

### 4.3. Obtede os resultados

- Descargade con `requests`, cun `User-Agent` propio e unha pausa de polo menos un segundo entre peticións.
- Gardade cada páxina en bytes en `data/raw/`. Se xa existe, non a descarguedes de novo.
- Partindo da páxina da edición actual, descubride as carreiras e a súa categoría Absoluta seguindo as ligazóns.
- Percorrede todas as páxinas de cada categoría sen saber de antemán cantas hai.
- Descargade tamén a lista de inscritos no circuíto.
- Comprobade que o número de filas de cada carreira é coherente co número de páxinas e gardade o resultado en `data/interim/`.
- Os nomes non se mostran. Nas saídas dos notebooks entregados non debe aparecer ningún nome: cando inspeccionedes os datos, eliminade antes esas columnas.

### 4.4. Avaliade a calidade e limpade

- Facede un perfil de cada carreira con pandas: valores baleiros, formatos, duplicados, valores imposibles e valores que significan o mesmo escritos de forma distinta.
- Separade a información mesturada: a columna de posto por sexo inclúe o sexo e o posto (M-3); a de posto por categoría inclúe a categoría, o sexo e o posto (MS2M-1).
- Convertede os tempos a segundos e decidide que facer cos tempos que faltan ou son imposibles. Non os borredes sen máis: marcádeos e explicade a decisión.
- Decidide como tratar as categorías especiais (por exemplo, `Especial` ou `Sen categoría`).
- Redactade un informe de calidade cunha táboa: problema · dimensión (completitude, validez, consistencia, unicidade, exactitude) · carreiras afectadas · cantas filas · como o detectastes · que decidistes.

### 4.5. Integrade os datos

- Unide todas as carreiras nunha soa táboa, cunha columna que identifique a carreira e a súa orde no circuíto.
- Cruzade os resultados coa lista de inscritos para saber, en cada participación, se a persoa está inscrita no circuíto ou corre por proba.
- Ligade as persoas entre carreiras seguindo a seguinte lógica de decisión:
  1. Se a persoa está na lista de inscritos, usase a clave do dorsal fixa do circuíto.
  2. Se non está na lista, comprobase se o dorsal é fiable para esa carreira.
  3. Se o dorsal non é fiable, usase o nome normalizado (maiúsculas, sen tildes, sen espazos dobres).
  4. Se a coincidencia segue sendo ambigua, tratase como caso dubidoso e rexistrase na análise de erros.
- Explicade os erros posibles da ligazón: falsos positivos (dúas persoas tomadas como unha) e falsos negativos (a mesma persoa tomada como dúas). Indicade cantos casos dubidosos atopastes e que decidistes.
- Pseudonimizade: substituíde a persoa por un código calculado con `HMAC-SHA256` e unha chave secreta gardada en `.env`, que non se sube ao repositorio. Todo o grupo debe usar a mesma chave: compartídea por un canal privado, nunca no repositorio.
- Gardade en `data/clean/` unha táboa `participacions.csv` (unha fila por persoa e carreira) sen nomes nin dorsais, e unha táboa `carreiras.csv` (unha fila por carreira). Comprobade que non perdedes nin duplicades filas ao unir.

```python
import hmac, hashlib

codigo = hmac.new(CHAVE, clave_persoa.encode(), hashlib.sha256).hexdigest()[:12]
```

Este proceso queda resumido na seguinte decisión:

- resultaos da carreira + lista de inscritos
- ¿está na lista de inscritos?
- si → clave do dorsal
- non → ¿o dorsal é fiable?
- si → clave do dorsal
- non → nome normalizado
- aplica HMAC-SHA256 para pseudonimizar
- garda `carreiras.csv` e `participacions.csv`

## 5. Legalidade e protección de datos

Neste proxecto trátase información de persoas participantes en carreiras populares, polo que é necesario aplicar un enfoque responsable e conforme coas normas de protección de datos.

### 5.1. Que datos persoais aparecen

Os datos que poden aparecer na web e nos ficheiros de traballo poden incluír:
- nome e apelidos;
- categoría, sexo, idade ou rango de idade;
- resultados de competición;
- dorsal e datos de participación;
- información asociada ás carreiras en que participa cada persoa.

### 5.2. Para que os vamos usar

Este proxecto usa eses datos exclusivamente para:
- analizar participación e rendemento;
- comparar resultados por categoría e tempada;
- elaborar gráficos e estatísticas agregadas;
- producir informes e conclusións sobre o circuíto.

Non se pretende identificar individuos para fins comerciais, de seguimento nin de uso non autorizado.

### 5.3. Medidas que aplicamos

- Eliminación previa de nomes en saídas públicas ou notebooks entregados.
- Pseudonimización ou xeneralización sempre que sexa posible.
- Uso de agregación en gráficos e informes para evitar a identificación individual.
- Redución ao mínimo dos campos necesarios.
- Non exposición de información sensible en documentos públicos.
- Tratamento dos datos só dentro do ámbito do proxecto e con finalidade académica.

## 6. Estrutura do repositorio

```text
coruna-corre-analise/
├── README.md
├── requirements.txt
├── .gitignore
├── .env.example
├── src/
│   ├── __init__.py
│   ├── config.py
│   ├── scraper.py
│   ├── preprocess.py
│   ├── merge_data.py
│   ├── analysis.py
│   └── utils.py
├── scripts/
│   ├── run_pipeline.py
│   └── fetch_data.py
├── data/
│   ├── raw/
│   ├── interim/
│   ├── clean/
│   └── externos/
├── output/
│   ├── charts/
│   └── reports/
├── notebooks/
│   └── exploratory.ipynb
├── tests/
│   ├── __init__.py
│   └── test_preprocess.py
├── docs/
│   └── architecture.md
└── LICENSE
```

## 7. Requisitos

- Python 3.10+
- `pip`
- Git

## 8. Instalación

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## 9. Execución

```bash
python scripts/run_pipeline.py
```

## 10. Analizade

Respondede cada pregunta con pandas, cun resultado, unha gráfica (título, eixos con unidades e lenda se fai falta) e unha frase de interpretación. Se os datos non permiten concluír algo, dicídeo.

### Participación

1. Participantes por sexo en cada carreira e evolución ao longo do circuíto.
2. Distribución por categorías de idade e diferenza entre sexos dentro de cada categoría.

### Inscritos no circuíto e corredores por proba

1. En cada carreira, que porcentaxe de participantes están inscritos no circuíto e que porcentaxe corren por proba? Cambia ao longo do ano?
2. En cantas carreiras participa de media unha persoa inscrita no circuíto? Cantas corren todas as carreiras, cantas abandonan e en que momento?

1. Repiten as persoas que corren por proba? Hai quen corre varias carreiras sen inscribirse no circuíto?
2. Hai diferenzas por sexo e categoría entre inscritos no circuíto e corredores por proba?
3. Os inscritos no circuíto quedan en mellores postos que os corredores por proba?

### Rendemento

1. Distribución dos tempos por categoría e sexo.
2. Quen mellora máis entre a primeira e a última carreira en que participa? Melloran máis os inscritos no circuíto?

Pista para a pregunta 9: os percorridos non son idénticos, así que comparar tempos directamente pode enganar. Probade a usar a posición relativa de cada persoa na carreira (o seu percentil dentro do seu sexo) e comparádea coa mellora en tempo. Explicade que medida escollestes e por que.

## 11. Protexede os datos segundo o destinatario

Preparade unha entrega distinta para cada un destes destinatarios e gardádeas en `output/`. Para cada unha, explicade no README que datos contén, que técnicas aplicastes e por que.

| Destinatario | Que necesita | Que se espera |
|---|---|---|
| Nota de prensa ou web municipal | Cifras de participación por carreira, sexo e categoría | Só táboas agregadas, sen ningunha persoa identificable |
| Equipo de investigación sobre rendemento deportivo | Datos fila a fila para estudar a evolución das persoas ao longo do circuíto | Pseudonimización con HMAC-SHA256, cuasi-identificadores xeneralizados e `k` calculado e explicado |
| Organización do circuíto | Saber quen corre cada carreira para xestionar o circuíto | Xustificación de que datos son necesarios e cales non, e que non se poden reenviar a terceiros |

Para cada entrega, o arquivo debe ir dentro de `output/` e debe incluír unha explicación breve sobre:

- que datos contén;
- que nivel de agregación ou anonimización aplica;
- que técnicas se usaron (agregación, xeneralización, pseudonimización, HMAC, eliminación de dorsais ou nomes);
- por que esa versión é adecuada para ese destinatario.

## 4.8. Documentade

O README debe incluír toda a documentación do proxecto para que calquera persoa poida reproducir o fluxo, comprender as decisións e revisar o traballo. Neste apartado recóllense os elementos mínimos que deben aparecer no documento final.

### Descrición do proxecto e das fontes

- Descrición do proxecto: finalidade, alcance, fonte dos datos e contexto do circuíto de carreiras de Coruña.
- Fontes de datos:
  - Resultados de carreiras: `https://www.corunacorre.com` (ou URL exacta da edición/resultado consultada)
  - Lista de inscritos: `https://www.corunacorre.com`
  - Regulamento do circuíto: PDF publicado na web do circuíto
- Data de descarga:
  - `DD/MM/AAAA` da última descarga realizada
  - indicar se foi unha única descarga ou varias iteracións

### Execución paso a paso

1. Crear o entorno virtual.
2. Instalar as dependencias.
3. Crear o ficheiro `.env` co seguinte formato:

```bash
CHAVE_PERSOA=tu_clave_secreta_aqui
```

4. Executar:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python scripts/run_pipeline.py
```

5. Comprobar que se xeneran os ficheiros en `data/raw/`, `data/interim/`, `data/clean/` e `output/`.

### Legalidade e protección de datos

- Explicar o `robots.txt` da web e o seu significado.
- Comentar se non existe e que normas seguiron aplicándose.
- Indicar o aviso legal da web e o apartado de protección de datos consultado.
- Explicar que datos persoais aparecen, para que se usan e que medidas se aplican.
- Describir a pseudonimización con HMAC-SHA256 e o uso dunha chave secreta gardada en `.env` e non subida ao repositorio.

### Informe de calidade e decisións de limpeza

- Recoller un informe con problemas detectados por carreira.
- Indicar dimensión afectada: completitude, validez, consistencia, unicidade ou exactitude.
- Describir as decisións tomadas sobre:
  - tempos baleiros ou imposibles;
  - columnas mesturadas (`posto por sexo`, `posto por categoría`);
  - categorías especiais (`Especial`, `Sin categoría`);
  - duplicados e valores equivalentes con formato distinto.
- Explicar que se marcou e que se decidiu conservar, transformar ou descartar.

### Decisións de integración

- Explicar como se ligaron as persoas entre carreiras.
- Describir a prioridade da decisión:
  - lista de inscritos → dorsal fixo;
  - dorsal fiable → dorsal;
  - dorsal non fiable → nome normalizado;
  - caso dubidoso → rexistro especial e revisión manual.
- Explicar os principais erros de ligazón:
  - falsos positivos;
  - falsos negativos;
  - casos dubidosos detectados.
- Indicar a estratégia final adoptada e o número de casos duros que quedaron sen resolución.

### Entregas para cada destinatario

- Describir o contenido de cada entrega en `output/` e o público ao que vai dirixida.
- Explicar en cada caso:
  - que datos contén;
  - que nivel de agregación ou anonimización aplica;
  - por que esa versión é adecuada para ese destinatario.

### Partes opcionais realizadas

- Indicar calquera traballo complementario realizado, como:
  - notebooks extra;
  - ficheiros auxiliares;
  - análises exploratorias;
  - informes adicionais;
  - scripts de apoio.

#### O1. Meteoroloxía

- Obtede o tempo de cada día de carreira (temperatura e precipitación) dunha fonte aberta, por exemplo MeteoGalicia, e gardádeo en `data/externos/`.
- Integrádeo na táboa `carreiras.csv`.
- Respondede: inflúe a choiva na participación, sobre todo na de quen corre por proba? Inflúe a temperatura nos tempos?
- Con poucas carreiras, a resposta honesta pode ser que non se pode concluír. Explicade por que.

#### O2. San Silvestre

- Descargade a clasificación da última edición da San Silvestre da Coruña (`sansilvestrecoruna.com`), coas mesmas boas prácticas.
- Ligade as persoas co circuíto. Non hai ningunha clave común: usade o nome normalizado (por exemplo, a través do mesmo código HMAC) e explicade os erros posibles.
- Respondede: cantas persoas da San Silvestre correron despois algunha carreira do circuíto? Cantas se inscribiron no circuíto? Como son por sexo e idade?

#### O3. Edición anterior do circuíto

- Descargade unha edición anterior do circuíto desde o histórico da web. Se o formato cambia, adaptade o código sen duplicalo.
- Comparade as dúas edicións: participación por sexo e categoría, persoas que repiten dun ano a outro e evolución dos tempos.

#### O4. Clasificación do circuíto

- Calculade a clasificación do circuíto aplicando as normas de puntuación do regulamento.
- Descargade a clasificación que publica a web e comparádea coa vosa persoa a persoa.
- Explicade as diferenzas que atopedes: erros vosos, casos que o regulamento non deixa claros ou posibles erros da clasificación publicada.

### Presentación

- Incluir o enlace á presentación final en `presentacion/`:

```text
presentacion/
├── ...
```

- Se a presentación está no repositorio, indicar a ruta exacta e un resumo do que contén.

### Reparto do traballo

- Indicar que fixo cada persoa do grupo.
- Incluir ligazóns ás issues, ramas e pull requests relevantes.
- Exemplo:

```text
Ana: issue #12, rama ana/feature-scraping, PR #23
Berto: issue #15, rama berto/quality-report, PR #24
...
```

Se non se dispón de números definitivos, deixar os marcadores como placeholders para completar ao final do proxecto.

### Uso da IA

- Explicar cando se usou IA no proxecto: para axuda na análise, organización do código, redacción de explicacións, depuración ou revisión de textos.
- Indicar que a IA non substituíu a decisión final do grupo e que o código e os resultados foron revisados polo equipo.
- Se se usaron prompts ou ferramentas concretas, mencionalos de forma breve.

## 12. Colaboración

O proxecto xestionarase seguindo boas prácticas de desenvolvemento con GitHub:

- issues para tarefas e seguimento;
- ramas por funcionalidade ou problema;
- pull requests con revisión de código;
- commits claros e documentación mínima do cambio.

## 13. Licenza

Consultar a licenza do proxecto segundo corresponda.
