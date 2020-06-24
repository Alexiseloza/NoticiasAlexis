<script>
  import { onMount } from "svelte";
  import Noticias from "./components/Noticias.svelte";
  import Footer from "./components/Footer.svelte";
  import { each } from "svelte/internal";

  // let BASEURL = "https://newsapi.org/v2";
  // let APIKEY = "3f263a6832ca48328d7f58d238d9d9e4";

  // const noticias = (async (country = "ar") => {
  //   const URL = `${BASEURL}/top-headlines?country=${country}&category=general&apiKey=${APIKEY}`;
  //   const response = await fetch(URL);

  //   return await response.json();
  //   console.log(response);
  // })();

  // function fetchNoticias() {
  //   const URL = `https://newsapi.org/v2/top-headlines?country=ar&category=general&apiKey=3f263a6832ca48328d7f58d238d9d9e4`;
  //   fetch(URL)
  //     .then(res => res.json())
  //     .then(data => {
  //       let noticias = articles;
  //       console.log(articles);
  //     });
  // }
  let articles = [{}, {}, {}];
  onMount(async () => {
    const url = `https://newsapi.org/v2/top-headlines?country=ar&category=general&apiKey=3f263a6832ca48328d7f58d238d9d9e4`;
    const res = await fetch(url);
    const json = await res.json();
    articles = json.articles;
    console.log(json.articles);
  });
</script>

<style>
  h1 {
    color: #1f145e;
    text-transform: uppercase;
    font-size: 3em;
    font-weight: 100;
  }
  .container {
    background-color: rgb(205, 209, 209);
  }
</style>

<head>
  <title>New APP with Svelte JS | powered Alexis</title>
  <link
    rel="stylesheet"
    href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/css/bootstrap.min.css"
    integrity="sha384-9aIt2nRpC12Uk9gS9baDl411NQApFmC26EwAOH8WgZl5MYYxFfc+NcPb1dKGj7Sk"
    crossorigin="anonymous" />
</head>
<nav class="navbar navbar-expand-lg navbar-dark bg-dark mb-5 mt-0">
  <a class="navbar-brand" href="/">
    <img
      src=""
      width="30"
      height="30"
      class="d-inline-block align-top"
      alt=""
      loading="lazy" />
    Noticias Generales
  </a>
</nav>
<div class="container">
  <h1 class="display-4 text-center">Svelte Noticas</h1>
  <div class="row justify-content-md-center">

    {#each articles as article}
      <div class="col-12">
        <Noticias
          title={article.title}
          author={article.author}
          url={article.url}
          publishedAt={article.publishedAt}
          urlToImage={article.urlToImage}
          description={article.description} />

      </div>
    {/each}
  </div>
</div>
<div class="col-12">
  <Footer />
</div>
