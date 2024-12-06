# 🛠️ Documentação da API Assaí Efficiency Tools

![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)
![Status](https://img.shields.io/badge/status-production-green.svg)
![License](https://img.shields.io/badge/license-Private-red.svg)

`#api` `#servicenow` `#access-management` `#security` `#integration`

## 🎯 Visão Geral

A API Assaí Efficiency Tools fornece serviços para gerenciamento de acessos RUB, incluindo funcionalidades de reset de senha e concessão de acessos através de integração com o ServiceNow.

![ServiceNow](https://img.shields.io/badge/integration-ServiceNow-brightgreen.svg)
![Security](https://img.shields.io/badge/security-OAuth2-orange.svg)
![Documentation](https://img.shields.io/badge/swagger-valid-brightgreen.svg)

## 🔌 Endpoints

### 1. 🔍 Verificação de Disponibilidade

![HTTP](https://img.shields.io/badge/GET-endpoint-blue.svg)

Endpoint básico para verificar se o serviço está disponível.

```http
GET /
```

**Respostas:**
- ![200](https://img.shields.io/badge/200-OK-success.svg) API está funcionando normalmente

### 2. 🔑 Reset de Senha

![HTTP](https://img.shields.io/badge/POST-endpoint-green.svg)
![Auth](https://img.shields.io/badge/requires-authentication-red.svg)

```http
POST /webhook/servicenow/
```

**Request Body:**
```json
{
  "usuario": "string",
  "senha": "string",
  "sistema": "string",
  "ticket": "string",
  "contact_type": "string",
  "tipo": "string"
}
```

**Campos Obrigatórios:**
![Required](https://img.shields.io/badge/required-usuario-blue.svg)
![Required](https://img.shields.io/badge/required-senha-blue.svg)
![Required](https://img.shields.io/badge/required-sistema-blue.svg)
![Required](https://img.shields.io/badge/required-ticket-blue.svg)
![Required](https://img.shields.io/badge/required-tipo-blue.svg)

**Exemplo de Resposta Sucesso (200):**
```json
{
  "status": "sucesso",
  "mensagem": "Reset de senha processado",
  "ticket": "RITM4373327"
}
```

### 3. 🔐 Concessão de Acesso

![HTTP](https://img.shields.io/badge/POST-endpoint-green.svg)
![Auth](https://img.shields.io/badge/requires-authentication-red.svg)

```http
POST /webhook/servicenow/
```

**Request Body:**
```json
{
  "matricula": "string",
  "acao": "string",
  "data_inicial": "YYYY-MM-DD",
  "data_final": "YYYY-MM-DD",
  "sistema": "string",
  "perfil": "string",
  "ticket": "string"
}
```

**Campos Obrigatórios:**
![Required](https://img.shields.io/badge/required-matricula-blue.svg)
![Required](https://img.shields.io/badge/required-acao-blue.svg)
![Required](https://img.shields.io/badge/required-sistema-blue.svg)
![Required](https://img.shields.io/badge/required-ticket-blue.svg)

**Campos Opcionais:**
![Optional](https://img.shields.io/badge/optional-data__inicial-lightgrey.svg)
![Optional](https://img.shields.io/badge/optional-data__final-lightgrey.svg)
![Optional](https://img.shields.io/badge/optional-perfil-lightgrey.svg)

**Exemplo de Resposta Sucesso (200):**
```json
{
  "status": "sucesso",
  "mensagem": "Concessão de acesso processada",
  "ticket": "RITM4373327"
}
```

## 🛡️ Considerações de Segurança

![Security](https://img.shields.io/badge/HTTPS-required-critical.svg)
![Security](https://img.shields.io/badge/Authentication-required-critical.svg)

1. Todos os endpoints devem ser acessados através de HTTPS
2. Os tickets do ServiceNow são utilizados para rastreabilidade
3. As senhas devem ser transmitidas de forma segura
4. O acesso à API deve ser autenticado e autorizado apropriadamente

## ⚠️ Tratamento de Erros

A API retorna respostas HTTP padrão indicando o sucesso ou falha da operação:

![Status](https://img.shields.io/badge/200-Success-success.svg) Sucesso
![Status](https://img.shields.io/badge/400-Bad%20Request-red.svg) Erro na requisição
![Status](https://img.shields.io/badge/401-Unauthorized-red.svg) Não autorizado
![Status](https://img.shields.io/badge/403-Forbidden-red.svg) Acesso proibido
![Status](https://img.shields.io/badge/404-Not%20Found-red.svg) Recurso não encontrado
![Status](https://img.shields.io/badge/500-Server%20Error-red.svg) Erro interno do servidor