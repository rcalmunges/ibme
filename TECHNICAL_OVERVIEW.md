
# 🧠 Detalhamento Técnico e Tópicos de Estudo - IBME Valença

Este documento serve como um guia para desenvolvedores e recrutadores entenderem a profundidade técnica e as decisões de arquitetura aplicadas neste projeto.

---

## 1. Gerenciamento de Estado e Performance (React)

### Otimização de Renderização
- **Code Splitting (React.lazy):** As rotas administrativas (`/admin/*`) são carregadas sob demanda (lazy loaded). Isso reduz drasticamente o tamanho do *bundle* inicial, garantindo que usuários comuns carreguem o site rapidamente sem baixar o código do painel de controle.
- **Hooks Personalizados:** A lógica de interação com o banco de dados foi abstraída em funções assíncronas dentro de `useEffect`, garantindo que o carregamento de dados não bloqueie a renderização da UI.

### Contexto e Props
- A aplicação utiliza uma estrutura limpa onde o estado global de autenticação (`Session`) é gerenciado pelo cliente do Supabase e propagado para componentes protegidos, evitando *Prop Drilling* excessivo.

---

## 2. Padrões de Projeto e Arquitetura

### Componentização
Adotei o padrão de componentes reutilizáveis e atômicos.
- **UI Components:** Botões, Modais, Inputs e Cards são componentes isolados que recebem dados via props, tornando a manutenção visual centralizada.
- **Layout Pattern:** O uso de um componente `<Layout>` (HOC) envolve as rotas públicas, garantindo consistência de Header/Footer, enquanto as rotas de Admin possuem um `<AdminLayout>` próprio com Sidebar e lógica de sessão.

### Camada de Serviços (Service Layer)
A comunicação com o backend não é feita diretamente nos componentes de forma desordenada.
- **`supabaseClient.ts`:** Singleton que inicializa a conexão.
- **Helpers:** Funções utilitárias como `uploadHelper.ts` (para upload de imagens) e `auditHelper.ts` (para logs) encapsulam lógicas complexas, mantendo os componentes React limpos e focados apenas na visualização.

---

## 3. Segurança e Dados

### Autenticação e Autorização
- **Row Level Security (RLS):** A segurança não depende apenas do Frontend. No banco de dados (PostgreSQL), regras de RLS garantem que apenas usuários com a *role* correta possam executar comandos `INSERT`, `UPDATE` ou `DELETE`.
- **Proteção de Rotas:** O Frontend verifica a sessão do usuário antes de renderizar qualquer rota `/admin`. Se o token for inválido, o redirecionamento para o login é imediato.

### Tratamento de Dados Sensíveis
- As chaves de API são expostas apenas via variáveis de ambiente (`import.meta.env`), seguindo as práticas de segurança do Vite.
- Senhas de usuários nunca são expostas no Frontend após o login; o sistema utiliza tokens JWT seguros.

---

## 4. Integrações e Funcionalidades Avançadas

### Geração de Documentos (Client-Side)
Uma das features mais complexas é a geração de arquivos sem backend dedicado.
- **PDFs:** Uso da biblioteca `jspdf` e `jspdf-autotable` para desenhar tabelas financeiras linha a linha no navegador do cliente.
- **Carteirinha Digital:** Uso de `html2canvas` para "fotografar" um nó do DOM (o design da carteirinha em HTML/CSS) e convertê-lo para uma imagem PNG de alta resolução para download.

### Sistema de Backup e Exportação
- Implementação da biblioteca `jszip` para criar um arquivo `.zip` contendo todos os dados do banco (JSON) e fotos de membros.
- O Frontend itera sobre as tabelas, busca os dados, converte para Blob e empacota tudo em um único arquivo para download, permitindo backup offline.

---

## 5. Qualidade de Código (TypeScript)

O projeto utiliza **TypeScript** em modo estrito para prevenir erros em tempo de execução.

- **Interfaces Globais:** O arquivo `types.ts` centraliza todas as definições de modelos (`User`, `Transaction`, `Member`). Isso garante que, se o modelo do banco mudar, o compilador avisará todos os componentes que precisam ser atualizados.
- **Null Safety:** Tratamento extensivo de valores `null` ou `undefined` vindos da API, evitando a famosa "Tela Branca da Morte" (White Screen of Death).

---

## 📊 Estrutura de Banco de Dados (PostgreSQL)

O projeto utiliza um banco relacional com as seguintes tabelas principais:

| Tabela | Função | Relacionamentos |
| :--- | :--- | :--- |
| `members` | Dados cadastrais dos membros | FK para `users` (auth) |
| `finance` | Registro de dízimos e despesas | - |
| `posts` | Conteúdo do Blog (CMS) | - |
| `projects` | Gestão de ministérios e tarefas | - |
| `audit_logs` | Histórico de ações de segurança | FK para `users` |
| `notifications` | Sistema de avisos internos | - |

---

**Documentação gerada automaticamente para fins de portfólio.**
