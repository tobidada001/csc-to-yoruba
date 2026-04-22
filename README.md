#  YorubaAI - Learn Computer Science in Yorùbá

**YorubaAI** is an interactive AI-powered web application that helps students and learners understand Computer Science concepts explained in Yorùbá. Whether you're curious about programming, algorithms, data structures, or any CS topic, YorubaAI breaks it down into simple, clear explanations in the Yorùbá language.

##  Features

-  **Search & Ask**: Ask any Computer Science question through an intuitive search interface
-  **AI-Powered Responses**: Get intelligent explanations powered by AI, delivered in Yorùbá
-  **Interactive Chat**: Conversational interface for follow-up questions and deeper learning
-  **Responsive Design**: Works seamlessly on desktop, tablet, and mobile devices
-  **Fast & Lightweight**: Built with Vue 3 and Vite for optimal performance
-  **Modern UI**: Beautiful, user-friendly interface with Tailwind CSS

##  Getting Started

### Prerequisites

- Node.js (v20.19.0 or ≥22.12.0)
- npm or yarn

### Installation

1. Clone the repository:

```bash
git clone <repository-url>
cd csc-to-yoruba
```

2. Install dependencies:

```bash
npm install
```

### Development

Run the development server with hot-reload:

```bash
npm run dev
```

The application will be available at `http://localhost:5173`

### Production Build

Build for production:

```bash
npm run build
```

Preview the production build:

```bash
npm run preview
```

### Code Quality

Run linting and formatting:

```bash
npm run lint        # Run ESLint and Oxlint
npm run format      # Format code with Prettier
```

## 🏗️ Project Structure

```
src/
├── pages/
│   ├── HomePage.vue        # Landing page with search functionality
│   ├── AnswerPage.vue      # Chat interface for Q&A
│   └── NotFound.vue        # 404 page
├── components/
│   └── LoadSpinner.vue     # Loading indicator
├── router/
│   └── index.js            # Vue Router configuration
├── assets/
│   └── main.css            # Global styles
├── App.vue                 # Root component
└── main.js                 # Application entry point
```

##  Tech Stack

- **Frontend Framework**: Vue 3
- **Build Tool**: Vite
- **Router**: Vue Router
- **Styling**: Tailwind CSS
- **Linting**: ESLint, Oxlint
- **Code Formatting**: Prettier
- **AI API**: Hugging Face Spaces (CSC-in-Yoruba model)

##  How It Works

1. **Home Page**: Users visit the homepage and enter their Computer Science question in the search box
2. **Question Submission**: Clicking "Ask" redirects to the chat page with the question pre-filled
3. **AI Response**: The question is sent to the Hugging Face API endpoint which processes it and returns an explanation in Yorùbá
4. **Interactive Chat**: Users can continue asking follow-up questions in the chat interface

##  Use Cases

-  Students learning Computer Science who prefer explanations in Yorùbá
-  Beginners exploring tech concepts in their native language
-  Educators teaching CS to Yorùbá-speaking communities
-  Bridging language barriers in tech education

##  Browser Compatibility

- Chrome, Edge, Brave, and other Chromium-based browsers (recommended)
- Firefox
- Safari

For the best development experience with Vue 3, install the [Vue.js devtools extension](https://devtools.vuejs.org/).

##  License

Add license information here.

##  Contributing

Contributions are welcome! Feel free to open issues and submit pull requests.

##  Feedback

Have suggestions or found a bug? Please open an issue on GitHub.

---

**Built with ❤️ to make tech education accessible to Yorùbá-speaking communities.**
