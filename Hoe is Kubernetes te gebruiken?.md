# Hoe is Kubernetes te gebruiken?

## Inleiding
Ik ga onderzoeken hoe Kubernetes gebruikt kan worden om software projecten schaalbaar te maken, hierbij ga ik 1 of meerdere prototypes bouwen en documenteren. De enige voorkennis die ik over Kubernetes heb opgedaan, is via een [workshop](https://github.com/debugged/workshops) van [Debugged](https://debugged.nl/?gclid=CjwKCAiApvebBhAvEiwAe7mHSN7ONtGM5xsVN1K8ZzEnTrDmJjKs69b7Fgj6jzaR5KVz__UMxisU9RoCQ9wQAvD_BwE).

## Inhoudsopgave
- [Setup](https://github.com/BrucevandeVen/Kubernetes/blob/main/Hoe%20is%20Kubernetes%20te%20gebruiken%3F.md#setup)
- [Docker](https://github.com/BrucevandeVen/Kubernetes/blob/main/Hoe%20is%20Kubernetes%20te%20gebruiken%3F.md#docker)
- [Deployment.yaml](https://github.com/BrucevandeVen/Kubernetes/blob/main/Hoe%20is%20Kubernetes%20te%20gebruiken%3F.md#deploymentyaml)
- [Kubernetes Commands](https://github.com/BrucevandeVen/Kubernetes/blob/main/Hoe%20is%20Kubernetes%20te%20gebruiken%3F.md#kubernetes-commands)
- [NodePorts](https://github.com/BrucevandeVen/Kubernetes/edit/main/Hoe%20is%20Kubernetes%20te%20gebruiken%3F.md#nodeports)

### Setup  
Gebruikte DOT Framework Methodes:
- Field, Document Analysis
- Workshop, Prototyping
- Library, Literature Study
- Library, Community research
- Library, Available Product Analysis  
  
Om Kubernetes te kunnen gebruiken moeten er wat voorwerk verricht worden.  
1. Installeer [Docker Desktop](https://docs.docker.com/desktop/install/windows-install/)
2. Ga in Docker Desktop naar instellingen en klik op de Kubernetes tab
3. Vink de checkbox "Enable Kubernetes" aan, nu wordt er een Kubernetes cluster aangemaakt
4. Als dit klaar is met installeren en opstarten ziet het er zo uit:  
![image](https://user-images.githubusercontent.com/58031089/203558343-d999734b-4376-4e1a-af8d-eb8cb7734761.png)

### Docker  
Gebruikte DOT Framework Methodes:
- Field, Document Analysis
- Workshop, Prototyping
- Library, Literature Study
- Library, Community research
- Library, Available Product Analysis  
  
Voor mijn prototype heb ik 2 .NET 6 API's gemaakt, deze zet ik op Docker Hub om later te kunnen gebruiken in de Kubernetes omgeving. Vooraf heb ik 2 repositories aangemaakt op Docker Hub, deze namen zijn gelijk aan de image namen.  
  
Commands:  
```
docker build -t [Docker gebruikersnaam]/[image naam] .
```
```
docker push [Docker gebruikersnaam]/[image naam]:[versie naam]
```
De repositories op Docker Hub:  
![image](https://user-images.githubusercontent.com/58031089/203558722-360224cd-8a60-4762-9b50-d92d75bf7dff.png)

### Deployment.yaml  
Gebruikte DOT Framework Methodes:
- Field, Document Analysis
- Workshop, Prototyping
- Library, Literature Study
- Library, Community research
- Library, Available Product Analysis  
  
In de Kubernetes deployment.yaml worden de Docker images weer opgehaald van Docker Hub om te gebruiken in de Kubernet cluster. Als eerste probeer ik 1 pod aan te maken en te deployen in de Kubernetes cluster die 1 API bevat. De yaml file heet collectionapi-depl.yaml.  
De yaml file:  
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: collectionapi-depl
spec:
  replicas: 1
  selector:
    matchLabels:
      app: collectionservice
  template:
    metadata:
      labels:
        app: collectionservice
    spec:
      containers:
        - name: collectionservice
          image: brucevandeven/collectionapi:latest
```
"name:" is de naam van de deployment.  
"replicas:" staat voor het aantal instanties of pods.  
"app:" is de naam van de pod.  
"containers:" zijn de gespicificeerde containers die opgehaald moeten worden op te deployen.  

### Kubernetes Commands  
Gebruikte DOT Framework Methodes:
- Workshop, Prototyping
- Field, Document Analysis
- Library, Literature Study
- Library, Community research
- Library, Available Product Analysis  
  
Om de deployment.yaml file uit te kunnen voeren kan de command line gebruikt worden. Als de Setup goed gevolgt is kan de command "kubectl" gebruikt worden, om te testen of kubectl werkt gebruik deze command:  
```
kubectl get nodes
```
![image](https://user-images.githubusercontent.com/58031089/203567294-75874dd5-7472-4593-bba2-f78269fe8cf1.png)  
Als de nodes niet worden weergegeven moet waarschijnlijk de context veranderd worden naar docker-desktop met deze commands:  
```
kubectl config get-contexts
```
```
kubectl config use-context docker-desktop
```
meer informatie hierover op [docs.docker](https://docs.docker.com/desktop/kubernetes/#use-the-kubectl-command).  
  
Om de yaml file uit te voeren moet er een command worden uitgevoerd, dit is ook het moment om er achter te komen dat er iets mis kan zijn met je yaml file:  
```
kubectl apply -f collectionapi-depl.yaml
```
Hierna kan er met 2 commands gekeken worden of het heeft gewerkt:  
```
kubectl get pods
```
```
kubectl get deployments
```
In Docker Desktop is te zien dat er een Pod en een Container is aangemaakt en draaien:  
![image](https://user-images.githubusercontent.com/58031089/203575327-7bd8b1e8-2afb-4c52-8c24-465902f84049.png)  

### NodePort, LoadBalancer and Ingress Controller
Gebruikte DOT Framework Methodes:  
- Field, Interview
- Field, Document Analysis
- Library, Literature Study
- Library, Community research
- Library, Available Product Analysis  
  
NodePorts kunnen worden gebruikt om tijdens de ontwikkelen te verbinden met de verschillende pods binnen een Node, echter is het af te raden te gebruiken en in plaats daarvan een Ingress controller te gebruiken.  
Er zijn verschillende methodes om te verbinden met de pods binnen een Node:  
- NodePorts
- LoadBalancer
- Ingress Controller  
  
In een [artikel van Medium](https://medium.com/google-cloud/kubernetes-nodeport-vs-loadbalancer-vs-ingress-when-should-i-use-what-922f010849e0) staat beschreven wat de voordelen en nadelen zijn van verschillende methodes en hoe de yaml files er uit zouden kunnen zien om deze methodes te kunnen gebruiken in jouw Kubernetes Cluster.  
De NodePorts hebben 3 nadelen:  
- Kan niet verbonden worden met meerdere services (1 per NodePort)
- Kan alleen gebruikt worden op ports 30000-32767
- Als het Node/VM IP adres veranderd moet er werk verricht worden.  
  
Uiteindelijk is de NodePort dus niet de beste optie om je services te openen naar de buitenwereld, eventueel voor test projecten die kort bestaan zou dit wel een goede snelle en goedkope oplossing kunnen zijn.
