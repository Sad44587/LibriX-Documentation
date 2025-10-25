# Math Functions Reference

## Trigonometry

### `Math.atan2(y, x)`
Returns the angle in radians between -π and π for coordinates `(x, y)`.  
- **Parameters**:
  - `y` (number) — y-coordinate
  - `x` (number) — x-coordinate  
- **Returns**: `number` — angle in radians  
- **Usage**: Useful for finding the angle of a vector from the origin.

### `Math.sign(x)`
Returns the sign of a number.  
- **Parameters**:
  - `x` (number)  
- **Returns**:
  - `1` if x > 0
  - `-1` if x < 0
  - `0` if x = 0  

---

## Clamping and Interpolation

### `Math.clamp(x, minVal, maxVal)`
Clamps a value between `minVal` and `maxVal`.  
- **Parameters**:  
  - `x` (number) — value to clamp  
  - `minVal` (number) — minimum allowed value  
  - `maxVal` (number) — maximum allowed value  
- **Returns**: `number` — clamped value

### `Math.clamp01(x)`
Clamps a value between `0` and `1`.  
- **Parameters**:  
  - `x` (number)  
- **Returns**: `number`  

### `Math.lerp(a, b, t)`
Linearly interpolates between `a` and `b` by `t` (0–1).  
- **Parameters**:
  - `a` (number) — start value  
  - `b` (number) — end value  
  - `t` (number) — interpolation factor  
- **Returns**: `number` — interpolated value  

### `Math.inverseLerp(a, b, value)`
Returns the interpolation factor `t` such that `lerp(a, b, t) = value`.  
- **Parameters**:
  - `a` (number) — start value  
  - `b` (number) — end value  
  - `value` (number) — value to find factor for  
- **Returns**: `number` — factor `t`  

### `Math.remap(value, inMin, inMax, outMin, outMax, doClamp)`
Remaps a value from one range to another. Optionally clamps the result.  
- **Parameters**:
  - `value` (number) — input value  
  - `inMin`, `inMax` (number) — input range  
  - `outMin`, `outMax` (number) — output range  
  - `doClamp` (boolean, optional) — clamp result to output range  
- **Returns**: `number`  
- **Alias**: `Math.map`

---

## Rounding and Fraction

### `Math.round(x, n)`
Rounds a number to `n` decimal places.  
- **Parameters**:
  - `x` (number)  
  - `n` (integer, optional, default 0) — decimal places  
- **Returns**: `number`  

### `Math.fract(x)`
Returns the fractional part of a number.  
- **Parameters**:
  - `x` (number)  
- **Returns**: `number`  

---

## Value Wrapping and Oscillation

### `Math.repeatf(value, length)`
Repeats a value in the range `[0, length)`.  
- **Parameters**:
  - `value` (number)  
  - `length` (number)  
- **Returns**: `number`  

### `Math.wrap(value, minVal, maxVal)`
Wraps a value to `[minVal, maxVal)`.  
- **Parameters**:
  - `value` (number)  
  - `minVal` (number)  
  - `maxVal` (number)  
- **Returns**: `number`  

### `Math.pingpong(value, length)`
Oscillates a value between `0` and `length`.  
- **Parameters**:
  - `value` (number)  
  - `length` (number)  
- **Returns**: `number`  

---

## Geometry and Distances

### `Math.hypot(a, b)`
Returns the hypotenuse (distance) in 2D.  
- **Parameters**: `a, b` (number, optional)  
- **Returns**: `number`  

### `Math.rsqrt(number)`
Returns the reciprocal of the square root (`1/√x`). Optimized for 3D calculations.  
- **Parameters**: `number` (number)  
- **Returns**: `number`  

### `Math.distance(a, b)`
Returns the distance between two numbers or vectors.  
- **Parameters**: `a, b` (number or Vector3)  
- **Returns**: `number`  

### `Math.distanceSquared(a, b)`
Returns the squared distance for comparisons (avoids sqrt).  
- **Parameters**: `a, b` (number or Vector3)  
- **Returns**: `number`  

---

## Smooth Interpolation

### `Math.smoothstep(edge0, edge1, x)`
Smooth interpolation between two edges.  

### `Math.smootherstep(edge0, edge1, x)`
Even smoother interpolation than `smoothstep`.  

---

## Easing Functions

- `Math.easeInQuad(t)`  
- `Math.easeOutQuad(t)`  
- `Math.easeInOutQuad(t)`  
- `Math.easeInCubic(t)`  
- `Math.easeOutCubic(t)`  
- `Math.easeInOutCubic(t)`  

---

## Random and Combinatorics

- `Math.randomRange(min, max, integer)` — random number  
- `Math.factorial(n)` — factorial  
- `Math.binomial(n, k)` — combinations  
- `Math.gcd(a, b)` — greatest common divisor  
- `Math.lcm(a, b)` — least common multiple  

---

## Angle Helpers

- `Math.normalizeAngleRad(theta)` — radians to [-π, π)  
- `Math.normalizeAngleDeg(d)` — degrees to [-180, 180]  

---

## Approximation

- `Math.approxEqual(a, b, tol)` — checks approximate equality  

---

## Linear Regression

- `Math.linearRegression(xs, ys)` — returns slope and intercept  

---

## Vector Helpers (Roblox)

- `Math.vectorLerp(a, b, t)` — Lerp between Vector3  
- `Math.vectorDistance(a, b)` — distance between Vector3  
