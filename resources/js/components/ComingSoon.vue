<script setup>
const props = defineProps({
    name: { type: String, default: '4138 Commons' },
    tagline: { type: String, default: 'Coming Soon' },
});

const year = new Date().getFullYear();
</script>

<template>
    <main
        class="relative flex min-h-screen flex-col items-center justify-center overflow-hidden bg-gradient-to-b from-slate-50 to-blue-100 px-6 py-16 text-center text-slate-800"
    >
        <!-- Soft decorative glow -->
        <div
            class="pointer-events-none absolute -top-40 left-1/2 h-96 w-96 -translate-x-1/2 rounded-full bg-blue-300/40 blur-3xl"
            aria-hidden="true"
        ></div>

        <div class="relative z-10 flex max-w-2xl flex-col items-center">
            <!-- Building mark -->
            <div
                class="mb-8 flex h-16 w-16 items-center justify-center rounded-2xl bg-white shadow-lg shadow-slate-900/5 ring-1 ring-slate-900/5"
            >
                <svg
                    class="h-9 w-9 text-blue-600"
                    viewBox="0 0 24 24"
                    fill="none"
                    stroke="currentColor"
                    stroke-width="1.6"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    aria-hidden="true"
                >
                    <path d="M6 22V4a2 2 0 0 1 2-2h8a2 2 0 0 1 2 2v18Z" />
                    <path d="M6 12H4a2 2 0 0 0-2 2v6a2 2 0 0 0 2 2h2" />
                    <path d="M18 9h2a2 2 0 0 1 2 2v9a2 2 0 0 1-2 2h-2" />
                    <path d="M10 6h4" />
                    <path d="M10 10h4" />
                    <path d="M10 14h4" />
                    <path d="M10 18h4" />
                </svg>
            </div>

            <!-- Brand logo (replaces text title) -->
            <img
                src="/images/logo.png"
                :alt="name"
                class="w-72 max-w-full sm:w-96"
                width="913"
                height="143"
            />

            <p class="mt-6 text-sm font-semibold uppercase tracking-[0.3em] text-blue-600">
                {{ tagline }}
            </p>

            <p class="mt-8 max-w-lg text-balance text-lg leading-relaxed text-slate-600">
                Premium commercial suites for lease at 4138 Bristol Highway,
                Johnson City, Tennessee. Our new website is on its way.
            </p>

            <div class="mt-10 h-px w-24 bg-slate-300/70" aria-hidden="true"></div>
        </div>

        <footer class="relative z-10 mt-16 text-sm text-slate-500">
            <p>&copy; {{ year }} {{ name }}. All Rights Reserved.</p>
            <p class="mt-1">
                a
                <a
                    href="https://moonwhale.media"
                    target="_blank"
                    rel="noopener"
                    class="font-medium text-blue-600 underline-offset-2 hover:underline"
                    >moonwhale.media</a
                >
                production
            </p>
        </footer>
    </main>
</template>
