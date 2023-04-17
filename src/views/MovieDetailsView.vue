<script setup>
</script>

<template>
    <main>
        <section>
            <h2>Movie Title (2023)</h2>
            <div class="movie-details">
                <img src="https://placekitten.com/400/500" alt="movie-poster" />
                <div class="movie-details">
                    <ul>
                        <li>"Tagline"</li>
                        <li>Release Date - 2023/04/05</li>
                        <li>Runtime - 1hr 45min</li>
                        <li>Genres - Slice of Life</li>
                        <li>Language - English</li>
                        <li>Link</li>
                        <li>Main Cast - Lorem ipsum dolor sit amet</li>
                        <li>Description:<br><br>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vestibulum vestibulum porta enim eget imperdiet. Suspendisse at sapien rhoncus felis varius congue eget vitae justo. Aenean sit amet ex dolor. Praesent efficitur, eros maximus laoreet rutrum, nisi enim consectetur tellus, vitae gravida sem odio sed felis. Suspendisse non velit at nulla volutpat condimentum vel a arcu. Maecenas odio nisl, egestas imperdiet mauris sit amet, mollis sagittis justo. Interdum et malesuada fames ac ante ipsum primis in faucibus. Maecenas cursus blandit tellus, in condimentum ipsum ultricies eu. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Morbi consequat scelerisque leo, sit amet accumsan ante varius eget. Nam laoreet interdum libero a tincidunt.</li>
                    </ul>
                </div>
            </div>
        </section>
        <section id="suggested">
            <div class="list">
                <h3>Recommended Films:</h3>
                <ul>
                    <RouterLink :to="{ name: 'movie-details' }">
                        <li>Movie Title (2023)</li>
                    </RouterLink>
                    <RouterLink :to="{ name: 'movie-details' }">
                        <li>Movie Title (2023)</li>
                    </RouterLink>
                    <RouterLink :to="{ name: 'movie-details' }">
                        <li>Movie Title (2023)</li>
                    </RouterLink>
                    <RouterLink :to="{ name: 'movie-details' }">
                        <li>Movie Title (2023)</li>
                    </RouterLink>
                    <RouterLink :to="{ name: 'movie-details' }">
                        <li>Movie Title (2023)</li>
                    </RouterLink>
                </ul>
            </div>
            <div class="list">
                <h3>Similar Films:</h3>
                <ul>
                    <RouterLink :to="{ name: 'movie-details' }">
                        <li>Movie Title (2023)</li>
                    </RouterLink>
                    <RouterLink :to="{ name: 'movie-details' }">
                        <li>Movie Title (2023)</li>
                    </RouterLink>
                    <RouterLink :to="{ name: 'movie-details' }">
                        <li>Movie Title (2023)</li>
                    </RouterLink>
                    <RouterLink :to="{ name: 'movie-details' }">
                        <li>Movie Title (2023)</li>
                    </RouterLink>
                    <RouterLink :to="{ name: 'movie-details' }">
                        <li>Movie Title (2023)</li>
                    </RouterLink>
                </ul>
            </div>
        </section>
    </main>
</template>