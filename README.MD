# Cloud Native com Kotlin
Aprenda a construir uma aplicação nativa na nuvem, usando Kotlin! Cloud Native é uma abordagem no desenvolvimento de software que utiliza a computação em nuvem para "criar e executar aplicativos escaláveis em ambientes modernos e dinâmicos, como nuvens públicas, privadas e híbridas". E nesta formação você vai aprender tudo isso, utilizando Kotlin e Kubernetes.

📚 Tópicos e Tecnologias
O projeto foi dividido em duas grandes etapas:

Aplicações Resilientes e Assíncronas: Foco na construção de uma API robusta, capaz de lidar com falhas e executar operações de forma não-bloqueante.

Deploy e Observabilidade: Foco em empacotar a aplicação, orquestrá-la em um ambiente de produção e monitorar seu comportamento.

🛠️ Tecnologias Utilizadas
1. Aplicações Resilientes e Assíncronas
Retrofit

O que é? Um cliente HTTP type-safe para Java e Kotlin, análogo ao Feign Client do ecossistema Spring. Permite a definição de uma interface com anotações que descrevem as chamadas HTTP (endpoints, parâmetros, headers), e o Retrofit gera uma implementação funcional, simplificando drasticamente o consumo de APIs REST.

Alternativas: Ktor Client, Feign Client, OkHttp.

Resilience4j

O que é? Uma biblioteca leve e funcional focada em resiliência de aplicações. Embora seja mais conhecida por sua implementação do padrão Circuit Breaker, ela oferece um conjunto completo de ferramentas, como:

Circuit Breaker: Isola falhas para evitar que um serviço indisponível derrube toda a aplicação.

Retry: Tenta executar novamente uma operação que falhou.

Rate Limiter: Controla a quantidade de chamadas que podem ser feitas em um período de tempo.

Bulkhead: Limita o número de chamadas concorrentes para um serviço, evitando esgotamento de recursos.

Alternativas: Netflix Hystrix (legado), Sentinel.

Kotlin Coroutines

O que é? A forma idiomática e moderna de lidar com código assíncrono e concorrência em Kotlin. Coroutines são "threads leves" que permitem executar operações longas (como I/O de rede) sem bloquear a thread principal, de uma forma que o código continua legível e sequencial, evitando o "Callback Hell".

Alternativas: Programação Reativa com RxJava/RxKotlin, Project Loom (Virtual Threads), ThreadPools e Futures.

Kotest

O que é? Um framework de testes flexível e poderoso para Kotlin. Oferece múltiplos estilos de escrita de testes (permitindo uma sintaxe mais descritiva) e uma biblioteca de asserções (assertions) muito rica e intuitiva.

Alternativas: JUnit 5, Spek, MockK (para mocking).

2. Deploy e Observabilidade
Docker

O que é? Plataforma para criar, implantar e executar aplicações em contêineres. Um contêiner empacota o código da aplicação junto com todas as suas dependências (bibliotecas, runtime, etc) em uma unidade isolada e portátil, garantindo consistência entre os ambientes.

Alternativas: Podman, containerd.

Docker Hub

O que é? Um serviço de registro (registry) para imagens de contêiner. Funciona como um repositório central para armazenar imagens Docker, permitindo que sejam facilmente baixadas em qualquer ambiente de execução.

Alternativas: GitHub Container Registry, AWS ECR, Google Artifact Registry.

k3d

O que é? Ferramenta para executar um cluster Kubernetes leve (baseado na distribuição k3s) dentro de contêineres Docker. É uma solução excelente para desenvolvimento e testes locais por ser extremamente rápida e consumir poucos recursos.

Alternativas: Minikube, Kind, Docker Desktop Kubernetes.

OpenShift Sandbox & OpenShift CLI (oc)

O que é?

OpenShift: Uma distribuição Kubernetes mantida pela Red Hat, com foco em funcionalidades para o ambiente corporativo, segurança e experiência do desenvolvedor.

Sandbox: Um ambiente OpenShift gratuito fornecido pela Red Hat para experimentação e desenvolvimento.

OpenShift CLI (oc): A ferramenta de linha de comando para interagir com o cluster, que estende o kubectl com comandos específicos do OpenShift.

Alternativas: Kubernetes (vanilla), Amazon EKS, Google GKE, Azure AKS.

Spring Actuator, Prometheus & Grafana

O que são? O trio clássico para observabilidade de aplicações.

Spring Boot Actuator: Expõe endpoints na aplicação (/actuator/prometheus) que fornecem métricas internas em tempo real.

Prometheus: Um banco de dados de séries temporais que coleta (scrape) as métricas do Actuator e as armazena, servindo como base para monitoramento e alertas.

Grafana: Uma plataforma de visualização que se conecta ao Prometheus para criar dashboards com gráficos, medidores e tabelas, tornando as métricas fáceis de interpretar.

Alternativas: Datadog, New Relic, Dynatrace, Stack ELK/EFK (para logging).
