# Bài tập tuần 1
- 21110153 - Nguyễn Lê Bảo Duy
---------------------
## Steps

### Step 1: Init project
```code
npx create-expo-app@latest client --template (blank-minimun)
```

**Setup expo router**
```code
npx expo install expo-router react-native-safe-area-context react-native-screens expo-linking expo-constants expo-status-bar
```

**Source structure convention**</br>

<img width="253" alt="Screenshot 2025-02-22 at 3 17 01 PM" src="https://github.com/user-attachments/assets/54f1faf5-cbd5-4b0e-9f31-32401c045155" />

### Step 2: On boarding Screen
```code
app/_layout.tsx

const RootLayout = () => {
  return (
    <SafeAreaProvider className="">
      <Stack
        screenOptions={{
          headerShown: false,
        }}
      ></Stack>
    </SafeAreaProvider>
  );
};

export default RootLayout;
```

### Step 3: Redirect to Home Screen in 10 secs
Using 2 build-in functions: **SetTimeout** and **SetInterval**
```code
app/index.tsx

import "expo-router/entry";

import { Link, router } from "expo-router";

import { ScrollView, View, Text, Image } from "react-native";
import { SafeAreaView } from "react-native-safe-area-context";
import { useEffect, useState } from "react";
import Button from "~/components/Button";
import { images } from "@constants/index";
import Item from "~/components/Item";

const App = () => {
  const [counter, setCounter] = useState(10);

  useEffect(() => {
    setTimeout(() => {
      clearInterval(interval);

      router.push("/home");
    }, 10000);

    const interval = setInterval(() => {
      setCounter((prev) => prev - 1);
    }, 1000);
  }, []);

  return (
    <View/>...<View>
  );
};

export default App;

```

---------------------
## Result
![simulator_screenshot_828E911B-42BD-47A6-BF16-F25876F79011](https://github.com/user-attachments/assets/54f1faf5-cbd5-4b0e-9f31-32401c045155)
</br>
![simulator_screenshot_501FB1E3-52A8-46A8-AEE3-8EA86096F568](https://github.com/user-attachments/assets/5c5de192-5fb0-4e3d-8994-d907d4b781d1)

