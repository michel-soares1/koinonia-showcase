# Koinonia — Plataforma SaaS de Acessibilidade

> SaaS multi-tenant focado em acessibilidade e gestão para comunidades religiosas, com ênfase em inclusão (Libras), comunicação em tempo real e proteção de dados sensíveis.

🌐 **Site:** [koinoniaig.com.br](https://koinoniaig.com.br)

---

![Status](https://img.shields.io/badge/status-em%20produção-success)
![Versão](https://img.shields.io/badge/versão-0.9.x-blue)
![Licença](https://img.shields.io/badge/código-proprietário-lightgrey)

![Next.js](https://img.shields.io/badge/Next.js-14-black?logo=next.js)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white)
![Supabase](https://img.shields.io/badge/Supabase-3FCF8E?logo=supabase&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-06B6D4?logo=tailwindcss&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-000000?logo=vercel&logoColor=white)

> **Nota:** Este repositório é uma **vitrine (showcase)**. O código-fonte é proprietário e mantido em repositório privado. Aqui você encontra a descrição da arquitetura, da stack e das decisões técnicas do projeto.

---

## 📖 Sobre o Projeto

O **Koinonia** é uma plataforma SaaS multi-tenant que oferece a comunidades religiosas um conjunto de ferramentas digitais com foco em **acessibilidade** e **proteção de dados**. O objetivo é tornar conteúdos e serviços acessíveis a pessoas surdas e com deficiência auditiva, além de oferecer canais seguros de comunicação e gestão.

O produto está **em produção**, atendendo a uma comunidade-piloto, com arquitetura preparada para escalar para múltiplos tenants de forma isolada e segura.

---

## ✨ Principais Funcionalidades

- **Acessibilidade em Libras** — integração de avatar de língua de sinais para inclusão de pessoas surdas
- **Transcrição de áudio** — conversão de fala em texto para acessibilidade auditiva
- **Aconselhamento por vídeo (P2P)** — comunicação em tempo real via WebRTC, com notas criptografadas
- **Doações via Pix e cartão** — integração com gateway de pagamento nacional
- **PWA** — aplicação instalável, com experiência mobile-first
- **Multi-tenant** — isolamento completo de dados por organização

---

## 🏗️ Arquitetura

A plataforma adota uma estratégia de **Defense in Depth** com múltiplas camadas de segurança:

```
┌─────────────────────────────────────────────┐
│  UI (Next.js App Router + Tailwind)           │
├─────────────────────────────────────────────┤
│  API Route Handlers (validação + autorização) │
├─────────────────────────────────────────────┤
│  Row Level Security (isolamento multi-tenant)  │
├─────────────────────────────────────────────┤
│  Criptografia client-side (AES-GCM + PBKDF2)   │
└─────────────────────────────────────────────┘
```

**Princípios aplicados:**

- **Isolamento multi-tenant** garantido a nível de banco de dados (Row Level Security), não apenas na aplicação
- **Criptografia de ponta** para dados sensíveis, com derivação de chave no lado do cliente
- **Discriminação semântica de API** seguindo boas práticas de segurança (anti-enumeração / CWE-209)
- **Migrações idempotentes** e versionamento semântico com disciplina de releases por sprint
- **Validação empírica de segurança** em cenários cross-tenant antes de cada release

---

## 🛠️ Stack Técnica

### Frontend
- **Next.js 14** (App Router, Server Components)
- **TypeScript**
- **Tailwind CSS**
- **PWA** (Progressive Web App)

### Backend & Banco de Dados
- **Supabase** (PostgreSQL gerenciado)
- **Row Level Security (RLS)** — isolamento multi-tenant
- **Supabase Auth** — autenticação e gestão de sessão
- **Supabase Realtime** — sincronização em tempo real

### Segurança
- **AES-GCM 256** — criptografia de dados sensíveis
- **PBKDF2** — derivação de chave (client-side)
- Conformidade com a **LGPD**

### Comunicação em Tempo Real
- **WebRTC** — vídeo ponto a ponto (P2P)
- **Signaling** via Supabase Realtime, com backoff de reconexão

### Pagamentos
- Integração **Pix** e **cartão** via gateway nacional (Asaas)

### DevOps & Infraestrutura
- **Vercel** — deploy e CI/CD
- **GitHub** — versionamento e releases
- **Versionamento semântico** com SSOT (Single Source of Truth)

---

## 🔒 Destaques de Engenharia

- Implementação de **isolamento multi-tenant real** com Row Level Security validado empiricamente em cenários cross-tenant
- **Criptografia auditada** de notas confidenciais, com propriedade de confidencialidade por design (chaves derivadas por titular + sessão)
- **Pipeline de comunicação WebRTC** com signaling resiliente e reconexão automática
- Disciplina de **smoke tests empíricos** antes de cada release (schema + funcional + RLS)

---

## 📌 Status

Plataforma em **produção ativa**, em evolução contínua por sprints curtos com releases versionados.

---

## 👤 Autor

Desenvolvido como projeto solo (fundador + desenvolvedor), unindo experiência em **desenvolvimento full-stack** e **15+ anos em dados e inteligência de mercado** (Python, SQL, PySpark, Databricks, Power BI).

📫 **Contato:** michel.felippin@gmail.com

---

<sub>Este repositório apresenta a arquitetura e a stack do projeto para fins de portfólio. O código-fonte é proprietário e não está disponível publicamente.</sub>
