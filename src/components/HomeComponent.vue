<template>
    <main>
        <div class="search-box">
            <input type="text" class="search-bar" placeholder="Search..">
        </div>

        <div class="weather-wrap">
            <div class="location-box">
                <div class="location">Nairobi, KE</div>
                <div class="date">Monday 20 January 2023</div>
                
                <div class="weather-box">
                    <div class="temp">9°C</div>
                    <div class="weather">Rain</div>
                </div>
            </div>
        </div>
    </main>
</template>

<script>
export default {
    data(){
        return {
            api_key: 'f41ba71a687a7e883bbf4df15e2c525e',
            api_endpoint: 'https://api.openweathermap.org',
        }
    }
}
</script>

<style scoped>


</style>