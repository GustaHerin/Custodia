# TundraDrive

[![Repositório Oficial](https://img.shields.io/badge/TundraLab-TundraDrive-2563EB?logo=github)](https://github.com/TundraLab/TundraDrive)
[![Autor Único](https://img.shields.io/badge/Autor%20e%20Dev%20Único-%40GustaHerin-181717?logo=github)](https://github.com/GustaHerin)
[![.NET 10](https://img.shields.io/badge/.NET-10.0-512BD4?logo=dotnet&logoColor=white)](#arquitetura-e-tecnologias)
[![Avalonia UI](https://img.shields.io/badge/Avalonia%20UI-11.3.8-8B44AC)](#arquitetura-e-tecnologias)
[![Licença](https://img.shields.io/badge/License-All%20Rights%20Reserved-red)](LICENSE)

> **Repositório empresarial oficial:** [`https://github.com/TundraLab/TundraDrive`](https://github.com/TundraLab/TundraDrive)

Cliente nativo do Google Drive para Linux para sincronização bidirecional, backup unidirecional, gerenciamento avançado de arquivos e automação local via API REST isolada.

## Autoria e Responsabilidade Técnica

Este repositório pessoal serve como vitrine de portfólio e referência pública do projeto desenvolvido na organização **TundraLab**.

- **Autor, arquiteto e único desenvolvedor:** **Gustavo Henrique Novaes Gomes** ([`@GustaHerin`](https://github.com/GustaHerin))
- **Escopo de atuação na empresa:** Responsável integral e exclusivo por toda a concepção, arquitetura de software, motor de sincronização, interface gráfica desktop, API local, camadas de segurança, suíte de testes automatizados e empacotamento para Linux do **TundraDrive** dentro da **TundraLab**.
- **Repositório corporativo do código-fonte e releases:** [TundraLab/TundraDrive](https://github.com/TundraLab/TundraDrive)

## Prévia da Interface

![Prévia das telas do TundraDrive](docs/images/preview-showcase.png)

## Principais Funcionalidades Projetadas

- **Sincronização e Backup em Tempo Real:** Operação por pasta em modo **Bidirecional (`PC <-> Drive`)** ou **Backup (`PC -> Drive`)**, com `FileSystemWatcher`, verificação por hash MD5/SHA256, regras de exclusão e resolução de conflitos.
- **Gerenciador de Arquivos e Multimídia:** Modo Lista e Grade com miniaturas em cache, seleção múltipla em lote (`Ctrl + Clique`, `Shift + Clique`, `Ctrl + A`), drag-and-drop e pré-visualização interna de imagens, vídeos, áudio, PDF e documentos Office.
- **Fila de Transferências e Auditoria:** Acompanhamento em tempo real para uploads, downloads e exclusões com detalhes expansíveis e histórico persistido para auditoria.
- **Múltiplas Contas com Isolamento:** Suporte a várias contas Google com arquivo `credentials.json` isolado por perfil, gráfico detalhado de cota (Drive, Gmail/Fotos e Lixeira) e revogação individual.
- **Integração Nativa com Desktop Linux:** Testado em **Fedora** e **Pop!_OS**, com suporte a **GNOME**, **COSMIC** e **KDE Plasma 5/6**, bandeja do sistema, autostart XDG, notificações via D-Bus (`org.freedesktop.Notifications`) e suporte a Lixeira no padrão FreeDesktop.
- **API REST Local (`127.0.0.1:5080`):** Servidor ASP.NET Core Minimal API em loopback com especificação OpenAPI 3.0.3 para integração com scripts locais e agentes de IA.
- **Segurança por Padrão:** Proteção contra `Path Traversal` no sincronizador e downloads, proteção contra CSRF e DNS rebinding na API loopback (`Host`/`Origin`/`Referer`), validação explícita de credenciais OAuth2 Desktop (`installed`) e armazenamento local com permissões POSIX restritas (`0700`/`0600`).

## Arquitetura e Tecnologias

| Camada | Tecnologias e Responsabilidades |
| :--- | :--- |
| **Core (`TundraDrive.Core`)** | C# / `.NET 10.0`, Google Drive API v3, SQLite + Dapper, OAuth2 local, `FileSystemWatcher`, hashes MD5/SHA256 e proteção de caminhos |
| **API Local (`TundraDrive.Api`)** | ASP.NET Core Minimal API restrita a `127.0.0.1:5080`, validação CSRF/DNS rebinding e OpenAPI 3.0.3 |
| **Desktop (`TundraDrive.Desktop`)** | Avalonia UI 11.3.8 (MVVM com `CommunityToolkit.Mvvm`), D-Bus notifications, integração KDE/GNOME/COSMIC e limpador de memória |
| **Qualidade e Distribuição** | Testes automatizados com xUnit e empacotamento Linux (`AppImage x86_64`, `.rpm` e `.deb`) |

---

## Licença e Propriedade Intelectual

**Todos os Direitos Reservados (`All Rights Reserved`)**
Copyright © 2026 **TundraLab** e **Gustavo Henrique Novaes Gomes** ([`@GustaHerin`](https://github.com/GustaHerin)).

- **Código-fonte (Portfólio e Auditoria):** Este projeto é exibido publicamente apenas para leitura, avaliação técnica e portfólio. Não é concedida permissão para copiar, modificar, redistribuir ou utilizar o código-fonte (no todo ou em parte) para fins comerciais ou projetos externos sem autorização prévia por escrito.
- **Uso dos pacotes oficiais (`.AppImage` / `.rpm`):** Usuários finais podem baixar, instalar e executar gratuitamente os instaladores oficiais publicados em **TundraLab/TundraDrive** para uso pessoal ou corporativo interno, sendo vedada a redistribuição ou modificação comercial.

Consulte os termos completos em [LICENSE](LICENSE).

Para acessar o projeto oficial na organização: **[github.com/TundraLab/TundraDrive](https://github.com/TundraLab/TundraDrive)**
