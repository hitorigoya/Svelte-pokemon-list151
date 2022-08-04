<script>
    export let type;
</script>

{#if type === "ノーマル"}
    <span class="normal">{type}</span>
{:else if type === "くさ"}
    <span class="grass">{type}</span>
{:else if type === "ほのお"}
    <span class="fire">{type}</span>
{:else if type === "みず"}
    <span class="water">{type}</span>
{:else if type === "でんき"}
    <span class="electric">{type}</span>
{:else if type === "こおり"}
    <span class="ice">{type}</span>
{:else if type === "かくとう"}
    <span class="fighting">{type}</span>
{:else if type === "どく"}
    <span class="poison">{type}</span>
{:else if type === "じめん"}
    <span class="ground">{type}</span>
{:else if type === "ひこう"}
    <span class="flying">{type}</span>
{:else if type === "エスパー"}
    <span class="psychic">{type}</span>
{:else if type === "むし"}
    <span class="bug">{type}</span>
{:else if type === "いわ"}
    <span class="rock">{type}</span>
{:else if type === "ゴースト"}
    <span class="ghost">{type}</span>
{:else if type === "ドラゴン"}
    <span class="dragon">{type}</span>
{:else if type === "あく"}
    <span class="dark">{type}</span>
{:else if type === "はがね"}
    <span class="steel">{type}</span>
{:else if type === "フェアリー"}
    <span class="fairy">{type}</span>
{:else}
    <span>{type}</span>
{/if}

<style>
    span {
        font-size: 14px;
        padding: 2px 4px;
        border-radius: 4px;
        color: #252526;
    }
    @media (max-width: 768px) {
        span {
            font-size: 12px;
        }
    }
    .normal {
        background-color: #a8a77a;
    }
    .grass {
        background-color: #7ac74c;
    }
    .fire {
        background-color: #ee8130;
    }
    .water {
        background-color: #6390f0;
    }
    .electric {
        background-color: #f7d02c;
    }
    .ice {
        background-color: #96d9d6;
    }
    .fighting {
        background-color: #c22e28;
        color: #f7f7f7;
    }
    .poison {
        background-color: #a33ea1;
        color: #f7f7f7;
    }
    .ground {
        background-color: #e2bf65;
    }
    .flying {
        background-color: #a98ff3;
    }
    .psychic {
        background-color: #f95587;
    }
    .bug {
        background-color: #a6b91a;
    }
    .rock {
        background-color: #b6a136;
    }
    .ghost {
        background-color: #735797;
        color: #f7f7f7;
    }
    .dragon {
        background-color: #6f35fc;
        color: #f7f7f7;
    }
    .dark {
        background-color: #705746;
    }
    .steel {
        background-color: #b7b7ce;
    }
    .fairy {
        background-color: #d685ad;
        color: #fff;
    }
</style>
