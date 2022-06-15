# 2. Motoko backend
The backend functions are located in the `src/persistent_storage/main.mo` Motoko file. The backend stores the counter value, and has functions to get, increment and reset the counter value. Furthermore the backend insures the counter value persists upgrades of the dapp.

## 2.1. Counter variable
The current counter value is stored as a number in the actor.

```javascript
actor {
    stable var counter : Nat = 0;
}
```

## 2.2. increment()
The `increment()` function increments the counter variable.

```javascript
public func increment() : async Nat {
    counter += 1;
    return counter;
};
```

The function is returning the incremented counter variable.

## 2.3. get()
The `get()` function returns the current counter value.

```javascript
public query func get() : async Nat {
    return counter;
};
```

## 2.4. reset()
The `reset()` function resets the counter value to 0 and returns the value.

```javascript
public func reset() : async Nat {
    counter := 0;
    return counter;
};
```

## 2.5. Candid interface
The Candid interface is automatically created, and it has a convenient UI, which provides an easy, user-friendly way to test the backend. 