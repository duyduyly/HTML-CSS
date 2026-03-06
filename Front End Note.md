# Note About Front-End

- [Structure standard CEO in the Front End](#Structure-Standard-CEO-in-the-Front-End)
- [Standard Use Row and Column in Bootstrap](#Standard-Use-Row-and-Column-in-Bootstrap)
- [Padding and Margin](#Padding-and-Margin)

-----------------
<br/>

## Structure Standard CEO in the Front-End
- Meta tags are used to provide information about the webpage to search engines and social media platforms. They are placed in the `<head>` section of the HTML document and can include information such as the title, description, keywords, and author of the webpage. Meta tags can also be used to control how search engines index the webpage and how it is displayed in search results.
- Structure standard CEO is a standard structure for HTML documents that is used to improve SEO and user experience. It consists of the following tags:

```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Learn SCSS for Beginners</title>

    <meta name="description" content="Complete SCSS tutorial for frontend developers.">

    <meta name="robots" content="index, follow">

    <meta property="og:title" content="Learn SCSS for Beginners">
    <meta property="og:description" content="Complete SCSS tutorial">
    <meta property="og:image" content="image.jpg">
    <meta property="og:url" content="https://example.com">
</head>

<body>

<header>
    <!-- Logo + menu -->
</header>

<nav>
    <!-- Menu Redirect -->
</nav>

<!--or-->
<header>
    <!-- Logo -->
    <nav>
        <!-- Menu Redirect -->
    </nav>
</header>

<main>

    <section>
        <h1>Main Title</h1>
        <p>Main Content</p>
    </section>

    <section>
        <h2>Part of Content</h2>
        <p>Detail Content</p>
    </section>

    <article>
        <h2>Post</h2>
        <p>Detail Of Posting</p>
    </article>
 
    <aside>
        <!-- Sidebar -->
    </aside>

</main>

<footer>
    <!-- Info of footer -->
</footer>

</body>
```

Meaning of tags:
- `Header` : Header of page, usually contains logo and menu
- `Nav` : Navigation, usually contains menu redirect
- `Main` : Main content of page
- `Section` : A part of content, usually has a title
- `Article` : An independent post, usually has a title
- `Aside` : Sidebar, usually contains related content or ads
- `Footer` : Footer of page, usually contains info of page

| Tag     | Mean                                             |
|---------|--------------------------------------------------|
| Header  | Header of page, usually contains logo and menu   |
| Nav     | Navigation, usually contains menu redirect       |
| Main    | Main content of page                             |
| Section | A part of content, usually has a title           |
| Article | An independent post, usually has a title         |
| Aside   | Sidebar, usually contains related content or ads |
| Footer  | Footer of page, usually contains info of page    |


-----------------
<br/>

## Standard Use Row and Column in Bootstrap



- Layout Bootstrap usually use 12 columns, so we can divide the page into 12 parts
```text
section
 └── container
      └── row
           └── col
                └── content-wrapper
```


### Fast food
```text
Bootstrap layout rule

section
  container
    row
      col
        wrapper(content)

Rules:
- row just divide grid, not style
- col just divide grid, not style
- style or css in wrapper content
- group content in div to make it easier to style
- spacing at wrapper content, not row or col
- each block in figma is a section


"Style is Css"
```

-----------------
<br/>

## Padding and Margin
- Padding is the space between the content and the border of the element
- Margin is the space between the element and other elements

| Property    | Description                      |
|-------------|----------------------------------|
| **margin**  | distance **outside** the element |
| **padding** | distance **inside** the element  |

```text
margin from outside
 ┌─────────────────────┐
 │      padding(inside)│
 │  ┌───────────────┐  │
 │  │    content    │  │
 │  └───────────────┘  │
 └─────────────────────┘
```

### when to use margin and padding
- Use `margin` to create space between elements
- Use `padding` to create space between the content and the border of the element
- use `padding` for layout and `margin` for spacing between blocks

**Example:**
```html
<style>
    .card {
        padding: 20px;
        margin-bottom: 30px;
        background: #eee;
    }
</style>

<div class="card">
  <h2>Title</h2>
  <p>Text</p>
</div>


<!--padding: 20px; --> space between content and border of card
<!--margin-bottom: 30px; --> space between card and other elements below it.
```