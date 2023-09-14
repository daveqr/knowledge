# React Contexts

You can have multiple contexts for different types of data.



You can use contexts for specific components. The context will only be visible to the component you wrap and its children. You don't need to wrap the entire application with each provider unless you need the provider globally.

```
function Home() {
  return (
    <AuthProvider>
      <ThemeProvider>
        <Landing />
      </ThemeProvider>
    </AuthProvider>
  );
}
```

## Example

1. **Create the context**

	```
	import { FC, ReactNode, createContext, useContext, useState } from "react";
	
	import User from "../models/User";
	
	// The values your context supports
	interface AuthContextType {
	  user: User | null;
	  login: (user: User) => void;
	  logout: () => void;
	}
	
	// Create the context using the createContext React API method to create a new context.
	// Set its type to AuthContextType to specify the type of data that will be shared through this context.
	// `undefined` is the default value.
	// The createContext function returns a context object that can be used with the useContext hook.
	export const AuthContext = createContext<AuthContextType | undefined>(undefined);
	
	// AuthProvider component that accepts children as a prop.
	export const AuthProvider: FC<{ children: ReactNode }> = ({ children }) => {
	  const [user, setUser] = useState<User | null>(null);
	
	  // hook method to log user in
	  const login = (userData: User) => {
	    setUser(userData);
	  };
	
	  // hook method to log user out
	  const logout = () => {
	    setUser(null);
	  };
	
	  // Provide the context values to the wrapped components
	  return (
	    <AuthContext.Provider value={{ user, login, logout }}>
	      {children}
	    </AuthContext.Provider>
	  );
	};
	
	// Custom hook to access the AuthContext values.
	// It uses the useContext hook to retrieve the context and provides type safety.
	export const useAuth = () => {
	  const context = useContext(AuthContext);
	  if (!context) {
	    throw new Error("useAuth must be used within an AuthProvider");
	  }
	  return context;
	};
	```

2. **Wrap context around the component in index.tsx or it's top-level component.**

	```
	root.render(
	  <React.StrictMode>
	    <AuthProvider>
	      <App />
	    </AuthProvider>
	  </React.StrictMode>
	);
	```

3. **Use the context in one of the wrapped Components.**

	```
	import React from "react";
	import { useAuth } from "./AuthContext";
	
	const UserProfile = () => {
	  // Use the custom hook to access authentication data
	  const { user, login, logout } = useAuth();
	
	  return (
	    <div>
	      {user ? (
	        // If a user is authenticated, display user information and a logout button
	        <>
	          <h2>Welcome, {user.name}!</h2>
	          <button onClick={logout}>Logout</button>
	        </>
	      ) : (
	        // If no user is authenticated, display a login button
	        <button onClick={() => login({ name: "John Doe" })}>Login</button>
	      )}
	    </div>
	  );
	};
	
	export default UserProfile;
	```


## Passing properties to child comopnents

If the context is a simple wrapper, you can inline the `children` type

```
export const AuthProvider: FC<{ children: ReactNode }> = ({ children }) => {
```

However, if you need to pass additional properties, you can do so via props as necessary.

1. **Define a props interface**

	```
	// Define a props interface for the AuthProvider component
	import { ReactNode } from "react";
	
	interface AuthProviderProps {
	  children: ReactNode; // Child components or elements
	  initialUser: User | null; // Represents the initial user authentication state
	}
	```

2. **Use the props interface in a functional component**

	```
	// AuthProvider component
	const AuthProvider: React.FC<AuthProviderProps> = ({ children, initialUser }) => {
	```

3. **Wrap the Component with the Provider and pass the property**

	```
	function App() {
	  const initialUser = getInitialUser(); // Fetch or set initial user data
	
	  return (
	    <AuthProvider initialUser={initialUser}>
	      {/* Your app components */}
	    </AuthProvider>
	  );
	}
	```
