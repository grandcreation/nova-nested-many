<template>
    <div>
        <LoadingButton
            type="button"
            class="whitespace-nowrap"
            @click="$emit('run-action', selectedActionKey)"
            :processing="selectedActionKey === runningAction"
            :disabled="!!runningAction"
            align="center"
        >
            {{ selectedActionName }}
        </LoadingButton>
    </div>
</template>
<script>
    export default {
        emits: ['run-action'],
        props: {
            actions: { type: Array },

            runningAction: {
                type: String,
                required: true
            }
        },

        data: () => ({
            selectedActionKey: '',
            selectedActionName: ''
        }),

        created() {
            this.selectedActionKey = this.actions[0].uriKey;
            this.selectedActionName = this.actions[0].name;
        }
    };
</script>
