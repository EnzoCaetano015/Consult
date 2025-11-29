# Sistema de Consulta – Consulte

![Logo do Sistema]({{file:file-1dEnr8iLDjGALfEkbM6JkP}})

**Consult** é um sistema web de gerenciamento de cadastros feito com React, TypeScript e Vite.  Ele oferece uma interface simples para **administradores** cadastrarem e manterem registros de pessoas e para **visualizadores** filtrarem e exportarem essas informações.  O projeto é dividido em um front‑end (este repositório) e um back‑end (submódulo `consult‑API`), cujo endereço base é definido no arquivo de configuração `src/Config/config.tsx`【634139411257951†L0-L0】.

## Funcionalidades

### Fluxo de navegação

- **Splash screen** – tela inicial com o logotipo, exibida por 3 s antes de redirecionar para o login.  A navegação é controlada pelas rotas configuradas em `src/Routes/routes.tsx`【865685392707298†L11-L15】.
- **Tela de login** – usuários escolhem entre os perfis **Visualizador** ou **Administrador**, informam nome e senha e enviam os dados para a API.  O tipo de usuário define a rota de redirecionamento【731303679189020†L19-L48】.  Caso as credenciais sejam válidas, o servidor devolve a rota apropriada para a aplicação.
- **Painel do administrador** – formulário para cadastrar novos registros (nome, cargo, data de nascimento, telefone, e‑mail, LinkedIn e estado).  A página lista os registros cadastrados em uma tabela paginada e permite excluir itens individuais【296609556911540†L43-L79】【296609556911540†L94-L107】.  Os dados são recuperados do back‑end em blocos via parâmetro `offset` e podem ser carregados gradualmente na interface【296609556911540†L43-L79】.
- **Painel de consultas (visualizador)** – tabela com todos os registros cadastrados.  O usuário pode filtrar por **cargo**, **faixa etária**, **estado** e escolher quais colunas (telefone, e‑mail, LinkedIn, estado) deseja visualizar【707307599491846†L61-L96】.  Também é possível exportar a tabela filtrada para um arquivo Excel (.xlsx)【707307599491846†L82-L103】.

### Outros destaques

- **Animações de entrada** – o hook `useInView` verifica se um elemento está visível na viewport e aplica classes CSS de animação (fade‑in, jump‑in ou slide‑in) à medida que o usuário rola a página【102675014089562†L0-L31】【813594434103876†L0-L60】.
- **Máscaras de formulário** – nos campos de data e telefone do painel de administração são usadas máscaras (`react‑input‑mask`) para padronizar a entrada de dados【296609556911540†L128-L147】.
- **Exportação para Excel** – a funcionalidade de consulta utiliza a biblioteca `xlsx` para gerar um arquivo `.xlsx` com as colunas selecionadas【707307599491846†L82-L103】.

## Tecnologias utilizadas

|Camada|Tecnologias principais|
|---|---|
|Front‑end|[React](https://react.dev/) 18 com [TypeScript](https://www.typescriptlang.org/), [Vite](https://vitejs.dev/) para build, [React Router DOM](https://reactrouter.com/) para rotas, [axios](https://axios-http.com/) para chamadas HTTP, [lucide‑react](https://lucide.dev/icons) para ícones e [react‑input‑mask](https://github.com/sanniassin/react-input-mask) para máscaras de input【358123878349820†L11-L18】.|
|Exportação|[xlsx](https://sheetjs.com/) para gerar arquivos Excel【358123878349820†L18-L19】.|
|Estilização|CSS Modules e animações personalizadas definidas em `Hook/Hook.css`【813594434103876†L0-L60】.|

## Pré‑requisitos

Para rodar o projeto localmente você precisa ter [Node.js](https://nodejs.org/) (recomenda‑se versão >= 18) e `npm` ou `yarn` instalados.

## Instalação e execução

1. **Clone o repositório com o submódulo**:

   ```bash
   git clone --recurse-submodules https://github.com/EnzoCaetano015/Consulte.git
   cd Consulte
   ```

2. **Instale as dependências**:

   ```bash
   npm install
   ```

3. **Configure a base da API**:

   Edite o arquivo `src/Config/config.tsx` e altere a constante `URL` para apontar para o endereço da sua API (por padrão está definida como `https://consult-api.caetanodev.com/api/`)【634139411257951†L0-L0】.

4. **Execute o servidor de desenvolvimento**:

   ```bash
   npm run dev
   ```

   O Vite iniciará a aplicação em `http://localhost:5173` (ou outra porta livre).  Abra o navegador e acesse a rota `/` para visualizar a splash screen.

5. **Build para produção**:

   Para gerar os arquivos estáticos otimizados execute:

   ```bash
   npm run build
   ```

   Os arquivos ficarão na pasta `dist/`.  Use `npm run preview` para testar o build localmente.

## Estrutura de pastas

```
src/
├─ Config/         # configuração da URL da API
├─ Hook/           # hook personalizado e estilos de animação
├─ Pages/
│  ├─ Splash/      # tela de splash (logo + redirecionamento)
│  ├─ Home/        # tela de login
│  ├─ Admin/       # painel de administração (CRUD)
│  └─ Client/      # painel de consultas e exportação
├─ Routes/         # definição das rotas da aplicação【865685392707298†L11-L15】
├─ App.tsx         # componente principal
└─ main.tsx        # ponto de entrada da aplicação
```

O back‑end (`consult‑API`) fica no submódulo `backend/` e expõe endpoints REST para autenticação e manipulação dos registros.  Consulte o repositório correspondente para detalhes de instalação e configuração.

## Contribuindo

Contribuições são bem‑vindas!  Para propor melhorias ou correções:

1. Faça um fork do projeto e crie uma branch com a sua feature.
2. Realize suas alterações seguindo os padrões existentes.
3. Abra um *pull request* descrevendo as mudanças propostas.

## Licença

Até o momento este projeto não possui um arquivo de licença definido.  Caso deseje utilizar o código em um projeto próprio, considere entrar em contato com o autor para esclarecimentos.
