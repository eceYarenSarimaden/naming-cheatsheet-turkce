<p align="center">
  <a href="https://github.com/kettanaito/naming-cheatsheet">
    <img src="https://github.com/kettanaito/naming-cheatsheet/assets/46245749/468e4f15-f605-43b8-a551-d041353c7801" alt="Swift language" width="20%" />
    <img src="./naming-cheatsheet.png" alt="Naming cheatsheet" />
    <img src="https://github.com/kettanaito/naming-cheatsheet/assets/46245749/0198a889-c6ab-4385-9004-08210bbdbade" alt="Kotlin language" width="20%" />
  </a>
</p>

# Mobil Geliştiriciler için Adlandırma Kılavuzu

- [İngilizce dili](#i̇ngilizce-dili)
- [Adlandırma kuralları](#adlandırma-kuralları)
- [Kısa - Sezgisel - Açıklayıcı](#kısa---sezgisel---açıklayıcı)
- [Kısaltma Kullanmayın](#kısaltma-kullanmayın)
- [Bağlamın (Context) tekrarlanmasından kaçının](#bağlamın-context-tekrarlanmasından-kaçının)
- [Beklenen sonucu yansıtın](#beklenen-sonucu-yansıtın)
- [Fonksiyonları adlandırmak](#fonksiyonları-adlandırmak)
  - [A/HC/LC deseni](#ahclc-deseni)
    - [Eylemler (Actions)](#eylemler-actions)
    - [Bağlam (Context)](#bağlam-context)
    - [Ön ekler (Prefixes)](#ön-ekler-prefixes)
- [Tekil ve Çoğul (Singular and Plurals)](#tekil-ve-çoğul-singular-and-plurals)

---

Zaman zaman bir şeylere isim vermek zor olabilir. Bu döküman, bu süreci daha kolay hale getirmeyi amaçlıyor.

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

> Beğenseniz de beğenmeseniz de, İngilizce programlamada egemen bir dil olarak kabul edilmektedir: Tüm programlama dillerinin sözdizimi (syntax) İngilizce olarak yazılır, ayrıca sayısız dokümantasyon ve eğitim materyali de İngilizce olarak hazırlanmıştır. Kodunuzu İngilizce olarak yazarak, kodunuzun bütünlüğünü büyük ölçüde artırırsınız.

---

## Adlandırma kuralları

Yalnızca **bir** tane adlandırma kuralı seçin ve onunla devam edin. Bu, `camelCase`, `PascalCase`, `snake_case` veya başka bir şey olabilir, önemli olan tutarlı olmasıdır. Birçok programlama dilinin kendi isimlendirme kuralları vardır; bunları öğrenmek için kullandığınız programlama dilinin dokümanlarını kontrol edebilir veya GitHub'da popüler olan projeleri inceleyebilirsiniz.

### Swift

```swift
// Değişken tanımlamak için iki farklı kural kullanılmış, tutarlı değil.
let page_count = 5
let shouldUpdate = true

// Tutarlı
let pageCount = 5
let shouldUpdate = true
```

### Kotlin

```kt
// Değişken tanımlamak için iki farklı kural kullanılmış, tutarlı değil.
val page_count = 5
val shouldUpdate = true

// Tutarlı
val pageCount = 5
val shouldUpdate = true
```

> Ayrıca bir çok Android projesinde bir XML öğesine ID verirken `snake_case`
```xml
<TextView android:id="@+id/text_view_e_mail />
```
> ya da sabit değerleri tanımlarken `UPPER_SNAKE_CASE` kullanıldığını da görebilirsiniz.
```kotlin
const val DEFAULT_PAGE_SIZE = 20
```

---

## Kısa - Sezgisel - Açıklayıcı

Bir isim _kısa_, _sezgisel_ ve _açıklayıcı_ olmalıdır:

- **Kısa**. Bir ismin yazılması ve hatırlanması uzun sürmemelidir;
- **Sezgisel**. Bir isim mümkün olduğunca doğal bir şekilde okunmalı, günlük konuşma diline olabildiğince yakın olmalıdır;
- **Açıklayıcı**. Bir isim ne yaptığını/neye sahip olduğunu en etkili şekilde yansıtmalıdır.

### Swift

```swift
/* Kötü */
let a = 5 // "a" herhangi bir şeyi ifade edebilir.
let isPaginatable = a > 10 // "Paginatable" son derece doğal bir şekilde okunmuyor.
let shouldPaginatize = a > 10 // Kafanıza göre fiiller uydurmayın!

/* İyi */
let postCount = 5
let hasPagination = postCount > 10
let shouldPaginate = postCount > 10 // alternatif
```

### Kotlin

```kt
/* Kötü */
val a = 5 // "a" herhangi bir şeyi ifade edebilir.
val isPaginatable = a > 10 // "Paginatable" son derece doğal bir şekilde okunmuyor.
val shouldPaginatize = a > 10 // Kafanıza göre fiiller uydurmayın!

/* İyi */
val postCount = 5
val hasPagination = postCount > 10
val shouldPaginate = postCount > 10 // alternatif
```

---

## Kısaltma Kullanmayın

Kısaltmalar, kodun okunabilirliğini azaltmaktan başka bir işe yaramaz. Bazen kısa ve açıklayıcı bir isim bulmak zor olabilir, ancak bunu yapmamak için kısaltma kullanmak bir bahane değildir.

### Swift

```swift
/* Kötü */
let btnTpd = {}

/* İyi */
let buttonTapped = {}
```

### Kotlin

```kt
/* Kötü */
val onBtnClk = {}

/* İyi */
val onButtonClick = {}
```

---

## Bağlamın (Context) Tekrarlanmasından Kaçının

Bir isim tanımlandığı bağlamı tekrarlamamalıdır. Eğer bağlamı kaldırmak ismin okunabilirliğini azaltmıyorsa, isimden ilgili bağlamı kaldırın.

### Swift

```swift
class Product {
  let name: String
  var isFavorite: Bool
  
  init(name: String, isFavorite: Bool = false) {
    self.name = name
    self.isFavorite = isFavorite
  }

  // Fonksiyonun ismi, bağlamı (Product) tekrar eder.
  func func setProductAsFavorite() {
    isFavorite.toggle()
    if isFavorite {
      print("\(name) favorilere eklendi.")
    } else {
      print("\(name) favorilerden çıkarıldı.")
    }
  }

  // Çağrıldığı yerde `Product(name: "iPhone 14 Pro").setAsFavorite()` olarak güzelce okunur.
  func setAsFavorite() {
    isFavorite.toggle()
    if isFavorite {
      print("\(name) favorilere eklendi.")
    } else {
      print("\(name) favorilerden çıkarıldı.")
    }
  }
}
```

### Kotlin

```kotlin
class Product(val name: String, var isFavorite: Boolean = false) {

  // Fonksiyonun ismi, bağlamı (Product) tekrar eder.
  fun setProductAsFavorite() {
    isFavorite = !isFavorite
    if (isFavorite) {
      println("$name favorilere eklendi.")
    } else {
      println("$name favorilerden çıkarıldı.")
    }
  }

  // Çağrıldığı yerde `Product(name = "iPhone 14 Pro").setAsFavorite()` olarak güzelce okunur.
  fun setAsFavorite() {
    isFavorite = !isFavorite
    if (isFavorite) {
      println("$name favorilere eklendi.")
    } else {
      println("$name favorilerden çıkarıldı.")
    }
  }
}
```

---

## Beklenen Sonucu Yansıtın

Bir isim kendisinden beklenen sonucu yansıtmalıdır.

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
| `sendPushNotification` | `send`   | `Push`     | `Notification`    |                  |
| `handleSwipeGesture`   | `handle` | `Swipe`    | `Gesture`         |                  |

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

### `handle`

Bir eylemi yönetir. Genellikle bir callback fonksiyonlarını adlandırırken kullanılır.

#### Swift

```swift
func handleLinkTapped() {
    print("Tapped a link!")
}

link.addTarget(self, action: #selector(handleLinkTapped), for: .touchUpInside)
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

Geçerli bağlamın (context) bir özelliğini veya durumunu açıklar (genellikle `Boolean`).

#### Swift

```swift
struct Product {
  let isFavorite: Bool = false // özellik
}

if isFavorite {
    ...
}
```

#### Kotlin

```kt
data class Product(
  val isFavorite: Boolean = false // özellik
)

if (isFavorite) {
    ...
}
```

### `has`

Mevcut bağlamın (context) belirli bir değere veya duruma (genellikle `Boolean`) sahip olup olmadığını açıklar.

#### Swift

```swift
/* Kötü */
let isProductsExist = productsCount > 0
let areProductsPresent = productsCount > 0

/* İyi */
let hasProducts = productsCount > 0
```

#### Kotlin

```kt
/* Kötü */
val isProductsExist = productsCount > 0
val areProductsPresent = productsCount > 0

/* İyi */
val hasProducts = productsCount > 0
```

### `should`

Belirli bir eylemle birleştirilmiş pozitif bir koşullu ifadeyi (genellikle `Boolean`) yansıtır.

#### Swift

```swift
func shouldUpdateUrl(_ url: String, expectedUrl: String) -> Bool {
    return url != expectedUrl
}
```

#### Kotlin

```kt
fun shouldUpdateUrl(url: String, expectedUrl: String): Boolean {
    return url != expectedUrl
}
```

### `on`

`on` ön eki, onDataReceived (veri alındığında), onErrorOccurred (hata oluştuğunda) gibi bir olayın gerçekleştiği veya bir durumun olduğu zamanı veya noktayı belirten fonksiyonlarda kullanılan yaygın bir ön ektir.

#### Swift

```swift
func onLocationUpdated() {
    ...
}
```

#### Kotlin

```kt
fun onItemClick() {
  ...
}
```

### `min`/`max`

Minimum veya maksimum değeri temsil eder. Sınırları veya limitleri tanımlarken kullanılır.

#### Swift

```swift
// Belirli bir aralıkta rastgele bir sayı oluşturan fonksiyon.
func generateRandomNumberInRange(minNumber: Int, maxNumber: Int) -> Int {
    return Int.random(in: minNumber...maxNumber)
}
```

#### Kotlin

```kt
// Belirli bir aralıkta rastgele bir sayı oluşturan fonksiyon.
fun generateRandomNumberInRange(minNumber: Int, maxNumber: Int): Int {
    return (minNumber..maxNumber).random()
}
```

### `prev`/`next`

Mevcut bağlamda (context) bir değişkenin önceki veya sonraki durumunu belirtir. Durum (state) geçişlerini tanımlarken kullanılır.

#### Swift

```swift
var currentPage: Int = 0
var prevPage: Int?
var nextPage: Int?

func fetchPageData() {
    // Belirli bir sayfadan verileri almak için API çağrısı yapılır.
    // Örneğin, currentPage değişkeni kullanılarak API'ye istek gönderilir.
    
    // API'den veri alındıktan sonra prevPage ve nextPage değerleri güncellenir.
    
    // Örnek olarak, prevPage ve nextPage değerleri güncellendiğinde bir işlem yapılabilir.
    if let previousPage = prevPage {
        // Önceki sayfaya geçilebilir, örneğin geri butonu etkinleştirilebilir.
    } else {
        // Önceki sayfa yok, geri butonu devre dışı bırakılabilir.
    }
    
    if let nextPage = nextPage {
        // Sonraki sayfaya geçilebilir, örneğin ileri butonu etkinleştirilebilir.
    } else {
        // Sonraki sayfa yok, ileri butonu devre dışı bırakılabilir.
    }
    
    // Alınan verileri kullanıcı arayüzünde göstermek veya başka işlemler yapmak için kullanılabilir.
}

func goToPreviousPage() {
    if let previousPage = prevPage {
        currentPage = previousPage
        fetchPageData()
    }
}

func goToNextPage() {
    if let nextPage = nextPage {
        currentPage = nextPage
        fetchPageData()
    }
}
```

#### Kotlin

```kt
var currentPage: Int = 0
var prevPage: Int? = null
var nextPage: Int? = null

fun fetchPageData() {
    // Belirli bir sayfadan verileri almak için API çağrısı yapılır.
    // Örneğin, currentPage değişkeni kullanılarak API'ye istek gönderilir.
    
    // API'den veri alındıktan sonra prevPage ve nextPage değerleri güncellenir.
    
    // Örnek olarak, prevPage ve nextPage değerleri güncellendiğinde bir işlem yapılabilir.
    if (prevPage != null) {
        // Önceki sayfaya geçilebilir, örneğin geri butonu etkinleştirilebilir.
    } else {
        // Önceki sayfa yok, geri butonu devre dışı bırakılabilir.
    }
    
    if (nextPage != null) {
        // Sonraki sayfaya geçilebilir, örneğin ileri butonu etkinleştirilebilir.
    } else {
        // Sonraki sayfa yok, ileri butonu devre dışı bırakılabilir.
    }
    
    // Alınan verileri kullanıcı arayüzünde göstermek veya başka işlemler yapmak için kullanılabilir.
}

fun goToPreviousPage() {
    if (prevPage != null) {
        currentPage = prevPage!!
        fetchPageData()
    }
}

fun goToNextPage() {
    if (nextPage != null) {
        currentPage = nextPage!!
        fetchPageData()
    }
}
```

### `calculate`

Herhangi bir matematiksel işlemi hesaplamak için kullanılabilir.

#### Swift

```swift
func calculateSum(of numbers: [Int]) -> Int {
    return numbers.reduce(0, +)
}
```

#### Kotlin

```kt
fun calculateSum(numbers: List<Int>): Int {
    return numbers.reduce { acc, num -> acc + num }
}
```

### `show`

Herhangi bir View öğesini ekranda görünür yapmak için kullanılabilir.

#### Swift

```swift
func showActivityIndicator() {
  ...
}
```

#### Kotlin

```kt
fun showLoading() {
  ...
}
```

### `hide`

Herhangi bir View öğesini gizlemek için kullanılabilir.

#### Swift

```swift
extension UIViewController {
  func hideKeyboardWhenTappedAround() {
    let tap: UITapGestureRecognizer = UITapGestureRecognizer(target: self, action: #selector(UIViewController.dismissKeyboard))
    view.addGestureRecognizer(tap)
  }

  func dismissKeyboard() {
    view.endEditing(true)
  }
}
```

#### Kotlin

```kt
fun hideCancelButton() {
  binding.buttonCancel.visibility = View.GONE
}
```

---

## Tekil ve Çoğul (Singular and Plurals)

Bir ön ek gibi, değişken adları da tek bir değer veya birden çok değer taşımalarına bağlı olarak tekil veya çoğul yapılabilir.

#### Swift

```swift
/* Kötü */
let friends = "Bob"
let friend = ["Bob", "Tony", "Tanya"]
let friendList = ["Bob", "Tony", "Tanya"] // "friendList" yerine "friends" kullanın.

/* İyi */
let friend = "Bob"
let friends = ["Bob", "Tony", "Tanya"]
```

#### Kotlin

```kt
/* Kötü */
val friends = "Bob"
val friend = arrayOf("Bob", "Tony", "Tanya")
val friendList = arrayOf("Bob", "Tony", "Tanya") // "friendList" yerine "friends" kullanın.

/* İyi */
val friend = "Bob"
val friends = arrayOf("Bob", "Tony", "Tanya")
```
