<script setup>
    import AppLayout from "@/Layouts/AppLayout.vue";
    import Container from "@/Components/Container.vue";
    import { computed } from "vue";
    import { formatDistance, parseISO } from "date-fns";

    const props = defineProps(['post']);

const formattedDate = computed(() => formatDistance(parseISO(props.post.created_at), new Date()));

</script>

<template>
    <AppLayout :title="post.title">
        <Container>
            <h1 class="text-2xl font-bold">{{ post.title }}</h1>
            <span class="block mt-1 text-gray-600 text-sm">{{ formattedDate }} ago by {{ post.user.name }}</span>
            <article class="mt-6">
                <pre class="whitespace-pre-wrap font-sans">{{ post.content }}</pre>
            </article>
        </Container>

    </AppLayout>
</template>