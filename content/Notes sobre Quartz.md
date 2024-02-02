---
title: Notes sobre Quartz
aliases: 
tags:
  - quartz
description: Notes i comentaris sobre coses que cal tenir en compte de Quartz i coses que no m'agraden
date: 2024-01-02
draft: false
---
>[!note] Nota: 
>Consulta, també, [[Quartz - Flux de treball]]

# 1	Notes i comentaris sobre Quartz

## 1.1	Notes 
### 1.1.1	Instruccions del flux de treball 
1. **`npx quartz build --serve`** 
	1. Genera l’HTML a partir del Markdown
	2. Posa en marxa el servidor local HTTP (http://localhost:8080) que permet visualitzar el lloc en local.
	3. Sincronitza el contingut del celler amb el servidor HTTP local de manera automàtica de manera que els canvis duts a terme al celler, mentre el constructor i servidor estan en marxa, es veuen immediatament al navegador.
2. **`npx quartz sync`** 
	1. Sincronitza l’HTML a GitHub
	2. Podem accedir al codi de GitHub des de l’URL: [https://froses.github.io/froses-notes/](https://froses.github.io/froses-notes/)

### 1.1.2	Configuració de Quartz 

Hi ha dos grans blocs de configuració de Quartz:
- Configuració general
- Disseny

#### 1.1.2.1	Configuració general: `quartz.config.ts`
Destaco, només, els paràmetres que, d’entrada, em semblen més rellevants:

- **`pageTitle`**: Títol del lloc web.
-  **`enablePopovers`**: Per si vols activar les vistes prèvies emergents al teu lloc.
- **`analytics`**: Especificacions sobre qui durà a terme les analítiques del teu lloc web. Pots especificar que no faci analítiques (`null`) o pots triar entre **Plausible** o **Google**. Per defecte, **Plausible** perquè és sensible a la privacitat.
- **`ignorePatterns`**: Llista de patrons [glob](https://en.wikipedia.org/wiki/Glob_(programming)) per especificar quins fitxers ha d’ignorar Quartz. Més informació a la secció [Private Pages](https://quartz.jzhao.xyz/features/private-pages).
- **`defaultDateType`**: Quina data es mostrarà, per defecte, a les pàgines i als llistats de pàgines: data de creació, de modificació o de publicació.
- **`thema`**: Configura l’aspecte del lloc:
	- **`typography`**: Tipus de lletra a utilitzar (Qualsevol de les de [Google Fonts](https://fonts.google.com/)).
	- **`colors`**: Colors per a les diverses parts del lloc (fons de pàgina, vores, enllaços, cos del text, ressaltat…)

#### 1.1.2.2	Connectors

>De moment, no es toca. Hi ha els que hi ha.

### 1.1.3	Configuració de disseny: `quartz.layout.ts`

Cada pàgina està formada per múltiples seccions que contenen **`QuartzComponents`**:

- `head`
- `beforeBody`
	- `BreadCrumbs`: Fil d’Ariadna.
	- `ArticleTitle`: Títol de l’article.
	- `ContentMeta`: Metadades.
	- `TagList`: Llista d’etiquetes.
- `pageBody`
- `left`
	- `PageTitle`: Títol de la pàgina.
	- `Search`: Camp de cerca.
	- `DarkMode`: Icona per assignar el mode fosc o clar.
	- `Explorer`: Explorador de notes (només a escriptori)
- `right`
	- `Graph`: Mapa gràfic del lloc i de la nota que s’estigui mostrant.
	- `TableOfContents`: Llista de les capçaleres de la nota que s’està mostrant (només escriptori)
	- `Backlinks`: Enlaços inversos.
- `footer`

![Parts de la pàgina.](https://quartz.jzhao.xyz/images/quartz-layout.png)


### 1.1.4	Distribució per defecte del web de Quartz

Aquest és l’URL del lloc web de Quartz: [https://quartz.jzhao.xyz/](https://quartz.jzhao.xyz/)

La distribució del lloc web de Quartz és la distribució per defecte i, en definitiva, la que tinc aplicada al lloc web.
#### 1.1.4.1	Banda esquerra
1. Títol del lloc (“Quartz 4.0”)
2. Cercador
3. Selector de mode clar / fosc
4. Explorador

#### 1.1.4.2	Part central

1. La nota que hagis seleccionat a l’explorador i si no n’has seleccionat cap, mostra la pàgina d’inici (`index.html`).
2. Al peu de pàgina, es mostren els crèdits de Quartz, en anglès.

#### 1.1.4.3	Banda dreta
1. Vista gràfica
2. Taula de continguts de la nota que s’estigui visualitzant
3. Enllaços inversos


## 1.2	Comentaris 

### 1.2.1	Coses que no m’acaben d’agradar
- El codi HTML generat no és `responsive`. Això vol dir que els elements situats a una banda i una altra de la nota, no es veuen tret que la finestra es faci més gran. Per exemple, l’explorador de notes no es veu.
- No hi ha possibilitat de treballar totalment des d’un dispositiu mòbil. Podràs escriure, perquè es tracta d’un celler normal, però no podràs desplegar. Ho hauràs de fer des d’un Mac.
- No queda clar si es poden traduir els noms de les seccions. Per exemple, podem aconseguir que digui `Explorador` en comptes d’`Explorer`?
### 1.2.2	Observacions
- On es desa el celler? On sigui, però cal mirar si es pot sincronitzar amb GitHub, només els Markdown. D’aquesta manera, seria multidispositiu.