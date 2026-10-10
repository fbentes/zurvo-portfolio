# Zurvo — portfólio técnico

> Material de portfólio de **Fábio A. C. Bentes**. Descreve a **engenharia** do projeto Zurvo, e não o produto.
> O código-fonte e as regras de negócio são privados. Posso apresentar o projeto em uma demonstração ao vivo.

## Sobre

O Zurvo é um aplicativo móvel e web de encontros geolocalizado, construído por mim de ponta a ponta: API, banco de dados, aplicativo Flutter e aplicação web. Em desenvolvimento desde setembro de 2026.

## Competências demonstradas

| Área | O que o projeto exercita |
|---|---|
| **Backend** | Java 25, Spring Boot 4.1 (MVC), Spring Security, JPA, Maven |
| **Segurança** | autenticação com tokens de curta duração e renovação segura de sessão, login social, tratamento cuidadoso de dados pessoais |
| **Dados** | PostgreSQL, migrations versionadas com Flyway |
| **Tempo real** | WebSocket com STOMP, autenticado e com eventos privados por usuário |
| **Mobile** | Flutter (Dart), um único código para Android e iOS |
| **Web** | Svelte 5, Vite |
| **Integrações** | armazenamento de objetos compatível com S3 (envio direto do app), gateway de pagamento, login com Google |
| **Contrato de API** | OpenAPI único, consumido pelo celular e pela web |
| **Qualidade** | desenvolvimento orientado a especificações (mais de 30 specs), ADRs, mais de 260 testes automatizados, *feature flags* |
| **Entrega** | Docker Compose para desenvolvimento, ambiente de staging na nuvem |

## Visão geral da arquitetura

![Visão geral da arquitetura do Zurvo](arquitetura.svg)

## Decisões de engenharia

- **Contrato primeiro:** o contrato OpenAPI fica no backend e é a fonte comum para o celular e a web, o que evita divergência entre os clientes.
- **Arquivos fora do servidor:** o app envia as imagens direto ao armazenamento, por URL temporária assinada, e o backend só confere e registra. Isso reduz carga, custo e superfície de ataque.
- **Recursos desligados por padrão:** cada integração nova entra atrás de uma *feature flag* com valor seguro, e a configuração incompleta falha na subida com mensagem clara.
- **Escala em estágios:** o plano de crescimento está documentado em ADR, com gatilhos mensuráveis para cada evolução de infraestrutura, em vez de arquitetura sofisticada antes da hora.
- **Decisões registradas:** mudanças relevantes viram ADR, e cada funcionalidade tem especificação, plano e evidências de execução.
- **Manutenção de plataforma:** atualização do runtime para Java 25, verificada pela suíte de testes completa.

## Telas de exemplo

As imagens vêm de protótipo e de dados **fictícios**, em baixa resolução.

| Mapa | Conversas |
|:--:|:--:|
| <img src="imagens/01-mapa.png" width="240"> | <img src="imagens/02-conversas.png" width="240"> |

## Estado do projeto

Em desenvolvimento ativo, por verticais. Este material descreve a engenharia, e nem todos os recursos do produto estão concluídos.

## Propriedade intelectual

O Zurvo-app foi depositado no **Instituto Nacional da Propriedade Industrial (INPI)** como programa de computador (Lei nº 9.609/1998):

- **Processo INPI:** `512026009066-0` (depositado em 10/10/2026)
- **Titular:** Fábio Anderson Corrêa Bentes
- **Hash SHA-512 do código-fonte registrado (v1.0.0):** `91db0367270f22f0a1005182884dd7b0f53fa67b71b4541a4ae791fb6ccd68a7eba66fba25b9c4afec07c138fca7f0d03e5a35b5a177d10f4e89d774f879345b`

O código-fonte é privado e não foi enviado ao INPI, que guarda apenas o hash. A consulta pública do processo é feita em [busca.inpi.gov.br](https://busca.inpi.gov.br/pePI/), em Programa de Computador.

---

© 2026 Fábio A. C. Bentes. Todos os direitos reservados. Veja [LICENSE](LICENSE).
