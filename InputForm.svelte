<script>
    import { createEventDispatcher } from 'svelte'
    const dispatch = createEventDispatcher()

    export let fields = []
    export let title = ''
    export let valueKey     = 'value'
    export let label        = (field, index) => field.label || key
    export let separator    = (field, index) => ':'
    export let type         = (field, index) => field.type || 'text'
    export let defaultValue = (field, index) => field.default || ''

    $: {
        fields = fields.map((field, index) => {
            if (field[valueKey] === undefined) {
                field[valueKey] = defaultValue(field, index)
            }
            return field
        })
    }

    const emitEvents = (event, index) => {
        fields[index][valueKey] = event.target.value
        dispatch('change', { field: fields[index] })
    }
</script>

<form>
    {#if title}
        <legend>{title}</legend>
    {/if}
    {#each fields as field, index}
        <div class="label-input-pair">
            <label>
                {label(field, index)}{separator(field, index)}
            </label>
            <input
                on:keyup={e => emitEvents(e, index)}
                type={type(field, index)}
                value={field[valueKey]}
            >
        </div>
    {/each}
</form>
