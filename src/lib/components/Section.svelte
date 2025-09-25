<script lang="ts">
    interface Props {
        children: any
    }

    let { children }: Props = $props();
</script>

<div class="section-layout">
    <section class="cw-grid">
        {@render children?.()}
    </section>
</div>

<style lang="scss">
    .section-layout {
        display: grid;
        grid-template-columns: 1fr var(--section-width) 1fr;
        grid-template-areas: "gutter-1 section gutter-2";

        section {
            grid-area: section;
        }
    }
</style>