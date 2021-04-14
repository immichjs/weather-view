<template>
    <div class="bg-indigo-400 rounded-2xl py-12 px-5 pr-10 text-white font-medium flex flex-col w-64 shadow-xl">
        <h1>Detalhes do tempo</h1>
        <ul>
            <li>
                <div class="flex justify-between">
                    <span>Núvem</span>
                    <span>{{ cloud }} %</span>
                </div>
            </li>
            <li>
                <div class="flex justify-between">
                    <span>Humidade</span>
                    <span>{{ humidity }} %</span>
                </div>
            </li>
            <li>
                <div class="flex justify-between">
                    <span>Vento</span>
                    <span>{{ windDir }}</span>
                    <span>{{ windKph }} %</span>
                </div>
            </li>
            <li>
                <div class="flex justify-between">
                    <span>Sensação</span>
                    <span>{{ feelslikeC }} °C</span>
                </div>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    props: {
        cloud: Number,
        humidity: Number,
        windDir: String,
        windKph: Number,
        feelslikeC: Number,
    }
}
</script>

<style>

</style>
