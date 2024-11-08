# interview-toolbox
A collection of notes for interviews

## Forward
After years of doing interviews on both sides, I've found that I enjoy
unrehearsed interviews the most, but I accept that some preparation is good.

These notes help me recall the locations of relevant documentation quickly to
minimize hemming and hawing.

## React
###### `like_button.js`[^1]
```jsx
'use strict';

const { useState } = React;

const e = React.createElement;

function LikeButton() {
  const [liked, setLiked] = useState(false);

  if (liked) {
    return 'You liked this.';
  }

  return (
    <button onClick={() => setLiked(true)}>
      Like
    </button>
  );
}

const domContainer = document.querySelector('#like_button_container');
const root = ReactDOM.createRoot(domContainer);
root.render(e(LikeButton));
```

###### `MyComponent`[^2]
```jsx
function MyComponent() {
  const [error, setError] = useState(null);
  const [isLoaded, setIsLoaded] = useState(false);
  const [items, setItems] = useState([]);

  // Note: the empty deps array [] means
  // this useEffect will run once
  // similar to componentDidMount()
  useEffect(() => {
    fetch("https://api.example.com/items")
      .then(res => res.json())
      .then(
        (result) => {
          setIsLoaded(true);
          setItems(result);
        },
        // Note: it's important to handle errors here
        // instead of a catch() block so that we don't swallow
        // exceptions from actual bugs in components.
        (error) => {
          setIsLoaded(true);
          setError(error);
        }
      )
  }, [])

  if (error) {
    return <div>Error: {error.message}</div>;
  } else if (!isLoaded) {
    return <div>Loading...</div>;
  } else {
    return (
      <ul>
        {items.map(item => (
          <li key={item.id}>
            {item.name} {item.price}
          </li>
        ))}
      </ul>
    );
  }
}
```

## License
Content at [legacy.reactjs.org](https://legacy.reactjs.org/) is CC-BY-4.0 licensed, as found in the [LICENSE-DOCS.md](https://github.com/reactjs/legacy.reactjs.org/blob/main/LICENSE-DOCS.md) file.  
Content submitted to [react.dev](https://react.dev/) is CC-BY-4.0 licensed, as found in the [LICENSE-DOCS.md](https://github.com/reactjs/react.dev/blob/main/LICENSE-DOCS.md) file.

[^1]: https://legacy.reactjs.org/docs/add-react-to-a-website.html
[^2]: https://legacy.reactjs.org/docs/faq-ajax.html
