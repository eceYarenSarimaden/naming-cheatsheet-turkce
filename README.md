<p align="center">
  <a href="https://github.com/kettanaito/naming-cheatsheet">
    <img src="./naming-cheatsheet.png" alt="Naming cheatsheet" />
  </a>
</p>

# Mobil Geliştiriciler için Adlandırma Kılavuzu

- [İngilizce dili](#i̇ngilizce-dili)
- [Adlandırma kuralı](#adlandırma-kuralı)
- [Kısa - Sezgisel - Açıklayıcı](#kısa---sezgisel---açıklayıcı)
- [Kısaltmalardan kaçının](#kısaltmalardan-kaçının)
- [İçeriğin tekrarlanmasından kaçının](#i̇çeriğin-tekrarlanmasından-kaçının)
- [Beklenen sonucu yansıtın](#beklenen-sonucu-yansıtın)
- [Fonksiyonları adlandırmak](#fonksiyonları-adlandırmak)
  - [A/HC/LC deseni](#ahclc-deseni)
    - [Eylemler](#eylemler)
    - [Context](#context)
    - [Prefixes](#prefixes)
- [Singular and Plurals](#singular-and-plurals)

---

Bir şeylere isim vermek zordur. Bu döküman, bu süreci daha kolay hale getirmeyi amaçlıyor.

Bu öneriler herhangi bir programlama dilinde uygulanabilir olsa da, bunları pratikte göstermek için Swift ve Kotlin'i kullanacağım.

## İngilizce dili

Değişkenleri ve fonksiyonları adlandırırken İngilizce dilini kullanın.

### Swift

```swift
/* Kötü */
let primerNombre = "Gustavo"
let amigos = ["Kate", "John"]

/* İyi */
let firstName = "Gustavo"
let friends = ["Kate", "John"]
```

### Kotlin

```kt
/* Kötü */
val primerNombre = "Gustavo"
val amigos = listOf("Kate", "John")

/* İyi */
val firstName = "Gustavo"
val friends = listOf("Kate", "John")
```

> Beğenseniz de beğenmeseniz de, İngilizce programlamada egemen bir dil olarak kabul edilmektedir: Tüm programlama dillerinin sözdizimi(syntax) İngilizce olarak yazılır, ayrıca sayısız dokümantasyon ve eğitim materyali de İngilizce olarak hazırlanmıştır. Kodunuzu İngilizce olarak yazarak, kodunuzun bütünlüğünü büyük ölçüde artırırsınız.

## Adlandırma kuralı

Yalnızca **bir** tane isimlendirme kuralı seçin ve ona uyun. Bu, `camelCase`, `PascalCase`, `snake_case` veya başka bir şey olabilir, önemli olan tutarlı olmasıdır. Birçok programlama dilinin kendi isimlendirme kuralları vardır; kullandığınız programlama dilinin dokümanlarını kontrol edin veya GitHub'da popüler olan projeleri inceleyin!

### Swift

```swift
/* Kötü */
let page_count = 5
let shouldUpdate = true

/* İyi */
let pageCount = 5
let shouldUpdate = true

/* Ayrıca iyi */
let page_count = 5
let should_update = true
```

### Kotlin

```kt
/* Kötü */
val page_count = 5
val shouldUpdate = true

/* İyi */
val pageCount = 5
val shouldUpdate = true

/* Ayrıca iyi */
val page_count = 5
val should_update = true
```

## Kısa - Sezgisel - Açıklayıcı

Bir isim _kısa_, _sezgisel_ ve _açıklayıcı_ olmalıdır:

- **Kısa**. Bir ismin yazılması ve hatırlanması uzun sürmemelidir;
- **Sezgisel**. Bir isim mümkün olduğunca doğal bir şekilde okunmalı, günlük konuşma diline olabildiğince yakın olmalıdır;
- **Açıklayıcı**. Bir isim ne yaptığını/neye sahip olduğunu en etkili şekilde yansıtmalıdır.

### Swift

```swift
/* Kötü */
let a = 5 // "a" herhangi bir şeyi ifade edebilir
let isPaginatable = a > 10 // "Paginatable" son derece doğal bir şekilde okunmuyor
let shouldPaginatize = a > 10 // Uydurma fiiller eğlenceli olabilir!

/* İyi */
let postCount = 5
let hasPagination = postCount > 10
let shouldPaginate = postCount > 10 // alternatif olarak
```

### Kotlin

```kt
/* Kötü */
val a = 5 // "a" herhangi bir şeyi ifade edebilir
val isPaginatable = a > 10 // "Paginatable" son derece doğal bir şekilde okunmuyor
val shouldPaginatize = a > 10 // Uydurma fiiller eğlenceli olabilir!

/* İyi */
val postCount = 5
val hasPagination = postCount > 10
val shouldPaginate = postCount > 10 // alternatif olarak
```

## Kısaltmalardan Kaçının

Kısaltmaları **kullanmayın**. Kısaltmalar, kodun okunabilirliğini azaltmaktan başka bir işe yaramaz. Kısa ve açıklayıcı bir isim bulmak zor olabilir, ancak bunu yapmamak için kısaltma kullanmak bir bahane değildir.

### Swift

```swift
/* Kötü */
let onItmClk = {}

/* İyi */
let onItemClick = {}
```

### Kotlin

```kt
/* Kötü */
val onItmClk = {}

/* İyi */
val onItemClick = {}
```

## İçeriğin Tekrarlanmasından Kaçının

Bir isim tanımlandığı içeriği tekrarlamamalıdır. Eğer bu ismin okunabilirliğini azaltmıyorsa, her zaman isimden ilgili içeriği kaldırın.

### Swift

```swift
class MenuItem {
  /* Metot ismi içeriği ("MenuItem") tekrar eder */
  func handleMenuItemClick(event: Event) {
    . . .
  }
  
  /* `MenuItem().handleClick()` olarak güzel bir şekilde okunur */
  func handleClick(event: Event) {
    . . .
  }
}
```

### Kotlin

```kt
class MenuItem {  
  /* Metod ismi içeriği ("MenuItem") tekrar eder */
  fun handleMenuItemClick(event: Event) {
    . . .
  }

  /* `MenuItem().handleClick()` olarak güzel bir şekilde okunur */
  fun handleClick(event: Event) {
    . . .
  }
}
```

## Beklenen Sonucu Yansıtın

Bir isim beklenen sonucu yansıtmalıdır.

### Swift

```swift
/* Kötü */
let isDisabled = itemCount <= 3
button.isEnabled = !isDisabled

/* İyi */
let isEnabled = itemCount > 3
button.isEnabled = isEnabled
```

### Kotlin

```kt
/* Kötü */
val isDisabled = itemCount <= 3
binding.button.isEnabled = !isDisabled

/* İyi */
val isEnabled = itemCount > 3
binding.button.isEnabled = isEnabled
```

---

# Fonksiyonları adlandırmak

## A/HC/LC Deseni

Fonksiyonları adlandırırken izlenecek işe yarar bir desen vardır:

```
prefix? + action (A) + high context (HC) + low context? (LC)
```

Aşağıdaki tabloda bu desenin nasıl uygulanabileceğine bir göz atın.

| Name                   | Prefix   | Action (A) | High context (HC) | Low context (LC) |
| ---------------------- | -------- | ---------- | ----------------- | ---------------- |
| `getUser`              |          | `get`      | `User`            |                  |
| `getUserMessages`      |          | `get`      | `User`            | `Messages`       |
| `handleClickOutside`   |          | `handle`   | `Click`           | `Outside`        |
| `shouldDisplayMessage` | `should` | `Display`  | `Message`         |                  |

> **Not:** Bir değişkenin anlamını içeriğin sırası etkiler. Örneğin, `shouldUpdateComponent` ifadesi _sizin_ bir bileşeni güncellemek üzere olduğunuz anlamına gelirken, `shouldComponentUpdate` size _bileşenin kendisini_ güncelleyeceğini söyler ve yalnızca ne zaman güncellenmesi gerektiğini kontrol edersiniz. Başka bir deyişle, **`high context` bir değişkenin anlamını vurgular**.

---

## Eylemler

Fonksiyon adının fiil kısmı. Fonksiyonun _ne yaptığını_ açıklayan en önemli kısımdır.

### `get`

Verilere anında erişir (i.e. shorthand getter of internal data).

#### Swift

```swift
func getFruitCount() -> Int {
  return self.fruits.count
}
```

#### Kotlin

```kt
fun getFruitCount(): Int {
  return fruits.size
}
```

> Ayrıca bkz [compose](#compose).

Asenkron işlemler gerçekleştirirken de `get`'i kullanabilirsiniz:

#### Swift

```swift
func getUser(id: String) async throws -> User {
  let url = URL(string: "/api/user/\(id)")!
  let (data, _) = try await URLSession.shared.data(from: url)
  let user = try JSONDecoder().decode(User.self, from: data)
  return user
}
```

#### Kotlin

```kt
suspend fun getUser(id: String): User {
  val url = URL("/api/user/$id")
  val connection = url.openConnection() as HttpURLConnection
  val data = connection.inputStream.bufferedReader().use { it.readText() }
  val user = Gson().fromJson(data, User::class.java)
  return user
}
```

### `set`

Değeri `A` olan bir değişkenin değerini `B` olarak ayarlar.

#### Swift

```swift
var fruits = 0

func setFruits(_ nextFruits: Int) {
  fruits = nextFruits
}

setFruits(5)
print(fruits) // 5 yazar
```

#### Kotlin

```kt
var fruits = 0

fun setFruits(nextFruits: Int) {
  fruits = nextFruits
}

setFruits(5)
println(fruits) // 5 yazar
```

### `reset`

Bir değişkeni ilk değerine veya durumuna geri ayarlar.

#### Swift

```swift
let initialFruits = 5
var fruits = initialFruits

func setFruits(_ nextFruits: Int) {
  fruits = nextFruits
}

setFruits(10)
print(fruits) // 10

func resetFruits() {
  fruits = initialFruits
}

resetFruits()
print(fruits) // 5
```

#### Kotlin

```kt
val initialFruits = 5
var fruits = initialFruits

fun setFruits(nextFruits: Int) {
  fruits = nextFruits
}

setFruits(10)
println(fruits) // 10

fun resetFruits() {
  fruits = initialFruits
}

resetFruits()
println(fruits) // 5
```

### `remove`

Removes something _from_ somewhere.

For example, if you have a collection of selected filters on a search page, removing one of them from the collection is `removeFilter`, **not** `deleteFilter` (and this is how you would naturally say it in English as well):

```js
function removeFilter(filterName, filters) {
  return filters.filter((name) => name !== filterName)
}

const selectedFilters = ['price', 'availability', 'size']
removeFilter('price', selectedFilters)
```

> See also [delete](#delete).

### `delete`

Completely erases something from the realms of existence.

Imagine you are a content editor, and there is that notorious post you wish to get rid of. Once you clicked a shiny "Delete post" button, the CMS performed a `deletePost` action, **not** `removePost`.

```js
function deletePost(id) {
  return database.find({ id }).delete()
}
```

> See also [remove](#remove).

> **`remove` or `delete`?**
>
> When the difference between `remove` and `delete` is not so obvious to you, I'd suggest looking at their opposite actions - `add` and `create`.
> The key difference between `add` and `create` is that `add` needs a destination while `create` **requires no destination**. You `add` an item _to somewhere_, but you don't "`create` it _to somewhere_".
> Simply pair `remove` with `add` and `delete` with `create`.
>
> Explained in detail [here](https://github.com/kettanaito/naming-cheatsheet/issues/74#issue-1174942962).

### `compose`

Creates new data from the existing one. Mostly applicable to strings, objects, or functions.

```js
function composePageUrl(pageName, pageId) {
  return pageName.toLowerCase() + '-' + pageId
}
```

> See also [get](#get).

### `handle`

Handles an action. Often used when naming a callback method.

```js
function handleLinkClick() {
  console.log('Clicked a link!')
}

link.addEventListener('click', handleLinkClick)
```

---

## Context

A domain that a function operates on.

A function is often an action on _something_. It is important to state what its operable domain is, or at least an expected data type.

```js
/* A pure function operating with primitives */
function filter(list, predicate) {
  return list.filter(predicate)
}

/* Function operating exactly on posts */
function getRecentPosts(posts) {
  return filter(posts, (post) => post.date === Date.now())
}
```

> Some language-specific assumptions may allow omitting the context. For example, in JavaScript, it's common that `filter` operates on Array. Adding explicit `filterArray` would be unnecessary.

---

## Prefixes

Prefix enhances the meaning of a variable. It is rarely used in function names.

### `is`

Describes a characteristic or state of the current context (usually `boolean`).

```js
const color = 'blue'
const isBlue = color === 'blue' // characteristic
const isPresent = true // state

if (isBlue && isPresent) {
  console.log('Blue is present!')
}
```

### `has`

Describes whether the current context possesses a certain value or state (usually `boolean`).

```js
/* Bad */
const isProductsExist = productsCount > 0
const areProductsPresent = productsCount > 0

/* Good */
const hasProducts = productsCount > 0
```

### `should`

Reflects a positive conditional statement (usually `boolean`) coupled with a certain action.

```js
function shouldUpdateUrl(url, expectedUrl) {
  return url !== expectedUrl
}
```

### `min`/`max`

Represents a minimum or maximum value. Used when describing boundaries or limits.

```js
/**
 * Renders a random amount of posts within
 * the given min/max boundaries.
 */
function renderPosts(posts, minPosts, maxPosts) {
  return posts.slice(0, randomBetween(minPosts, maxPosts))
}
```

### `prev`/`next`

Indicate the previous or the next state of a variable in the current context. Used when describing state transitions.

```jsx
async function getPosts() {
  const prevPosts = this.state.posts

  const latestPosts = await fetch('...')
  const nextPosts = concat(prevPosts, latestPosts)

  this.setState({ posts: nextPosts })
}
```

## Singular and Plurals

Like a prefix, variable names can be made singular or plural depending on whether they hold a single value or multiple values.

```js
/* Bad */
const friends = 'Bob'
const friend = ['Bob', 'Tony', 'Tanya']

/* Good */
const friend = 'Bob'
const friends = ['Bob', 'Tony', 'Tanya']
```
