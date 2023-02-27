# Productes fabricats

Hem d'ampliar el programa amb un nou tipus de productes, els que es poden fabricar amb productes en estoc.

Per exemple les armes a un videojoc:

![image](https://user-images.githubusercontent.com/110727546/221373787-f84cea5f-f792-4c4f-9fff-22a668aa7f6b.png)

![image](https://user-images.githubusercontent.com/110727546/221373833-a197cb00-5110-46f9-b434-ed5d2e7c7bbf.png)

![image](https://user-images.githubusercontent.com/110727546/221373884-7a2f8c67-0dcb-4644-a12b-6b249fe68ccb.png)

Tot i que en realitat és habitual haver de fabricar coses dins d'una empresa sense necessitat de que apareguin zombies.

Així el nostre programa ara tindrà una altra taula anomenada llistatMaterials, aquesta taula contindrà les quantitats de cada producte necessaris per fabricar un altre producte.

## llistatMaterials:

| Materials  | | |
| ----------- | ----------- |----------- |
| idMaterial | INT | PK |
| producteFabricat | INT | FK (productesFabricats) |
| idProducte | INT | FK (productes) |
| quantitat | INT | |

## ProductesFabricats:

| ProductesFabricats  | | |
| ----------- | ----------- |----------- |
| idProducteFabricat | INT | PK |
| nom | Varchar |  |


### Exemple llança:

Així si tenim per exemple el producte llança, el qual necessita per fabricar-se:

- Un pal d'escombra
- 0.1 de cinta americana
- 1 ganivet de cacera:

| Taula productes | 
| ----------- | 
| idProducte = 40 |
| nom = Llança |
| preu = 100 |
| idProducte = 1 |
| nom = pal escombra |
| preu = 10 |
| idProducte = 2 |
| nom = cinta americana |
| preu = 5 |
| idProducte = 3 |
| nom = ganivet cacera |
| preu = 72 |

| Taula llistatMaterials | 
| ----------- | 
| idProducteFabricat = 40 |
| idProducte = 1 |
| quantitat = 1 |
| idProducteFabricat = 40 |
| idProducte = 2 |
| quantitat = 0.1 |
| idProducteFabricat = 40 |
| idProducte = 3 |
| quantitat = 1 |

![image](https://user-images.githubusercontent.com/110727546/221374290-0b3f5b97-af67-4fe7-851b-e3926b0ded00.png)

## Exercici:

- Implementem la taula llistatMaterials i productesFabricats.
- Crearem dos productes fabricats que necessitin almenys 2 productes per fabricar-se.
- Crearem una part nova del programa, fabricació de productes, amb les següents seccions:
  - Llistat de productes a fabricar i la seva "recepta", materials necessaris i quantitat dels mateixos.
  - Previsió de fabricació: Indiquem un producte i la quantitat que volem fabricar i ens indica els materials necessaris per fabricar-ho tot.
  - Estoc de productes a fabricar: Ens llista la quantitat de productes fabricats que podem construïr amb la quantitat de estoc dels productes actuals.



