# DevTinder Frontend - UI (part 2) Development 🚀

## 📌 Code Demonstration Links  
🔗 **Backend Repository:** [DevTinder Backend](https://github.com/akshadjaiswal/devTinder-backend)  
🔗 **Frontend Repository:** [DevTinder Frontend](https://github.com/akshadjaiswal/devTinder-frontend)  

---

## 📌 Overview  
DevTinder is a **MERN stack** web application designed to help developers **connect and collaborate**, similar to Tinder but for the tech community.  

This update focuses on **building the authentication page, integrating API calls, and implementing state management using Redux Toolkit**. The login system ensures secure authentication using **JWT tokens stored in cookies**, with proper CORS configuration to handle credentials.  

---

## ✅ Steps Completed  

### **1️⃣ Created Login Page**  
- Designed a **responsive login page** with an input form for email and password.  
- Used controlled components in React to handle form inputs.  
- Added form validation to prevent empty fields or incorrect email formats.  
- Styled the page using **Tailwind CSS** for a clean UI.  

### **2️⃣ Installed & Configured Axios**  
- Installed **Axios**, a promise-based HTTP client, to manage API requests efficiently.  
- Set up **global Axios defaults** to include the backend’s base URL for easy request handling.  
- Used **async-await** inside API functions to ensure proper request handling.  

### **3️⃣ Installed & Configured CORS in Backend**  
- Installed **CORS (Cross-Origin Resource Sharing)** middleware to allow the frontend to communicate with the backend.  
- Configured CORS settings in the backend by specifying:  
  - **origin**: Allows requests only from the frontend domain.  
  - **credentials: true**: Enables sending cookies with API requests.  
- Without proper CORS configuration, the browser blocks API requests due to security policies.  

### **4️⃣ Making API Calls with Credentials**  
- Modified all Axios requests to include `{ withCredentials: true }`.  
- This ensures the backend sends **cookies containing the JWT token** to the frontend.  
- If `credentials: true` is not passed, the backend will **not store or retrieve session tokens**, breaking authentication.  
- Implemented proper error handling to display user-friendly messages if login fails.  

### **5️⃣ Installed Redux Toolkit & React Redux**  
- Installed **Redux Toolkit**, which simplifies global state management compared to traditional Redux.  
- Installed **React Redux**, allowing components to connect with the Redux store.  
- Redux helps manage authentication state across different components, ensuring data consistency.  

### **6️⃣ Configured Redux Store**  
- Wrapped the application with `<Provider>` to enable global state management.  
- Created **Redux slices** to manage authentication, including:  
  - **User data storage** after login.  
  - **Token storage for future API requests**.  
- Added the authentication slice to the **Redux store** and ensured state updates upon login.  

### **7️⃣ Installed Redux DevTools for Chrome**  
- Installed **Redux DevTools**, a browser extension to monitor state changes.  
- Verified that login updates **Redux state correctly**, ensuring user authentication status is reflected across components.  

### **8️⃣ Verified Login Flow & Redux Integration**  
- Logged in with test credentials and **confirmed that user data is stored in Redux state**.  
- Checked **Redux DevTools** to monitor state updates after login.  
- Ensured that token persistence works properly for future API calls.  

### **9️⃣ Updated Navbar After Login**  
- Modified the **Navbar component** to reflect authentication status dynamically.  
- Once logged in, the navbar:  
  - **Displays the user’s profile picture** retrieved from Redux state.  
  - **Shows a welcome message** with the logged-in user’s name.  
- Ensured that these updates happen instantly after login without requiring a page refresh.  

### **🔟 Code Refactoring & Organization**  
- Created a **constants file** for storing the backend’s base URL.  
- Moved **reusable UI components** (Navbar, Footer, etc.) to a dedicated **components folder**.  
- Ensured that all API calls are **modular and reusable**, improving code maintainability.  

---

## 🎯 Next Steps  

- **Build Signup Page**: Develop user registration with proper validation and API integration.  
- **Session Persistence**: Implement logic to keep users logged in even after a page refresh.  
- **Logout Functionality**: Add a **logout button** that clears the session and updates UI dynamically.  
- **Feed Page Development**: Start building the **developer feed UI**, where users can explore profiles.  

---

## 🔥 Conclusion  
The **authentication system** is now integrated with the backend, and state management is fully set up using **Redux Toolkit**. The next focus will be on improving **user session management, signup functionality, and logout handling**.  

With **Axios for API calls, Redux for state management, and CORS for secure token handling**, DevTinder’s authentication is now **structured, secure, and scalable**. 🚀  
