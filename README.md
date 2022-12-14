# How to create single repo for managing several apps with shared code

## 1. Initialize workspace

```bash
npx create-nx-workspace@latest --packageManager=yarn --nxCloud=false
```

| Q                                                    | A                      |
| ---------------------------------------------------- | ---------------------- |
| Choose what to create                                | integrated             |
| What to create in the new workspace                  | react-native           |
| Repository name                                      | react-native-multi-app |
| Application name                                     | MultiApp               |
| Enable distributed caching to make your CI faster... | no                     |

## 2. Generate one more application

```bash
nx generate @nrwl/react-native:app MultiApp2
```

**OR**

#### install Nx Console plugin in the VSCode.

1. cmd+shift+p
1. type "Nx:generate (ui)
1. choose @nrwl/react-native:application
1. Name it MultiApp2 and disable tests.
1. Press run;

## 3. Generate components library

1. cmd+shift+p
1. type "Nx:generate (ui) -> choose @nrwl/react-native:library
1. Name it ui-components.
1. Press run;

## 3. Generate component

1. cmd+shift+p
1. type "Nx:generate (ui)
1. choose @nrwl/react-native:component.
1. Name it button, choose project "ui-components" and select "export".
1. Press run;

Now, we can use this component in our apps by:

`import { Button } from '@react-native-multi-app/ui-components';`

## 4. Run apps
```
cd apps/multi-app2/ios && pod install --repo-update && cd -
```
```
npx nx run multi-app2:run-ios
```

# About Nx

## Development server

Run `nx serve MultiApp` for a dev server. Navigate to http://localhost:4200/. The app will automatically reload if you change any of the source files.

## Understand this workspace

cmd+shift+p -> type "nx: Show full project graph"
Run `nx graph` to see a diagram of the dependencies of the projects.

## Further help

Visit the [Nx Documentation](https://nx.dev) to learn more.
