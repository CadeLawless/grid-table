# Grid Table CSS Solution

A lightweight and responsive CSS-based grid table layout for displaying tabular data in a structured and visually appealing manner.

## Features

- **Fully Responsive**: Adapts seamlessly to different screen sizes.
- **Accessible**: Uses `data-label` attributes to maintain readability in smaller viewports.
- **Customizable**: Easily modify styles to fit your design needs.
- **No JavaScript**: Primarily CSS-driven for better performance.

## Usage

### HTML Structure

```html
<div class='grid-table'>
    <div class='grid-row header-row'>
        <div class='grid-cell'>Column 1</div>
        <div class='grid-cell'>Column 2</div>
        <div class='grid-cell'>Column 3</div>
        <div class='grid-cell'>Actions</div>
    </div>
    <div class='grid-row'>
        <div class='grid-cell grid-cell-title' data-label='Column 1'>Data 1</div>
        <div class='grid-cell' data-label='Column 2'>Data 2</div>
        <div class='grid-cell' data-label='Column 3'>Data 3</div>
        <div class='grid-cell button-cell'>
            <a class='blue_button' href='#'>Action</a>
        </div>
    </div>
</div>
```

### CSS Desktop

```css
.grid-table {
    display: grid;
    grid-template-columns: repeat(5, auto);
    grid-auto-rows: auto;
    margin-bottom: 2rem;

    &.justify-center .grid-cell {
        text-align: center;
    }

    & .grid-row {
        display: contents;

        &.header-row .grid-cell {
            font-weight: bold;
            text-align: center;
            background-color: #404040;
            color: #FFFFFF;
        }

        &:not(.header-row):nth-child(odd) .grid-cell {
            background-color: #e8e9eb;
        }

        & .grid-cell {
            padding: 0.6rem;
            display: flex;
            flex-direction: column;
            justify-content: center;                    
        }
    }
}
```
### CSS Mobile

```css
.grid-table {
    grid-template-columns: repeat(auto-fit, minmax(min(300px, 100%), 1fr));
    gap: 0.7rem;

    &.full-width-mobile {
        grid-template-columns: 1fr;
    }

    & .grid-row {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        gap: 0.8rem;
        padding: 0.5rem;
        border: 1px solid lightgrey;
        border-radius: 4px;
        background-color: white;
    
        &.header-row {
            display: none;
        }

        &:not(.header-row):nth-child(odd) .grid-cell {
            background-color: unset;
        }
    
        & .grid-cell {
            padding: 0;
            overflow-wrap: anywhere;

            &:not(.grid-cell-title, .empty-cell)::before {
                content: attr(data-label);
                color: grey;
                display: block;
                text-align: center;
                font-size: 0.9rem;
            }

            &:not(.button-cell) {
                flex-grow: 1;
            }

            &.grid-cell-title {
                flex-basis: 100%;
                font-weight: bold;
                font-size: 1.2rem;
                margin-bottom: -0.5rem;
            }

            &.empty-cell {
                display: none;
            }

            &.button-cell {
                flex-basis: 100%;
                align-items: center;

                & a {
                    margin: 0;
                    font-size: 0.9rem;
                    padding: 0.4rem 0.9rem;
                }
            }
        }
    }
}
```
### Best Practice for Different Page Requirements
The best way to handle varying table structures across different pages is to set the column layout dynamically using inline `<style>` rules, along with a separate mobile stylesheet.

```html
<style>
    .grid-table {
        grid-template-columns: repeat(4, auto);
    }
</style>

<link rel="stylesheet" type="text/css" href="path/to/grid-table-mobile.css" media="(max-width: 800px)" />
```

This approach allows each page to define its own column structure and `max-width` media query while keeping the mobile layout consistent across different table designs.
## Installation

1. Clone the repository:
   ```sh
   git clone https://github.com/yourusername/grid-table-css.git
   ```
2. Include the CSS file in your project:
   ```html
   <link rel="stylesheet" href="path/to/grid-table.css">
   ```

## Contributing

Pull requests are welcome! For major changes, please open an issue first to discuss what you'd like to change.

## Contact

For any inquiries, please reach out via GitHub issues.

