<script>
export default {
    data: () => ({
        names: ['FGREG', 'EFKEWP', 'DLPAQDK', 'D23342']
    }),
};
</script>

<template>
    <div style="display: flex">
        <ul v-for="name in names">
            <li> {{ name }}</li>
            <li>Tamanho: {{ name.length }}</li>
        </ul>
    </div>
</template>
