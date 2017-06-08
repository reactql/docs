# Match parameters

---

If you have a route like this:

```jsx
<Route path="/page/:name" component={Page} />
```

... then the `name` param will be passed to `<Page>` as follows:

```jsx
// The <Page> component that we've passed to `component=` in our <Route>
const Page = ({ match }) => (
  <h1>Changed route: {match.params.name}</h1>
);

// The 'shape' of the props we can expect to be passed by <Route>
Page.propTypes = {
  match: React.PropTypes.shape({
    params: React.PropTypes.object,
  }).isRequired,
};
```

You can declare multiple parameters that will be made available via `props.match.params;`
