<template>
    <div>
        {{ counter }}

        {{ computedCounter }}

        <button @click="increment">Increment</button>
    </div>
</template>

<script>
    import { computed, defineComponent } from '@vue/composition-api';
    import { useCounterStore } from './store';
    import { storeToRefs } from "pinia";

    export default defineComponent({
        name: 'App',
        setup() {
            const counterStore = useCounterStore();

            const { counter } = storeToRefs(counterStore);

            const computedCounter = computed(() => counterStore.counter)

            return {
                counter,
                computedCounter,
                increment: counterStore.increment,
            };
        },
    });
</script>

<style scoped>

</style>
