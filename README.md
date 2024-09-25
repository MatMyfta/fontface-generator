# FontFace Generator

A simple Svelte application that generates the CSS `@font-face` code for uploaded font files. Built with Svelte (using JSX syntax) and Tailwind CSS, this frontend-only application follows modern UI/UX best practices to provide an intuitive user experience.

## Features

- **Step-by-Step Interface**: Guided process divided into three steps with a progress bar:
  1. **Upload Fonts**: Upload multiple font files.
  2. **Font Settings**: Customize font weight, style, and other @font-face settings.
  3. **Generated Code**: View and copy the generated @font-face CSS code.
- **Modern UI/UX**: Responsive design with a clean and intuitive interface.
- **No Server Required**: All operations are performed on the client side using the File API.

## Prerequisites

- Node.js (v12 or later)
- npm (Node Package Manager)

## Installation

1. Clone the Repository

```bash
git clone https://github.com/MatMyfta/fontface-generator.git
cd fontface-generator
```

2. Install Dependencies

```bash
npm install
Running the Application
```

3. Start the development server:

```bash
npm run dev
```

## Usage

1. **Upload Fonts**
    - Navigate to the application in your browser.
    - In **Step 1**, click on the file input to select font files from your computer.
    - Supported formats: .ttf, .otf, .woff, .woff2
    - After selecting files, click the Next button to proceed.
2. **Customize Font Settings**
    - In **Step 2**, you'll see a list of uploaded font files.
    - For each font, you can:
      - **Edit the Font Family Name**: Defaulted to the file name without extension.
      - **Select Font Weight**: Choose from common weights like normal, bold, or numerical values (100 to 900).
      - **Select Font Style**: Choose between normal, italic, or oblique.
    - Once you're satisfied with the settings, click the Generate button.
3. **Copy Generated Code**
   - In **Step 3**, the generated @font-face CSS code will be displayed.
   - Click the **Copy to Clipboard** button to copy the code.
   - You can now paste this code into your CSS files to use the fonts on your website.
4. **Navigation**
   - At any point in **Step 2** or **Step 3**, you can go back to the previous step using the **Back** button.

## Technologies Used

- **Svelte**: Frontend framework for building reactive user interfaces.
- **JSX Syntax**: Using svelte-preprocess to write components in JSX.
- **Tailwind CSS**: Utility-first CSS framework for styling.
- **PostCSS**: Tool for transforming CSS with JavaScript plugins.

## License

This project is licensed under the MIT License.
