# either

## Install

```bash
$ yarn add @elsangedy/either
```

## Usage

```ts
class Failure = {}

class User = {}

type GetUserById = (id: number) => Promise<Either<Failure, User>>

const getUserById: GetUserById = async (id) => {
  if (id === 1) {
    return right(new User())
  }

  return left(new Failure())
}

const result = await getUserById(1)

isLeft(result) // falase
isRight(result) // true
getLeft(result) // undefined
getRight(result) // User

//-----

class State {}
class StateError {}
class StateSuccess {}

const state = result.fold<State>(
  (e) => {
    // handle left case
    return new StateError('user not found')
  },
  (user) => {
    // handle right case
    return new StateSuccess(user)
  }
)
```

## API

### TODO
