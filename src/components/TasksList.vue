<script setup>


const props =defineProps({
    tasks:{
        type:Array,
        required:true

    }
})
</script>


<template >
    <div>
        <ul>
            <li v-for="(task,index) in tasks" :key="index"
            style="
                display: flex;
                justify-content: space-between;
                align-items: center;
                margin-right: auto;
                margin-bottom: 0.5rem;
                background: #2b2b3f;
                padding: 0.5rem;
                border-radius: 0.25rem;
            "
            >
            <span
                :style="{
                    flexGrow: 1,
                    color: task.done ? '#888' : '#fff',
                    textDecoration: task.done ? 'line-through' : 'none'
                }"
            >
            {{ task.task }}
            </span>
            <div>
                    <button
                        :disabled="task.done"
                        @click="$emit('mark-done', index)"
                        style="
                        background: #00c851;
                        margin-left: auto;
                        color: white;
                        border: none;
                        padding: 0.3rem 0.6rem;
                        border-radius: 0.25rem;
                        cursor: pointer;
                        font-size: 0.9rem;
                        "  
                    >
                    {{ task.done ? '✓ Done' : 'Mark Done' }}
                </button>
                <button
                    @click="$emit('remove-task', index)"
                    style="
                        background: transparent;
                        color: #ff4444;
                        border: none;
                        padding: 0.3rem 0.6rem;
                        margin-left: 0.5rem;
                        border-radius: 0.25rem;
                        cursor: pointer;
                        font-size: 0.9rem;
                    "
                >
                Remove
                </button>

            </div>
            




            </li>
        </ul>
    </div>
</template>

