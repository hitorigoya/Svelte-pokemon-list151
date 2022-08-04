<script>
    import { onMount } from "svelte";
    import Type from "./Type.svelte";

    let pokeList = [];
    let pokeListOriginal = [];
    let currentSort = "";

    onMount(async () => {
        const res = await fetch("pokemon-list151.json");
        pokeListOriginal = await res.json();
        console.log(pokeListOriginal);
        numberSort();
        currentSort = "number";
    });

    const numberSort = () => {
        pokeList = pokeListOriginal.map((x) => x);
        pokeList.sort((a, b) => {
            return a.no - b.no;
        });
    };

    const nameSort = () => {
        pokeList = pokeListOriginal.map((x) => x);
        pokeList.sort((a, b) => {
            if (a.name < b.name) {
                return -1;
            }
            if (a.name > b.name) {
                return 1;
            }
            return 0;
        });
    };

    const typeSort = () => {
        pokeList = pokeListOriginal.map((x) => x);
        pokeList.sort((a, b) => {
            if (a.types < b.types) {
                return -1;
            }
            if (a.types > b.types) {
                return 1;
            }
            return 0;
        });
    };

    const abilitySort = () => {
        pokeList = pokeListOriginal.map((x) => x);
        pokeList.sort((a, b) => {
            if (a.abilities < b.abilities) {
                return -1;
            }
            if (a.abilities > b.abilities) {
                return 1;
            }
            return 0;
        });
    };
</script>

<table>
    <thead>
        <tr>
            <th />
            <th
                on:click={numberSort}
                on:click={() => {
                    currentSort = "number";
                }}
                class:selected={currentSort === "number"}>No.</th
            >
            <th
                on:click={nameSort}
                on:click={() => {
                    currentSort = "name";
                }}
                class:selected={currentSort === "name"}>Name</th
            >
            <th
                on:click={typeSort}
                on:click={() => {
                    currentSort = "type";
                }}
                class:selected={currentSort === "type"}>Type</th
            >
            <th
                on:click={abilitySort}
                on:click={() => {
                    currentSort = "ability";
                }}
                class:selected={currentSort === "ability"}>Ability</th
            >
        </tr>
    </thead>
    <tbody>
        {#each pokeList as pokeItem}
            <tr>
                <td class="img_td">
                    <img
                        src="images/{pokeItem.no
                            .toString()
                            .padStart(3, '0')}MS.png"
                        alt=""
                    />
                </td>
                <td>{pokeItem.no}</td>
                <td>{pokeItem.name}</td>
                <td>
                    <div class="type_td">
                        {#each pokeItem.types as type}
                            <Type {type} />
                        {/each}
                    </div>
                </td>
                <td>
                    <div class="ability_td">
                        {#each pokeItem.abilities as ability}
                            <span class="ability">{ability}</span>
                        {/each}
                    </div>
                </td>
            </tr>
        {/each}
    </tbody>
</table>

<style>
    table {
        border-collapse: collapse;
        margin: auto;
    }
    th {
        padding: 4px 16px;
        text-align: start;
    }
    th:hover {
        cursor: pointer;
    }

    td {
        padding: 4px 16px;
    }

    tr {
        border: none;
        border-bottom: 1px solid #3b3b3d;
    }

    tbody tr:last-of-type {
        border-bottom: none;
    }

    tbody tr:hover {
        background-color: rgb(255, 62, 0, 0.04);
    }

    img {
        display: block;
    }

    tr:hover img {
        transform: translateX(-4px);
    }

    .img_td {
        padding: 0;
    }

    .type_td {
        display: flex;
        flex-wrap: wrap;
        gap: 8px;
    }
    .ability_td {
        display: flex;
        flex-wrap: wrap;
        column-gap: 16px;
        row-gap: 8px;
    }
    .selected {
        color: #ff3e00;
    }
    @media (max-width: 768px) {
        th,
        td {
            font-size: 14px;
            padding: 4px 8px;
        }
    }
</style>
