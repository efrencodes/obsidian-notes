### Recommendation

Como recomendación para quien no tiene experiencia con desarrollo mobile es usar expo.

Para crear un nuevo proyecto usando el cli de expo

```bash
yarn create expo-app --template blank-typescript
```

### Boilerplate

Boilerplate de React Native

[GitHub - infinitered/ignite: Infinite Red's battle-tested React Native project boilerplate, along with a CLI, component/model generators, and more!](https://github.com/infinitered/ignite)

### Testing

- React Native Testing Library - unit test
- Detox Test - e2e
- Appium - e2e
- Maestro - e2e

### Push notifications services

- Expo
- OneSignal
- Firebase Cloud Messaging
- AWS Amplify

### Third-party libraries

- Camara

[https://github.com/mrousavy/react-native-vision-camera](https://github.com/mrousavy/react-native-vision-camera)

- Biometic Authentication

[LocalAuthentication](https://docs.expo.dev/versions/latest/sdk/local-authentication/)

- Expo Router

[Introduction to Expo Router](https://docs.expo.dev/router/introduction/)

### Deployments

[fastlane - App automation done right](https://fastlane.tools/)

### Beta Deployment

[TestFlight - Apple Developer](https://developer.apple.com/testflight/)

### Extensions of Code VS

- React native tools
- Eslint
- Expo tools

### Libraries UI

- React native paper

[React Native Paper](https://callstack.github.io/react-native-paper/index.html)

- Magnus UI

[A Utility-First React Native UI Framework](https://magnus-ui.com/)

- NativeBase

[NativeBase: Universal Components for React & React Native](https://nativebase.io/)

- UI kitten

[UI Kitten - React Native UI Library based on Eva Design System](https://akveo.github.io/react-native-ui-kitten/)

- Tamagui

[Tamagui](https://tamagui.dev/)

- NativeWind UI

[NativeWindUI](https://nativewindui.com/)

### Libraries State

- Zustand

[Zustand](https://zustand-demo.pmnd.rs/)

### Libraries DataFetch

- TanStack Query

[TanStack Query](https://tanstack.com/query/latest)

### Styles

- StylesSheet es una abstracción de similar a CSS normal

```jsx
const styles = StyleSheet.create({
  container: {
    flex: 1,
    padding: 24,
    backgroundColor: '#eaeaea',
  },
  title: {
    marginTop: 16,
    paddingVertical: 8,
    borderWidth: 4,
    borderColor: '#20232a',
    borderRadius: 6,
    backgroundColor: '#61dafb',
    color: '#20232a',
    textAlign: 'center',
    fontSize: 30,
    fontWeight: 'bold',
  },
});
```