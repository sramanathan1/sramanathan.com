# sramanathan.com
<!DOCTYPE html>
<html class="no-js">
    <head>
        <meta charset="utf-8">
        <title>SR SW</title>
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <link rel="stylesheet" href="css/main.css">
    </head>
    <body>
    <div class="Top">Top Content</div>
    <div class="Container">
        <div class="Left">Left Content</div>
        <div class="Middle">Middle Content</div>
        <div class="Right">Right Content</div>
    </div>
    </body>
</html>

/*I love me some border-box*/
* {
    box-sizing: border-box;
}
/*This just stops me getting horizontal scrolling if anything overflows the width*/
body {
    overflow-x: hidden;
}
/*Just removing default browser padding/margin*/
html,
body {
    padding: 0;
    margin: 0;
    color: #ebebeb;
}
/*Flexbox gives us the flexiness we need. The top just stays put as there is no scrolling on the body due to the page never exceeding viewport height*/
.Top {
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: darkgreen;
    font-size: 3rem;
    position: relative;
    z-index: 10;
    height: 100px;
}
/*This is our main wrapping element, it's made 100vh high to ensure it is always the correct size and then moved into place and padded with negative margin and padding*/
.Container {
    display: flex;
    overflow: hidden;
    height: 100vh;
    margin-top: -100px;
    padding-top: 100px;
    position: relative;
    width: 100%;
    backface-visibility: hidden;
    will-change: overflow;
}
/*All the scrollable sections should overflow and be whatever height they need to be. As they are flex-items (due to being inside a flex container) they could be made to stretch full height at all times if needed.
WebKit inertia scrolling is being added here for any present/future devices that are able to make use of it.
*/
.Left,
.Middle,
.Right {
    overflow: auto;
    height: auto;
    padding: .5rem;
    -webkit-overflow-scrolling: touch;
    -ms-overflow-style: none;
}
/*Entirely optional – just wanted to remove the scrollbar on WebKit browsers as I find them ugly*/
.Left::-webkit-scrollbar,
.Middle::-webkit-scrollbar,
.Right::-webkit-scrollbar {
    display: none;
}
/*  Left and Right are set sizes while the Middle is set to flex one so it occupies all remaining space. This could be set as a width too if prefereable, perhaps using calc.*/
.Left {
    width: 12.5rem;
    background-color: indigo;
}

.Middle {
    flex: 1;
}

.Right {
    width: 12.5rem;
    background-color: violet;
}
