<script>
    export let open = true
</script>

<style>
    /* source: https://www.w3schools.com/howto/howto_css_modals.asp */
    .modal {
        /* display: none; /* Hidden by default */
        position: fixed; /* Stay in place */
        z-index: 1; /* Sit on top */
        left: 0;
        top: 0;
        width: 100%; /* Full width */
        height: 100%; /* Full height */
        overflow: auto; /* Enable scroll if needed */
        background-color: rgba(0,0,0,0.4);
    }

    .modal-content {
        margin: 5% auto; /* 15% from the top and centered */
        padding: 20px;
        border: 1px solid #888;
        width: 80%; /* Could be more or less, depending on screen size */
    }

    /* The Close Button */
    .close {
        float: right;
        color: #aaa;
        font-size: 28px;
        font-weight: bold;
    }

    .close:hover, .close:focus {
        color: black;
        text-decoration: none;
        cursor: pointer;
    }
</style>

{#if open}
    <div class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <span on:click={() => open = !open} class="close">&times;</span>
            </div>
            <slot></slot>
        </div>
    </div>
{/if}
