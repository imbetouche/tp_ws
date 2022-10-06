# TP curl - comprendre les requêtes et les réponses HTTP

Pour les questions suivantes, vous devez utiliser l'url suivante : https://webhook.site/6f594809-a4b4-483e-841b-0c3b0a00edfe

Pour tous les appels vous devez ajouter un header pour identifier votre appel parmis ceux des autres étudiants : x-student : VOTRE_NOM

## Faire un appel curl : copier la commande exécutée et indiquer la requête et la réponse
-LA REQUETE : curl https://webhook.site/d4ec90aa-8173-48dd-8414-6fb832ea2a26 --Header "x-student:BETOUCHE" -v
_LA REPONSE : 
*   Trying 46.4.105.116:443...
* Connected to webhook.site (46.4.105.116) port 443 (#0)
* ALPN, offering h2
* ALPN, offering http/1.1
* successfully set certificate verify locations:
*  CAfile: /etc/ssl/certs/ca-certificates.crt
*  CApath: /etc/ssl/certs
* TLSv1.3 (OUT), TLS handshake, Client hello (1):
* TLSv1.3 (IN), TLS handshake, Server hello (2):
* TLSv1.3 (IN), TLS handshake, Encrypted Extensions (8):
* TLSv1.3 (IN), TLS handshake, Certificate (11):
* TLSv1.3 (IN), TLS handshake, CERT verify (15):
* TLSv1.3 (IN), TLS handshake, Finished (20):
* TLSv1.3 (OUT), TLS change cipher, Change cipher spec (1):
* TLSv1.3 (OUT), TLS handshake, Finished (20):
* SSL connection using TLSv1.3 / TLS_AES_256_GCM_SHA384
* ALPN, server did not agree to a protocol
* Server certificate:
*  subject: CN=webhook.site
*  start date: Jul 31 23:09:19 2022 GMT
*  expire date: Oct 29 23:09:18 2022 GMT
*  subjectAltName: host "webhook.site" matched cert's "webhook.site"
*  issuer: C=US; O=Let's Encrypt; CN=R3
*  SSL certificate verify ok.
> GET /d4ec90aa-8173-48dd-8414-6fb832ea2a26 HTTP/1.1
> Host: webhook.site
> User-Agent: curl/7.74.0
> Accept: */*
> x-student:BETOUCHE
> 
* TLSv1.3 (IN), TLS handshake, Newsession Ticket (4):
* TLSv1.3 (IN), TLS handshake, Newsession Ticket (4):
* old SSL session ID is stale, removing
* Mark bundle as not supporting multiuse
< HTTP/1.1 200 OK
< Server: nginx
< Content-Type: text/plain; charset=UTF-8
< Transfer-Encoding: chunked
< Vary: Accept-Encoding
< X-Request-Id: 61fd0fd6-14ca-4b8c-bac0-eb0c6dc4471d
< X-Token-Id: d4ec90aa-8173-48dd-8414-6fb832ea2a26
< Cache-Control: no-cache, private
< Date: Thu, 22 Sep 2022 12:38:29 GMT
< 
* Connection #0 to host webhook.site left intact


## Quel est la version du protocole utilisé par le serveur ?
- La version du protocole utilisé esr : curl 7.74.0

## Quels sont les headers que l'on envoie dans la requête ? Quels sont leur sens ?
- x-student:BETOUCHE        => la personne qui fait l'appelle ou l'utilisateur
- Host: webhook.site        => il montre qui est le serveur qui parle
- User-Agent: curl/7.74.0   => un agent softwar qui agit a la place de l'utilisateur
    - Accept: */*               => 

## Quelles informations pouvez-vous trouver à propos du certificat SSL ?
Server certificate:
*  subject: CN=webhook.site
*  start date: Jul 31 23:09:19 2022 GMT
*  expire date: Oct 29 23:09:18 2022 GMT
*  subjectAltName: host "webhook.site" matched cert's "webhook.site"
*  issuer: C=US; O=Let's Encrypt; CN=R3
*  SSL certificate verify ok.


## Quel est le code de la réponse ? Que signifie-t-il ?
200 ok qui est le succee

## Quels headers recevez vous dans la response ? Quels sont leur sens ?

HTTP/1.1 200 OK
< Server: nginx   ==> type du serveur
< Content-Type: text/plain; charset=UTF-8 ==> type du contenue
< Transfer-Encoding: chunked
< Vary: Accept-Encoding
< X-Request-Id: 2f245931-995a-46fb-b0e5-c4db571d313a ==> id de la requette
< X-Token-Id: 6f594809-a4b4-483e-841b-0c3b0a00edfe ==> id du token
< Cache-Control: no-cache, private ==> le cache est privee on peut pas l'utiliser
< Date: Thu, 06 Oct 2022 12:05:23 GMT ==> date et heure de la requette


## Faire un appel curl en envoyant du texte brut : copier la commande exécutée et indiquer la requête et la réponse
curl -X POST --data "salam doing well?" https://webhook.site/6f594809-a4b4-483e-841b-0c3b0a00edfe 
curl -X POST -H "Content-Type: text/plain"  --data "salam doing well?" https://webhook.site/6f594809-a4b4-483e-841b-0c3b0a00edfe

requete 
POST /6f594809-a4b4-483e-841b-0c3b0a00edfe HTTP/1.1
> Host: webhook.site
> User-Agent: curl/7.74.0
> Accept: */*
> Content-Type: text/plain
> Content-Length: 17

reponse 
HTTP/1.1 200 OK
< Server: nginx
< Content-Type: text/plain; charset=UTF-8
< Transfer-Encoding: chunked
< Vary: Accept-Encoding
< X-Request-Id: 4aa84d40-f605-4141-9a09-5941b4bae26d
< X-Token-Id: 6f594809-a4b4-483e-841b-0c3b0a00edfe
< Cache-Control: no-cache, private
< Date: Thu, 06 Oct 2022 12:36:27 GMT

## Faire un appel curl en envoyant du JSON (avec les bons headers) : copier la commande exécutée et indiquer la requête et la réponse
curl -d "auteurs.json" -X POST https://webhook.site/37f00faa-5d4f-4572-97a8-2db3c5b785c5


## Faire une appel curl en envoyant une basic authentication en utilisant 2 méthodes différentes : copier les commandes exécutées et indiquer la requête et la réponse à chaque fois 
methode 1: curl https://webhook.site/37f00faa-5d4f-4572-97a8-2db3c5b785c5 -H "X-student: BETOUCHE" -u "hello" -v

GET /37f00faa-5d4f-4572-97a8-2db3c5b785c5 HTTP/1.1
> Host: webhook.site
> Authorization: Basic aGVsbG86aGVsbGhlbGxv
> User-Agent: curl/7.74.0
> Accept: */*
> X-student: BETOUCHE

HTTP/1.1 200 OK
< Server: nginx
< Content-Type: text/plain; charset=UTF-8
< Transfer-Encoding: chunked
< Vary: Accept-Encoding
< X-Request-Id: 9d231644-c781-47dc-ad8d-5b4f551eb11f
< X-Token-Id: 37f00faa-5d4f-4572-97a8-2db3c5b785c5
< Cache-Control: no-cache, private
< Date: Thu, 06 Oct 2022 13:08:12 GMT
methode 2: curl https://webhook.site/37f00faa-5d4f-4572-97a8-2db3c5b785c5 -H "X-student: BETOUCHE" -H "Authorization: Basic aGVsbG86aGVsbGhlbGxv" -v


## Exécuter la commande suivante avec la méthode GET puis indiquer la réponse : curl https://demo.api-platform.com/books/07dd4786-aaa7-4d08-a467-076b76f1d1b6 


## Exécuter la commande suivante avec la méthode PATCH  puis indiquer la réponse : curl https://demo.api-platform.com/top_books/1


## Quel est le code HTTP reçu ? Quel est sa signification ?


## Exécuter la commande suivante puis indiquer la réponse : curl https://demo.api-platform.com/top_books/1


## Exécuter la commande suivante puis indiquer la réponse : curl https://demo.api-platform.com/top_books/9999


## Quel est le code HTTP ? Que signifie-t-il ?


## Exécuter la requête suivante et copier la réponse : curl https://google.fr


## Quel est le code HTTP reçu ? Pouvez-vous expliquer cette réponse ?


## Comment éviter cette réponse ? Trouvez 2 solutions différentes et détaillez les.
