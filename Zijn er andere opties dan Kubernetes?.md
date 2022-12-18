# Zijn er andere opties dan Kubernetes?
## Inleiding
De grootste non-functional requirement die Kubernetes aanpakt is schaalbaarheid, daarbij zit ook monitoring en cyber security. Zijn er ook andere manieren om een IT-infrastructuur schaalbaar en veilig te maken?

## Schaalbaarheid
Schaalbaarheid binnen de IT staat voor hoe goed een applicatie/software systeem kan presteren onder toenemende en afnemende werklast. Kubernetes is een auto-scaling tool om een applicatie op of af te schalen.
  
Er zijn verschillende strategieën die gebruikt kunnen worden om software schaalbaar te maken:

- **Gedistribueerde architectuur:** Dit houdt in dat de software opgedeeld wordt in kleinere componenten die op verschillende servers of apparaten kunnen draaien en met elkaar communiceren via API's of berichtenstelsels. Dit maakt het mogelijk om de belasting op de software te verhogen door meer servers of apparaten aan het netwerk toe te voegen.
- **Microservices-architectuur (voorbeeld van gedistribueerde architectuur):** Dit houdt in dat de software opgedeeld wordt in kleine, onafhankelijke services die afzonderlijk kunnen worden ontwikkeld, geïmplementeerd en geschaald. Dit biedt meer flexibiliteit en een gemakkelijkere onderhoud.
- **Load Balancer:** Dit is een software- of hardwarecomponent dat inkomende verzoeken gelijkmatig verdeelt over meerdere servers of apparaten, om de prestaties te verbeteren en het risico op overbelasting van een enkele server te verminderen. (Bron: [VMware](https://www.vmware.com/topics/glossary/content/software-load-balancing.html))
- **Caching:** Dit houdt in dat vaak gebruikte gegevens in het geheugen opgeslagen worden, zodat ze snel opgehaald kunnen worden zonder dat er toegang tot een tragere opslagmedium nodig is.
- **Database met schaalbaarheid:** Dit houdt in dat je een databasemanagementsysteem gebruikt dat ontworpen is om een grote hoeveelheid gegevens en transacties te verwerken zonder te vertragen.
- **Asynchrone verwerking:** Dit houdt in dat u een berichtenwachtrij of ander mechanisme gebruikt om lange-termijn taken los te koppelen van het hoofdverzoek-antwoord-proces, zodat ze op de achtergrond uitgevoerd kunnen worden zonder het hoofdthread te blokkeren. Dit kan helpen om de responsiviteit van de software te verbeteren.
- **Auto-scaling:** Dit houdt in dat de software automatisch resources (zoals servers of containers) toevoegt of verwijdert op basis van de belasting, om ervoor te zorgen dat de benodigde verwerkingskracht altijd beschikbaar is.

## Monitoring
Er zijn verschillende manieren om software te monitoren. Een van de voornaamste is logging, in mijn [onderzoek over logging in .NET](https://github.com/BrucevandeVen/Logging) heb ik onderzocht wat logging is en hoe het geïmplementeerd kan worden in .NET.  
Logging kan ervoor zorgen dat error's sneller worden opgespoort omdat de applicatie dit logt naar een plek waar dit gemonitort kan worden.  
Verder zijn er een aantal alternatieven die Kubernetes als auto-scaling tool kunnen vervangen, hier is verderop onderzoek naar gedaan.  
  
Kubernetes biedt ook zelf logging in zijn clusters.

## Cyber Security
Kubernetes biedt een aantal functies om de cybersecurity te versterken en te helpen bij het beveiligen van containers:  
- **Identity and access management (IAM):** Kubernetes biedt ondersteuning voor IAM om te helpen bij het beveiligen van toegang tot de platformresources. Dit omvat ondersteuning voor het gebruik van verschillende authenticatieproviders, zoals OAuth en OpenID Connect, en het gebruik van rollen-gebaseerde toegangsbeleid (RBAC) om te bepalen welke gebruikers toegang hebben tot welke resources. (Bron: [Kubernetes.io](https://kubernetes.io/docs/concepts/security/overview/))
- **Network security:** Kubernetes biedt verschillende manieren om het netwerkverkeer te beveiligen, zoals het gebruik van netwerksegmentatie om te bepalen welke containers toegang hebben tot welke andere containers en het gebruik van encrypted netwerkverkeer om te voorkomen dat gegevens tijdens het transport worden afgeluisterd.
- **Container security:** Kubernetes biedt ondersteuning voor het beveiligen van containers zelf, zoals het gebruik van image signing om te verifiëren dat containers zijn gemaakt van vertrouwde images, en het gebruik van container runtime security om te voorkomen dat containers ongewenste toegang hebben tot hostresources.
- **Security policies:** Kubernetes biedt ondersteuning voor het instellen van beleid om te bepalen wat wel en niet is toegestaan binnen het platform. Dit kan bijvoorbeeld omvatten het beperken van de resources die een container mag gebruiken, of het verplichten van encrypted netwerkverkeer voor bepaalde workloads.

## Kubernetes auto-scaling alternatieven
