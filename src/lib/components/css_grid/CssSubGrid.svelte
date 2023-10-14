<h1>
    Change window width to see the difference in how the images resize
    themselves
</h1>
<h3>
    Each card is a grid with 2 columns, the first column is the image, the
    second is the text. All cards are inside another parent grid with 4 columns.
    Each card spans 2 columns. 
    <br>
    <br>
    This is important for the subgrid, that the element spans 2 or more columns, in order for the child columns
    to line up with the parent.
</h3>
<hr />
<h1>With Subgrid</h1>
<h3>
    With subgrid, each card child grid respects the parent grid columns.
    Meaning that the images all retain same width throughout the window resizing.
</h3>
<div class="with-subgrid card-grid">
    <div class="card">
        <h2>Lorem ipsum</h2>
        <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Assumenda
            recusandae maxime distinctio quos ullam incidunt.
        </p>
        <img src="//unsplash.it/501" alt="" />
    </div>
    <div class="card">
        <h2>Omnis, veritatis odio.</h2>
        <p>
            Enim molestiae recusandae ut dolor sit amet consectetur adipisicing.
            odit possimus eius inventore. Quasi illo unde neque? Itaque,
            deleniti adipisci?
        </p>
        <img src="//unsplash.it/502" alt="" />
    </div>
    <div class="card">
        <h2>Exercitationem, libero quam!</h2>
        <p>
            Error maiores culpa eaque. Quam quisquam quae nostrum ipsa dolorum
            atque aperiam fugit soluta error!
        </p>
        <img src="//unsplash.it/503" alt="" />
    </div>
    <div class="card">
        <h2>Quibusdam, recusandae odio.</h2>
        <p>
            Corporis laboriosam, neque est commodi architecto voluptatem, ipsam
            corrupti ullam similique eligendi hic qui natus?
        </p>
        <img src="//unsplash.it/504" alt="" />
    </div>
    <div class="card">
        <h2>Modi, exer citat ionem dicta.</h2>
        <p>
            Laboriosam, aliquam tempore minus dolorem ullam et veniam
            asperiores, eveniet vitae odit itaque eligendi ducimus?
        </p>
        <img src="//unsplash.it/505" alt="" />
    </div>
    <div class="card">
        <h2>Dolore.</h2>
        <p>
            Reprehenderit, labore. Lorem ipsum dolor sit amet, consectetur
            adipisicing elit. Sunt, aut. harum vitae voluptate alias saepe
            debitis quo perspiciatis, delectus fugiat modi eveniet.
        </p>
        <img src="//unsplash.it/506" alt="" />
    </div>
</div>
<br />
<br />
<hr />
<h1>Without Subgrid</h1>
<br />
<br />
<h3>
    Without subgrid, each card child grid is independent of the parent grid.
    Meaning that the images all have different widths depending on the window
    resizing.
</h3>
<div class="card-grid">
    <div class="card">
        <h2>Lorem ipsum</h2>
        <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Assumenda
            recusandae maxime distinctio quos ullam incidunt.
        </p>
        <img src="//unsplash.it/501" alt="" />
    </div>
    <div class="card">
        <h2>Omnis, veritatis odio.</h2>
        <p>
            Enim molestiae recusandae ut dolor sit amet consectetur adipisicing.
            odit possimus eius inventore. Quasi illo unde neque? Itaque,
            deleniti adipisci?
        </p>
        <img src="//unsplash.it/502" alt="" />
    </div>
    <div class="card">
        <h2>Exercitationem, libero quam!</h2>
        <p>
            Error maiores culpa eaque. Quam quisquam quae nostrum ipsa dolorum
            atque aperiam fugit soluta error!
        </p>
        <img src="//unsplash.it/503" alt="" />
    </div>
    <div class="card">
        <h2>Quibusdam, recusandae odio.</h2>
        <p>
            Corporis laboriosam, neque est commodi architecto voluptatem, ipsam
            corrupti ullam similique eligendi hic qui natus?
        </p>
        <img src="//unsplash.it/504" alt="" />
    </div>
    <div class="card">
        <h2>Modi, exer citat ionem dicta.</h2>
        <p>
            Laboriosam, aliquam tempore minus dolorem ullam et veniam
            asperiores, eveniet vitae odit itaque eligendi ducimus?
        </p>
        <img src="//unsplash.it/505" alt="" />
    </div>
    <div class="card">
        <h2>Dolore.</h2>
        <p>
            Reprehenderit, labore. Lorem ipsum dolor sit amet, consectetur
            adipisicing elit. Sunt, aut. harum vitae voluptate alias saepe
            debitis quo perspiciatis, delectus fugiat modi eveniet.
        </p>
        <img src="//unsplash.it/506" alt="" />
    </div>
</div>

<!-- CSS Before -->
<!-- <style>
    body {
        font-size: 1.125rem;
        line-height: 1.5;
    }

    .card-grid {
        display: grid;
        gap: 2rem;
        grid-template-columns: 1fr 1fr;

        /*   other styling */
        width: min(90%, 60rem);
        margin-inline: auto;
    }

    .card {
        display: grid;
        grid-template-columns: minmax(6ch, 20ch) 1fr;
        grid-template-rows: min-content 1fr;
        gap: 1em;
        border: 3px solid black;
    }

    .card h2 {
        grid-column: 2;
        padding-top: 1rem;
        padding-right: 1em;
        font-size: 1.75rem;
        line-height: 1;
    }

    .card p {
        grid-column: 2;
        padding-bottom: 1rem;
        padding-right: 1em;
    }

    .card img {
        grid-column: 1;
        grid-row: 1 / span 2;
        width: 100%;
        height: 100%;
        object-fit: cover;
    }

    img {
        max-width: 100%;
    }

    h2,
    h3,
    p {
        margin: 0;
    }

    h1 {
        margin: 2em;
        text-align: center;
    }
</style> -->

<!-- CSS After -->
<style>
    :global(html) {
        font-family: Arial, Helvetica, sans-serif;
    }

    body {
        font-size: 1.125rem;
        line-height: 1.5;
    }

    img {
        max-width: 100%;
    }

    h2,
    h3,
    p {
        margin: 0;
    }

    h1,
    h2, 
    h3{
        margin: 2rem auto;
        text-align: center;
        max-width: 30rem;
        
    }

    .with-subgrid.card-grid {
        display: grid;
        gap: 2rem;
        grid-template-columns:
            minmax(6ch, 20ch) 1fr
            minmax(6ch, 20ch) 1fr; /* MODIFIED */

        /*   other styling */
        width: min(90%, 60rem);
        margin-inline: auto;
    }

    .with-subgrid .card {
        grid-column: span 2; /* ADDED */
        grid-template-columns: subgrid; /* ADDED */

        display: grid;
        /* grid-template-columns: minmax(6ch, 20ch) 1fr; */ /* DISABLED */
        grid-template-rows: min-content 1fr;
        gap: 1em;
        border: 3px solid black;
    }

    .with-subgrid .card h2 {
        grid-column: 2;
        padding-top: 1rem;
        padding-right: 1em;
        font-size: 1.75rem;
        line-height: 1;
    }

    .with-subgrid .card p {
        grid-column: 2;
        padding-bottom: 1rem;
        padding-right: 1em;
    }

    .with-subgrid .card img {
        grid-column: 1;
        grid-row: 1 / span 2;
        width: 100%;
        height: 100%;
        object-fit: cover;
    }

    .card-grid {
        display: grid;
        gap: 2rem;
        grid-template-columns: 1fr 1fr;

        /*   other styling */
        width: min(90%, 60rem);
        margin-inline: auto;
    }

    .card {
        display: grid;
        grid-template-columns: minmax(6ch, 20ch) 1fr;
        grid-template-rows: min-content 1fr;
        gap: 1em;
        border: 3px solid black;
    }

    .card h2 {
        grid-column: 2;
        padding-top: 1rem;
        padding-right: 1em;
        font-size: 1.75rem;
        line-height: 1;
    }

    .card p {
        grid-column: 2;
        padding-bottom: 1rem;
        padding-right: 1em;
    }

    .card img {
        grid-column: 1;
        grid-row: 1 / span 2;
        width: 100%;
        height: 100%;
        object-fit: cover;
    }
</style>
