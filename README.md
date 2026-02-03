
# 🏛️ Plataforma Digital - IBME Valença

![Status](https://img.shields.io/badge/Status-Online-brightgreen?style=for-the-badge)
![React](https://img.shields.io/badge/React-18.2-blue?style=for-the-badge&logo=react)
![TypeScript](https://img.shields.io/badge/TypeScript-5.0-blue?style=for-the-badge&logo=typescript)
![Supabase](https://img.shields.io/badge/Supabase-Backend-green?style=for-the-badge&logo=supabase)
![Tailwind](https://img.shields.io/badge/Tailwind-CSS-3.4-38b2ac?style=for-the-badge&logo=tailwind-css)

> **Uma Solução Full-Stack Serverless** completa para gestão eclesiástica, comunicação comunitária e transparência financeira.

## 📸 Visão Geral

Este projeto foi desenvolvido para modernizar a infraestrutura digital da **Igreja Batista Missionária Ebenézer (Valença-BA)**. O sistema substitui processos manuais (planilhas e papel) por um ecossistema digital integrado, funcionando como uma **SPA (Single Page Application)** de alta performance.

A plataforma atende a três públicos distintos:
1.  **Visitantes:** Acesso a informações, cultos, blog e doações.
2.  **Membros:** Área restrita para materiais exclusivos e carteirinha digital.
3.  **Liderança:** Painel ERP para gestão financeira, de pessoas e conteúdo.

### 🔗 Links
- **Deploy (Online):** [Acesse o Site Oficial (ibmevalenca.com.br)](https://ibme.dreamsdesigner.com.br/)
- **Documentação Técnica:** [Ver Detalhes de Arquitetura](./TECHNICAL_OVERVIEW.md)

---

## 🚀 Tecnologias e Skills Aplicadas

O projeto foi construído utilizando uma stack moderna, focada em performance, SEO e manutenibilidade.

### Frontend (Core)
- **React 18:** Arquitetura baseada em componentes funcionais e Hooks.
- **TypeScript:** Tipagem estrita para garantir integridade de dados (Interfaces para Membros, Transações, Projetos).
- **Vite:** Build tool de última geração para HMR instantâneo e bundle otimizado.

### Estilização e UI
- **Tailwind CSS:** Design System responsivo, animações CSS nativas e layout Mobile-First.
- **Lucide React:** Biblioteca de ícones vetoriais otimizados.
- **UX/UI:** Design limpo, focado em acessibilidade e facilidade de uso para usuários não-técnicos.

### Backend & Integração (Serverless)
- **Supabase:** Utilizado como Backend-as-a-Service (BaaS).
- **Auth:** Sistema de autenticação robusto e persistência de sessão.
- **PostgreSQL:** Banco de dados relacional para dados complexos.
- **Storage:** Armazenamento de mídia (CDN) para fotos e documentos.

---

## ✨ Funcionalidades de Destaque

### 1. Painel Administrativo (ERP)
Um dashboard protegido onde a liderança pode:
- **Financeiro:** Controle de fluxo de caixa (entradas/saídas) com gráficos interativos e filtros de período.
- **Secretaria:** CRUD completo de membros com upload de fotos.
- **CMS:** Editor de texto rico para Blog e gerenciamento de Galeria.
- **Projetos:** Gestão estilo Kanban (Drag & Drop) para acompanhamento de ministérios.

### 2. Carteirinha Digital & PDF
O sistema gera dinamicamente documentos no navegador:
- **Carteirinha de Membro:** Renderização de HTML para Canvas/Imagem em tempo real.
- **Relatórios Financeiros:** Geração de PDFs detalhados para prestação de contas.

### 3. Sistema de Auditoria
Implementação de Logs de Auditoria que rastreiam ações críticas (quem criou, editou ou excluiu registros), garantindo segurança e rastreabilidade.

## 👨‍💻 Autor

Desenvolvido com foco em excelência técnica e impacto social.

**Robson Calmunges** - *Full Stack Developer*
