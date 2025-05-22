# Axion - Projeto Processo Seletivo
# LEMBRAR DE TIRAR PERMISSOES DE GET NA ROTA PUBLIC DO STRAPI
## Como rodar na sua máquina

## Ferramentas utilizadas
- Strapi + Node.js -> Back-end (criei collections, populei e dei permissões)
- React + Next.js -> Front-end
- Git -> Versionamento
- Insomnia -> Testes

## Documentação criada para desenvolvimento ágil
> Clique no tópico que deseja ver os detalhes para acessar a documentação

1. [Planejamento de *tasks* a serem realizadas dentro do tempo](./docs-backlog/tasks-plan.md)
2. [Requisitos levantados com priorização](./docs-backlog/requisitos.md)
3. [Quadro Kanban](./docs-backlog/kanban.md)
4. [Testes p/ garantir funcionamento da API](./docs-backlog/testes.md)

## Melhorias adicionais
- Documentação da API com exemplos de uso no Insomnia
- Validações dos campos no Strapi (max length e required)
- 


Feito com ❤️ por ***Matheus Madureira***

Perfeito! Você está com tudo bem estruturado e já dominou a parte do **Strapi + API**. Agora sim é hora de começar o **front-end com Next.js + React** e integrar com a API — de forma segura, escalável e elegante.

---

## ✅ **1. Sobre remover a permissão pública no Strapi**

**Sim!** Mas só **depois** que seu front-end já estiver fazendo requisições **com token JWT**, ou seja:

### 🧭 Etapas corretas:

1. Faça o login funcionar no front
2. Pegue o token e armazene (localStorage ou cookie)
3. Use esse token para fazer requisições com:

   ```http
   Authorization: Bearer <seu-token>
   ```
4. **Testou tudo e está OK?**
5. **Agora sim**: vá no Strapi > `Settings > Roles > Public` e desmarque as permissões de `find` e `findOne`.

---

## ✅ **2. Plano de desenvolvimento do front-end**

Agora vou montar um **passo a passo atualizado**, considerando **seu ambiente, requisitos e tecnologia escolhida (Next.js + React + Tailwind)**.

---

## 🗂️ Etapa 0 – Estrutura e Setup Inicial

```bash
# Na pasta /frontend
npx create-next-app@latest . --ts
npm install axios tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

Configure o Tailwind em `tailwind.config.js` e o CSS em `globals.css`.

### ✔️ Estrutura de pastas recomendada:

```
/frontend
  /public
    /assets          ← imagens e favicon
  /src
    /components      ← botão, input, card
    /pages
      index.tsx      ← redireciona ou é a página inicial protegida
      login.tsx
      pessoas.tsx
      comidas.tsx
      locais.tsx
    /services        ← api.ts (axios configurado)
    /utils           ← helpers (ex: storage, auth)
    /hooks           ← custom hooks se precisar
    /styles          ← tailwind + custom css
```

---

## 🧩 Etapa 1 – Página de Login

### ✅ Requisitos cobertos:

* RF001, RF006

**O que fazer:**

* Criar formulário com campos `email` e `senha`
* Requisição:

  ```ts
  POST http://localhost:1337/auth/local
  {
    identifier: email,
    password: senha
  }
  ```
* Se retornar sucesso: armazenar JWT (ex: `localStorage.setItem('token', res.data.jwt)`)

---

## 🔒 Etapa 2 – Proteção de Rotas

### ✅ Requisitos cobertos:

* RF002, RF007

* Criar função ou hook que **verifica o token**

* Em cada rota de lista (`pessoas.tsx`, etc):

  * Checar se token existe
  * Se não, redirecionar para `/login`

* Criar botão de **Logout** (limpa o token e redireciona)

---

## 🧾 Etapa 3 – Listas (pessoas, comidas, locais)

### ✅ Requisitos cobertos:

* RF003, RF004, RF005, RF008

* Criar componente `Card.tsx`:

  * Props: `name`, `imageUrl`
  * Use `backgroundImage` com Tailwind/inline

* Buscar dados com `axios`:

  ```ts
  axios.get('/pessoas', {
    headers: {
      Authorization: `Bearer ${token}`
    }
  })
  ```

* Adicionar lógica para:

  * Ordenar lista por nome (A-Z / Z-A)
  * Exibir mensagem "sem resultados" caso array.length === 0

---

## 🎨 Etapa 4 – Estilo, Layout e Fontes

### ✅ Requisitos cobertos:

* RNF001 a RNF008

**Checklist:**

* [ ] Adicionar fonte `Open Sans` do Google Fonts
* [ ] Usar Tailwind CSS para layout
* [ ] Aplicar cores da Axion (pegue do GitHub)
* [ ] Fazer switch de tema (escuro/claro) com `useState` ou lib
* [ ] Aplicar **fade-in** nos cards usando Tailwind (`transition`, `duration-500`, etc)
* [ ] Garantir responsividade com classes Tailwind (`grid-cols`, `md:grid`, etc)

---

## 🔁 Etapa 5 – Teste Final e Deploy (Opcional)

* Testar todos os fluxos
* Documentar no README como rodar o front e o back
* (Se quiser impressionar ainda mais) Fazer deploy do front (ex: Vercel)

---

## ✅ Recomendo começar por:

1. ✅ Criar estrutura base do projeto Next.js com Tailwind
2. ✅ Criar página de login com integração real via JWT
3. 🔒 Implementar sistema de sessão
4. 🧾 Criar página de uma das listas (ex: Pessoas)
5. 🔁 Reutilizar o card para outras listas

---

Se quiser, posso te gerar um exemplo de código para:

* Página de login com axios + validação
* Função `getServerSideProps` para proteger rotas privadas
* Componente `Card.tsx` estilizado com Tailwind

Quer que eu crie isso agora?

