<script>
 import axios from "axios"
 let url = "https://api.themoviedb.org/3/search/movie?&api_key=04c35731a5ee918f014970082a0088b1&query="
  let movies = []
  let movie = ""
const search = (e) => {
  e.preventDefault()
  axios.get(url + movie).then((result)=>{
    movies = result.data.results
    movie = ""
  })
 }
</script>
<form class="flex w-full  h-20" on:submit|preventDefault={search}>
 <input class="p-4 h-12 w-3/4 ml-[4%] border border-2 solid border-sky-300 rounded" type="text" placeholder="Enter Your Movie Name" bind:value={movie}>
  <button type="submit" class="h-12 ml-2 bg-sky-400 hover:bg-sky-800 text-white items-center w-20 rounded">Search</button>
</form>
  <div class="grid gap-4 grid-cols-2">
   {#each movies as movie}
     <div class="grid-wrapper">
<!-- Card -->
<div class="card-container box">
	<div class="card-flip">
    <!-- Card Front -->
    <div  class="card front">
      <img src={"https://image.tmdb.org/t/p/original/" + movie.poster_path} class="card-img-top img-fluid" alt="movie-poster">
        <div class="card-block">
          <h5 class="card-title">{ movie.original_title }</h5>
              <p class="card-text">{ movie.vote_average }/10 </p>
                <p class="card-text"><small class="text-muted">{movie.release_date}</small></p>
          </div>
    </div>
    <!-- End Card Front -->

    <!-- Card Back -->
    <div class="card back">
      <div class="card-header warning-color"></div>
        <div class="card-block text-center">
          <h4 class="card-title">Popularity</h4>
					<p class="card-text"><a href="#" class="rating">{movie.popularity}</a></p>
           <p class="card-text">{ movie.overview}</p>
          <a href="#" class="btn orange">Watch</a>
        </div>
						
  </div>
      <!-- End Card Back -->
	</div>
</div>
   </div>
     {/each}
 </div>

