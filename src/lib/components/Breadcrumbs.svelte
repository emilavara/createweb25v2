<script lang="ts">
    import { page } from "$app/stores";
    import { get } from "svelte/store";

    type Crumb = {
        name: string;
        path: string;
    };

    const labelMap: Record<string, string> = {
        "": "CreateWeb",
        "case": "Case",
        "tjanster": "Tjänster",
        "om-oss": "Om oss",
        "kontakt": "Kontakt"
    };

    function getBreadcrumbs(): Crumb[] {
        const url = get(page).url.pathname.replace(/\/+$/, "");
        const segments = url.split("/").filter(Boolean);

        const crumbs: Crumb[] = [];
        crumbs.push({ name: labelMap[""], path: "/" });

        segments.forEach((seg, i) => {
            const path = "/" + segments.slice(0, i + 1).join("/");
            crumbs.push({
                name: labelMap[seg] || decodeURIComponent(seg),
                path
            });
        });

        return crumbs;
    }

    const breadcrumbs = getBreadcrumbs();
</script>

<div class="cw-breadcrumbs">
    {#each breadcrumbs as crumb, i}
        {#if i < breadcrumbs.length - 1}
            <a href={crumb.path} class="breadcrumb">{crumb.name}</a>
            <span class="separator">›</span>
        {:else}
            <span class="breadcrumb">{crumb.name}</span>
        {/if}
    {/each}
</div>

<style lang="scss">
.cw-breadcrumbs {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    font-size: 0.9rem;
    color: #666;

    .breadcrumb {
        text-decoration: none;
        color: inherit;
        transition: color 0.2s ease;

        &:hover {
            color: #000;
        }

        &.current {
            font-weight: 600;
            color: #000;
            pointer-events: none;
        }
    }

    .separator {
        color: #aaa;
        user-select: none;
    }
}
</style>