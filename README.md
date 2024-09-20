# BlogApp

Welcome to my **BlogApp** repository! This project is a modern, feature-rich blogging platform built using **React.js** and **Appwrite** as the backend service. The application offers user authentication, post creation, editing, and deletion, along with a rich text editor for content management. It follows industry-standard production practices to ensure scalability, performance, and maintainability.



## Features

### User Management
- **User Registration:** Users can create accounts via a sign-up form with validation.
- **User Authentication:** Secure login and logout functionality, powered by Appwrite's authentication service.
- **Logout:** Seamless logouts, clearing authentication tokens and ensuring security.

### Post Creation
- **Rich Text Editor:** Authenticated users can create posts using the **TinyMCE** rich text editor.
- **Image Uploads:** Users can upload featured images to accompany their blog posts, securely stored in **Appwrite**.

### Post Management
- **Post Listing:** All posts are displayed in a user-friendly, organized list.

### Post Update and Deletion
- **Post Editing:** Users can edit their posts if they are logged in and own the post.
- **Post Deletion:** Users can delete their posts with proper authorization checks.

### Routing and Navigation
- **Efficient Route Management:** Uses **react-router-dom** for smooth transitions between different sections of the app.
- **Dedicated Routes:** Separate routes for authentication (login, signup, logout), post creation, editing, and viewing.



## Tech Stack
- **Frontend:** React.js (with hooks)
- **Form Handling:** React Hook Form
- **Rich Text Editor:** TinyMCE
- **State Management:** Redux Toolkit
- **Routing:** react-router-dom
- **Backend:** Appwrite (for database, storage, and authentication)



## Getting Started

To get started with the BlogApp project, follow these steps:

1. **Clone the repository:**
    ```bash
    git clone https://github.com/yashrajpatil13/blogApp.git
    ```

2. **Install dependencies:**
    ```bash
    npm install
    ```

3. **Set up environment variables:**
    - Configure your **Appwrite** project credentials in a `.env` file:
      ```bash
      VITE_APPWRITE_URL= 'https://cloud.appwrite.io/v1'
      VITE_APPWRITE_PROJECT_ID=your-project-id
      VITE_APPWRITE_DATABASE_ID=your-database-id
      VITE_APPWRITE_COLLECTION_ID=your-collection-id
      VITE_APPWRITE_BUCKET_ID=your-bucket-id
      VITE_TINY_EDITOR_API_KEY=your-tinymce-api-key
      ```

4. **Run the development server:**
    ```bash
    npm run dev
    ```

5. **Build for production:**
    ```bash
    npm run build
    ```

6. **Deployment:**
    Deploy the project on your preferred hosting platform. For instance, you can use Vercel, Netlify, or any platform that supports static site hosting.


## Live Demo
You can check out the live demo of **BlogApp** here: [Live Demo](https://blog-app-appwrite-seven.vercel.app/)


## Repository
To explore the code, fork, or contribute, visit the GitHub repository: [GitHub Repository](https://github.com/yashrajpatil13/BlogApp)


## Contributing
Contributions from the community are always welcomed! If you'd like to contribute, please fork the repository, create a new branch, and submit a pull request.

1. Fork the project
2. Create your feature branch (`git checkout -b feature/new-feature`)
3. Commit your changes (`git commit -m 'Add some feature'`)
4. Push to the branch (`git push origin feature/new-feature`)
5. Open a pull request

