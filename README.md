# Spacetraders.io Javascript/Typescript SDK

## Install

`yarn add spacetraders-sdk`

or

`npm i spacetraders-sdk`

## Usage

The SDK will keep your username + token in memory. It's important that you save the token for a new user otherwise you'll lose access to that user.

```typescript
import { SpaceTraders } from 'spacetraders-sdk'

const spaceTraders = new SpaceTraders()

// Already existing user
spaceTraders.init('username', 'token')

// Claim a new user
const token = await spaceTraders.init('username')
```

### Basic rate-limiting

```typescript
/**
 * How many jobs can be running at the same time.
 */
maxConcurrent?: number
/**
 * How long to wait after launching a job before launching another one.
 */
minTime?: number

```

```typescript
import { SpaceTraders } from 'spacetraders-sdk'

const spaceTraders = new SpaceTraders({ maxConcurrent: 2, minTime: 500 })
```

## Methods

### [createFlightPlan](https://api.spacetraders.io/#api-flight_plans-NewFlightPlan)

Submit a new flight plan

```typescript
spaceTraders.createFlightPlan(shipId: string, destination: number): Promise<FlightPlanResponse>
```

### [getAccount](https://api.spacetraders.io/#api-users-GetInfo)

Get your info

```typescript
spaceTraders.getAccount(): Promise<AccountResponse>
```

### [getFlightPlan](https://api.spacetraders.io/#api-flight_plans-GetFlightPlan)

Get info on an existing flight plan

```typescript
spaceTraders.getFlightPlan(): Promise<FlightPlanResponse>
```

### [getMarketplace](https://api.spacetraders.io/#api-marketplace-marketplace)

Get info on a locations marketplace

```typescript
spaceTraders.getMarketplace(location: string): Promise<MarketplaceResponse>
```

### [getStatus](https://api.spacetraders.io/#api-game-status)

Use to determine whether the server is alive

```typescript
spaceTraders.getStatus(): Promise<StatusResponse>
```

### [listLocations](https://api.spacetraders.io/#api-locations-locations)

Get locations in a system

```typescript
spaceTraders.listLocations(system?: string, type?: string): Promise<LocationsResponse>
```

### [payBackLoan](https://api.spacetraders.io/#api-loans)

Payback your loan

```typescript
spaceTraders.payBackLoan(loanId: string): Promise<AccountResponse>
```

### [purchaseGood](https://api.spacetraders.io/#api-purchase_orders-NewPurchaseOrder)

Place a new purchase order

```typescript
spaceTraders.purchaseGood(shipId: string, good: string, quantity: number): Promise<PurchaseResponse>
```

### [purchaseShip](https://api.spacetraders.io/#api-ships-NewShip)

Buy a new ship

```typescript
spaceTraders.purchaseShip(location: string, type: string): Promise<AccountResponse>
```

### [sellGood](https://api.spacetraders.io/#api-sell_orders-NewSellOrder)

Place a new sell order

```typescript
spaceTraders.sellGood(shipId: string, good: string, quantity: number): Promise<PurchaseResponse>
```

### [takeOutLoan](https://api.spacetraders.io/#api-loans-NewLoan)

Request a new loan

```typescript
spaceTraders.takeOutLoan(type: LoanType): Promise<AccountResponse>
```

### [viewAvailableLoans](https://api.spacetraders.io/#api-loans-loans)

Get available loans

```typescript
spaceTraders.viewAvailableLoans(): Promise<AvailableLoanResponse>
```

### [viewAvailableShips](https://api.spacetraders.io/#api-ships-ships)

Get info on available ships

```typescript
spaceTraders.viewAvailableShips(): Promise<AvailableShipResponse>
```
