# DevTinder Frontend - UI (Part - 3)🚀  

## 📌 Code Demonstration Links  
🔗 **Backend Repository:** [DevTinder Backend](https://github.com/akshadjaiswal/devTinder-backend)  
🔗 **Frontend Repository:** [DevTinder Frontend](https://github.com/akshadjaiswal/devTinder-frontend)  

---

## 📌 Overview  
DevTinder is a **MERN stack** web application designed to help developers **connect and collaborate**. The latest update focuses on:  
- **Authentication restrictions**: Preventing unauthorized access.  
- **Logout functionality**: Clearing sessions and redirecting users.  
- **Fetching feed data**: Storing developer profiles in Redux.  
- **Profile updates**: Editing user details with live previews.  

---

## ✅ Steps Completed  

### **1️⃣ Restricting Access for Unauthenticated Users**  
- Implemented route protection to **prevent access** to certain pages without login.  
- If the **JWT token is missing**, the user is **automatically redirected** to the login page.  
- Improved user experience by ensuring proper authentication checks.  

### **2️⃣ Implemented Logout Feature**  
- Created a **Logout button** that clears user session and authentication state.  
- Upon logout, the user is **redirected to the login page**.  
- Ensured Redux store updates correctly after logout.  

### **3️⃣ Fetching & Storing Feed Data in Redux**  
- Integrated **API call to fetch the feed** from the backend.  
- Stored the retrieved **developer profiles** in the Redux store for global access.  
- Ensured the feed **updates dynamically** without requiring a full page refresh.  

### **4️⃣ Built User Card Component for Feed Page**  
- Designed a **UserCard component** to display user profiles.  
- Included essential details like **name, profile picture, and skills**.  
- Styled using **Tailwind CSS & Daisy UI** for a clean and responsive layout.  

### **5️⃣ Implemented Profile Update API**  
- Added **API endpoint for updating user profiles**.  
- Allowed users to modify their profile details securely.  
- Ensured **real-time UI updates** upon successful edits.  

### **6️⃣ Live Preview of Profile Updates**  
- Used the **UserCard component** to provide a **live preview** of profile changes.  
- Users can see updates in real-time before saving them to the database.  
- Improved **user experience** by making the edit process more interactive.  

### **7️⃣ Created Profile Edit Form**  
- Developed a **Profile Edit Form** for updating user information.  
- Ensured **successful submission and validation** before saving data.  
- Updated Redux store to reflect changes across the app **instantly**.  

---

## 🎯 Next Steps  

- **Implement Connection Requests**: Allow users to send & receive connection requests.  
- **Improve UI & Design**: Enhance the look and feel of the feed and profile pages.  
- **Optimize API Calls**: Reduce unnecessary requests and improve performance.  
- **Add Dark Mode Support**: Improve user experience with theme toggling.  

---

## 🔥 Conclusion  
The **authentication system, feed integration, and profile updates** are now fully implemented in DevTinder. Users can securely log in, explore developer profiles, and update their own details in real-time.  

With **Redux for state management, Axios for API calls, and Tailwind for styling**, DevTinder is becoming more robust and scalable. 🚀  
