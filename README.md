# next.js-docs-pt-br
Tradução não oficial da documentação do Next.js para português do Brasil (pt-BR).

## Iniciando

Bem-vindo(a) à documentação do Next.js!

Se você é novo(a) com o Next.js nós recomendados que você comece com o curso de aprendizagem.

O curso interativo com perguntas para fixar o conhecimento irão guiar vocẽ através de tudo que você precisa saber para usar o Next.js

Se você tem alguma pergunta sobre qualquer coisa relacionada ao Next.js, você é sempre bem-vindo(a) para perguntar à nossa comunidade em [GitHub Discussion](https://github.com/vercel/next.js/discussions).

[Fonte original](https://nextjs.org/docs/getting-started)

### Requisitos do Sistema

- [Node.js 12.0](https://nodejs.org/) ou superior
- Suporte ao MacOS, Windows (incluindo WSL), e Linux

## Configuração

Nós recomendadmos a criação de uma nova aplicação Next.js utilizando `create-next-app`, o qual configura tudo automaticamente para você. Para criar um projeto, execute o comando:

```bash
npx create-next-app
# ou
yarn create next-app
```
Depois de concluir a instalação, siga as instruções para iniciar o servidor de desenvolvimento. Experimente editar `pages/index.js` e veja o resultado no navegador.

Para mais informações sobre como usar `create-next-app`, você pode verificar a sua respectiva [documentação](https://nextjs.org/docs/api-reference/create-next-app).

## Configuração Manual

Instale `next`, `react` e `react-dom` em seu projeto:

```bash
npm install next react react-dom
# ou
yarn add next react react-dom
```
Abra o arquivo `package.json` e adicione os seguintes itens em `scripts`:

```json
"scripts": {
  "dev": "next dev",
  "build": "next build",
  "start": "next start",
  "lint": "next lint
}
```
Estes scripts se referem aos diferentes estágios de desenvolvimento de uma aplicação:

- `dev` - Executa [`next dev`](https://nextjs.org/docs/api-reference/cli#development) que inicia o Next.js em modo de desenvolvimento
- `build` - Executa [`next build`](https://nextjs.org/docs/api-reference/cli#build) que inicia a aplicação para utilização em produção
- `start` - Executa [`next start`](https://nextjs.org/docs/api-reference/cli#production) que inicia um servidor de produção do Next.js
- `lint` - Executa [`next lint`](https://nextjs.org/docs/api-reference/cli#lint) que realiza a configuração nativa do ESLint do Next.js

O Next.js é construído em torno do conceito de [páginas](https://nextjs.org/docs/basic-features/pages). Uma página é um [componente React](https://reactjs.org/docs/components-and-props.html) exportado de um arquivo `.js`, `.jsx`, `.ts` ou `.tsx` dentro do diretório `pages`.

As páginas são associadas com uma rota baseada em seu respectivo nome de arquivo. Por exemplo, `pages/about.js` é mapeada para `/about`. Você pode até adicionar parâmetros de rota dinâmica com o nome do arquivo.

Crie um diretorio `pages` dentro do seu projeto.

Defina `./pages/index.js` com o seguinte conteúdo:

```JavaScript
function HomePage() {
  return <div>Welcome to Next.js!</js>
}

export default HomePage
```

Para começar o desenvolvimento da sua aplicação, execute `npm run dev` ou `yarn dev`. Isso inicia o servidor de desenvolvimento em `http://localhost:3000`.

Visite `http://localhost:3000` no navegador para visualizar a sua aplicação.

Até agora, nós temos:

- Compilação automática e empacotamento de módulos (com webpack e babel)
- React Fast Refresh
- Geração estática e renderização do lado do servidor de `./pages/`
- Serviço de arquivo estático. `/public/` é mapeado para `/`

Alé disso, qualquer aplicação Next.js está pronta para produção desde o início, saiba mais em nossa [documentação de Implantação](https://nextjs.org/docs/deployment).

## Relacionado

Para mais informações sobre o que fazer em seguida, nós recomendamos as seguintes seções:

- [Páginas](https://nextjs.org/docs/basic-features/pages)
Aprenda mais sobre o que são as páginas no Next.js.

- [Suporte a CSS](https://nextjs.org/docs/basic-features/built-in-css-support)
Use o suporte nativo a CSS para adicionar estilos personalizados à sua aplicação.

- [CLI](https://nextjs.org/docs/api-reference/cli)
Aprenda mais sobre a ferramenta de linha de comando Next.js CLI.

[Funcionalidades Básicas: Páginas](https://nextjs.org/docs/basic-features/pages)

# Páginas

No Next.js, uma página é um [componente React](https://reactjs.org/docs/components-and-props.html) exportado de um arquivo `.js`, `.jsx`, `.ts` ou`.tsx` dentro do diretíro `pages`. Cada página está associada com uma rota baseada em seu respectivo nome de arquivo.

Exemplo: Se você criar `pages/about.js` que exporta um componente React como o exibido abaixo, ela será acessada em `/about`.

```JavaScript
function About() {
  return <div>About</div>
}

export default About
```

### Páginas com Rotas Dinâmicas

O Next.js dá suporte a páginas com rotas dinâmicas. Por exemplo, se você criar um arquivo chamado `pages/posts/[id].js`, então página referente a ele será acessível em `posts/1`, `posts/2`, etc.

Para saber mais sobre roteamento dinâmico, verifique a [documentação de Roteamento Dinâmico](https://nextjs.org/docs/routing/dynamic-routes).

## Pré-renderização

Por padrão, o Next.js pré-renderiza todas as páginas. Isso significa que o Next.js gera HTML para cada página antecipadamente, ao invés disso ser feito pelo JavaScript do lado do cliente. Pré-renderização pode resultar em melhor performance e SEO.

Cada HTML gerado é associado com o mínimo de código JavaScript para a respectiva página. Quando a página é carregada pelo navegador, o JavaScript executa e torna a página inteiramente interativa. (Esse processo é denominado de hidratação.)

### Duas formas de Pré-Renderização

O Next.js tem duas formas de pré-renderização: Geração Estática e Geração do Lado do Servidor. A diferença é está em quando o HTML é gerado para uma página.

- [Geração Estática (Recomendada)](https://nextjs.org/docs/basic-features/pages#static-generation-recommended): O HTML é gerado em `build time` e será reutilizado em cada requisição.
- [Renderização do lado do Servidor](https://nextjs.org/docs/basic-features/pages#server-side-rendering): O HTML é gerado em cada requisição.

É importante notar que o Next.js permite que você escolha o tipo de pré-renderização a ser utilizado para cada página. Você pode criar aplicação Next.js "híbridas" ao utilizar a Geração Estática para a maioria das páginas e a Renderização do lado do Servidor em outras.

Nós recomendados a utilização de Geração Estática em relação à Renderização do lado do Servidor por razão de performance. Página geradas estaticamente podem ser armazenadas em cache por um CDN sem configuração extra para impulsionar a performance. Entretanto, em alguns casos, a Renderização do lado do Servidor pode ser a única opção.

Você também pode utilizar a Renderização do lado do Cliente em conjunto com a Geração Estática ou Renderizaçãoo do lado do Servidor. Isso significa que algumas partes da página podem ser renderizadas inteiramente pelo JavaScript do lado do cliente. Para saber mais, verifique a documentação do [Data Fetching](https://nextjs.org/docs/basic-features/data-fetching#fetching-data-on-the-client-side).

## Geração Estática (Recomendada)

Exemplos:

- [Exemplo com WordPress](https://github.com/vercel/next.js/tree/canary/examples/cms-wordpress) ([Demo](https://next-blog-wordpress.vercel.app/))
- [Template Inicial para Blog usando arquivos markdown](https://github.com/vercel/next.js/tree/canary/examples/blog-starter) ([Demo](https://next-blog-starter.vercel.app/))
- [Exemplo com DatoCMS](https://github.com/vercel/next.js/tree/canary/examples/cms-datocms) ([Demo](https://next-blog-datocms.vercel.app/))
- [Exemplo com TakeShape](https://github.com/vercel/next.js/tree/canary/examples/cms-takeshape) ([Demo](https://next-blog-takeshape.vercel.app/))
- [Exemplo com Sanity](https://github.com/vercel/next.js/tree/canary/examples/cms-sanity) ([Demo](https://next-blog-sanity.vercel.app/))
- [Exemplo com Prismic](https://github.com/vercel/next.js/tree/canary/examples/cms-prismic) ([Demo](https://next-blog-prismic.vercel.app/))
- [Exemplo com Contentful](https://github.com/vercel/next.js/tree/canary/examples/cms-contentful) ([Demo](https://next-blog-contentful.vercel.app/))
- [Exemplo com Strapi](https://github.com/vercel/next.js/tree/canary/examples/cms-strapi) ([Demo](https://next-blog-strapi.vercel.app/))
- [Exemplo com Prepr](https://github.com/vercel/next.js/tree/canary/examples/cms-prepr) ([Demo](https://next-blog-prepr.vercel.app/))
- [Exemplo com Agility CMS]() ([Demo](https://next-blog-agilitycms.vercel.app/))
- [Exemplo com Cosmic](https://github.com/vercel/next.js/tree/canary/examples/cms-cosmic) ([Demo](https://next-blog-cosmic.vercel.app/))
- [Exemplo com ButterCMS](https://github.com/vercel/next.js/tree/canary/examples/cms-buttercms) ([Demo](https://next-blog-buttercms.vercel.app/))
- [Exemplo com Storyblok](https://github.com/vercel/next.js/tree/canary/examples/cms-storyblok) ([Demo](https://next-blog-storyblok.vercel.app/))
- [Exemplo com GraphCMS](https://github.com/vercel/next.js/tree/canary/examples/cms-graphcms) ([Demo](https://next-blog-graphcms.vercel.app/))
- [Exemplo com Kontent](https://github.com/vercel/next.js/tree/canary/examples/cms-kontent) ([Demo](https://next-blog-kontent.vercel.app/))
- [Demo com Static Tweet](https://static-tweet.vercel.app/)

Se uma página utiliza `Geração Estática`, a página HTML é gerada em `build time`. Isso significa que em produção, a página HTML é gerada quando você executa o comando `next build`. Esse HTML será então reutilizado em cada requisição. Ele pode ser armazenado em cache por uma CDN.

Dentro do Next.js, você pode gerar páginas estáticas com ou sem dados. Vamos verificar cada um desses casos.

### Geração Estática sem dados

Por padrão, o Next.js pré-renderiza páginas utilizando Geração Estática sem fazer o fetch dos dados. Segue um exemplo

```JavaScript
function About(){
  return <div>About</div>
}

export default About
``` 

Observe que essa página não precisa fazer o fetch de nenhum dado externo para ser pré-renderizada. Em casos como esse, o Next.js gera um único arquivo HTML por página em build time.

### Geração Estática com dados

Algumas páginas necessitam fazer o fetch de dados externos para pré-renderizar. Existem dois cenários, e um ou ambos podem ser aplicados. Para cada um dos casos, você pode usar estas funções fornecidas pelo Next.js:

1. O conteúdo da sua página depente de dados externos: Utilize 'getStaticProps'.
2. Os paths da sua página dependem de dados externos: Utilize 'getStaticPaths (geralmente em conjunto com `getStaticProps`).

#### Cenário 1: O conteúdo da sua página depende de dados externos

Exemplo: A página do seu blog pode precisar fazer o fetch da lista de posts provenientes de um CMS (sistema gerenciador de conteúdo).

```JavaScript
// TODO: Precisa fazer o fetch dos `posts` (chamando algum endpoint da API)
//       antes que está página seja pré-renderizada.
function Blog({ posts }) {
  return (
    <ul>
      {posts.map((posts) => (
        <li>{post.title}</li>
      ))}
    </ul>
  )
}

export default Blog
```
Para fazer o fetch desses dados em pré-renderização, o Next.js permite que você exportar uma função `async` chamada `getStaticProps` do mesmo arquivo. Essa função é chamada em build time e permite que você passe os dados por meio dos `props` da página em pré-renderização.

```JavaScript
function Blog({ posts }) {
  // Renderizar posts...
}

// Essa função é chamada em build time
export async function getStaticProps() {
  // Faz a requisição a um endpoint de uma API externa para obter os posts
  const res = await fetch('https://.../posts')
  const posts = await res.json()

  // Retornando { props: { posts } }, o componente Blog
  // receberá `posts` como uma prop em build time
  return {
    props: {
      posts,
    },
  }
}

export default Blog

```
Para saber mais sobre como `getStaticProps` funciona, verifique a [documentação do Fetch de Dados](https://nextjs.org/docs/basic-features/data-fetching#getstaticprops-static-generation).

#### Cenário 2: Os paths da sua página dependem de dados externos

O Next.js permite que você crie páginas com rotas dinâmicas. Por exemplo, vocẽ pode criar um arquivo chamado `pages/posts/[id].js` para mostrar um único post do blog baseado no `id`. Isso permite você mostrar um post do blog com o `id: 1` quando você acessa `posts/1`.

Para saber mais sobre roteamento dinâmico, verifique a [documentação de Roteamento Dinâmico](https://nextjs.org/docs/routing/dynamic-routes).

Entretanto, qual `id` vocẽ quer pré-renderizar em build time pode depender de dados externos.

Exemplo: suponha que você adicionou apenas um post no blog (com `id: 1`) ao banco de dados. Neste caso, você só irá querer pré-renderizar `posts/1` em build time.

Mais tarde, você pode adicionar um segundo post com `id: 2`. Então você também irá querer pré-renderizar `posts/2`.

Dessa forma, os paths que são pré-renderizados dependem de dados externos. Para resolver isso, o Next.js permite que você exporte uma função `async` chamada `getStaticPaths` à partir de uma página dinâmica (`pages/posts/[id].js` neste caso). Essa função é chamda em build time e permite que você especifique quais os paths que você quer pré-renderizar.

```JavaScript
// Essa função é chamada em build time
export async function getStaticPaths() {
  // Faz a requisição a um endpoint de uma API externa para obter os posts
  const res = await fetch('https://.../posts')
  const posts = await res.json()

  // Obtém os paths que nós queremos pré-renderizar baseados nos posts
  const paths = posts.map((post) => ({
    params: { id: post.id },
  }))

  // Iremos pré-renderizar apenas esses paths em build time
  // { fallback: false } means other routes should 404.
  return { paths, fallback: false }
}

```
Também em `pages/posts/[id].js`, você precisa exportar `getStaticProps`, assim você pode fazer o fetch dos dados sobre o post com esse `id` e usar para pré-renderizar a página:

```JavaScript
function Post({ post }) {
  // Renderizar post...
}

export async function getStaticPaths() {
  // ...
}

// Essa função também é chamada em build time
export async function getStaticProps({ params }) {
  // params contém o `id` do post.
  // Se a rota é `/posts/1`, então params.id é 1
  const res = await fetch(`https://.../posts/${params.id}`)
  const post = await res.json()

  // Passa os dados do post para a p
  return { props: { post } }
}

export default Post

```
Para saber mais sobre como `getStaticPaths` funciona, verifique a [documentação do Fetch de Dados](https://nextjs.org/docs/basic-features/data-fetching#getstaticpaths-static-generation).

### When should I use Geração Estática?

Nós recomendamos a utilização de Geração Estática (com ou sem dados) sempre que possível porque sua página pode ser construída uma única vez e servida pelo CDN, o que torna muito mais rápido do que ter uma página renderizada pelo servidor em cada requisição.

Você pode usar Geração Estática em muitos tipos de páginas, incluindo:

- Páginas de Marketing
- Posts de Blogs
- Listagem de produtos de E-commerce
- Ajuda e documentação

Você deve se perguntar: "Eu posso pré-renderizar essa página antes da requisição do cliente?" Se a resposta for sim, então você deve escolher Geração Estática.

Por outro lado, Geração Estática não é uma oba ideia se você não pode pré-renderizar a página antes da requisição do usuário. Talvez sua página exiba dados atualizados com frequência, e a página de conteúdo muda em cada requisição.

Em casos como esse, você pode escolher um dos itens abaixo:

- Use Geração Estática com renderização do lado do Cliente: Você pode pular a pré-renderização de algumas partes da página e então usar o JavaScript do lado do cliente para populá-los. Para saber mais sobre essa abordagem, verifique a [documentação do Fetch de Dados](https://nextjs.org/docs/basic-features/data-fetching#fetching-data-on-the-client-side).
- Use Renderização do Lado do Servidor: O Next.js pré-renderiza uma página emn cada requisição. Ela será mais lenta porque a página não pode ser amazenada em cache, mas a página pré-renderizada sempre estará atualizada. Nõs falaremos sobre essa abordagem logo abaixo.

### Renderização do lado do Leite

CONTINUA em https://nextjs.org/docs/basic-features/pages#server-side-rendering














