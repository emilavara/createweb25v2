<script lang="ts">
    type BP = 'xs' | 'lg';
    type ResponsiveValue = number | Partial<Record<BP, number>>;

    interface Props {
        span?: ResponsiveValue;
        start?: ResponsiveValue;
        end?: ResponsiveValue;
        class?: string;
        children?: any;
        style?: string;
    }

    let { span, start, end, class: className, children, style }: Props = $props();

    function normalizeSpan(value?: ResponsiveValue): ResponsiveValue | undefined {
        if (value == null) return undefined;
        if (typeof value === 'number') {
            return { xs: 12, lg: value }; // default xs:12
        }
        return { xs: value.xs ?? 12, lg: value.lg };
    }

    function classesFor(prefix: string, value?: ResponsiveValue): string[] {
        if (value == null) return [];
        if (typeof value === 'number') return [`${prefix}-${value}`]; // desktop-only
        const out: string[] = [];
        if (value.xs != null) out.push(`${prefix}-xs-${value.xs}`);
        if (value.lg != null) out.push(`${prefix}-${value.lg}`);
        return out;
    }

    const columnClasses = $derived(() => {
        const normalizedSpan = normalizeSpan(span);
        return [
            ...classesFor('cw-col', normalizedSpan),
            ...classesFor('cw-cs', start),
            ...classesFor('cw-ce', end)
        ].join(' ');
    });
</script>

<div {style} class={`${columnClasses()} ${className ?? ''}`}>
    {@render children?.()}
</div>

<!--

kolumnkomponent för "emils fett coola grid system™ 2022"

användning:
- `span`: ange hur många kolumner komponenten ska spänna över. Tar antingen ett nummer (för lg) eller ett objekt med brytpunkter `{ xs, lg }`.
- `start` / `end`: ange exakt vilken kolumn komponenten ska börja och sluta på (kan också vara responsivt).

exempel:
<Column span={6}>Halv bredd på stora skärmar, default 12 på xs</Column>
<Column span={{ xs: 12, lg: 4 }}>Responsiv kolumn</Column>
<Column start={{ xs: 1, lg: 3 }} end={{ xs: 13, lg: 9 }}>Placera med gridlines</Column>

tänk på:
- om ingen `xs`-span anges, används automatiskt 12 (full bredd på mobil).
- blanda inte `span` med `start`/`end` – välj ett av sätten.

-->