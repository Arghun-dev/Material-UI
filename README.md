# Material-UI

## 1. Handling Background Image in Material UI

```js
import BackgroundImage from '../../assets/login/login-background-image/login-bg.png';

const styles = theme => ({
    root: {
        height: '100vh',
        backgroundImage: `linear-gradient(to left bottom, rgba(107, 189, 197, .7), rgba(222, 252, 255, .7), rgba(107, 189, 197, .7)), url(${BackgroundImage})`,
        display: 'flex',
        justifyContent: 'center',
        alignItems: 'center'
    }
})

export default styles;
```

## 2. Changing the font family of Material UI

check this page: `https://material-ui.com/customization/typography/`

1. first download the font files which you want to use for example I want to use `Vazir` font download the `Vazir.woff2` file. and save it inside font folder of your code.

2. then create a `AppStyle.js` file and import the `Vazir.woff2` file to your code:

```js
import { createMuiTheme } from '@material-ui/core';
import Vazir from './font/Vazir.woff2';

const vazir = {
    fontFamily: 'Vazir',
    fontStyle: 'normal',
    fontDisplay: 'swap',
    fontWeight: 400,
    src: `
      local('Vazir'),
      local('Vazir-Regular'),
      url(${Vazir.Woff2}) format('woff2')
    `,
    unicodeRange:
        'U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF',
};

const theme = createMuiTheme({
    typography: {
        fontFamily: 'vazir',
    },
    overrides: {
        MuiCssBaseline: {
            '@global': {
                '@font-face': [vazir],
            },
        },
    },
});

export default theme
```

and then in `App.js` file:

```js
import React, { Suspense } from 'react';
import { Switch, Route } from 'react-router-dom';

// Material-UI
import CircularProgress from '@material-ui/core/CircularProgress';
import { ThemeProvider } from '@material-ui/core';
import withStyles from '@material-ui/core/styles/withStyles';
import theme from './AppStyle';

// screens
const Login = React.lazy(() => import('./screens/login/Login'));
const Dashboard = React.lazy(() => import('./screens/dashboard/Dashboard'));

function App() {
  return (
    <ThemeProvider theme={theme}>
      <Suspense fallback={<CircularProgress />}>
        <Switch>
          <Route exact path='/' render={() => <Login />} />
          <Route exact path='/dashboard' render={() => <Dashboard />} />
        </Switch>
      </Suspense>
    </ThemeProvider>
  );
}

export default App;
```

As you can see I wrapped all the components with `ThemeProvider` and then I have imported the `theme` file from `AppStyle.js` and I used it in `<ThemeProvider theme={theme} />`


## 3. Make Materil-UI RTL

check this link: `https://material-ui.com/guides/right-to-left/`


## 4. Hidden component

check this link: `https://material-ui.com/components/hidden/`
