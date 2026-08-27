# Pesquisa: 10 Projetos GitHub que Consomem APIs

Todos os projetos abaixo foram **clonados localmente** (`git clone --depth 1`) e analisados diretamente no código-fonte (arquivos de dependências como `package.json`/`composer.json`/`build.gradle`, e trechos de código onde as chamadas HTTP são feitas) para confirmar o framework utilizado e a(s) API(s) consumida(s).

## Tabela resumo

| # | Projeto | Repositório | Framework/Stack | API(s) consumida(s) | Onde a API aparece no código |
|---|---------|--------------|------------------|----------------------|-------------------------------|
| 1 | **coinpulse** | [adrianhajdin/coinpulse](https://github.com/adrianhajdin/coinpulse) | Next.js (React) + TypeScript | CoinGecko API (dados de criptomoedas) | `lib/*.ts` — função `fetcher()` monta a URL a partir de `process.env.COINGECKO_BASE_URL` e envia o header `x-cg-pro-api-key` |
| 2 | **github-finder** | [mehmetsagir/github-finder](https://github.com/mehmetsagir/github-finder) | Vue.js + Vuex + Axios | GitHub REST API | `src/store/index.js` — `baseURL: "https://api.github.com/users/"` |
| 3 | **exportify** | [watsonbox/exportify](https://github.com/watsonbox/exportify) | React + TypeScript | Spotify Web API | `src/components/PlaylistTable.tsx` e `src/components/data/*.ts` — chamadas a `https://api.spotify.com/v1/...` (playlists, tracks, artists, audio-features) |
| 4 | **coingecko-api** | [codenix-sv/coingecko-api](https://github.com/codenix-sv/coingecko-api) | PHP (biblioteca) + Guzzle HTTP Client | CoinGecko API | `src/CoinGeckoClient.php` — `BASE_URI = 'https://api.coingecko.com'` |
| 5 | **php-tmdb/api** | [php-tmdb/api](https://github.com/php-tmdb/api) | PHP (biblioteca) + Guzzle HTTP Client | TMDB (The Movie Database) API v3 | `lib/Tmdb/Client.php` — `TMDB_URI = 'api.themoviedb.org/3'` |
| 6 | **Pokedex** | [skydoves/Pokedex](https://github.com/skydoves/Pokedex) | Kotlin + Jetpack Compose + Retrofit + Hilt (Android, multi-módulo) | PokeAPI | `core-network/.../NetworkModule.kt` — `.baseUrl("https://pokeapi.co/api/v2/")` |
| 7 | **github-finder** | [devzgabriel/github-finder](https://github.com/devzgabriel/github-finder) | React + TypeScript + Axios | GitHub REST API | `src/services/api.ts` — `baseURL: 'https://api.github.com/users/'` |
| 8 | **News-App** | [Raj-m01/News-App](https://github.com/Raj-m01/News-App) | Kotlin (Android) + Retrofit | NewsAPI (newsapi.org) | `app/.../retrofit/NewsApi.kt` e `RetrofitHelper.kt` — endpoints `newsapi.org/v2/top-headlines` |
| 9 | **wttr.in** | [chubin/wttr.in](https://github.com/chubin/wttr.in) | Go | Nominatim (OpenStreetMap, geocoding) + World Weather Online (dados climáticas) | `internal/location/nominatim.go` (geocoding) e `internal/weather/weatherer_wwo_cached.go` (fonte `weather:wwo`) |
| 10 | **noaa_coops** | [GClunies/noaa_coops](https://github.com/GClunies/noaa_coops) | Python (biblioteca) + `requests` | NOAA CO-OPS Tides & Currents API | `noaa_coops/*.py` — chamadas a `https://api.tidesandcurrents.noaa.gov/api/prod/datagetter` e `.../mdapi/prod/webapi/stations.json` |

## Resumo de cada projeto

**1. coinpulse** — Dashboard de criptomoedas construído em Next.js, com gráficos de candlestick (via `lightweight-charts`) para visualizar a variação de preços de moedas em tempo real. Toda a base de dados vem da API paga/gratuita do CoinGecko, incluindo cotações, pools de liquidez e dados de mercado.

**2. github-finder (mehmetsagir)** — Aplicação simples em Vue.js onde o usuário digita um nome de usuário do GitHub e a aplicação busca e exibe o perfil (repositórios, seguidores, bio) usando a API pública do GitHub. Bom projeto introdutório de consumo de API REST com Vuex para gerenciar estado.

**3. exportify** — Ferramenta que permite exportar playlists do Spotify para arquivos CSV. Usa o fluxo de autenticação OAuth do Spotify (implicit grant) para obter um token de acesso e depois faz várias chamadas à API oficial (`/v1/me`, `/v1/playlists`, `/v1/tracks`) para montar os dados.

**4. coingecko-api (codenix-sv)** — Não é uma aplicação com interface, e sim uma biblioteca/SDK em PHP que encapsula todos os endpoints da API do CoinGecko, facilitando o uso dela em outros projetos PHP via Guzzle.

**5. php-tmdb/api** — Outro SDK, dessa vez para a API do TMDB (The Movie Database). Oferece tanto acesso a dados "crus" (JSON) quanto um modelo orientado a objetos com repositórios e factories para filmes, séries e atores.

**6. Pokedex (skydoves)** — Aplicativo Android nativo bem estruturado (arquitetura multi-módulo, Jetpack Compose, Hilt para injeção de dependência, Retrofit para rede) que funciona como uma Pokédex completa, consumindo a PokeAPI pública para listar e detalhar Pokémon.

**7. github-finder (devzgabriel)** — Praticamente o mesmo conceito do projeto #2, mas implementado em React + TypeScript. Bom para comparar como o mesmo problema (consumir a API do GitHub) é resolvido em frameworks diferentes (Vue vs React).

**8. News-App** — App Android simples que lista manchetes de notícias por categoria e país, consumindo a NewsAPI via Retrofit. Um exemplo clássico de projeto de estudo para quem está aprendendo Android + consumo de API REST.

**9. wttr.in** — Um serviço de clima muito conhecido no meio Linux/terminal (dá pra consultar via `curl wttr.in`). Internamente, ele mesmo é um consumidor de APIs: usa o Nominatim (OpenStreetMap) para geocodificação de localizações digitadas pelo usuário e a World Weather Online para os dados meteorológicos, agregando tudo numa saída ASCII bonita.

**10. noaa_coops** — Biblioteca Python enxuta e bem focada, que serve de wrapper para a API pública da NOAA (agência oceânica/atmosférica dos EUA), permitindo consultar dados de marés e correntes marítimas de estações costeiras dos EUA.

## Critério de seleção

Evitei os projetos "óbvios" e super famosos (ex.: VS Code, Kubernetes, React) e priorizei aplicações **de porte pequeno/médio**, fáceis de clonar e ler o código-fonte por completo, cobrindo uma variedade de linguagens e frameworks (Next.js, Vue, PHP, Kotlin/Android, Go) e de tipos de API (REST pública gratuita, REST com autenticação/token, API de geocoding).

## Metodologia de análise

Para cada repositório:
1. `git clone --depth 1 <url>` para trazer o código para análise local.
2. Inspeção do arquivo de dependências (`package.json`, `composer.json` ou `build.gradle.kts`) para identificar o framework/bibliotecas principais (ex.: Next.js, Vue, Guzzle, Retrofit).
3. Busca por padrões de chamada HTTP no código-fonte (`fetch`, `axios`, `baseURL`, `BASE_URI`, `retrofit.Builder().baseUrl(...)`) para confirmar qual API externa é consumida e como.