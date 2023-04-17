<script setup>
</script>

<template>
    <main>
        <h2>Popular:</h2>
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
    </main>
</template>