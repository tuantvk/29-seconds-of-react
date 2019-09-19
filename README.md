![Logo](/logo.png)

# 29 seconds of React

<p align="center">
  <a href="https://github.com/tuantvk/29-seconds-of-react/issues">
    <img src="https://img.shields.io/github/issues/tuantvk/29-seconds-of-react.svg" alt="issues" />
  </a>
  <a href="#">
    <img src="https://img.shields.io/github/forks/tuantvk/29-seconds-of-react.svg" alt="forks" />
  </a>
  <a href="#">
    <img src="https://img.shields.io/github/stars/tuantvk/29-seconds-of-react.svg" alt="stars" />
  </a>
  <a href="https://github.com/tuantvk/29-seconds-of-react/blob/master/LICENSE">
    <img src="https://img.shields.io/github/license/tuantvk/29-seconds-of-react.svg" alt="LICENSE" />
  </a>
</p>

> Bộ sưu tập cho React snippets giúp bạn hiểu mọi thứ trong 29 giây hoặc ít hơn.

>**Chú thích:**
>
>Tại sao lại là 29 giây hoặc ít hơn? Bài viết được dịch từ [30 seconds of React](https://github.com/30-seconds/30-seconds-of-react), theo nhà người ta, chúng ta có thể phải mất tới 30 giây để hiểu hết được ý nghĩa của một vấn đề nào đó, nhưng với tôi chúng ta là người **Việt Nam**, chúng ta phải khác biệt nên chúng ta chỉ cần 29 giây :alien: :alien:, và đó là lý do của tiêu đề đã bị đổi thành *29 seconds of React*.

- Sử dụng <kbd>Ctrl</kbd> + <kbd>F</kbd> hoặc <kbd>command</kbd> + <kbd>F</kbd> để tìm kiếm nhanh một snippet.
- Contributions, hãy đọc [contribution guide](CONTRIBUTING.md).
- Snippets viết bằng React 16.8+, sử dụng hooks. [Xem thêm Hooks](https://reactjs.org/docs/hooks-intro.html)

### Xem [Prerequisites](/Prerequisite.md) 

#### Các project khác

- [30 Seconds of Code](https://30secondsofcode.org)
- [30 Seconds of CSS](https://30-seconds.github.io/30-seconds-of-css/)
- [30 Seconds of Interviews](https://30secondsofinterviews.org/)
- [Javascript Interview Questions Developer - My Repo 😎](https://github.com/tuantvk/javascript-interview-questions-developer)
- [React Native Testing](https://github.com/tuantvk/WtfReactNativeTesting)
- [React mobx cli](https://github.com/tuantvk/react-mobx-cli)

## Table of Contents


### Array

<details>
<summary>Xem nội dung</summary>

* [DataList](#datalist)
* [DataTable](#datatable)
* [MappedTable](#mappedtable)
</details>


### Input

<details>
<summary>Xem nội dung</summary>

* [Input](#input)
* [LimitedTextarea](#limitedtextarea)
* [LimitedWordTextarea](#limitedwordtextarea)
* [MultiselectCheckbox](#multiselectcheckbox)
* [PasswordRevealer](#passwordrevealer)
* [Select](#select)
* [Slider](#slider)
* [TextArea](#textarea)
</details>


### Object

<details>
<summary>Xem nội dung</summary>

* [TreeView](#treeview)
</details>


### String

<details>
<summary>Xem nội dung</summary>

* [AutoLink](#autolink)
</details>


### Visual

<details>
<summary>Xem nội dung</summary>

* [Accordion](#accordion)
* [Carousel](#carousel)
* [Collapse](#collapse)
* [CountDown](#countdown)
* [FileDrop](#filedrop)
* [Mailto](#mailto)
* [Modal](#modal)
* [StarRating](#starrating)
* [Tabs](#tabs)
* [Ticker](#ticker)
* [Toggle](#toggle)
* [Tooltip](#tooltip)
</details>


---

## Array
### DataList

Renders một danh sách các phần tử từ một mảng cho trước.

* Sử dụng giá trị của prop `isOrdered` là điều kiện để hiển thị danh sách `<ol>` hoặc `<ul>`.
* Sử dụng `Array.prototype.map` để hiển thị các mục trong `data` như là thẻ `<li>`, cung cấp một `key` được tạo ra từ sự kết hợp của index và giá trị của nó.
* Nếu prop `isOrdered` không có sẽ hiển thị thẻ `<ul>` vì nó là một danh sách mặc định.

```jsx
function DataList({ isOrdered, data }) {
  const list = data.map((val, i) => <li key={`${i}_${val}`}>{val}</li>);
  return isOrdered ? <ol>{list}</ol> : <ul>{list}</ul>;
}
```

<details>
<summary>Ví dụ</summary>

```jsx
const names = ['John', 'Paul', 'Mary'];
ReactDOM.render(<DataList data={names} />, document.getElementById('root'));
ReactDOM.render(<DataList data={names} isOrdered />, document.getElementById('root'));
```
</details>

<br>[⬆ Quay lại đầu trang](#table-of-contents)

### DataTable

Hiển thị một table với các hàng được tạo động từ một mảng cho trước.

* Hiển thị một phần tử `<table>`với hai cột (`ID` và `Value`).
* Sử dụng `Array.prototype.map` để hiển thị các mục trong `data` như là thẻ `<tr>`, cung cấp một `key` được tạo ra từ sự kết hợp của index và giá trị của nó.

```jsx
function DataTable({ data }) {
  return (
    <table>
      <thead>
        <tr>
          <th>ID</th>
          <th>Value</th>
        </tr>
      </thead>
      <tbody>
        {data.map((val, i) => (
          <tr key={`${i}_${val}`}>
            <td>{i}</td>
            <td>{val}</td>
          </tr>
        ))}
      </tbody>
    </table>
  );
}
```

<details>
<summary>Ví dụ</summary>

```jsx
const people = ['John', 'Jesse'];
ReactDOM.render(<DataTable data={people} />, document.getElementById('root'));
```
</details>

<br>[⬆ Quay lại đầu trang](#table-of-contents)

### MappedTable

Hiển thị một table với các hàng được tạo động từ một mảng các đối tượng và một danh sách các tên thuộc tính.

* Sử dụng `Object.keys()`, `Array.prototype.filter()`, `Array.prototype.includes()` và `Array.prototype.reduce()` để tạo ra một mảng `filteredData`, chứa tất cả các đối tượng có các key chỉ định trong `propertyNames`.
* Hiển thị một phần tử `<table>` với các cột bằng với số lượng giá trị trong `propertyNames`.
* Sử dụng `Array.prototype.map` để hiển thị từng giá trị trong mảng `propertyNames` như là thẻ `<th>`.
* Sử dụng `Array.prototype.map` để hiển thị từng đối tượng trong mảng `filteredData` như là thẻ `<tr>`, chứa một `<td>` cho mỗi giá trị trong đối tượng.

```jsx
function MappedTable({ data, propertyNames }) {
  let filteredData = data.map(v =>
    Object.keys(v)
      .filter(k => propertyNames.includes(k))
      .reduce((acc, key) => ((acc[key] = v[key]), acc), {})
  );
  return (
    <table>
      <thead>
        <tr>
          {propertyNames.map(val => (
            <th key={`h_${val}`}>{val}</th>
          ))}
        </tr>
      </thead>
      <tbody>
        {filteredData.map((val, i) => (
          <tr key={`i_${i}`}>
            {propertyNames.map(p => (
              <td key={`i_${i}_${p}`}>{val[p]}</td>
            ))}
          </tr>
        ))}
      </tbody>
    </table>
  );
}
```
#### Ghi chú

Component này không hoạt động với các đối tượng lồng nhau và sẽ break nếu có các đối tượng lồng nhau bên trong bất kỳ thuộc tính nào trong `propertyNames`.,<!-tags: array,object -->,<!-expertise: 1 -->

<details>
<summary>Ví dụ</summary>

```jsx
const people = [
  { name: 'John', surname: 'Smith', age: 42 },
  { name: 'Adam', surname: 'Smith', gender: 'male' }
];
const propertyNames = ['name', 'surname', 'age'];
ReactDOM.render(
  <MappedTable data={people} propertyNames={propertyNames} />,
  document.getElementById('root')
);
```
</details>

<br>[⬆ Quay lại đầu trang](#table-of-contents)


## Input
### Input

Hiển thị một phần tử `<input>` khi thay đổi giá trị sẽ gọi hàm callback và truyền giá trị của nó cho parent component.

* Sử dụng các giá trị mặc định ban đầu cho các tham số của phần tử `<input>`.
* Hiển thị một thẻ `<input>` với các thuộc tính phù hợp và sử dụng hàm `callback` trong sự kiện `onChange` để truyền giá trị của của input cho parent component.

```jsx
function Input({ callback, type = 'text', disabled = false, readOnly = false, placeholder = '' }) {
  return (
    <input
      type={type}
      disabled={disabled}
      readOnly={readOnly}
      placeholder={placeholder}
      onChange={({ target: { value } }) => callback(value)}
    />
  );
}
```

<details>
<summary>Ví dụ</summary>

```jsx
ReactDOM.render(
  <Input type="text" placeholder="Insert some text here..." callback={val => console.log(val)} />,
  document.getElementById('root')
);
```
</details>

<br>[⬆ Quay lại đầu trang](#table-of-contents)

### LimitedTextarea

Hiển thị một textarea component giới hạn kí tự.

* Sử dụng hook `React.useState()` tạo một biến `content` và xét giá trị cho nó là `value`. Tạo hàm `setFormattedContent`, nó sẽ cắt nội dung nếu như vượt quá số lượng `limit`.
* Sử dụng hook `React.useEffect()` để gọi hàm `setFormattedContent` với giá trị truyền vào là biến `content`.
* Sử dụng `<div>` để bao thẻ `<textarea>` và thẻ `<p>` hiển thị độ dài của `content` và hàm `onChange` của thẻ `<textarea>`sẽ gọi hàm `setFormattedContent` và truyền giá trị là `event.target.value`.

```jsx
function LimitedTextarea({ rows, cols, initialValue, limit }) {
  const [content, setContent] = React.useState(initialValue);

  const setFormattedContent = text => {
    text.length > limit ? setContent(text.slice(0, limit)) : setContent(text);
  };

  React.useEffect(() => {
    setFormattedContent(content);
  }, [limit]);

  return (
    <div>
      <textarea
        rows={rows}
        cols={cols}
        onChange={event => setFormattedContent(event.target.value)}
        value={content}
      />
      <p>
        {content.length}/{limit}
      </p>
    </div>
  );
}
```

<details>
<summary>Ví dụ</summary>

```jsx
ReactDOM.render(<LimitedTextarea limit={32} initialValue="Hello!" />, document.getElementById('root'));
```
</details>

<br>[⬆ Quay lại đầu trang](#table-of-contents)

### LimitedWordTextarea

Hiển thị một textarea component hạn chế từ.

* Sử dụng hook `React.useState()`để tạo biến `content` và `wordCount` xét giá trị cho chúng là `value` và `0`.
* Tạo hàm `setFormattedContent`, sử dụng `String.prototype.split(' ')` để biến đầu vào thành một mảng các từ và kiểm tra kết quả , sử dụng `Array.prototype.filter(Boolean)`để kiếm tra `độ dài` có lớn hơn `limit`.
* Nếu độ dài lớn hơn `limit`, sẽ cắt giá trị và xét lại giá trị cho `content` và `wordCount` nếu không sẽ trả về giá trị mặc định.
* Sử dụng hook `React.useEffect()` để gọi hàm `setFormattedContent` với giá trị truyền vào là biến `content`.
* Sử dụng `<div>` để bọc thẻ `<textarea>` và thẻ `<p>` hiển thị độ dài của `wordCount` và hàm `onChange` của thẻ `<textarea>` sẽ gọi hàm `setFormattedContent` và truyền giá trị là `event.target.value`.

```jsx
function LimitedWordTextarea({ rows, cols, value, limit }) {
  const [content, setContent] = React.useState(value);
  const [wordCount, setWordCount] = React.useState(0);

  const setFormattedContent = text => {
    let words = text.split(' ');
    if (words.filter(Boolean).length > limit) {
      setContent(
        text
          .split(' ')
          .slice(0, limit)
          .join(' ')
      );
      setWordCount(limit);
    } else {
      setContent(text);
      setWordCount(words.filter(Boolean).length);
    }
  };

  React.useEffect(() => {
    setFormattedContent(content);
  }, []);

  return (
    <div>
      <textarea
        rows={rows}
        cols={cols}
        onChange={event => setFormattedContent(event.target.value)}
        value={content}
      />
      <p>
        {wordCount}/{limit}
      </p>
    </div>
  );
}
```

<details>
<summary>Ví dụ</summary>

```jsx
ReactDOM.render(
  <LimitedWordTextArea limit={5} value="Hello there!" />,
  document.getElementById('root')
);
```
</details>

<br>[⬆ Quay lại đầu trang](#table-of-contents)

### MultiselectCheckbox

Hiển thị một danh sách checkbox sử dụng hàm callback để chọn giá trị hoặc nhiều giá trị từ parent component.

* Sử dụng `React.setState()` để tạo một biến `data` và xét giá trị khởi là từ prop `options`.
* Tạo một function `toggle` được sử dụng để chuyển đổi `checked` cập nhật giá trị cho `data` và gọi hàm `onChange` để truyền lại cho parent component.
* Hiển thị phần tử `<ul>` và sử dụng `Array.prototype.map()` để lặp từng phần tử trong `data` hiển thị các phần tử `<li>` và `<input>` bên trong.
* Mỗi phần tử `<input>` có thuộc tính `type='checkbox'`và giá trị `readOnly`.

```jsx
const style = {
  listContainer: {
    listStyle: 'none',
    paddingLeft: 0
  },
  itemStyle: {
    cursor: 'pointer',
    padding: 5
  }
};

function MultiselectCheckbox({ options, onChange }) {
  const [data, setData] = React.useState(options);

  const toggle = item => {
    data.map((_, key) => {
      if (data[key].label === item.label) data[key].checked = !item.checked;
    });
    setData([...data]);
    onChange(data);
  };

  return (
    <ul style={style.listContainer}>
      {data.map(item => {
        return (
          <li key={item.label} style={style.itemStyle} onClick={() => toggle(item)}>
            <input readOnly type="checkbox" checked={item.checked || false} />
            {item.label}
          </li>
        );
      })}
    </ul>
  );
}
```

<details>
<summary>Ví dụ</summary>

```jsx
const options = [{ label: 'Item One' }, { label: 'Item Two' }];

ReactDOM.render(
  <MultiselectCheckbox
    options={options}
    onChange={data => {
      console.log(data);
    }}
  />,
  document.getElementById('root')
);
```
</details>

<br>[⬆ Quay lại đầu trang](#table-of-contents)

### PasswordRevealer

Hiển thị trường nhập mật khẩu bằng cách bật tắt.

* Sử dụng hook `React.useState()` tạo một biến `shown` và cho nó giá trị là `false`.
* Sử dụng một thẻ `<div>` đê bọc `<input>` và phần tử `<button>` để thay đổi trạng thái `"text"` và `"password"`.

```jsx
function PasswordRevealer({ value }) {
  const [shown, setShown] = React.useState(false);

  return (
    <div>
      <input type={shown ? 'text' : 'password'} value={value} onChange={() => {}} />
      <button onClick={() => setShown(!shown)}>Show/Hide</button>
    </div>
  );
}
```

<details>
<summary>Ví dụ</summary>

```jsx
ReactDOM.render(<PasswordRevealer />, document.getElementById('root'));
```
</details>

<br>[⬆ Quay lại đầu trang](#table-of-contents)

### Select

Hiển thị một phần tử `<select>` khi thay đổi giá trị sẽ gọi hàm callback và truyền giá trị của nó cho parent component.

* Sử dụng các giá trị mặc định ban đầu cho các tham số của phần tử `<select>`.
* Hiển thị một phần tử `<select>` với các thuộc tính phù hợp và sử dụng hàm `callback` là `onChange` để thay đổi giá trị của textarea từ parent component.
* Các giá trị của mảng `values` sẽ truyền `value`, `text` và thuộc tính `selected` sẽ là giá trị ban đầu của phần tử `<select>`.

```jsx
function Select({ values, callback, disabled = false, readonly = false, selected }) {
  return (
    <select
      disabled={disabled}
      readOnly={readonly}
      onChange={({ target: { value } }) => callback(value)}
    >
      {values.map(([value, text]) => (
        <option selected={selected === value} value={value}>
          {text}
        </option>
      ))}
    </select>
  );
}
```

<details>
<summary>Ví dụ</summary>

```jsx
let choices = [
  ['grapefruit', 'Grapefruit'],
  ['lime', 'Lime'],
  ['coconut', 'Coconut'],
  ['mango', 'Mango']
];
ReactDOM.render(
  <Select values={choices} selected="lime" callback={val => console.log(val)} />,
  document.getElementById('root')
);
```
</details>

<br>[⬆ Quay lại đầu trang](#table-of-contents)

### Slider

Hiển thị một phần tử slider khi sử dụng sẽ gọi hàm callback và truyền giá trị của nó cho parent component.

* Sử dụng object destructuring để xét các giá trị ban đầu cho thuộc tính có phần tử `<input>`.
* Hiển thị một phần tử `<input>` có type `"range"` và các thuộc tính phù hợp, sử dụng hàm `callback` trong sự kiện `onChange` để truyền ngược lại giá trị cho input parent component.

```jsx
function Slider({ callback, disabled = false, readOnly = false }) {
  return (
    <input
      type="range"
      disabled={disabled}
      readOnly={readOnly}
      onChange={({ target: { value } }) => callback(value)}
    />
  );
}
```

<details>
<summary>Ví dụ</summary>

```jsx
ReactDOM.render(<Slider callback={val => console.log(val)} />, document.getElementById('root'));
```
</details>

<br>[⬆ Quay lại đầu trang](#table-of-contents)

### TextArea

Hiển thị một phần tử `<textarea>` khi thay đổi giá trị sẽ gọi hàm callback và truyền giá trị của nó cho parent component.

* Sử dụng object destructuring để xét các giá trị ban đầu cho thuộc tính có phần tử `<textarea>`.
* Hiển thị một phần tử `<textarea>` với các thuộc tính phù hợp và sử dụng hàm `callback` trong sự kiện `onChange` để truyền ngược lại giá trị cho textarea parent component.

```jsx
function TextArea({
  callback,
  cols = 20,
  rows = 2,
  disabled = false,
  readOnly = false,
  placeholder = ''
}) {
  return (
    <textarea
      cols={cols}
      rows={rows}
      disabled={disabled}
      readOnly={readOnly}
      placeholder={placeholder}
      onChange={({ target: { value } }) => callback(value)}
    />
  );
}
```

<details>
<summary>Ví dụ</summary>

```jsx
ReactDOM.render(
  <TextArea placeholder="Insert some text here..." callback={val => console.log(val)} />,
  document.getElementById('root')
);
```
</details>

<br>[⬆ Quay lại đầu trang](#table-of-contents)


## Object
### TreeView

Hiển thị dạng cây của một đối tượng JSON hoặc mảng có nội dung có thể thu gọn.

* Sử dụng object destructuring để xét các giá trị ban đầu cho thuộc tính
* Sử dụng giá trị của prop `toggled` để xác định trạng thái ban đầu của nội dung (được thu gọn / mở rộng).
* Sử dụng hook `React.setState()` để tạo biến `isToggled` và xét cho chúng giá trị bằng với prop `toggled` ban đầu.
* Trả về một `<div>` để bọc nội dung của component và thẻ `<span>`, sử dụng để thay đổi giá trị của biến `isToggled`.
* Xác định sự xuất hiện của component, dựa trên biến `isParentToggled`, `isToggled`, `name` và `Array.isArray()` với `data`.
* Với mỗi phần tử trong `data` xác định nó là object hay mảng và hiển thị đệ quy một sub-tree.
* Mặt khác, hiển thị một phần tử `<p>` với thuộc tính style thích hợp..

```css
.tree-element {
  margin: 0;
  position: relative;
}

div.tree-element:before {
  content: '';
  position: absolute;
  top: 24px;
  left: 1px;
  height: calc(100% - 48px);
  border-left: 1px solid gray;
}

.toggler {
  position: absolute;
  top: 10px;
  left: 0px;
  width: 0;
  height: 0;
  border-top: 4px solid transparent;
  border-bottom: 4px solid transparent;
  border-left: 5px solid gray;
  cursor: pointer;
}

.toggler.closed {
  transform: rotate(90deg);
}

.collapsed {
  display: none;
}
```

```jsx
function TreeView({
  data,
  toggled = true,
  name = null,
  isLast = true,
  isChildElement = false,
  isParentToggled = true
}) {
  const [isToggled, setIsToggled] = React.useState(toggled);

  return (
    <div
      style={{ marginLeft: isChildElement ? 16 : 4 + 'px' }}
      className={isParentToggled ? 'tree-element' : 'tree-element collapsed'}
    >
      <span
        className={isToggled ? 'toggler' : 'toggler closed'}
        onClick={() => setIsToggled(!isToggled)}
      />
      {name ? <strong>&nbsp;&nbsp;{name}: </strong> : <span>&nbsp;&nbsp;</span>}
      {Array.isArray(data) ? '[' : '{'}
      {!isToggled && '...'}
      {Object.keys(data).map((v, i, a) =>
        typeof data[v] == 'object' ? (
          <TreeView
            data={data[v]}
            isLast={i === a.length - 1}
            name={Array.isArray(data) ? null : v}
            isChildElement
            isParentToggled={isParentToggled && isToggled}
          />
        ) : (
          <p
            style={{ marginLeft: 16 + 'px' }}
            className={isToggled ? 'tree-element' : 'tree-element collapsed'}
          >
            {Array.isArray(data) ? '' : <strong>{v}: </strong>}
            {data[v]}
            {i === a.length - 1 ? '' : ','}
          </p>
        )
      )}
      {Array.isArray(data) ? ']' : '}'}
      {!isLast ? ',' : ''}
    </div>
  );
}
```

<details>
<summary>Ví dụ</summary>

```jsx
let data = {
  lorem: {
    ipsum: 'dolor sit',
    amet: {
      consectetur: 'adipiscing',
      elit: [
        'duis',
        'vitae',
        {
          semper: 'orci'
        },
        {
          est: 'sed ornare'
        },
        'etiam',
        ['laoreet', 'tincidunt'],
        ['vestibulum', 'ante']
      ]
    },
    ipsum: 'primis'
  }
};
ReactDOM.render(<TreeView data={data} name="data" />, document.getElementById('root'));
```
</details>

<br>[⬆ Quay lại đầu trang](#table-of-contents)


## String
### AutoLink

Hiển thị một chuỗi dưới dạng plaintext, với các URL được chuyển đổi thành các phần tử `<a>` phù hợp.

* Sử dụng `String.prototype.split()` và `String.prototype.match()` với regular expression để tìm URL trong chuỗi.
* Trả về một `<React.Fragment>` với các URL trùng khớp được hiển thị dưới dạng các phần tử `<a>`,  và phần còn lại của chuỗi được hiển thị dưới dạng plaintext.

```jsx
function AutoLink({ text }) {
  const delimiter = /((?:https?:\/\/)?(?:(?:[a-z0-9]?(?:[a-z0-9\-]{1,61}[a-z0-9])?\.[^\.|\s])+[a-z\.]*[a-z]+|(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)(?:\.(?:25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)){3})(?::\d{1,5})*[a-z0-9.,_\/~#&=;%+?\-\\(\\)]*)/gi;

  return (
    <React.Fragment>
      {text.split(delimiter).map(word => {
        let match = word.match(delimiter);
        if (match) {
          let url = match[0];
          return <a href={url.startsWith('http') ? url : `http://${url}`}>{url}</a>;
        }
        return word;
      })}
    </React.Fragment>
  );
}
```

<details>
<summary>Ví dụ</summary>

```jsx
ReactDOM.render(
  <AutoLink text="foo bar baz http://example.org bar" />,
  document.getElementById('root')
);
```
</details>

<br>[⬆ Quay lại đầu trang](#table-of-contents)


## Visual
### Accordion

Hiển thị một menu accordion với với nội dung component có thể thu gọn.

* Xác định component `AccordionItem`, truyền nó cho `Accordion` và bỏ những thuộc tính không cần thiết `AccordionItem` bằng cách xác định tên của hàm trong `props.children`.
* Mỗi component `AccordionItem` hiển thị một `<button>` sử dụng để cập nhật lại `Accordion` thông qua hàm callback `props.handleClick` và nội dung của component, được truyền qua `props.children`, được xác định qua biến `props.isCollapsed` và dựa trên `style`.
* Trong component `Accordion`, sử dụng hook `React.useState()` để khởi tạo giá trị ban đầu cho `bindIndex` có giá trị là `props.defaultIndex`.
* Sử dụng `Array.prototype.map` để hiển thị từng phần tử.
* Xác định `changeItem`, sẽ được thực thi khi click vào `button` của `AccordionItem`.
`changeItem` sẽ gọi hàm callback, `onItemClick` và cập nhật `bindIndex` dựa trên component đã được click.

```jsx
function AccordionItem(props) {
  const style = {
    collapsed: {
      display: 'none'
    },
    expanded: {
      display: 'block'
    },
    buttonStyle: {
      display: 'block',
      width: '100%'
    }
  };

  return (
    <div>
      <button style={style.buttonStyle} onClick={() => props.handleClick()}>
        {props.label}
      </button>
      <div
        className="collapse-content"
        style={props.isCollapsed ? style.collapsed : style.expanded}
        aria-expanded={props.isCollapsed}
      >
        {props.children}
      </div>
    </div>
  );
}

function Accordion(props) {
  const [bindIndex, setBindIndex] = React.useState(props.defaultIndex);

  const changeItem = itemIndex => {
    if (typeof props.onItemClick === 'function') props.onItemClick(itemIndex);
    if (itemIndex !== bindIndex) setBindIndex(itemIndex);
  };
  const items = props.children.filter(item => item.type.name === 'AccordionItem');

  return (
    <div className="wrapper">
      {items.map(({ props }) => (
        <AccordionItem
          isCollapsed={bindIndex === props.index}
          label={props.label}
          handleClick={() => changeItem(props.index)}
          children={props.children}
        />
      ))}
    </div>
  );
}
```

<details>
<summary>Ví dụ</summary>

```jsx
ReactDOM.render(
  <Accordion defaultIndex="1" onItemClick={console.log}>
    <AccordionItem label="A" index="1">
      Lorem ipsum
    </AccordionItem>
    <AccordionItem label="B" index="2">
      Dolor sit amet
    </AccordionItem>
  </Accordion>,
  document.getElementById('root')
);
```
</details>

<br>[⬆ Quay lại đầu trang](#table-of-contents)

### Carousel

Hiển thị một carousel component.

* Sử dụng hook `React.setState()` để tạo biến `active` và xét giá trị ban đầu bằng `0` (vị trí đầu tiên của danh sách).
* Sử dụng đối tượng `style`, để tạo từng style cho mỗi component khác nhau.
* Sử dụng hook `React.useEffect()` để cập nhật giá trị của `active` xét cho nó vị trí của item tiếp theo, sử dụng `setTimeout`.
* Lấy prop `carouselItems`, để tính toán và xét giá trị cho `visible` là được hiển thị hay không hiển thị.
* Hiển thị những carousel item bằng cách dùng `React.cloneElement()` và truyền cho `props` với các kiểu style đã được định sẵn.

```jsx
function Carousel(props) {
  const [active, setActive] = React.useState(0);
  let scrollInterval = null;
  const style = {
    carousel: {
      position: 'relative'
    },
    carouselItem: {
      position: 'absolute',
      visibility: 'hidden'
    },
    visible: {
      visibility: 'visible'
    }
  };
  React.useEffect(() => {
    scrollInterval = setTimeout(() => {
      const { carouselItems } = props;
      setActive((active + 1) % carouselItems.length);
    }, 2000);
  });
  const { carouselItems, ...rest } = props;
  return (
    <div style={style.carousel}>
      {carouselItems.map((item, index) => {
        const activeStyle = active === index ? style.visible : {};
        return React.cloneElement(item, {
          ...rest,
          style: {
            ...style.carouselItem,
            ...activeStyle
          }
        });
      })}
    </div>
  );
}
```

<details>
<summary>Ví dụ</summary>

```jsx
ReactDOM.render(
  <Carousel
    carouselItems={[
      <div>carousel item 1</div>,
      <div>carousel item 2</div>,
      <div>carousel item 3</div>
    ]}
  />,
  document.getElementById('root')
);
```
</details>

<br>[⬆ Quay lại đầu trang](#table-of-contents)

### Collapse

Hiển thị một component với nội dung có thể thu gọn.

* Sử dụng hook `React.setState()` để tạo biến `isCollapsed` và xét giá trị ban đầu bằng `props.collapsed`.
* Sử dụng đối tượng `style`, để tạo từng style cho mỗi component khác nhau.
* Sử dụng một `<div>` để bọc `<button>` để cập nhật biến `isCollapsed` và nội dụng của component, thông qua `props.children`.
* Xác định sự xuất hiện của nội dung, dựa trên `isCollapsed` và áp dụng các style CSS thích hợp cho mỗi đối tượng.
* Cuối cùng, cập nhật giá trị của thuộc tính `aria-expanded` dựa trên `isCollapsed` để cho component có thể truy cập được.

```jsx
function Collapse(props) {
  const [isCollapsed, setIsCollapsed] = React.useState(props.collapsed);

  const style = {
    collapsed: {
      display: 'none'
    },
    expanded: {
      display: 'block'
    },
    buttonStyle: {
      display: 'block',
      width: '100%'
    }
  };

  return (
    <div>
      <button style={style.buttonStyle} onClick={() => setIsCollapsed(!isCollapsed)}>
        {isCollapsed ? 'Show' : 'Hide'} content
      </button>
      <div
        className="collapse-content"
        style={isCollapsed ? style.collapsed : style.expanded}
        aria-expanded={isCollapsed}
      >
        {props.children}
      </div>
    </div>
  );
}
```

<details>
<summary>Ví dụ</summary>

```jsx
ReactDOM.render(
  <Collapse>
    <h1>This is a collapse</h1>
    <p>Hello world!</p>
  </Collapse>,
  document.getElementById('root')
);
```
</details>

<br>[⬆ Quay lại đầu trang](#table-of-contents)

### CountDown

Hiển thị đồng hồ đếm ngược in thông báo khi nó về không.

* Sử dụng object destructuring để xét giá trị mặc định prop `hours`, `minutes` và `seconds`.
* Sử dụng hook `React.useState()` tạo các biến `time`, `paused` và `over`, xét cho chúng các giá trị ban đầu lần lượt là `false` và `false`.
* Tạo hàm `tick`, để cập nhật giá trị của `time` dựa trên giá trị hiện tại (tức là giảm thời gian xuống một giây).
* Nếu `paused` hoặc `over` là `true`, `tick` sẽ quay lại ngay lập tức.
* Tạo hàm `reset`, để cập nhật các biến về trạng thái ban đầu.
* Sử dụng hook `React.useEffect()` để gọi hàm `tick` mỗi giây thông qua hàm `setInterval()` và sử dụng `clearInterval()` để clear giá trị khi component unmounted.
* Sử dụng một `<div>` bọc thẻ `<p>` để hiển thị trạng thái của biến `time`, cũng như hai `<button>` pause/unpause và restart.
* Nếu `over` là `true`, bộ hẹn giờ sẽ hiển thị một thông báo thay vì giá trị của `time`.

```jsx
function CountDown({ hours = 0, minutes = 0, seconds = 0 }) {
  const [paused, setPaused] = React.useState(false);
  const [over, setOver] = React.useState(false);
  const [time, setTime] = React.useState({
    hours: parseInt(hours),
    minutes: parseInt(minutes),
    seconds: parseInt(seconds)
  });

  const tick = () => {
    if (paused || over) return;
    if (time.hours == 0 && time.minutes == 0 && time.seconds == 0) setOver(true);
    else if (time.minutes == 0 && time.seconds == 0)
      setTime({
        hours: time.hours - 1,
        minutes: 59,
        seconds: 59
      });
    else if (time.seconds == 0)
      setTime({
        hours: time.hours,
        minutes: time.minutes - 1,
        seconds: 59
      });
    else
      setTime({
        hours: time.hours,
        minutes: time.minutes,
        seconds: time.seconds - 1
      });
  };

  const reset = () => {
    setTime({
      hours: parseInt(hours),
      minutes: parseInt(minutes),
      seconds: parseInt(seconds)
    });
    setPaused(false);
    setOver(false);
  };

  React.useEffect(() => {
    let timerID = setInterval(() => tick(), 1000);
    return () => clearInterval(timerID);
  }, [tick]);

  return (
    <div>
      <p>{`${time.hours.toString().padStart(2, '0')}:${time.minutes
        .toString()
        .padStart(2, '0')}:${time.seconds.toString().padStart(2, '0')}`}</p>
      <div>{over ? "Time's up!" : ''}</div>
      <button onClick={() => setPaused(!paused)}>{paused ? 'Resume' : 'Pause'}</button>
      <button onClick={() => reset()}>Restart</button>
    </div>
  );
}
```

<details>
<summary>Ví dụ</summary>

```jsx
ReactDOM.render(<CountDown hours="1" minutes="45" />, document.getElementById('root'));
```
</details>

<br>[⬆ Quay lại đầu trang](#table-of-contents)

### FileDrop

Hiển thị một component kéo và thả cho một file.

* Tạo một ref gọi là `dropRef` cho component.
* Sử dụng hook `React.useState()` để tạo biến `drag` và `filename`, với giá trị ban đầu lần lượt là `false` và `''`.
Biến `dragCounter` và `drag` được sử dụng để xác định một file có đang kéo hay không, còn `filename` để xác định tên file khi đã thả.
* Tạo các hàm `handleDrag`, `handleDragIn`, `handleDragOut` và `handleDrop` để xử lý chức năng kéo và thả, liên kết chúng với ngữ cảnh của component.
* Each of the methods will handle a specific event, the listeners for which are created and removed in the `React.useEffect()` hook and its attached `cleanup()` method.
* Mỗi phương thức sẽ xử lý một sự kiện cụ thể, tạo các sự kiện lắng nghe và xóa chúng trong hook `React.useEffect()` và hàm `cleanup()`.
* `handleDrag` ngăn trình duyệt mở file đã kéo, `handleDragIn` và `handleDragOut` xử lý file được kéo vào và thoát khỏi component, trong khi `handleDrop` xử lý file bị thả và chuyển nó sang `props.handleDrop`.
* Trả về một `<div>` với style phù hợp và sử dụng `drag` và `filename` để xác định tên file và style.
* Cuối cùng, liên kết `ref` của `<div>` đã tạo với `dropRef`.

```css
.filedrop {
  min-height: 120px;
  border: 3px solid #d3d3d3;
  text-align: center;
  font-size: 24px;
  padding: 32px;
  border-radius: 4px;
}

.filedrop.drag {
  border: 3px dashed #1e90ff;
}

.filedrop.ready {
  border: 3px solid #32cd32;
}
```

```jsx
function FileDrop(props) {
  const [drag, setDrag] = React.useState(false);
  const [filename, setFilename] = React.useState('');
  let dropRef = React.createRef();
  let dragCounter = 0;

  const handleDrag = e => {
    e.preventDefault();
    e.stopPropagation();
  };

  const handleDragIn = e => {
    e.preventDefault();
    e.stopPropagation();
    dragCounter++;
    if (e.dataTransfer.items && e.dataTransfer.items.length > 0) setDrag(true);
  };

  const handleDragOut = e => {
    e.preventDefault();
    e.stopPropagation();
    dragCounter--;
    if (dragCounter === 0) setDrag(false);
  };

  const handleDrop = e => {
    e.preventDefault();
    e.stopPropagation();
    setDrag(false);
    if (e.dataTransfer.files && e.dataTransfer.files.length > 0) {
      props.handleDrop(e.dataTransfer.files[0]);
      setFilename(e.dataTransfer.files[0].name);
      e.dataTransfer.clearData();
      dragCounter = 0;
    }
  };

  React.useEffect(() => {
    let div = dropRef.current;
    div.addEventListener('dragenter', handleDragIn);
    div.addEventListener('dragleave', handleDragOut);
    div.addEventListener('dragover', handleDrag);
    div.addEventListener('drop', handleDrop);
    return function cleanup() {
      div.removeEventListener('dragenter', handleDragIn);
      div.removeEventListener('dragleave', handleDragOut);
      div.removeEventListener('dragover', handleDrag);
      div.removeEventListener('drop', handleDrop);
    };
  });

  return (
    <div
      ref={dropRef}
      className={drag ? 'filedrop drag' : filename ? 'filedrop ready' : 'filedrop'}
    >
      {filename && !drag ? <div>{filename}</div> : <div>Drop files here!</div>}
    </div>
  );
}
```

<details>
<summary>Ví dụ</summary>

```jsx
ReactDOM.render(<FileDrop handleDrop={console.log} />, document.getElementById('root'));
```
</details>

<br>[⬆ Quay lại đầu trang](#table-of-contents)

### Mailto

Hiển thị một liên kết được format để gửi email.

* Lấy các giá trị component qua prop, sử dụng `email`, `subject` và `body` để tạo một thẻ `<a>` với thuộc tính `href` thích hợp.
* Hiển thị nội dung của nó bằng `props.children` .

```jsx
function Mailto({ email, subject, body, ...props }) {
  return (
    <a href={`mailto:${email}?subject=${subject || ''}&body=${body || ''}`}>{props.children}</a>
  );
}
```

<details>
<summary>Ví dụ</summary>

```jsx
ReactDOM.render(
  <Mailto email="foo@bar.baz" subject="Hello" body="Hello world!">
    Mail me!
  </Mailto>,
  document.getElementById('root')
);
```
</details>

<br>[⬆ Quay lại đầu trang](#table-of-contents)

### Modal

Hiển thị một component Modal, có thể điều khiển thông qua các sự kiện.
Để sử dụng component, import `Modal` một lần và hiển thị nó thông qua thuộc tính của `isVisible`.

* Sử dụng object destructuring để xét giá trị ban đầu cho component Modal.
* Xác định `keydownHandler`, một phương thức xử lý tất cả các sự kiện bàn phím, có thể được sử dụng theo nhu cầu của bạn để làm một hành động nào đó (ví dụ: đóng Modal khi nhấn <kbd>Esc</kbd>).
* Sử dụng hook `React.useEffect()` để thêm hoặc xóa sự kiện `keydown`, khi gọi hàm `keydownHandler`.
* Sử dụng prop `isVisible` để xác định Modal có được hiển thị hay không.
* Sử dụng CSS để style cho Modal.

```css
.modal {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right:0;
  width: 100%;
  z-index: 9999;  
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: rgba(0, 0, 0, 0.25);
  animation-name: appear;
  animation-duration: 300ms;
}

.modal-dialog{
  width: 100%;
  max-width: 550px;
  background: white;
  position: relative;
  margin: 0 20px;
  max-height: calc(100vh - 40px);
  text-align: left;
  display: flex;
  flex-direction: column;
  overflow:hidden;
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2),0 6px 20px 0 rgba(0,0,0,0.19);
  -webkit-animation-name: animatetop;
  -webkit-animation-duration: 0.4s;
  animation-name: slide-in;
  animation-duration: 0.5s;
}

.modal-header,.modal-footer{
  display: flex;
  align-items: center;
  padding: 1rem;
}
.modal-header{
  border-bottom: 1px solid #dbdbdb;
  justify-content: space-between;
}
.modal-footer{
  border-top: 1px solid #dbdbdb;
  justify-content: flex-end;
}
.modal-close{
  cursor: pointer;
  padding: 1rem;
  margin: -1rem -1rem -1rem auto;
}
.modal-body{
  overflow: auto;
}
.modal-content{
  padding: 1rem;
}

@keyframes appear {
  from {opacity: 0;}
  to {opacity: 1;}
}
@keyframes slide-in {
  from {transform: translateY(-150px);}
  to { transform: translateY(0);}
}
```

```jsx
function Modal({ isVisible = false, title, content, footer, onClose }){  
  React.useEffect(() => {
    document.addEventListener('keydown', keydownHandler);
    return () => document.removeEventListener('keydown', keydownHandler);
  });

  function keydownHandler({ key }) {
    switch (key) {
      case 'Escape':  onClose(); break;
      default:
    }
  }

  return !isVisible ? null : (
    <div className="modal" onClick={onClose}>
        <div className="modal-dialog"  onClick={e => e.stopPropagation()}>
        <div className="modal-header">
          <h3 className="modal-title">{title}</h3>
          <span className="modal-close" onClick={onClose}>&times;</span>
        </div>
        <div className="modal-body">
          <div className="modal-content">{ content }</div>
        </div>
        {footer && <div className="modal-footer">{footer}</div>}
      </div>
    </div>
  )
}
```

<details>
<summary>Ví dụ</summary>

```jsx
//Add the component to the render function
function App() {
  const [ isModal, setModal] = React.useState(false);

  return (
    <React.Fragment>
      <button onClick={()=> setModal(true)}>Click Here</button>
      <Modal
        isVisible={ isModal }
        title= "Modal Title"
        content = {<p>Add your content here</p>}
        footer = {<button>Cancel</button>}
        onClose ={()=> setModal(false)}
      />
    </React.Fragment>
  )
}

ReactDOM.render( <App/>, document.getElementById('root'));
```
</details>

<br>[⬆ Quay lại đầu trang](#table-of-contents)

### StarRating

Hiển thị một star rating component.

* Component `Star` sẽ hiển thị từng ngôi sao riêng lẻ với style phù hợp dựa vào trạng thái của parent component.
* Trong component `StarRating`, sử dụng hook `React.useState()` để xác định trạng thái của biến `rating` và `selection` với giá trị mặc định ban đầu là `props.rating` (hoặc `0` nếu như không tồn tại) và `0`.
* Tạo một hàm, `hoverOver`, để cập nhật giá trị `selected` và `rating`.
* Tạo một `<div>` để bọc những component `<Star>`, sử dụng `Array.prototype.map` để hiển thị 5 phần tử, được tạo bằng `Array.from`, và hàm `onMouseLeave` sẽ xét `selection` thành `0`, hàm `onClick` sẽ xét giá trị cho `rating` và hàm `onMouseOver` xét cho `selection` bằng giá trị thuộc tính của `star-id` của `event.target`.
* Cuối cùng, truyền các giá trị cho component `<Star>` (`starId` và `marked`).

```jsx
function Star({ marked, starId }) {
  return (
    <span star-id={starId} style={{ color: '#ff9933' }} role="button">
      {marked ? '\u2605' : '\u2606'}
    </span>
  );
}

function StarRating(props) {
  const [rating, setRating] = React.useState(typeof props.rating == 'number' ? props.rating : 0);
  const [selection, setSelection] = React.useState(0);
  const hoverOver = event => {
    let val = 0;
    if (event && event.target && event.target.getAttribute('star-id'))
      val = event.target.getAttribute('star-id');
    setSelection(val);
  };
  return (
    <div
      onMouseOut={() => hoverOver(null)}
      onClick={(event) => setRating(event.target.getAttribute('star-id') || rating)}
      onMouseOver={hoverOver}
    >
      {Array.from({ length: 5 }, (v, i) => (
        <Star
          starId={i + 1}
          key={`star_${i + 1} `}
          marked={selection ? selection >= i + 1 : rating >= i + 1}
        />
      ))}
    </div>
  );
}
```

<details>
<summary>Ví dụ</summary>

```jsx
ReactDOM.render(<StarRating />, document.getElementById('root'));
ReactDOM.render(<StarRating rating={2} />, document.getElementById('root'));
```
</details>

<br>[⬆ Quay lại đầu trang](#table-of-contents)

### Tabs

Hiển thị một tab menu và xem component.

* Component `TabItem`, sẽ hiển thị các giá trị cần thiết thông qua tên trong hàm `props.children`.
* Sử dụng hook `React.useState()` để tạo biến `bindIndex` có giá trị ban đầu bằng `props.defaultIndex`.
* Sử dụng `Array.prototype.map` để hiển thị các `tab-menu` và `tab-view`.
* Hàm `changeTab`, sẽ chạy khi onlcik vào `<button>` từ `tab-menu`.
* Hàm `changeTab` sẽ gọi lại, `onTabClick` và cập nhật `bindIndex`, từ đó thì hiển thị lại, và thay đổi `style` và `className` của item `tab-view` và button `tab-menu` theo `index` của chúng.

```css
.tab-menu > button {
  cursor: pointer;
  padding: 8px 16px;
  border: 0;
  border-bottom: 2px solid transparent;
  background: none;
}
.tab-menu > button.focus {
  border-bottom: 2px solid #007bef;
}
.tab-menu > button:hover {
  border-bottom: 2px solid #007bef;
}
```

```jsx
function TabItem(props) {
  return <div {...props} />;
}

function Tabs(props) {
  const [bindIndex, setBindIndex] = React.useState(props.defaultIndex);
  const changeTab = newIndex => {
    if (typeof props.onTabClick === 'function') props.onTabClick(newIndex);
    setBindIndex(newIndex);
  };
  const items = props.children.filter(item => item.type.name === 'TabItem');

  return (
    <div className="wrapper">
      <div className="tab-menu">
        {items.map(({ props: { index, label } }) => (
          <button onClick={() => changeTab(index)} className={bindIndex === index ? 'focus' : ''}>
            {label}
          </button>
        ))}
      </div>
      <div className="tab-view">
        {items.map(({ props }) => (
          <div
            {...props}
            className="tab-view_item"
            key={props.index}
            style={{ display: bindIndex === props.index ? 'block' : 'none' }}
          />
        ))}
      </div>
    </div>
  );
}
```

<details>
<summary>Ví dụ</summary>

```jsx
ReactDOM.render(
  <Tabs defaultIndex="1" onTabClick={console.log}>
    <TabItem label="A" index="1">
      Lorem ipsum
    </TabItem>
    <TabItem label="B" index="2">
      Dolor sit amet
    </TabItem>
  </Tabs>,
  document.getElementById('root')
);
```
</details>

<br>[⬆ Quay lại đầu trang](#table-of-contents)

### Ticker

Hiển thị một ticker component.

* Sử dụng `React.useState()` để khởi tạo biến `ticker` và giá trị mặc định là `0`.
* Hàm `tick` và `reset` sẽ tăng theo `timer` dựa trên `interval` và reset `interval` tương ứng.
* Trả về một `<div>` với hai phần tử `<button>`, mỗi phần tử gọi lần lượt là `tick` và` reset`.

```jsx
// https://overreacted.io/making-setinterval-declarative-with-react-hooks/
function useInterval(callback, delay) {
  const savedCallback = React.useRef();

  // Remember the latest callback.
  React.useEffect(() => {
    savedCallback.current = callback;
  }, [callback]);

  // Set up the interval.
  React.useEffect(() => {
    function tick() {
      savedCallback.current();
    }
    if (delay !== null) {
      let id = setInterval(tick, delay);
      return () => clearInterval(id);
    }
  }, [delay]);
}

function Ticker(props) {
  const [ticker, setTicker] = React.useState(0);
  const [isRunning, setIsRunning] = React.useState(false);
  useInterval(
    () => {
      if (ticker < props.times) setTicker(ticker + 1);
      else setIsRunning(false);
    },
    isRunning ? props.interval : null
  );

  return (
    <div>
      <span style={{ fontSize: 100 }}>{ticker}</span>
      <button onClick={() => setIsRunning(true)}>Tick!</button>
      <button
        onClick={() => {
          setIsRunning(false);
          setTicker(0);
        }}
      >
        Reset
      </button>
    </div>
  );
}
```

<details>
<summary>Ví dụ</summary>

```jsx
ReactDOM.render(<Ticker times={5} interval={1000} />, document.getElementById('root'));
```
</details>

<br>[⬆ Quay lại đầu trang](#table-of-contents)

### Toggle

Hiển thị một toggle component.

* Sử dụng `React.useState()` để khởi tạo biến `isToggleOn` và giá trị mặc định là `false`.
* Sử dụng `style` để tạo kiểu cho mỗi component khác nhau.
* Trả về một `<button>` để làm thay đổi giá trị `isToggledOn` khi gọi sự kiện `onClick` và dựa trên biến `isToggledOn` sẽ thay đổi giá trị CSS của `style` button.

```jsx
function Toggle(props) {
  const [isToggleOn, setIsToggleOn] = React.useState(false);
  style = {
    on: {
      backgroundColor: 'green'
    },
    off: {
      backgroundColor: 'grey'
    }
  };

  return (
    <button onClick={() => setIsToggleOn(!isToggleOn)} style={isToggleOn ? style.on : style.off}>
      {isToggleOn ? 'ON' : 'OFF'}
    </button>
  );
}
```

<details>
<summary>Ví dụ</summary>

```jsx
ReactDOM.render(<Toggle />, document.getElementById('root'));
```
</details>

<br>[⬆ Quay lại đầu trang](#table-of-contents)

### Tooltip

Hiển thị một tooltip component.

* Sử dụng `React.useState()` để khởi tạo biến `show` và giá trị mặc định là `false`.
* Trả về một thẻ `<div>` có chứa `<div>` sẽ là tooltip và prop `children` truyền cho component.
* Hàm `onMouseEnter` và `onMouseLeave` sẽ làm thay đổi giá trị của biến `show`.

```css
.tooltip {
  position: relative;
  background: rgba(0, 0, 0, 0.7);
  color: white;
  visibility: hidden;
  padding: 5px;
  border-radius: 5px;
}
.tooltip-arrow {
  position: absolute;
  top: 100%;
  left: 50%;
  border-width: 5px;
  border-style: solid;
  border-color: rgba(0, 0, 0, 0.7) transparent transparent;
}
```

```jsx
function Tooltip({ children, text, ...rest }) {
  const [show, setShow] = React.useState(false);

  return (
    <div>
      <div className="tooltip" style={show ? { visibility: 'visible' } : {}}>
        {text}
        <span className="tooltip-arrow" />
      </div>
      <div {...rest} onMouseEnter={() => setShow(true)} onMouseLeave={() => setShow(false)}>
        {children}
      </div>
    </div>
  );
}
```

<details>
<summary>Ví dụ</summary>

```jsx
ReactDOM.render(
  <Tooltip text="Simple tooltip">
    <button>Hover me!</button>
  </Tooltip>,
  document.getElementById('root')
);
```
</details>

<br>[⬆ Quay lại đầu trang](#table-of-contents)


---

_Đây là repository đang hoàn thiện. Nếu bạn muốn trở thành contribute, hãy PRs hoặc tạo issues nếu như bạn cần hỗ trợ !_


### Hãy cùng nhau xây dựng một cộng đồng phát triển !
