<script lang="ts" context="module">
    export interface Link {
        href: string;
        text: string;
        newTab?: boolean;
    }
</script>


<script lang="ts">
    export let links: Link[];
</script>


<ul>
    {#each links as link}
    <a class="draw-border" href={link.href} target={link.newTab ? "_blank" : ""}>
        <li>{link.text}</li>
    </a>
    {/each}
</ul>


<style lang="scss">
    ul {
        list-style: none;
        
        width: 100%;
        margin: 0;
        padding: 0;
        
        display: flex;
        flex-direction: column;
    }
    
    li {
        width: 100%;
        
        
        font-family: "Analogue Italic";
        font-size: 1.5rem;
    }
    
    a {
        text-decoration: inherit;
        color: inherit;
        
        padding: 1rem 1.5rem;
        margin-top: 1rem;
        text-align: center;
    }
    
    a:first-child {
        margin-top: 0;
    }
    
    /* 
     * Link hovering styles
     * https://codepen.io/giana/pen/xdXpJB
     */
    @mixin btn-border-drawing($color: #ccc, $hover: black, $width: 2px, $vertical: top, $horizontal: left, $duration: 0.25s) {
        box-shadow: inset 0 0 0 $width $color;
        color: $color;
        transition: color $duration $duration/3;
        position: relative;
        
        &::before,
        &::after {
            border: 0 solid transparent;
            box-sizing: border-box;
            content: '';
            pointer-events: none;
            position: absolute;
            width: 0; height: 0;
            
            #{$vertical}: 0; 
            #{$horizontal}: 0;
        }
        
        &::before {
            $h-side: if($horizontal == 'left', 'right', 'left');
            
            border-#{$vertical}-width: $width;
            border-#{$h-side}-width: $width;
        }
        
        &::after {
            $v-side: if($vertical == 'top', 'bottom', 'top');
            
            border-#{$v-side}-width: $width;
            border-#{$horizontal}-width: $width;
        }
        
        &:hover {
            color: $hover;
            
            &::before,
            &::after {
                border-color: $hover;
                transition: border-color 0s, width $duration, height $duration;
                width: 100%;
                height: 100%;
            }
            
            &::before { transition-delay: 0s, 0s, $duration; }
            
            &::after { transition-delay: 0s, $duration, 0s; }
        }
    }
    
    .draw-border {
        @include btn-border-drawing(black, #dfcebf, 2px, bottom, right);
    }
</style>