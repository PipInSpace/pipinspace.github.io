# Ring

[pipinspace.github.io](https://pipinspace.github.io)
[tudbut.de](https://tudbut.de)

Format: <"Back" "Here" "Next">
To add a entry, ask the last user in the list to update their link, link "Back" to them and add the first user as the "Next" link

Example:
<style>
    .webring {
        height: 40px;
        display: flex;
        align-items: center;
        justify-content: center;
        margin-bottom: 20px;
        font-size: 20px;
    }

    .webring a {
        flex-grow: 0;
        display: flex;
        line-height: 0;
        margin-left: 5px;
        margin-right: 5px;
        align-items: center;
    }

    .webring a img {
        flex-grow: 0;
        height: 40px;
        width: calc(40px*2.5);
    }
</style>
<div class="webring">
    <a href="https://example.org">&lt <img src=""></a>
    <a href=""><img src="https://pipinspace.github.io/webring/logo.png"></a>
    <a href="https://tudbut.de"><img src="http://tudbut.de:81/webring/logo.png"> &gt</a>
</div>