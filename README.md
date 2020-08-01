# Material-UI

## Handling Background Image in Material UI

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
