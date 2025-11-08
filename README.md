# 🗓️ Uma Pergunta por Dia

> Um projeto inspirado no livro *"Uma Pergunta por Dia"*, recriado como uma plataforma web interativa onde os usuários respondem uma pergunta diferente todos os dias e acompanham suas respostas ao longo do tempo.

---

## 🚀 Visão Geral

**Uma Pergunta por Dia** é um sistema web desenvolvido em **Next.js** com **autenticação e banco de dados do Supabase**, pensado inicialmente como um **monólito modular**.  
A ideia central é simples: todo dia, o usuário acessa uma nova pergunta, responde e pode revisar suas respostas passadas — criando um registro pessoal de autoconhecimento e reflexão ao longo do tempo.

---

## 🧱 Stack Tecnológica

| Camada | Tecnologia | Função |
|--------|-------------|--------|
| **Frontend** | [Next.js 15+](https://nextjs.org/) | Framework React com renderização híbrida (SSR/SSG). |
| **Estilo & UI** | [Tailwind CSS](https://tailwindcss.com/) + [shadcn/ui](https://ui.shadcn.com/) | Design System e componentes reutilizáveis. |
| **Banco de Dados** | [PostgreSQL (via Supabase)](https://supabase.io) | Armazenamento de usuários, perguntas e respostas. |
| **Autenticação** | [Supabase Auth](https://supabase.com/auth) | Login e registro com email/senha. |
| **Deploy** | [Vercel](https://vercel.com/) | Hospedagem e CI/CD. |

---

## 🧩 Estrutura de Pastas

```

uma-pergunta-por-dia/
├── src/
│   ├── app/                # Rotas e páginas (Next.js App Router)
│   ├── components/         # Componentes reutilizáveis (shadcn/ui)
│   ├── modules/            # Módulos isolados (auth, question, user, etc.)
│   ├── lib/                # Configurações globais (ex: supabaseClient)
│   ├── hooks/              # Hooks customizados (useAuth, useSession, etc.)
│   └── styles/             # Estilos globais e temas
├── public/                 # Assets públicos
├── .env.local              # Variáveis de ambiente (não versionar)
├── package.json
├── tailwind.config.ts
├── tsconfig.json
└── README.md

````

---

## ⚙️ Instalação e Configuração

### 1️⃣ Clonar o repositório
```bash
git clone https://github.com/seu-usuario/uma-pergunta-por-dia.git
cd uma-pergunta-por-dia
````

### 2️⃣ Instalar dependências

```bash
pnpm install
```

### 3️⃣ Configurar variáveis de ambiente

Crie o arquivo `.env.local` com suas chaves do **Supabase**:

```env
NEXT_PUBLIC_SUPABASE_URL=https://xyzcompany.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=your-public-anon-key
```

### 4️⃣ Executar o servidor de desenvolvimento

```bash
pnpm dev
```

Abra em: [http://localhost:3000](http://localhost:3000)

---

## 🗃️ Estrutura do Banco de Dados (Supabase)

```sql
create table questions (
  id uuid primary key default uuid_generate_v4(),
  content text not null,
  created_at timestamp default now()
);

create table answers (
  id uuid primary key default uuid_generate_v4(),
  user_id uuid references auth.users(id),
  question_id uuid references questions(id),
  content text not null,
  created_at timestamp default now()
);

create table daily_sessions (
  id uuid primary key default uuid_generate_v4(),
  user_id uuid references auth.users(id),
  question_id uuid references questions(id),
  answered boolean default false,
  created_at timestamp default now()
);
```

---

## 🧭 Roadmap de Desenvolvimento

| Sprint | Foco                      | Entregas                                                                  |
| ------ | ------------------------- | ------------------------------------------------------------------------- |
| **1**  | Fundamentos               | Setup do projeto, Supabase Auth, modelagem e layout base                  |
| **2**  | Lógica do dia e UX        | Sistema de perguntas diárias, navegação e persistência de respostas       |
| **3**  | Histórico & Perfil        | Exibição de respostas anteriores, edição de perfil e personalização       |
| **4**  | Compartilhamento & Social | Recursos para compartilhar respostas e integração opcional entre usuários |
| **5**  | Deploy & Analytics        | Deploy na Vercel, monitoramento e ajustes de performance                  |

---

## 🧑‍💻 Scripts Disponíveis

| Comando                        | Descrição                             |
| ------------------------------ | ------------------------------------- |
| `pnpm dev`                     | Executa o ambiente de desenvolvimento |
| `pnpm build`                   | Gera a build de produção              |
| `pnpm start`                   | Inicia o servidor de produção         |
| `pnpm lint`                    | Executa verificação de linting        |
| `pnpm shadcn add <componente>` | Adiciona novos componentes shadcn/ui  |

---

## 🎨 Design System

O projeto utiliza o [shadcn/ui](https://ui.shadcn.com/) com o tema base **New York**.
Exemplo de componentes já disponíveis:

* `Button`
* `Input`
* `Card`
* `Navbar`
* `Dialog`
* `Toast`

Todos os componentes ficam em `/src/components/ui`.

---

## 🔒 Autenticação

A autenticação é feita com o **Supabase Auth**, incluindo:

* Registro com e-mail e senha
* Login persistente
* Logout
* Middleware de proteção de rotas
* Hook `useAuth()` para acesso rápido aos dados do usuário

---

## 📘 Licença

Este projeto está sob a licença **MIT**.
Sinta-se à vontade para estudar, modificar e contribuir.

---

## 🤝 Contribuição

Contribuições são bem-vindas!
Para contribuir:

1. Faça um fork do repositório
2. Crie uma branch: `git checkout -b feature/nova-feature`
3. Faça suas alterações e adicione commits
4. Envie um PR 🚀

---

### ✨ Autor

**Desenvolvido por [Santiago Souto (Thogar)](https://github.com/devsolto)**
💡 Projeto pessoal inspirado em *Uma Pergunta por Dia*, adaptado para o universo digital.
