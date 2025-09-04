Got it ✅
Now I’ll rewrite the **full documentation** clearly and professionally, with **Redux + MUI Custom Theme**, using both:

* [MUI Theme Creator](https://zenoo.github.io/mui-theme-creator/) (for visually generating theme configs).
* [MUI Official Theming Guide](https://mui.com/material-ui/customization/theming/) (for advanced customization and overrides).

This will be your **complete reference docs**.

---

# 📖 Reference Docs: MUI Custom Theme (Light & Dark) with Redux

---

## 1. 🔎 What is MUI Theming?

Material UI (MUI) provides a powerful **theme system** that allows you to:

* 🎨 Define **colors** (primary, secondary, background, etc.)
* 🌗 Support **light and dark modes**
* ✍️ Configure **typography** (font families, sizes, weights)
* 📐 Adjust **shape** (border radius)
* 🧱 Control **spacing** (layout unit, default 8px)
* 🎛️ Add **component overrides** for global styles

When wrapped with `ThemeProvider`, your theme applies globally across all MUI components.

👉 Official Docs: [MUI Theming Guide](https://mui.com/material-ui/customization/theming/)

---

## 2. 🎨 Designing Themes with MUI Theme Creator

Instead of writing the theme object manually, use [MUI Theme Creator](https://zenoo.github.io/mui-theme-creator/):

1. Open the tool.
2. Pick **palette colors** (primary, secondary, error, background).
3. Configure **typography, border radius, spacing**.
4. Export the theme as a `ThemeOptions` object.
5. Save it in your project (`lightTheme.ts` / `darkTheme.ts`).

👉 Example Export from Theme Creator:

```ts
import { ThemeOptions } from "@mui/material/styles";

export const themeOptions: ThemeOptions = {
  palette: {
    mode: "light",
    primary: { main: "#1b79d4" },
    secondary: { main: "#57a82d" },
  },
  shape: { borderRadius: 8 },
  spacing: 8,
  typography: {
    fontFamily: '"Roboto","Helvetica","Arial",sans-serif',
  },
};
```

---

## 3. ⚙️ Install Dependencies

```bash
npm install @mui/material @emotion/react @emotion/styled
npm install @reduxjs/toolkit react-redux
```

---

## 4. 📂 Recommended Folder Structure

```
src/
 ├── app/
 │    └── store.ts             # Redux store
 ├── features/
 │    └── theme/
 │         ├── themeSlice.ts   # Redux slice for theme
 │         ├── lightTheme.ts   # Light theme config (exported from Theme Creator)
 │         ├── darkTheme.ts    # Dark theme config (exported from Theme Creator)
 ├── components/
 │    └── ThemeToggle.tsx      # Toggle button
 ├── App.tsx
 └── main.tsx
```

---

## 5. 🌞 Light Theme & 🌙 Dark Theme

📁 `src/features/theme/lightTheme.ts`

```ts
import { ThemeOptions, createTheme } from "@mui/material/styles";

const lightThemeOptions: ThemeOptions = {
  palette: {
    mode: "light",
    primary: { main: "#1b79d4" },
    secondary: { main: "#57a82d" },
    background: {
      default: "#f5f5f5",
      paper: "#ffffff",
    },
  },
  shape: { borderRadius: 8 },
  spacing: 8,
  typography: {
    fontFamily: '"Roboto","Helvetica","Arial",sans-serif',
  },
};

export const lightTheme = createTheme(lightThemeOptions);
```

📁 `src/features/theme/darkTheme.ts`

```ts
import { ThemeOptions, createTheme } from "@mui/material/styles";

const darkThemeOptions: ThemeOptions = {
  palette: {
    mode: "dark",
    primary: { main: "#1b79d4" },
    secondary: { main: "#57a82d" },
    background: {
      default: "#121212",
      paper: "#1e1e1e",
    },
  },
  shape: { borderRadius: 8 },
  spacing: 8,
  typography: {
    fontFamily: '"Roboto","Helvetica","Arial",sans-serif',
  },
};

export const darkTheme = createTheme(darkThemeOptions);
```

---

## 6. 🧩 Redux Slice for Theme

📁 `src/features/theme/themeSlice.ts`

```ts
import { createSlice, PayloadAction } from "@reduxjs/toolkit";

type ThemeMode = "light" | "dark";

interface ThemeState {
  mode: ThemeMode;
}

const prefersDarkMode = window.matchMedia("(prefers-color-scheme: dark)").matches;

const initialState: ThemeState = {
  mode: (localStorage.getItem("themeMode") as ThemeMode) || (prefersDarkMode ? "dark" : "light"),
};

const themeSlice = createSlice({
  name: "theme",
  initialState,
  reducers: {
    toggleTheme: (state) => {
      state.mode = state.mode === "light" ? "dark" : "light";
      localStorage.setItem("themeMode", state.mode);
    },
    setTheme: (state, action: PayloadAction<ThemeMode>) => {
      state.mode = action.payload;
      localStorage.setItem("themeMode", state.mode);
    },
  },
});

export const { toggleTheme, setTheme } = themeSlice.actions;
export default themeSlice.reducer;
```

---

## 7. 🏗️ Redux Store

📁 `src/app/store.ts`

```ts
import { configureStore } from "@reduxjs/toolkit";
import themeReducer from "../features/theme/themeSlice";

export const store = configureStore({
  reducer: {
    theme: themeReducer,
  },
});

export type RootState = ReturnType<typeof store.getState>;
export type AppDispatch = typeof store.dispatch;
```

---

## 8. 🌍 Apply Theme Globally

📁 `src/main.tsx`

```tsx
import React from "react";
import ReactDOM from "react-dom/client";
import { Provider, useSelector } from "react-redux";
import { ThemeProvider, CssBaseline } from "@mui/material";
import { store, RootState } from "./app/store";
import App from "./App";
import { lightTheme } from "./features/theme/lightTheme";
import { darkTheme } from "./features/theme/darkTheme";

function ThemedApp() {
  const mode = useSelector((state: RootState) => state.theme.mode);
  const theme = mode === "light" ? lightTheme : darkTheme;

  return (
    <ThemeProvider theme={theme}>
      <CssBaseline />
      <App />
    </ThemeProvider>
  );
}

const root = ReactDOM.createRoot(document.getElementById("root") as HTMLElement);

root.render(
  <Provider store={store}>
    <ThemedApp />
  </Provider>
);
```

---

## 9. 🎛️ Theme Toggle Button

📁 `src/components/ThemeToggle.tsx`

```tsx
import { useDispatch, useSelector } from "react-redux";
import { IconButton } from "@mui/material";
import LightModeIcon from "@mui/icons-material/LightMode";
import DarkModeIcon from "@mui/icons-material/DarkMode";
import { RootState, AppDispatch } from "../app/store";
import { toggleTheme } from "../features/theme/themeSlice";

export default function ThemeToggle() {
  const mode = useSelector((state: RootState) => state.theme.mode);
  const dispatch = useDispatch<AppDispatch>();

  return (
    <IconButton onClick={() => dispatch(toggleTheme())} color="inherit">
      {mode === "light" ? <DarkModeIcon /> : <LightModeIcon />}
    </IconButton>
  );
}
```

---

## 10. 🎨 Example Usage in App

📁 `src/App.tsx`

```tsx
import { Typography, Button, AppBar, Toolbar } from "@mui/material";
import ThemeToggle from "./components/ThemeToggle";

function App() {
  return (
    <>
      <AppBar position="static">
        <Toolbar>
          <Typography variant="h6" sx={{ flexGrow: 1 }}>
            MUI + Redux Theme
          </Typography>
          <ThemeToggle />
        </Toolbar>
      </AppBar>

      <div style={{ padding: 20 }}>
        <Typography variant="h4" color="primary">
          Hello, Redux-powered Theme!
        </Typography>
        <Button variant="contained" color="secondary">
          Action
        </Button>
      </div>
    </>
  );
}

export default App;
```

---

## 11. 🔧 Advanced Customization

* **Component Overrides** → Use `components` inside your theme:
  👉 [Overrides Docs](https://mui.com/material-ui/customization/theme-components/)
* **Responsive Typography** → Use `responsiveFontSizes()` from MUI.
* **Multiple Themes** → Add more `themeOptions.ts` files for branding (Blue, Green, Corporate).
* **Persisting Mode** → Already included via `localStorage`.

---

## 📚 Reference Links

* 🎨 [MUI Theme Creator](https://zenoo.github.io/mui-theme-creator/)
* 📖 [MUI Official Theming Docs](https://mui.com/material-ui/customization/theming/)
* 🎛️ [MUI Theme Components Override](https://mui.com/material-ui/customization/theme-components/)
* 🧩 [Redux Toolkit Quick Start](https://redux-toolkit.js.org/tutorials/quick-start)

---

✅ With this setup you now have:

* Light & Dark themes generated via **MUI Theme Creator**
* Centralized state management via **Redux Toolkit**
* Auto-detection of **system preference** (OS light/dark)
* **LocalStorage persistence** for user preference
* Full extendability with **MUI theming system**

---

Do you also want me to expand this guide with a **multi-theme example** (e.g., Light, Dark, Blue, Green) so you can support more than 2 themes?
