<script>
import sounds from './sounds.json'
const audio = new Audio();
const sections = Object
    .keys(sounds)
    .map( section => ({
      section,
      title: section[0].toUpperCase() + section.slice(1),
    }));

    function playSound(section, file) {
        const path = `sounds/${section}/${file}`;
        audio.src = path;
        console.log(file);
        audio.play()
    }

</script>



<div class="container">
    {#each sections as { section, title } }
        {#each sounds[section] as { file, name } }
            <div class="sound-btn" on:click={()=> playSound(section, file)}>
                <span>{name}</span>
                <small>{section}</small>
            </div>
        {/each}
    {/each}
</div>

<style>
.container{
    width: 100%;
    height: 100%;
    text-align: center;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
}


.sound-btn{
    display: inline-flex;
    justify-content: center;
    justify-items: center;
    flex-direction: column;
    outline: 1px solid red;
    padding: 1.5em;
    margin: 0.5em;
    font-size: 1.25vw;
    cursor: pointer;
    width: 12vw;
    height: 12vh;
    vertical-align: middle;
    box-shadow: 3px 3px 3px red;
    transition: all 0.25s ease;
}

.sound-btn small{
    margin-top: 20px;
    opacity: 0.8;
}

.sound-btn:hover{
    background: yellow;
    color: #000;
}

.sound-btn:active{
    transform: translate(3px, 3px);
}

</style>
