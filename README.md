
Uma API RESTful desenvolvida em Java com Spring Boot 3 para o gerenciamento de cidades e consulta de dados meteorológicos em tempo real, integrada à API externa Open-Meteo.

##Arquitetura e Decisões Tecnológicas

O projeto foi estruturado seguindo boas práticas de desenvolvimento backend, focando em manutenibilidade, performance e desacoplamento de componentes.

###Tecnologias Utilizadas

Java 17 (LTS): Escolhido por ser uma versão de suporte de longo prazo estável, oferecendo recursos modernos da linguagem como Records, Text Blocks e sintaxe aprimorada para Pattern Matching.
Spring Boot 3.3.x:Framework base pela facilidade de configuração (convention over configuration), gerenciamento de dependências e ecossistema robusto para APIs REST.
Spring Data JPA & Hibernate:Adotado para abstração da camada de persistência de dados, permitindo a manipulação de entidades de forma orientada a objetos sem a necessidade de queries SQL manuais complexas.
Spring Boot DevTools: Incluído para acelerar o ciclo de desenvolvimento através do live reload de classes e recursos modificados no ambiente local.
Spring RestClient: Utilizado como cliente HTTP síncrono moderno introduzido no Spring Framework 6. Substitui o antigo `RestTemplate` oferecendo uma API fluente e declarativa para consumo da API do Open-Meteo.
Java Records: Utilizados para mapear os Data Transfer Objects (DTOs) da resposta do Open-Meteo. Garante imutabilidade e reduz significativamente o código boilerplate.
Jakarta Bean Validation: Garante a integridade dos dados recebidos via requisições HTTP (`@Valid`, `@RequestBody`), disparando exceções apropriadas antes da camada de persistência.
Maven: Gerenciador de dependências e ferramenta de build padronizada para o projeto.

## Integração Externa (Open-Meteo API)

A aplicação consome duas APIs públicas do provedor Open-Meteo de forma encadeada:
1. Geocoding API (`geocoding-api.open-meteo.com`): Mapeia o nome da cidade informada pelo usuário para suas coordenadas geográficas (`latitude` e `longitude`).
2. Weather Forecast API (`api.open-meteo.com`): Obtém os dados climáticos atuais (temperatura, humidade e velocidade do vento) com base nas coordenadas obtidas na consulta anterior.

## Como Executar o Projeto Localmente

### Pré-requisitos
Java Development Kit (JDK) 17+
Apache Maven 3.8+ (ou utilizar o wrapper `./mvnw` do projeto)
IDE de sua preferência (Spring Tool Suite, Eclipse, IntelliJ)
