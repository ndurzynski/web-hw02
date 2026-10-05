# Homework 2

Niki Durzynski, section 002

## 1. Cascade investigation

The first review box changed from rgb(225, 214, 151) to transparent after I removed its background-color declaration in the browser. The screenshots show the before and after. The saved CSS keeps the original color.

```css
.review p {
    background-color: transparent;
}
.review .quote {
    background-color: #e1d697;
}
```

The second selector has specificity 0,2,0. The first has 0,1,1, so the second wins. Removing its background declaration lets the first rule apply. The body background then shows through the box. Background color is not inherited. Source order breaks a tie in specificity, but these rules are not tied.

Before: evidence/final-480.png
After: evidence/cascade-after-480.png

## 2. Responsive trade-off

At a 480px viewport, the main review region and sidebar each measured 456px. The document's scrollWidth was 480px, so there was no horizontal scrolling. These values came from getComputedStyle, not screenshots of the Computed panel.

```css
.movie-frame {
    grid-template-columns: minmax(0, 1fr) 250px;
    width: 800px;
    max-width: calc(100% - 24px);
}
@media (max-width: 700px) {
    .movie-frame {
        grid-template-columns: minmax(0, 1fr);
        grid-template-areas: "reviews" "overview" "counter";
    }
    .review-columns {
        grid-template-columns: minmax(0, 1fr);
    }
}
```

I changed the mobile frame back to two columns for comparison. The main region shrank to 206px while the sidebar stayed 250px. It still fit, but the review text became narrow. Stacking gives the reviews more space. The trade-off is a longer page, with the overview below the reviews.

Final: evidence/final-480.png
Comparison: evidence/comparison-fixed-sidebar-480.png
Measurements: evidence/measurements.json

## Validation

W3C HTML validation returned zero errors, with informational notices about self-closing tags. W3C CSS validation returned zero errors and zero warnings. The responses are saved in evidence/html-validation.json and evidence/css-validation.xml.
