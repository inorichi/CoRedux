class: center, middle

# CoRedux (1.0.0 release)

## Redux implementation based on Kotlin coroutines

.footnote[By _Yahor Berdnikau_: Android developer **@Freeletics**]

---

### Javascript Redux
``` javascript
function reducer(state = 0, action) {
  switch (action.type) {
    case 'INCREMENT':
      return state + 1
    case 'DECREMENT':
      return state - 1
    default:
      return state
  }
}

*let store = createStore(reducer)

store.subscribe(() => console.log(store.getState()))
store.dispatch({ type: 'INCREMENT' })
store.dispatch({ type: 'INCREMENT' })
store.dispatch({ type: 'DECREMENT' })
```

---

### Javascript Redux
``` javascript
*function reducer(state = 0, action) {
  switch (action.type) {
    case 'INCREMENT':
      return state + 1
    case 'DECREMENT':
      return state - 1
    default:
      return state
  }
}

let store = createStore(reducer)

store.subscribe(() => console.log(store.getState()))
store.dispatch({ type: 'INCREMENT' })
store.dispatch({ type: 'INCREMENT' })
store.dispatch({ type: 'DECREMENT' })
```

---

### Javascript Redux
``` javascript
function reducer(state = 0, action) {
  switch (action.type) {
    case 'INCREMENT':
      return state + 1
    case 'DECREMENT':
      return state - 1
    default:
      return state
  }
}

let store = createStore(reducer)

*store.subscribe(() => console.log(store.getState()))
store.dispatch({ type: 'INCREMENT' })
store.dispatch({ type: 'INCREMENT' })
store.dispatch({ type: 'DECREMENT' })
```

---

### Javascript Redux
``` javascript
function reducer(state = 0, action) {
  switch (action.type) {
    case 'INCREMENT':
      return state + 1
    case 'DECREMENT':
      return state - 1
    default:
      return state
  }
}

let store = createStore(reducer)

store.subscribe(() => console.log(store.getState()))
*store.dispatch({ type: 'INCREMENT' })
store.dispatch({ type: 'INCREMENT' })
store.dispatch({ type: 'DECREMENT' })
```

---

### Javascript Redux
``` javascript
function reducer(state = 0, action) {
  switch (action.type) {
*   case 'INCREMENT':
      return state + 1
    case 'DECREMENT':
      return state - 1
    default:
      return state
  }
}

let store = createStore(reducer)

store.subscribe(() => console.log(store.getState()))
*store.dispatch({ type: 'INCREMENT' })
store.dispatch({ type: 'INCREMENT' })
store.dispatch({ type: 'DECREMENT' })
```

---

### RxRedux

```kotlin
fun reducer(
    state: State,
    action: Action
): State = when (action) {
    Action.Increment -> state.copy(value + 1)
    Action.Decrement -> state.copy(value - 1)
    else -> state
}

val actions : PublishSubject<Action> = Publishsubject.create()
actions
*   .reduxStore(0, ::reducer)
    .subscribe( state -> println(state))
subject.onNext(Action.Increment)
subject.onNext(Action.Increment)
subject.onNext(Action.Decrement)
```

---

### RxRedux

```kotlin
*fun reducer(
    state: State,
    action: Action
): State = when (action) {
    Action.Increment -> state.copy(value + 1)
    Action.Decrement -> state.copy(value - 1)
    else -> state
}

val actions : PublishSubject<Action> = Publishsubject.create()
actions
    .reduxStore(0, ::reducer)
    .subscribe( state -> println(state))
subject.onNext(Action.Increment)
subject.onNext(Action.Increment)
subject.onNext(Action.Decrement)
```

---

### RxRedux

```kotlin
fun reducer(
    state: State,
    action: Action
): State = when (action) {
    Action.Increment -> state.copy(value + 1)
    Action.Decrement -> state.copy(value - 1)
    else -> state
}

val actions : PublishSubject<Action> = Publishsubject.create()
actions
    .reduxStore(0, ::reducer)
*   .subscribe( state -> println(state))
subject.onNext(Action.Increment)
subject.onNext(Action.Increment)
subject.onNext(Action.Decrement)
```

---

### RxRedux

```kotlin
fun reducer(
    state: State,
    action: Action
): State = when (action) {
    Action.Increment -> state.copy(value + 1)
    Action.Decrement -> state.copy(value - 1)
    else -> state
}

val actions : PublishSubject<Action> = Publishsubject.create()
actions
    .reduxStore(0, ::reducer)
    .subscribe( state -> println(state))
*subject.onNext(Action.Increment)
subject.onNext(Action.Increment)
subject.onNext(Action.Decrement)
```

---

### RxRedux side effect

``` kotlin
typealias SideEffect<STATE, ACTION> = (
  actions: Observable<ACTION>,
  state: StateAccessor<STATE>
) -> Observable<out ACTION>
```

---

### RxRedux side effect

``` kotlin
typealias SideEffect<STATE, ACTION> = (
* actions: Observable<ACTION>,
  state: StateAccessor<STATE>
) -> Observable<out ACTION>
```

---

### RxRedux side effect

``` kotlin
typealias SideEffect<STATE, ACTION> = (
  actions: Observable<ACTION>,
* state: StateAccessor<STATE>
) -> Observable<out ACTION>
```

---

### RxRedux side effect

``` kotlin
typealias SideEffect<STATE, ACTION> = (
  actions: Observable<ACTION>,
  state: StateAccessor<STATE>
) -> `Observable<out ACTION>`
```

---

### CoRedux

``` kotlin
fun reducer(
    state: State,
    action: Action
): State = when (action) {
    Action.Increment -> state.copy(value + 1)
    Action.Decrement -> state.copy(value - 1)
    else -> state
}

*val store = coroutineScope.createStore("Counter", 0, ::reducer)

store.subscribe { state -> println(state) }
store.dispatch(Action.Increment)
store.dispatch(Action.Increment)
store.dispatch(Action.Decrement)
```

---

### CoRedux

``` kotlin
*fun reducer(
    state: State,
    action: Action
): State = when (action) {
    Action.Increment -> state.copy(value + 1)
    Action.Decrement -> state.copy(value - 1)
    else -> state
}

val store = coroutineScope.createStore("Counter", 0, ::reducer)

store.subscribe { state -> println(state) }
store.dispatch(Action.Increment)
store.dispatch(Action.Increment)
store.dispatch(Action.Decrement)
```

---

### CoRedux

``` kotlin
fun reducer(
    state: State,
    action: Action
): State = when (action) {
    Action.Increment -> state.copy(value + 1)
    Action.Decrement -> state.copy(value - 1)
    else -> state
}

val store = coroutineScope.createStore("Counter", 0, ::reducer)

*store.subscribe { state -> println(state) }
store.dispatch(Action.Increment)
store.dispatch(Action.Increment)
store.dispatch(Action.Decrement)
```

---

### CoRedux

``` kotlin
fun reducer(
    state: State,
    action: Action
): State = when (action) {
    Action.Increment -> state.copy(value + 1)
    Action.Decrement -> state.copy(value - 1)
    else -> state
}

val store = coroutineScope.createStore("Counter", 0, ::reducer)

store.subscribe { state -> println(state) }
*store.dispatch(Action.Increment)
store.dispatch(Action.Increment)
store.dispatch(Action.Decrement)
```

---

### CoRedux

``` kotlin
fun reducer(
    state: State,
    action: Action
): State = when (action) {
*   Action.Increment -> state.copy(value + 1)
    Action.Decrement -> state.copy(value - 1)
    else -> state
}

val store = coroutineScope.createStore("Counter", 0, ::reducer)

store.subscribe { state -> println(state) }
*store.dispatch(Action.Increment)
store.dispatch(Action.Increment)
store.dispatch(Action.Decrement)
```

---

### Coredux side effect

```kotlin
interface SideEffect<STATE : Any, ACTION : Any> {
    val name: String

    fun CoroutineScope.start(
        input: ReceiveChannel<ACTION>,
        stateAccessor: StateAccessor<STATE>,
        output: SendChannel<ACTION>,
        logger: SideEffectLogger
    ) : Job
}

val sideEffect = object : SideEffect( .. )
val store = coroutineScope.createStore("some", initialState,
    listOf(sideEffect), ::reducer)
```

---

### Coredux side effect

```kotlin
interface SideEffect<STATE : Any, ACTION : Any> {
    val name: String

    fun CoroutineScope.start(
*       input: ReceiveChannel<ACTION>,
        stateAccessor: StateAccessor<STATE>,
        output: SendChannel<ACTION>,
        logger: SideEffectLogger
    ) : Job
}

val sideEffect = object : SideEffect( .. )
val store = coroutineScope.createStore("some", initialState,
    listOf(sideEffect), ::reducer)
```

---

### Coredux side effect

```kotlin
interface SideEffect<STATE : Any, ACTION : Any> {
    val name: String

    fun CoroutineScope.start(
        input: ReceiveChannel<ACTION>,
*       stateAccessor: StateAccessor<STATE>,
        output: SendChannel<ACTION>,
        logger: SideEffectLogger
    ) : Job
}

val sideEffect = object : SideEffect( .. )
val store = coroutineScope.createStore("some", initialState,
    listOf(sideEffect), ::reducer)
```

---

### Coredux side effect

```kotlin
interface SideEffect<STATE : Any, ACTION : Any> {
    val name: String

    fun CoroutineScope.start(
        input: ReceiveChannel<ACTION>,
        stateAccessor: StateAccessor<STATE>,
*       output: SendChannel<ACTION>,
        logger: SideEffectLogger
    ) : Job
}

val sideEffect = object : SideEffect( .. )
val store = coroutineScope.createStore("some", initialState,
    listOf(sideEffect), ::reducer)
```

---

### Coredux side effect

```kotlin
interface SideEffect<STATE : Any, ACTION : Any> {
    val name: String

    fun CoroutineScope.start(
        input: ReceiveChannel<ACTION>,
        stateAccessor: StateAccessor<STATE>,
        output: SendChannel<ACTION>,
        logger: SideEffectLogger
    ) : Job
}

*val sideEffect = object : SideEffect( .. )
val store = coroutineScope.createStore("some", initialState,
    `listOf(sideEffect)`, ::reducer)
```

---

### Coredux simple side effect

```kotlin
val sideEffect = SimpleSideEffect("test") {
    state, action, logger, `handler` ->
        when {
            action is Action.Increment &&
                state() == 10 -> `handler` {
                delay(10)
                `Action.Decrement`
            }
            else -> null
        }
}
```

---

### Coredux cancellable side effect

``` kotlin
val sideEffect = CancellableSideEffect("test") {
    state, action, logger, handler ->
       when {
           action is Action.Increment &&
               state() == 10 -> `handler` { name, output ->
               launch {
                   delay(10)
*                  output.send(Action.Decrement)
*                  output.send(Action.Decrement)
               }
           }
           else -> null
       }
}
```

---

### Coredux logging

``` kotlin
interface LogSink {
    val sink: SendChannel<LogEntry>
}
```

---

### Coredux logging

``` kotlin
data class LogEntry(
    val storeName: String,
    val time: Long,
    val event: LogEvent
)
```

---

### Coredux logging

``` kotlin
data class LogEntry(
    val storeName: String,
    val time: Long,
    val event: `LogEvent`
)
```

---

### Coredux logging

``` kotlin
sealed class LogEvent {
*   object StoreCreated : LogEvent()
*   object StoreFinished : LogEvent()
    sealed class ReducerEvent : LogEvent() {
        object Start : ReducerEvent()
        data class DispatchState(val state: Any)
            : ReducerEvent()
        data class InputAction(val action: Any, val state: Any)
            : ReducerEvent()
        data class Exception(val reason: Throwable)
            : ReducerEvent()
        data class DispatchToSideEffects(val action: Any)
            : ReducerEvent()
    }
    ...
}

```

---

### Coredux logging

``` kotlin
sealed class LogEvent {
    object StoreCreated : LogEvent()
    object StoreFinished : LogEvent()
*   sealed class ReducerEvent : LogEvent() {
        object `Start` : ReducerEvent()
        data class `DispatchState`(val state: Any)
            : ReducerEvent()
        data class `InputAction`(val action: Any, val state: Any)
            : ReducerEvent()
        data class `Exception`(val reason: Throwable)
            : ReducerEvent()
        data class `DispatchToSideEffects`(val action: Any)
            : ReducerEvent()
    }
    ...
}

```

---

### Coredux logging

```kotlin
sealed class LogEvent {
    ...
*   sealed class SideEffectEvent : LogEvent() {
        abstract val name: String
        data class `Start`(name: String) : SideEffectEvent()
        data class `InputAction`(name: String, val action: Any)
            : SideEffectEvent()
        data class `DispatchingToReducer`(
            name: String,
            val action: Any
        ) : SideEffectEvent()
        class `Custom`(name: String, val event: Any)
            : SideEffectEvent()
    }
}
```

---

# Links

- Redux - https://redux.js.org/
- RxRedux - https://github.com/freeletics/RxRedux
- CoRedux - https://github.com/freeletics/CoRedux
- Kotlin coroutines - https://github.com/Kotlin/kotlinx.coroutines
- Coroutines in practice by Roman Elizarov - https://www.youtube.com/watch?v=a3agLJQ6vt8
