---
title: HSTS
slug: Glossary/HSTS
tags:
  - HSTS
  - HTTP
  - Segurança
translation_of: Glossary/HSTS
original_slug: Glossario/HSTS
---
**O HTTP Strict Transport Security** permite que um site informe ao navegador que ele nunca deve carregar o site usando HTTP e deve converter automaticamente todas as tentativas de acessar o site usando HTTP para solicitações HTTPS. Consiste em um cabeçalho HTTP [`Strict-Transport-Security`](/pt-BR/docs/Web/HTTP/Headers/Strict-Transport-Security "O cabeçalho de resposta HTTP Strict-Transport-Security (geralmente abreviado como HSTS) permite que um site informe aos navegadores que ele deve ser acessado apenas por HTTPS, em vez de usar HTTP."), enviado de volta pelo servidor com o recurso.

Em outras palavras, ele diz ao navegador que apenas altere o protocolo de HTTP para HTTPS em uma url (e será mais seguro) e solicitará que o navegador faça isso para cada solicitação.

## Leia Mais

- {{HTTPHeader("Strict-Transport-Security")}}
- Artigo OWASP: [HTTP Strict Transport Security](https://www.owasp.org/index.php/HTTP_Strict_Transport_Security)
- Wikipedia: {{interwiki("wikipedia", "HTTP Strict Transport Security")}}
