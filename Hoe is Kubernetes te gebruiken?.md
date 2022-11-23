# Hoe is Kubernetes te gebruiken?

## Inleiding
Ik ga onderzoeken hoe Kubernetes gebruikt kan worden om software projecten schaalbaar te maken, hierbij ga ik 1 of meerdere prototypes bouwen en documenteren. De enige voorkennis die ik over Kubernetes heb opgedaan, is via een [workshop](https://github.com/debugged/workshops) van [Debugged](https://debugged.nl/?gclid=CjwKCAiApvebBhAvEiwAe7mHSN7ONtGM5xsVN1K8ZzEnTrDmJjKs69b7Fgj6jzaR5KVz__UMxisU9RoCQ9wQAvD_BwE).

## Inhoudsopgave
- [Setup](https://github.com/BrucevandeVen/Kubernetes/blob/main/Hoe%20is%20Kubernetes%20te%20gebruiken%3F.md#setup)
- [Docker](https://github.com/BrucevandeVen/Kubernetes/blob/main/Hoe%20is%20Kubernetes%20te%20gebruiken%3F.md#docker)
- [Deployment.yaml](https://github.com/BrucevandeVen/Kubernetes/blob/main/Hoe%20is%20Kubernetes%20te%20gebruiken%3F.md#deploymentyaml)
- [Kubernetes Commands](https://github.com/BrucevandeVen/Kubernetes/blob/main/Hoe%20is%20Kubernetes%20te%20gebruiken%3F.md#kubernetes-commands)

### Setup
Om Kubernetes te kunnen gebruiken moeten er wat voorwerk verricht worden.  
1. Installeer [Docker Desktop](https://docs.docker.com/desktop/install/windows-install/)
2. Ga in Docker Desktop naar instellingen en klik op de Kubernetes tab
3. Vink de checkbox "Enable Kubernetes" aan, nu wordt er een Kubernetes cluster aangemaakt
4. Als dit klaar is met installeren en opstarten ziet het er zo uit:  
![image](https://user-images.githubusercontent.com/58031089/203558343-d999734b-4376-4e1a-af8d-eb8cb7734761.png)


### Docker
Voor mijn prototype heb ik 2 .NET 6 API's gemaakt, deze zet ik op Docker Hub om later te kunnen gebruiken in de Kubernetes omgeving. Vooraf heb ik 2 repositories aangemaakt op Docker Hub, deze namen zijn gelijk aan de image namen.  
  
Commands:  
1. docker build -t [Docker gebruikersnaam]/[image naam] .
2. docker push [Docker gebruikersnaam]/[image naam]:[versie naam]

### Deployment.yaml

### Kubernetes Commands
