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
- [Bağlamın (Context) tekrarlanmasından kaçının](#bağlam-context-tekrarlanmasından-kaçının)
- [Beklenen sonucu yansıtın](#beklenen-sonucu-yansıtın)
- [Fonksiyonları adlandırmak](#fonksiyonları-adlandırmak)
  - [A/HC/LC deseni](#ahclc-deseni)
    - [Eylemler](#eylemler-actions)
    - [Bağlam (Context)](#bağlam-context)
    - [Ön ekler (Prefixes)](#ön-ekler-prefixes)
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

## Bağlam (Context) Tekrarlanmasından Kaçının

Bir isim tanımlandığı bağlamı tekrarlamamalıdır. Eğer bağlamı kaldırmak ismin okunabilirliğini azaltmıyorsa, her zaman isimden ilgili bağlamı kaldırın.

### Swift

```swift
class MenuItem {
  /* Metot ismi, bağlamı ("MenuItem") tekrar eder */
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
  /* Metod ismi, bağlamı ("MenuItem") tekrar eder */
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

Fonksiyonları adlandırırken kullanılabilecek işe yarar bir desen vardır:

```
ön ek? + eylem (A) + önemli bağlam (HC) + yardımcı bağlam? (LC)
```

```
prefix? + action (A) + high context (HC) + low context? (LC)
```

Aşağıdaki tabloda bu desenin nasıl uygulanabileceğine bir göz atın.

| İsim (Name)            | Ön ek (Prefix) | Eylem (A - Action) | Önemli bağlam (HC - High context) | Yardımcı bağlam (LC - Low context) |
| ---------------------- | -------- | ---------- | ----------------- | ---------------- |
| `getUser`              |          | `get`      | `User`            |                  |
| `getUserMessages`      |          | `get`      | `User`            | `Messages`       |
| `handleClickOutside`   |          | `handle`   | `Click`           | `Outside`        |
| `shouldDisplayMessage` | `should` | `Display`  | `Message`         |                  |

> **Not:** Bir değişkenin anlamını bağlamın sırası etkiler. Örneğin, `shouldUpdateComponent` ifadesi _sizin_ bir bileşeni güncellemek üzere olduğunuz anlamına gelirken, `shouldComponentUpdate` size _bileşenin kendisini_ güncelleyeceğini söyler ve yalnızca ne zaman güncellenmesi gerektiğini kontrol edersiniz. Başka bir deyişle, **`high context` bir değişkenin anlamını vurgular**.

---

## Eylemler (Actions)

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

_Bir yerden_ bir şey çıkarır.

Örneğin, bir arama sayfasında seçili filtrelerden oluşan bir koleksiyonunuz varsa, bunlardan birini koleksiyondan kaldırmak, `deleteFilter` değil, `removeFilter`'dır (ve bunu doğal olarak İngilizce'de de böyle söylersiniz):

#### Swift

```swift
func removeFilter(_ filterName: String, _ filters: [String]) -> [String] {
  return filters.filter { $0 != filterName }
}

var selectedFilters = ["price", "availability", "size"]
selectedFilters = removeFilter("price", selectedFilters)
```

#### Kotlin

```kt
fun removeFilter(filterName: String, filters: MutableList<String>): List<String> {
  return filters.filter { it != filterName }
}

var selectedFilters = mutableListOf("price", "availability", "size")
selectedFilters = removeFilter("price", selectedFilters)
```

> Ayrıca bkz [delete](#delete).

### `delete`

Bir şeyi varlık aleminden tamamen siler.

Bir içerik editörü olduğunuzu ve kurtulmak istediğiniz kötü şöhretli bir gönderi olduğunu hayal edin. Parlak bir "Gönderiyi sil" butonuna tıkladığınızda, CMS bir `deletePost` eylemi gerçekleştirir, `removePost` **değil**.

#### Swift

```swift
func deletePost(id: Int) {
    database.find { $0.id == id }?.delete()
}
```

#### Kotlin

```kt
fun deletePost(id: Int) {
    database.find { it.id == id }?.delete()
}
```

> Ayrıca bkz [remove](#remove).

> **`remove` ve `delete` arasındaki fark ne?**
>
> `remove` ve `delete` arasındaki fark sizin için çok açık değilse, önerim bunların zıt eylemlerine, yani `add` ve `create`'e bakmanızdır.
> `add` ve `create` arasındaki temel fark, `add`'in bir hedefe ihtiyaç duyması, ancak `create`'in **hiçbir hedef gerektirmemesidir**. Bir öğeyi _bir yere_ eklersiniz (add), ancak onu _bir yere_ "oluşturmazsınız (create)".
> Basitçe `remove`'u `add` ile, `delete`'i `create` ile eşleştirin.
>
> [Burada](https://github.com/kettanaito/naming-cheatsheet/issues/74#issue-1174942962) ayrıntılı olarak açıklanmıştır.

### `compose`

Mevcut olan verilerden yeni veriler oluşturur. Çoğunlukla String'lere, nesnelere veya fonksiyonlara uygulanabilir.

#### Swift

```swift
func composePageUrl(pageName: String, pageId: String) -> String {
    return pageName.lowercased() + "-" + pageId
}
```

#### Kotlin

```kt
fun composePageUrl(pageName: String, pageId: String): String {
    return pageName.toLowerCase() + "-" + pageId
}
```

> Ayrıca bkz [get](#get).

### `handle`

Bir eylemi yönetir. Genellikle bir callback fonksiyonlarını adlandırırken kullanılır.

#### Swift

```swift
func handleLinkClick() {
    print("Clicked a link!")
}

link.addTarget(self, action: #selector(handleLinkClick), for: .touchUpInside)
```

#### Kotlin

```kt
fun handleLinkClick() {
    println("Clicked a link!")
}

link.setOnClickListener { handleLinkClick() }
```

---

## Bağlam (Context)

Bir fonksiyonun üzerinde çalıştığı etki alanını temsil eder.

Bir fonksiyon genellikle _bir şey_ üzerindeki bir eylemdir. Fonksiyonun etki alanının ne olduğunu ya da en azından beklenen veri türünü belirtmek önemlidir.

#### Swift

```swift
// Primitif/İlkel tiplerle çalışan sade bir fonksiyon
func filter<T>(_ list: [T], _ predicate: (T) -> Bool) -> [T] {
    return list.filter(predicate)
}

// Tam olarak gönderiler üzerinde işlem yapan bir fonksiyon
func getRecentPosts(_ posts: [Post]) -> [Post] {
    let currentDate = Date()
    return filter(posts) { $0.date == currentDate }
}
```

#### Kotlin

```kt
// Primitif/İlkel tiplerle çalışan sade bir fonksiyon
fun <T> filter(list: List<T>, predicate: (T) -> Boolean): List<T> {
    return list.filter(predicate)
}

// Tam olarak gönderiler üzerinde işlem yapan bir fonksiyon
fun getRecentPosts(posts: List<Post>): List<Post> {
    val currentDate = Date()
    return filter(posts) { it.date == currentDate }
}
```

> Dile özgü bazı varsayımlar, bağlamı (context) atlamayı mümkün kılabilir. Örneğin, JavaScript'te filtreleme işleminin bir diziye (array) yapılması yaygın bir durumdur. Bu yüzden `filter` yerine `filterArray` yazmak gereksiz olacaktır.

---

## Ön ekler (Prefixes)

Ön ek, bir değişkenin anlamını güçlendirir. Genellikle değişken isimlerinde kulllanılır, fonksiyon isimlerindeyse nadiren kullanılır.

### `is`

Geçerli bağlamın (context) bir özelliğini veya durumunu açıklar (genellikle `boolean`).

#### Swift

```swift
let color = "blue"
let isBlue = color == "blue" // özellik
let isPresent = true // durum

if isBlue && isPresent {
    print("Mavi mevcut!")
}
```

#### Kotlin

```kt
val color = "blue"
val isBlue = color == "blue" // özellik
val isPresent = true // durum

if (isBlue && isPresent) {
    println("Mavi mevcut!")
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
