# Starting the project

1. Create git repo
1. Add readme.md file

## React Setup

1. RUN create-react-app _folderName_
1. CD into _folderName_
1. RUN npm start (this is to make sure the frontend server is working)
1. Replace favicon.ico file
1. Remove and clean up unwanted files (App.css, App.test.js, logo.svg, setupTests.js)
1. Change the App.js file to look like this to start:

```javascript
import React from 'react'

function App() {
  return (
    <>
      <h1>Welcome to ProShop</h1>
    </>
  )
}

export default App
```

1. Remove index.css styling
1. Move .gitignore file to root of project
1. Add "node_modules", "node_modules/" and ".env" to the .gitignore file

## Basic components Setup

1. Add "components" folder to the src folder
1. Create a new file(component) "Header.js"
1. Use "rafce" to create a React arrow function component
1. Create a (component) "Footer.js"
1. Use "rafce" to create a React arrow function component
1. Go to App.js file to import the new components, the file will not look like this:

```javascript
import React from 'react'
import Header from './components/Header'
import Footer from './components/Footer'

function App() {
  return (
    <>
      <Header />
      <main>
        <h1>Welcome to ProShop</h1>
      </main>
      <Footer />
    </>
  )
}

export default App
```

## React Bootswatch

1. Add CDN for FontAwesome to the **index.html** file
1. Create **images** folder (inside the **public** folder) and add files as needed
1. Download the bootstrap.min.css file
1. Move that file into the **frontend** folder and then into the **src** folder
1. Import the bootstrap.min.css into the index.js file
1. RUN npm install react-bootstrap inside the **frontend** folder
1. Import the components you need from react bootstrap in each file

```javascript
import { Container } from 'react-bootstrap'
```

# Create the basic components

### Footer component

```javascript
import React from 'react'
import { Container, Row, Col } from 'react-bootstrap'

const Footer = () => {
  return (
    <footer>
      <Container>
        <Row>
          <Col className='text-center py-3'>Copyright &copy; ProShop</Col>
        </Row>
      </Container>
    </footer>
  )
}

export default Footer
```

### Header Navigation component

```javascript
import React from 'react'
import { Navbar, Nav, Container } from 'react-bootstrap'

const Header = () => {
  return (
    <header>
      <Navbar bg='dark' variant='dark' expand='lg' collapseOnSelect>
        <Container>
          <Navbar.Brand href='/'>ProShop</Navbar.Brand>
          <Navbar.Toggle aria-controls='basic-navbar-nav' />
          <Navbar.Collapse id='basic-navbar-nav'>
            <Nav className='ml-auto'>
              <Nav.Link href='/cart' className='fas fa-shopping-cart'>
                Cart
              </Nav.Link>
              <Nav.Link href='/login' className='fas fa-user'>
                Sign In
              </Nav.Link>
            </Nav>
          </Navbar.Collapse>
        </Container>
      </Navbar>
    </header>
  )
}

export default Header
```

### Product component

```javascript
import React from 'react'
import { Card } from 'react-bootstrap'

const Product = ({ product }) => {
  return (
    <Card className='my-3 p-3 rounded'>
      <a href={`/product/${product._id}`}>
        <Card.Img src={product.image} variant='top' />
      </a>

      <Card.Body>
        <a href={`/product/${product._id}`}>
          <Card.Title as='div'>
            <strong>{product.name}</strong>
          </Card.Title>
        </a>

        <Card.Text>
          <div className='my-3'>
            {product.rating} from {product.numReviews} reviews
          </div>
        </Card.Text>

        <Card.Text as='h3'>${product.price}</Card.Text>
      </Card.Body>
    </Card>
  )
}

export default Product
```

### HomeScreen component

```javascript
import React from 'react'
import { Row, Col } from 'react-bootstrap'
import Product from '../components/Product'
import products from '../products'

const HomeScreen = () => {
  return (
    <>
      <h1>Lastest Products</h1>
      <Row>
        {products.map((product) => (
          <Col sm={12} md={6} lg={4} xl={3}>
            <Product product={product} />
          </Col>
        ))}
      </Row>
    </>
  )
}

export default HomeScreen
```

### Main app component

1. After creating these components, make sure everything is imported in the right places and everything is working as expected

```javascript
import React from 'react'
import { Container } from 'react-bootstrap'
import Header from './components/Header'
import Footer from './components/Footer'
import HomeScreen from './screens/HomeScreen'

function App() {
  return (
    <>
      <Header />
      <main className='py-3'>
        <Container>
          <HomeScreen />
        </Container>
      </main>
      <Footer />
    </>
  )
}

export default App
```
