<script lang="typescript">
    export let volume = 0;

    const NB_BARS = 20;

    function color(i: number, volume: number) {
        const red = (255 * i) / NB_BARS;
        const green = 255 * (1 - i / NB_BARS);

        let alpha = 1;
        if (i >= volume) {
            alpha = 0.5;
        }

        return "background-color:rgba(" + red + ", " + green + ", 0, " + alpha + ")";
    }
</script>

<div class="horizontal-sound-meter" class:active={volume !== undefined}>
    {#each [...Array(NB_BARS).keys()] as i (i)}
        <div style={color(i, volume)} />
    {/each}
</div>

<style lang="scss">
    .horizontal-sound-meter {
        display: flex;
        flex-direction: row;
        width: 50%;
        height: 30px;
        margin-left: auto;
        margin-right: auto;
        margin-top: 1vh;
    }

    .horizontal-sound-meter div {
        margin-left: 5px;
        flex-grow: 1;
    }
</style>
