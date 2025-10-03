# Cloud Native com Kotlin
Aprenda a construir uma aplicação nativa na nuvem, usando Kotlin! Cloud Native é uma abordagem no desenvolvimento de software que utiliza a computação em nuvem para "criar e executar aplicativos escaláveis em ambientes modernos e dinâmicos, como nuvens públicas, privadas e híbridas". E nesta formação você vai aprender tudo isso, utilizando Kotlin e Kubernetes.
Trilha: https://cursos.alura.com.br/formacao-cloud-native-kotlin

## 📚 Tópicos e Tecnologias;

O projeto foi dividido em duas grandes etapas:;

1.  **Aplicações Resilientes e Assíncronas:** Foco na construção de uma API robusta, capaz de lidar com falhas e executar operações de forma não-bloqueante.;
2.  **Deploy e Observabilidade:** Foco em empacotar a aplicação, orquestrá-la em um ambiente de produção e monitorar seu comportamento.;

---

## 🛠️ Tecnologias Utilizadas;

### 1. Aplicações Resilientes e Assíncronas;

* **[Retrofit](https://square.github.io/retrofit/)**;
    * **O que é?** Um cliente HTTP type-safe para Java e Kotlin, análogo ao **Feign Client** do ecossistema Spring. Permite a definição de uma interface com anotações que descrevem as chamadas HTTP (endpoints, parâmetros, headers), e o Retrofit gera uma implementação funcional, simplificando drasticamente o consumo de APIs REST.;
    * **Alternativas:** [Ktor Client](https://ktor.io/docs/client-requests.html), [Feign Client](https://spring.io/projects/spring-cloud-openfeign), [OkHttp](https://square.github.io/okhttp/).;

* **[Resilience4j](https://resilience4j.readme.io/)**;
    * **O que é?** Uma biblioteca leve e funcional focada em resiliência de aplicações. Embora seja mais conhecida por sua implementação do padrão **Circuit Breaker**, ela oferece um conjunto completo de ferramentas, como:;
        * **Circuit Breaker:** Isola falhas para evitar que um serviço indisponível derrube toda a aplicação.;
        * **Retry:** Tenta executar novamente uma operação que falhou.;
        * **Rate Limiter:** Controla a quantidade de chamadas que podem ser feitas em um período de tempo.;
        * **Bulkhead:** Limita o número de chamadas concorrentes para um serviço, evitando esgotamento de recursos.;
    * **Alternativas:** [Netflix Hystrix](https://github.com/Netflix/Hystrix) (legado), [Sentinel](https://github.com/alibaba/Sentinel).;

* **[Kotlin Coroutines](https://kotlinlang.org/docs/coroutines-overview.html)**;
    * **O que é?** A forma idiomática e moderna de lidar com código assíncrono e concorrência em Kotlin. Coroutines são "threads leves" que permitem executar operações longas (como I/O de rede) sem bloquear a thread principal, de uma forma que o código continua legível e sequencial, evitando o "Callback Hell".;
    * **Alternativas:** Programação Reativa com [RxJava](https://github.com/ReactiveX/RxJava)/[RxKotlin](https://github.com/ReactiveX/RxKotlin), [Project Loom](https://wiki.openjdk.java.net/display/loom/Main) (Virtual Threads), `ThreadPools` e `Futures`.;

* **[Kotest](https://kotest.io/)**;
    * **O que é?** Um framework de testes flexível e poderoso para Kotlin. Oferece múltiplos estilos de escrita de testes (permitindo uma sintaxe mais descritiva) e uma biblioteca de asserções (`assertions`) muito rica e intuitiva.;
    * **Alternativas:** [JUnit 5](https://junit.org/junit5/), [Spek](https://www.spekframework.org/), [MockK](https://mockk.io/) (para mocking).;

### 2. Deploy e Observabilidade;

* **[Docker](https://www.docker.com/)**;
    * **O que é?** Plataforma para criar, implantar e executar aplicações em **contêineres**. Um contêiner empacota o código da aplicação junto com todas as suas dependências (bibliotecas, runtime, etc) em uma unidade isolada e portátil, garantindo consistência entre os ambientes.;
    * **Alternativas:** [Podman](https://podman.io/), [containerd](https://containerd.io/).;

* **[Docker Hub](https://hub.docker.com/)**;
    * **O que é?** Um serviço de registro (registry) para imagens de contêiner. Funciona como um repositório central para armazenar imagens Docker, permitindo que sejam facilmente baixadas em qualquer ambiente de execução.;
    * **Alternativas:** [GitHub Container Registry](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-container-registry), [AWS ECR](https://aws.amazon.com/ecr/), [Google Artifact Registry](https://cloud.google.com/artifact-registry).;

* **[k3d](https://k3d.io/)**;
    * **O que é?** Ferramenta para executar um cluster **Kubernetes** leve (baseado na distribuição [k3s](https://k3s.io/)) dentro de contêineres Docker. É uma solução excelente para desenvolvimento e testes locais por ser extremamente rápida e consumir poucos recursos.;
    * **Alternativas:** [Minikube](https://minikube.sigs.k8s.io/docs/), [Kind](https://kind.sigs.k8s.io/), [Docker Desktop Kubernetes](https://docs.docker.com/desktop/kubernetes/).;

* **[OpenShift Sandbox](https://developers.redhat.com/developer-sandbox) & [OpenShift CLI (`oc`)](https://docs.openshift.com/container-platform/4.11/cli_reference/openshift_cli/getting-started-cli.html)**;
    * **O que é?**;
        * **OpenShift:** Uma distribuição Kubernetes mantida pela Red Hat, com foco em funcionalidades para o ambiente corporativo, segurança e experiência do desenvolvedor.;
        * **Sandbox:** Um ambiente OpenShift gratuito fornecido pela Red Hat para experimentação e desenvolvimento.;
        * **OpenShift CLI (`oc`):** A ferramenta de linha de comando para interagir com o cluster, que estende o `kubectl` com comandos específicos do OpenShift.;
    * **Alternativas:** Kubernetes (vanilla), [Amazon EKS](https://aws.amazon.com/eks/), [Google GKE](https://cloud.google.com/kubernetes-engine), [Azure AKS](https://azure.microsoft.com/en-us/products/kubernetes-service).;

* **[Spring Actuator](https://docs.spring.io/spring-boot/docs/current/reference/html/actuator.html), [Prometheus](https://prometheus.io/) & [Grafana](https://grafana.com/)**;
    * **O que são?** O trio clássico para **observabilidade** de aplicações.;
        1.  **Spring Boot Actuator:** Expõe endpoints na sua aplicação (`/actuator/prometheus`) que fornecem métricas internas em tempo real.;
        2.  **Prometheus:** Um banco de dados de séries temporais que coleta (scrape) as métricas do Actuator e as armazena, servindo como base para monitoramento e alertas.;
        3.  **Grafana:** Uma plataforma de visualização que se conecta ao Prometheus para criar dashboards com gráficos, medidores e tabelas, tornando as métricas fáceis de interpretar.;
    * **Alternativas:** [Datadog](https://www.datadoghq.com/), [New Relic](https://newrelic.com/), [Dynatrace](https://www.dynatrace.com/), **Stack ELK/EFK** (para logging).;
