<!-- Hem -->
<script lang="ts">
    import Header from '$components/Header.svelte'
    import Section from '$components/Section.svelte'
    import Column from '$components/Column.svelte'
    import Footer from '$components/Footer.svelte'
</script>

<Header/>
<Section style="height: 100vh" lines="X-X-X" borderBottom={true}>
    <Column span={8} style="padding: 1rem;">
        <h2>Lorem ipsum dolor sit amet consectetur adipisicing elit. Ipsa, culpa!</h2>
    </Column>
</Section>
<Section style="height: 100vh" lines="XX-XX">
    <Column span={3}/>
    <Column span={6} style="padding: 1rem;">
        <h3>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Obcaecati itaque aliquid, deserunt iusto iste eaque ab doloremque repudiandae. Obcaecati, doloremque.
        </h3>
    </Column>
    <Column span={3}/>
</Section>
<Footer/>