# Architecture Micro-services avec RestTemplate


##  Architecture générale

L'architecture est composée de quatre services principaux :

###  **Eureka Server**

-   Rôle : registre central où les microservices se déclarent.
-   Permet le **découplage**, la **découverte dynamique** et le **load balancing**.
-   Port par défaut : **8761**

Accès :\
 `http://localhost:8761`

------------------------------------------------------------------------

###  **client-service**

-   Gère les opérations CRUD liées aux **clients**
-   Persisté dans une base MySQL : **clientservicedb**
-   S'enregistre automatiquement auprès d'Eureka
  
<img width="607" height="904" alt="jssssssss" src="https://github.com/user-attachments/assets/362db5d5-f019-40dc-ae2e-99238c9acac7" />

Via Gateway :\
 `http://localhost:8888/client-service/api/client`
 

------------------------------------------------------------------------

###  **voiture-service**

-   Gestion des **voitures**.
-   Chaque voiture est liée à un client, nécessitant un appel REST vers
    SERVICE-CLIENT.
-   Base MySQL : **carservicedb**

<img width="516" height="691" alt="kaaaassssss" src="https://github.com/user-attachments/assets/aed38a4d-c06d-4993-9728-1cdaef1d12aa" />

Via Gateway :\
 `http://localhost:8888/voiture-service/api/car`

------------------------------------------------------------------------

###  **API Gateway -- Spring Cloud Gateway**

-   Point d'entrée unique pour tous les microservices.
-   Routage basé sur les noms de services enregistrés dans Eureka.
-   Simplifie l'accès et protège l'architecture.
-   Port : **8888**

------------------------------------------------------------------------

##  Lancement 

1. Eureka Server
2. SERVICE-CLIENT
3. SERVICE-CAR
4. Gateway
<img width="898" height="425" alt="lance" src="https://github.com/user-attachments/assets/4f81a4f7-4094-47ae-b950-3072df6de803" />

Eureka affichera les microservices enregistrés et prêts à l'emploi.

------------------------------------------------------------------------



