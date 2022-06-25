<script lang="ts">
    let path = "src/assets/plastic_beach.jpg";
    let alt = "Plastic Beach Album Cover"

    function hide() {
        console.log("clicked");
    }
</script>

<div id="content">
    <a href="/">
        <img src={path} alt={alt}/>
    </a>

    <div id="hide" on:click={hide}>
        <svg width="47.672" height="47.672" version="1.1" viewBox="0 0 12.613 12.613" xmlns="http://www.w3.org/2000/svg">
            <!-- Created with Inkscape (http://www.inkscape.org/) -->
            <g transform="translate(-29.698 -32.222)">
            <path d="m35.242 16.17a0.069509 0.096653 0 0 1-0.0081 0.13585 0.069509 0.096653 0 0 1-0.09774-0.01056 0.069509 0.096653 0 0 1 0.0071-0.13596 0.069509 0.096653 0 0 1 0.09781 0.0091l-0.05219 0.06384z" fill="#7f440b" stroke-width="0"/>
            <ellipse transform="scale(-1)" cx="-36.005" cy="-38.529" rx="6.3066" ry="6.3066" fill-opacity=".4" stroke-width="0"/>
            <path transform="rotate(180 29.022 30.969)" d="m17.912 24.321 4.1509-5.22m4.1013 5.3042-4.0435-5.3037" fill="none" stroke="#f8f8f8" stroke-linecap="round" stroke-width=".79375"/>
            </g>
        </svg>
    </div>
</div>

<style lang="scss">
    $width: 250px;
    $height: 250px;

    #content {
        position: relative;
        display: inline-block;
        width: $width;
        height: $height;


        img {
            display: block;
            cursor: pointer;

            width: $width;
            height: $height;
        }

        #hide {
            position: absolute;
            top: 0px;
            right: 0px;
            margin-right: 10px;
            margin-top: 10px;
            transition: all 1s;
            transform-origin: 50% 50%;
            cursor: default;

            :hover {
                transform: scale(1.1);
                transition: transform 2ms ease-out;
            }
        }
    }
</style>