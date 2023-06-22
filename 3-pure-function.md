# Avoid side effects

do nothing but return output, based on nothing but input

函數的輸出應該只和輸入有關，也就是當你給相同的值，他的輸出永遠會相同。

且如果一個函數除了返回輸出之外，還執行任何其他的操作，那麼它就不是純函數。它對程序或世界的任何其他影響都是副作用（例如，將信息記錄到控制台，或更改 DOM）。

### side effect

```jsx
const user = {name: 'Jack', age: 18};

function renameUser(newName) {
	user.name = newName;
	console.log('Renamed');
}

renameUser('Rose'); // Renamed
user; // {name: 'Rose', age: 18}
```

他更改了外部的資料，這造成我們每次執行時，都可能會有不同的結果

### No side effect

```jsx
const user = {name: 'Jack', age: 18};

function renameUser(oldUser, newName) {
  return {
    ...oldUser,
    name: newName
  }
}

const user2 = renameUser(user, 'Rose');
user; // {name: 'Jack', age: 18}
user2 // {name: 'Rose', age: 18}
```

# Example of not pure function

1. 更改了 DOM

```jsx
function setColor(R, G, B) {
  const hex = rgbToHex(R, G, B);
  const colorMe = document.getElementById('color-me');
  colorMe.setAttribute('style', 'color: ' + hex);
}
```

1. 打印訊息到控制台

```jsx
function showTruthTable(operator) {
  console.table(computeTruthTable(operator));
}
```

1. 串接資料

```jsx
async function readJsonFile(filename) {
  const file = await fetch(
    'https://earthquake.usgs.gov/earthquakes/feed/v1.0/summary/all_hour.geojson'
  );
  return await file.json();
}
```

# 小結

FP 的重點不是追求純函數，而是對於非純函數要有明確的邊界