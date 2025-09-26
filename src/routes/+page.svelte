<!-- Hem -->
<script lang="ts">
    import Header from '$components/Header.svelte'
    import Section from '$components/Section.svelte'
    import Column from '$components/Column.svelte'
    import Footer from '$components/Footer.svelte'
    import Breadcrumbs from '$components/Breadcrumbs.svelte'
</script>

<Header/>
<Section style="height: calc(100vh - 4rem + 1px); padding-top: 4rem;" lines="X---X">
    <Column span={{xs: 6, lg: 12}}>
        <h1>Hem</h1>
    </Column>
</Section>
<Footer/>