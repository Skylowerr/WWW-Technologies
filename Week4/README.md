
### 1. Why are we using `clamp()` instead of media queries?
Using `clamp()` allows for **fluid typography and scaling** without the need for multiple "break points." While media queries create stepped changes (e.g., jumping from 16px to 20px at a specific width), `clamp(min, preferred, max)` ensures a smooth transition between values, making the UI feel more organic and reducing the amount of CSS code.

### 2. Why did we use `minmax()` instead of fixed columns?
`minmax()` provides **intrinsic web design** capabilities. Unlike fixed columns (e.g., `200px`), `minmax(200px, 1fr)` allows a column to shrink to a minimum functional size but also expand to fill available space. This prevents layout breaking on smaller screens and ensures the grid adapts to the content's needs automatically.

### 3. Why is it important to implement a mobile-first website?
Mobile-first design is crucial because it forces us to prioritize **essential content and performance**. It is technically easier to scale up a simple layout for desktops (progressive enhancement) than it is to shrink a complex desktop layout for mobile (graceful degradation).

### 4. What happens if we remove the variables that were defined at the beginning?
Removing CSS variables (`--primary-color`, etc.) would break the **consistency and maintainability** of the project. Any element relying on those variables would lose its styling.