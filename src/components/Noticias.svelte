<script>
  export let author;
  export let publishedAt;
  export let description;
  export let title;
  export let url;
  export let urlToImage;
</script>

<div class="col">
  <div class="card border-primary mb-3">
    <div class="card mb-3">
      <img src={urlToImage} class="card-img-top" alt={title} />
      <div class="card-body">
        <h5 class="card-title">{title}</h5>
        <p class="card-text text-danger">Fuente: {author}</p>
        <p class="card-text">{description}</p>
        <p class="card-text">
          Publicado el
          <span class="font-weight-bold">{publishedAt}</span>
        </p>

      </div>
      <a
        href={url}
        class="btn btn-outline-success m-2"
        role="button"
        aria-pressed="true">
        Ver Fuente
      </a>
    </div>
  </div>
</div>
