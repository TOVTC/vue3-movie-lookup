<script setup>
</script>

<template>
    <ul>
        <RouterLink :to="{ name: 'movie-details' }">
            <li>Movie Title (2025)</li>
        </RouterLink>
        <RouterLink :to="{ name: 'movie-details' }">
            <li>Movie Title (2024)</li>
        </RouterLink>
        <RouterLink :to="{ name: 'movie-details' }">
            <li>Movie Title (2023)</li>
        </RouterLink>
        <RouterLink :to="{ name: 'movie-details' }">
            <li>Movie Title (2022)</li>
        </RouterLink>
        <RouterLink :to="{ name: 'movie-details' }">
            <li>Movie Title (2021)</li>
        </RouterLink>
    </ul>
</template>