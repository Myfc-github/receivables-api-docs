---
title: Documentação API Fintera Recebíveis

language_tabs: # must be one of https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers
  - shell

toc_footers:
  - API mantida por <a href='https://www.fintera.com.br/'>Fintera</a>.

includes:
  - receivables/criar
  - receivables/cancelar_ou_estornar
  - receivables/cancelar
  - receivables/estornar

search: false

code_clipboard: true

meta:
  - name: description
    content: Documentação Fintera - Recebíveis
---

# Introdução

Seja bem-vindo(a) a documentação do Fintera Recebíveis.

# Autenticação

Todo acesso à API é feito utilizando o atributo `fintera_api_token` no _header_ da requisição.

O _Fintera api token_ pode ser obtido na página de _Gerenciar Conta Fintera_, ao entrar na aba de _Integrações_.
