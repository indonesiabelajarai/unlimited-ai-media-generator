# 🎨 Unlimited AI Media Generator

A powerful, local-first web application for generating Images, Videos, and Music using AI. Built with vanilla HTML, CSS, and JavaScript, it acts as a modern frontend interface for your n8n AI workflows.

## ✨ Features

### 🖼️ Image Generation
- **Capabilities**:
  - Custom text prompts
  - Multiple styles: Realistic, Anime, Digital Art, Oil Painting, Watercolor, 3D Render
  - Adjustable Aspect Ratios: Square (1:1), Landscape (16:9), Portrait (9:16)
  - Instant specific downloads

### 🎬 Video Generation
- **Capabilities**:
  - Text-to-Video generation
  - Styles: Cinematic, Anime, Realistic, Abstract, Vintage, 3D Animation
  - Variable Duration: 4s or 8s
  - Aspect Ratios: Landscape & Portrait

### 🎵 Music & Lyrics Generation
- **Two-Step Process**:
  1. **Lyrics Generator**: Create lyrics based on Theme, Language (Multilingual support), Genre, Mood, and Duration.
  2. **Music Generator**: Turn those lyrics into full songs with vocals, utilizing Suno AI.
- **Features**:
  - Integrated Audio Player with Waveform visualization
  - Album Art display
  - Metadata display (Title, Tags)

### ⚙️ App Features
- **Zero-Server Setup**: Runs entirely in the browser (client-side only).
- **Customizable Backends**: Point to your own n8n webhook URLs.
- **Theme Support**: Beautiful Dark and Light modes.
- **Responsive Design**: Works on Desktop and Mobile.

## 🌐 Live Demo

Try the live demo here: **[unlimitedai.indonesiabelajarai.com](https://unlimitedai.indonesiabelajarai.com)**

> **⚠️ Important**: This is a client-side demo. To generate actual media, you must click the **Settings (Gear Icon)** and provide your own **n8n Webhook URLs** (see setup guide below).

## 🚀 Getting Started

### Prerequisites
- A modern web browser.
- An actively running **n8n** instance (Local or Cloud).
- **n8n Workflow**: Import the provided workflow file (see setup guide below).

### Installation
1. **Clone the repository**:
   ```bash
   git clone https://github.com/indonesiabelajarai/unlimited-ai-media-generator.git
   cd unlimited-ai-media-generator
   ```

2. **Run the application**:
   - Since this is a static web app, you can simply open `index.html` in your browser.
   - For the best experience, use a local development server:
     ```bash
     # Using Python
     python3 -m http.server 8000
     
     # Or using VS Code Live Server extension
     ```
   - Open `http://localhost:8000` in your browser.

## ⚡ n8n Workflow Setup

We have included a complete, all-in-one workflow file to get you started immediately. This workflow handles all media generation tasks.

**Option 1: Import from File (Recommended)**
1. Navigate to the `n8n-workflow` folder in this repository.
2. Locate the file: `unlimited-ai-generator-n8n-flow.json`.
3. Open your n8n dashboard.
4. Click the menu in the top right (or "Add Workflow") and select **Import from File**.
5. Upload the JSON file.

**Option 2: Import from URL**
You can also import the workflow directly using the raw GitHub link:
1. Open your n8n dashboard.
2. Select **Import from URL**.
3. Paste the following link:
   ```
   https://raw.githubusercontent.com/indonesiabelajarai/unlimited-ai-media-generator/main/n8n-workflow/unlimited-ai-generator-n8n-flow.json
   ```

## 🔗 Connecting to n8n

To make the app functional, you need to connect it to your n8n workflows.

1. Open the app in your browser.
2. Click the **Settings (Gear Icon)** in the top right corner.
3. Enter your n8n Webhook URLs for each service:
   - **Image Generation Webhook**: Expects POST request.
   - **Video Generation Webhook**: Expects POST request.
   - **Lyrics Generation Webhook**: Expects POST request.
   - **Music Generation Webhook**: Expects POST request.
4. Click **Save Settings**.

### Workflow Interfaces (Inputs/Outputs)

If you are building your own n8n workflows, ensure they handle the following data structures:

**1. Image Webhook**
- **Input (JSON)**:
  ```json
  {
    "prompt": "your prompt",
    "style": "realistic",
    "width": 1920,
    "height": 1080
  }
  ```
- **Output**: Binary Image Data (image/png or image/jpeg).

**2. Video Webhook**
- **Input (JSON)**:
  ```json
  {
    "prompt": "your prompt",
    "style": "cinematic",
    "width": 848,
    "height": 480,
    "duration": 4
  }
  ```
- **Output**: Binary Video Data (video/mp4).

**3. Lyrics Webhook**
- **Input (JSON)**:
  ```json
  {
    "theme": "love",
    "language": "en",
    "genre": "pop",
    "mood": "happy",
    "duration": 60
  }
  ```
- **Output (JSON)**:
  ```json
  {
    "output": "Verse 1: ..."
  }
  ```
  *Note: The app checks for `output`, `lyrics`, `text`, `content`, or `result` fields.*

**4. Music Webhook**
- **Input (JSON)**:
  ```json
  {
    "lyrics": "Verse 1: ...",
    "genre": "pop",
    "mood": "happy",
    "voice": "male",
    "duration": 60
  }
  ```
- **Output (JSON)**: Response from Suno API (typically an array containing objects with `audioUrl` or `sourceAudioUrl`, `imageUrl`, `title`).

## 🛠️ Built With
- HTML5
- CSS3 (Variables, Flexbox, Grid)
- Vanilla JavaScript (ES6+)
- Inter Font Family

## 🤝 Contributing
Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License
This project is licensed under the MIT License - see the LICENSE file for details.
