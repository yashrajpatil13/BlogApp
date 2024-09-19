Following a detailed documentation of project making steps.

# Project Steps

## Step 1: Setting Up Environment Variables
- Create `.env` file: Place it in the project's root directory.
- **Add environment variables**: Include them in both `.env` and `.env.sample` for easy sharing and consistency.
- **Reload project**: `.env` files load only once; reload the project if changes are made.
- **Naming conventions**: Use variable names aligned with the framework/library.
- **Documentation**: Refer to official docs for accessing environment variables.
- **Production Standards**:
  - Create a `config` folder in `src`.
  - In the `conf` folder, create a conf file to export all environment variables as properties.
  - Wrap environment variables in `String` for consistent usage across the application.

## Step 2: Configuring Appwrite
- **Create `appwrite` folder**: Place this folder inside the `src` directory.
- **Set up `auth.js`**:
  - Write authentication logic as microservices to avoid vendor lock-in.
  - Implement services: `createAccount`, `login`, `getCurrentUser`, `logout`.
  - Export an object of the class to expose all methods via a single object.
- **Create `config.js`**:
  - Implement services for handling CRUD operations related to posts/blogs.
  - Include file services for managing file operations.

## Step 3: Configuring Redux Toolkit
- **Create `store` folder**: Place this folder inside the `src` directory.
- **Set up `store.js`**:
  - Configure the Redux store by creating and exporting it.
- **Create `authSlice.js`**:
  - Define `initialState` for authentication.
  - Implement reducers to manage authentication-related state.
- **Update `App.jsx`**:
  - Write code to conditionally render components based on the loading state managed by Redux.

## Step 4: Creating Production-Grade Components
- **Create `component` folder**: Place this folder inside the `src` directory.

### Create Common Components:
- **Header.jsx**:
  - **Authentication Check**: Verify the user's authentication status.
  - **Navigation Items**: Create an array of navigation items.
  - **Render Header**:
    - Include the `Header` inside a `Container` component.
    - Add a logo and iterate over the navigation array to render buttons.
    - Conditionally render the logout button based on the user's authentication status.
- **Footer.jsx**: Implement as needed for the application’s footer.
- **Container.jsx**: A wrapper component to structure content.

### Create Conditional Buttons:
- Implement components like a logout button that renders conditionally within the `Header`.

### Create `InputBtn.jsx`:
- **Production Practices**: Develop a reusable input box component for fields like username and password.
- **Use in Login Component**: In the login component, manage the state of the input component using the `useRef` hook, a common production-grade approach for accessing and manipulating DOM elements or component instances.

## Step 5: Creating Components and Integrating React Hook Form
### Create Components:
- **Select.jsx**: A component for dropdown selections.
- **PostCard.jsx**: A component for displaying individual posts.

### Create `Login.jsx`:
- **Import Dependencies**:
  - Import `login` from `authSlice` to store user data in the Redux store after successful login.
  - Import `login` from `authService` to create a login session with the backend (e.g., Appwrite).

### Setting Up React Hook Form:
- Define `useNavigate`, `useDispatch`, and initialize an `error` state using `useState`.
- Use `useForm` from React Hook Form to register input fields and handle form submission via `handleSubmit`.

### Creating the `login` Function:
- The `login` function is an async function that takes `data` (key-value pairs submitted by the form) as a parameter.
- Use `authService.login` to create a session with the backend, passing `data` as the parameter.
- On successful session creation, retrieve the user data using `authService.getCurrentUser`.
- Dispatch the retrieved user data to the Redux store using `authSlice.login`, creating a state corresponding to the logged-in user.
- Use `navigate` to programmatically redirect the user to the root route (`/`).
- Catch any errors, and update the error state accordingly.

### Returning the Form:
- Start with a basic form structure.
- Create a form element and pass the `login` function to the `onSubmit` attribute via `handleSubmit`.
  - Note: `handleSubmit` is an event handler that takes a function to execute upon form submission.
- Use the `Input` component for input fields, setting necessary attributes.
- For each input field, use the `register` function to bind the input field's name to the form's data.
  - Spread `register` to ensure its value isn't overwritten when used elsewhere in the code.
- Add validation rules, such as email validation, within the options object passed to `register`.
- Repeat the above steps for other input fields like the password field, making adjustments as necessary.

## Step 6: RTE and Post Form

### RTE
### Import Required Libraries:
- Import TinyMCE's Editor component from `@tinymce/tinymce-react`.
- Import `Controller` from `react-hook-form` to integrate form control with the editor.

### Component Parameters:
- Accept the following props:
    - `name`: Field name for form registration and data binding.
    - `control`: Control object from `react-hook-form` to manage form state.
    - `label`: Optional label to display above the editor.
    - `defaultValue`: Initial content of the editor, defaulting to `'Start writing here...'`.

### Render Label (Optional):
- If a label is provided, render it above the editor.

### Use Controller for Form Integration:
- Wrap the `Editor` inside `Controller` to connect the editor with `react-hook-form`.
- Pass `name` and `control` props to `Controller` to bind the editor with the form's state.

### Render TinyMCE Editor:
- In the `render` prop of `Controller`, render the `Editor` component.
- Set `initialValue` to display the initial content in the editor.
- Customize the editor settings (`init` object):
    - Set editor height to `500px`.
    - Enable necessary plugins such as image handling, text formatting, lists, etc.
    - Customize the toolbar with frequently used options (bold, italic, alignment, etc.).
    - Disable TinyMCE branding.
    - Define custom styles for the editor content.

### Control Form State:
- The `onChange` method ensures that any changes in the editor's content are reflected in the form's state, providing real-time updates and validation.


### Post Form
### Setup Basic Form Using `react-hook-form`:
- Initialize `useForm` to manage form state and validation.
- Define `defaultValues` for fields (title, slug, content, status) using the `post` prop.

### Configure Navigation and User Data:
- Use `useNavigate` from `react-router-dom` to handle programmatic redirection after form submission.
- Fetch `userData` from Redux store using `useSelector` to associate the post with the logged-in user.

### Handle Form Submission Logic:
- Define the `submit` function to handle form submission.
- If updating a post:
    - Check if a new image is uploaded, delete the old one, and update the post with new data.
- If creating a new post:
    - Upload the image, create the post, and navigate to the newly created post.

### Slug Generation with `useCallback`:
- Implement `slugTransform` to generate a URL-friendly slug from the title field by trimming spaces, lowercasing, and replacing spaces with dashes.

### Real-Time Slug Update Using `useEffect`:
- Watch the title field with `watch` and automatically update the slug field when the title changes using the `slugTransform` function.

### Implement Form Layout and Fields:
- Create form fields for title, slug, content, image, and status using custom input components like `Input`, `RTE`, and `Select`.
- Conditionally render fields and buttons based on whether a post exists (for update) or not (for create).

### Handle Image Upload and Preview:
- Include an image input field and preview the current image if editing an existing post.

### Submit Button and Conditional Rendering:
- Display "Update" if editing a post and "Submit" for new post creation.
"""
