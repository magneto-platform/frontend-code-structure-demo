## Front End Code File Structure ##

The following code structure is for demo. It's an example.

- `public/`
- `__tests__/`
- `__mocks__/` for manual mocking of `node_modules` like `fs` or `axios`.
- `src/`
	- `pages/`
		- `Home.js` (`home/Home.js`)
		- `Profile.js`
	- `components/`
		- `Order`
			- `index.js` (one approach of naming)
			- `index.test.js`
			- `order.scss`
		- `invoice`
			- `Invoice.js` (another approach of naming)
			- `Invoice.test.js`
			- `invoice.scss`
		- `template/`
			- `Nav.js` (`nav/Nav.js`)
			- `Sidebar.js`
			- `Footer.js`
	- `state/` contains and manages app's state by `Redux` and `Redux-Saga`.
		- `actions/`
		- `reducers/`
			- `seller/`
				- `SellerReducer.js`
				- `SellerReducer.test.js`
			- `product/`
			- `CombinedReducers.js` combines all the reducers.
		- `sagas/`
			- `seller/`
				- `SellerSaga.js` contains all SellerSaga workers.
				- `sellerSaga.test.js`
			- `product/`
			- `rootSaga.js` contains the root of all sagas.
		- `selectors/` selectors meant to select specific data from the state.
		- `services/` contains API calls.
			- `seller/`
				- `SellerAPI.js`
				- `SellerAPI.test.js`
				- `__mock__` for manual mocking and fake data.
		- `Store.js` the main store of the app.
	- `utils/`
	- `setupTests.js` jest configuration file.
- `.env`
- `package.json`

## Conventions & Guidelines ##

- Each React component should be reusable, styled and tested. 
	- `product/`
		- `index.js`
		- `product.scss`
		- `product.test.js`
- React components should have uppercase name e.g. `Component.js`, `Product.js`, `Nav.js` ... etc.
- Directory names should be lowercase or camelCase e.g. `actions`, `productList` ... etc.
- Some components should be aggregated which means some components will be nested under other components. For example; assume that we have two components `Post` and `Comment`. Assume that the `Comment` component is a part of `Post` component. `Comment` component doesn't stand without `Post` component. In this case, the file structure should look like;
	- `post/`
		- `Post.js`
		- `comment/`
			- `Comment.js`
- Avoid lengthy nested components.


## Considerations ##
- **Test Files**

| `__tests__` | `*.test.js` or `*.spec.js` |
| --- | --- |
| - Many schools see that tests are not consider a part of the code. Tests are set alongside the app, so they put tests within separate folder. | - According to our philosophy, do we consider the tests are a part of our app? If so, we should put test files along their executable code files.
| - Good for integrational and E2E tests. | - Good for unit tests and sometimes integrational tests. <br /> - Each file has its test next to it. <br /> - Good when we need to move any module or component to another place or another app. It'll be easy to move the executable code plus its tests. |

- **Component Names Inside Directory**

| `Component/index.js` | `Component/Component.js` |
| --- | --- |
| - e.g. `Post/index.js` | - e.g. `Post/Post.js` |
| - It'll be pretty shorter during importing process like <br /><br /> `import Post from './../Post'` | - It'll be a bit lengthy during importing process like <br /><br /> `import Post from './../Post/Post'` |
|  | - It may result in an issue during debugging. You'll see a lot of `index.js` files.<br />- You can use any of third parties to handle this concern. |


## Packages & Third Parties ##
- `Redux` for ...
