<!-- Hem -->
<script lang="ts">
    import Header from '$components/Header.svelte'
    import Section from '$components/Section.svelte'
    import Column from '$components/Column.svelte'
    import Footer from '$components/Footer.svelte'
    import Breadcrumbs from '$components/Breadcrumbs.svelte'
</script>

<Header/>
<Section class="pt-4" lines="XXXXX">
    <Column span={6} class="pt-4 px-1">
        <h1 class="lowercase">Vi skapar oförglömliga digitala upplevelser</h1>
        <p class="hero mt-2">Vi är en Stockholm-baserad digitalbyrå mer flera år <br> av erfarenhet av att skapa banbrytande applikationer <br> och webbplatser.</p>
        <div class="button-container mt-10">
            <div class="button-test">
                <div>Button 1</div>
                <div>-></div>
            </div>
            <div class="button-test">
                <div>Button 2</div>
                <div>-></div>
            </div>
        </div>
    </Column>
</Section>
<Section class="py-8" lines="XXXXX" borderTop={true}>
    <Column span={6} class="py-4 px-1">
        <p class="subheading text-accent">Det här kan vi</p>
        <h2>Createweb i ett <br/> nötskal</h2>
    </Column>
</Section>
<Footer/>

<style lang="scss">
    .button-test {
        width: calc(50% + 1rem);
        border-top: 1px solid var(--border-color);
        border-bottom: 1px solid var(--border-color);
        padding: 1.5rem;
        margin-left: -1rem;
        font-weight: 600;
        text-transform: uppercase;
        display: flex;
        justify-content: space-between;
        align-items: center;

        &:last-of-type {
            border: none;
        }
    }
</style>