UD2 – PRÀCTICA 4

Marc Brines Bañuls 2 ASIX IAW

Abans de començar amb instal·lacions anem a actualitzar el server per si hi ha paquets a actualitzar nous.

![](Aspose.Words.300e21ce-36a0-4350-96a3-af99e917fbf5.001.jpeg)

*Fig 1: Update a la màquina server.*

![](Aspose.Words.300e21ce-36a0-4350-96a3-af99e917fbf5.002.png)

*Fig 2: Upgrade de la màquina*

![](Aspose.Words.300e21ce-36a0-4350-96a3-af99e917fbf5.003.jpeg)

*Fig 3: Instal·lació de les ferramentes necesaries.*

![](Aspose.Words.300e21ce-36a0-4350-96a3-af99e917fbf5.004.png)

*Fig 4: Ens asegurem de que funciona.*

![](Aspose.Words.300e21ce-36a0-4350-96a3-af99e917fbf5.005.png)

*Fig 5: Agafem el usuari root i establim un tipus de contrasenya i una contrasenya.*

![](Aspose.Words.300e21ce-36a0-4350-96a3-af99e917fbf5.006.png)

*Fig 6: Apliquem els canvis.*

![](Aspose.Words.300e21ce-36a0-4350-96a3-af99e917fbf5.007.png)

*Fig 7: Verifiquem les pases anteriors.*

![](Aspose.Words.300e21ce-36a0-4350-96a3-af99e917fbf5.008.png)

*Fig 8: Creem el usuari dedicat al phpMyAdmin.*

![](Aspose.Words.300e21ce-36a0-4350-96a3-af99e917fbf5.009.png)

*Fig 9: Instal·lem el phpmyadmin i durant la instal·lació hem de sel·leccionar apache2.*

![](Aspose.Words.300e21ce-36a0-4350-96a3-af99e917fbf5.010.png)

*Fig 10: Fiquem que si al pas de l’imatge.*

![](Aspose.Words.300e21ce-36a0-4350-96a3-af99e917fbf5.011.png)

*Fig 11: Fiquem una contrasenya al phpmyadmin.*

Editem el fitxer de configuració del defaut, i enves de descomentar, he afegit el text següent per a previndre falles.

![](Aspose.Words.300e21ce-36a0-4350-96a3-af99e917fbf5.012.jpeg)

*Fig 12: Afegit al default*

![](Aspose.Words.300e21ce-36a0-4350-96a3-af99e917fbf5.013.jpeg)

*Fig 13: Reiniciem el servici i comprovem.*

![](Aspose.Words.300e21ce-36a0-4350-96a3-af99e917fbf5.014.jpeg)

*Fig 14: Altra comprovacio de altra forma.*

Des d’altra màquina conectada a la red del server entrem al navegador per a comprovar que ha funcionat tota la configuració anterior i ens apareix la GUI de phpmyadmin.

![](Aspose.Words.300e21ce-36a0-4350-96a3-af99e917fbf5.015.jpeg)

*Fig 15: Comprovació.*

![](Aspose.Words.300e21ce-36a0-4350-96a3-af99e917fbf5.016.jpeg)

*Fig 16: Fiquem usuari root i contrasenya que hem establit abans.*

![](Aspose.Words.300e21ce-36a0-4350-96a3-af99e917fbf5.017.png)

*Fig 17: Cambiem el metode de autenticació de root.*

![](Aspose.Words.300e21ce-36a0-4350-96a3-af99e917fbf5.018.jpeg)

*Fig 18: Comprovació.*

![](Aspose.Words.300e21ce-36a0-4350-96a3-af99e917fbf5.019.png)

*Fig 19: Ara anem a crear un usuari per a gastar.* Després d’instal·lar el htpasswd anem a emmagatzemar credencials de dos usuaris.

![](Aspose.Words.300e21ce-36a0-4350-96a3-af99e917fbf5.020.png)

*Fig 20: Fiquem dos usuaris.*

![](Aspose.Words.300e21ce-36a0-4350-96a3-af99e917fbf5.021.jpeg)

*Fig 21:  Editem el site de nginx i afegim la 4 i 5 línea.*

Una  vegada  acabem  fem  per  terminal  es  següent  comandament,  i  per  a  comprovar  anem  al phpmyadmin GUI i recarreguem on deuria de demanar-nos noves credencials.

![](Aspose.Words.300e21ce-36a0-4350-96a3-af99e917fbf5.022.png)

*Fig 22: Carreguem el nginx.*

![](Aspose.Words.300e21ce-36a0-4350-96a3-af99e917fbf5.023.jpeg)

*Fig 23: Iniciem amb el nou usuari que hem guardat anteriorment.*

![](Aspose.Words.300e21ce-36a0-4350-96a3-af99e917fbf5.024.png)

*Fig 24: Afegim seguretat al fitxer de la contrasenya.*

Ara anem a fer una guia també pas a pas per a pujar aquest projecte al github pages com feem anteriorment, com sempre, abans de res anem a crear el repositori a github.

![](Aspose.Words.300e21ce-36a0-4350-96a3-af99e917fbf5.025.png)

*Fig 25: Creació del repositori.*

![](Aspose.Words.300e21ce-36a0-4350-96a3-af99e917fbf5.026.png)

*Fig 26: Creació del directori.*

![](Aspose.Words.300e21ce-36a0-4350-96a3-af99e917fbf5.027.png)

*Fig 27: Creació del index.*

Marc Brines Bañuls 10 ASIX IAW

10

![](Aspose.Words.300e21ce-36a0-4350-96a3-af99e917fbf5.028.png)

*Fig 28: Inicialització del repositori.*

***Falta el git add . Que no m’he donat conter de la captura i el commit.***

![](Aspose.Words.300e21ce-36a0-4350-96a3-af99e917fbf5.029.png)

*Fig 29: Pujem la branca i conectem repositori.*

![](Aspose.Words.300e21ce-36a0-4350-96a3-af99e917fbf5.030.png)

*Fig 30: Pujem el fitxer. I fem un mkdocs gh-deploy per a les pages.*

Com durant la instal·lació no he fet servir els scripts ja que no se fer-los i per no copiar directament, ja que he seguit els pases de la web, vaig a ficar al mkdocs un enllaç on durà a escripts que diu la pràctica per a automatitzar punts de la instl·lació i configuració.
Marc Brines Bañuls 1 ASIX IAW

1
