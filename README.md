# StoreContext

A ref-based generic context for ultra fast React component updates.

## [`createStoreContext.tsx`](https://raw.githubusercontent.com/nicholasadamou/StoreContext/98e0487119d5a5062674aaea97ea476097a78ec3/src/createStoreContext.tsx)

```tsx
import createStoreContext from "./createStoreContext";

const { Provider, useStore } = createStoreContext({
  first: "",
  last: "",
});

const TextInput = ({ value }: { value: "first" | "last" }) => {
  const [fieldValue, setStore] = useStore((store) => store[value]);
  return (
    <div className="field">
      {value}:{" "}
      <input
        value={fieldValue}
        onChange={(e) => setStore({ [value]: e.target.value })}
      />
    </div>
  );
};

const Display = ({ value }: { value: "first" | "last" }) => {
  const [fieldValue] = useStore((store) => store[value]);
  return (
    <div className="value">
      {value}: {fieldValue}
    </div>
  );
};

const FormContainer = () => {
  return (
    <div className="container">
      <h5>FormContainer</h5>
      <TextInput value="first" />
      <TextInput value="last" />
    </div>
  );
};

const DisplayContainer = () => {
  return (
    <div className="container">
      <h5>DisplayContainer</h5>
      <Display value="first" />
      <Display value="last" />
    </div>
  );
};

const ContentContainer = () => {
  return (
    <div className="container">
      <h5>ContentContainer</h5>
      <FormContainer />
      <DisplayContainer />
    </div>
  );
};

const App = () => (
    <Provider>
      <div className="container">
        <h5>App</h5>
        <ContentContainer />
      </div>
    </Provider>
)

export default App;
```
