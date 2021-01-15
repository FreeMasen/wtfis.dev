# Quantile

## Industry Bullsh*t

In statistics, a _quantile_ is some bullsh*t about splitting
numbers into groups.

## Programming Bullsh*t

When collecting metrics, some assh*le is going to want to know
"What is the request latency at the 95th quantile?"... 

What the f*ck is a quantile...

That shit is just a median but with a % other than 50.

As a reminder a median is calculated by first sorting the numbers
then you pick the number that is exactly in the middle. So the median
of the numbers 1,2,3 is 2 and the 75th quantile is 3.

## Examples


<details>
<summary>Python</summary>

```python
quantile = 0.95 # 95%
latencies = [
    399, 353, 559, 755, 624, 972, 691, 203, 602, 447, 903, 497,
    579, 614, 811, 110, 718, 829, 989, 109, 620, 566, 943, 133,
    523, 669, 260, 294, 412, 743, 646, 522, 165, 670, 118, 803,
    652, 626, 719, 387, 161, 527, 984, 732, 601, 232, 746, 264,
    450, 930
]
count = len(latencies) # 50
index  = int(count * quantile) # 47
# [109, 110, 118, 133, 161, 165, 203, 232, 260, 264,
# 294, 353, 387, 399, 412, 447, 450, 497, 522, 523,
# 527, 559, 566, 579, 601, 602, 614, 620, 624, 626,
# 646, 652, 669, 670, 691, 718, 719, 732, 743, 746,
# 755, 803, 811, 829, 903, 930, 943, 972, 984, 989]
p95 = sorted(latencies)[index] # 972
```
</details>


<details>
<summary>
Rust
</summary>

```rust
fn main() {
    let quantile = 0.95;
    let mut latencies = vec![
        399, 353, 559, 755, 624, 972, 691, 203, 602, 447, 903, 497,
        579, 614, 811, 110, 718, 829, 989, 109, 620, 566, 943, 133,
        523, 669, 260, 294, 412, 743, 646, 522, 165, 670, 118, 803,
        652, 626, 719, 387, 161, 527, 984, 732, 601, 232, 746, 264,
        450, 930
    ];
    let index = (latencies.len() as f64 * quantile).floor() as usize; // 47
    // [109, 110, 118, 133, 161, 165, 203, 232, 260, 264,
    // 294, 353, 387, 399, 412, 447, 450, 497, 522, 523,
    // 527, 559, 566, 579, 601, 602, 614, 620, 624, 626,
    // 646, 652, 669, 670, 691, 718, 719, 732, 743, 746,
    // 755, 803, 811, 829, 903, 930, 943, 972, 984, 989]
    latencies.sort();
    
    println!("{}", latencies[index]); // 972
}

```

</details>


<details>
<summary>
Javascript
</summary>

```js
let quantile = 0.95; // 95%
let latencies = [
    399, 353, 559, 755, 624, 972, 691, 203, 602, 447, 903, 497,
    579, 614, 811, 110, 718, 829, 989, 109, 620, 566, 943, 133,
    523, 669, 260, 294, 412, 743, 646, 522, 165, 670, 118, 803,
    652, 626, 719, 387, 161, 527, 984, 732, 601, 232, 746, 264,
    450, 930
];
let index  = Math.floor(latencies.length * quantile); // 47
// [109, 110, 118, 133, 161, 165, 203, 232, 260, 264,
// 294, 353, 387, 399, 412, 447, 450, 497, 522, 523,
// 527, 559, 566, 579, 601, 602, 614, 620, 624, 626,
// 646, 652, 669, 670, 691, 718, 719, 732, 743, 746,
// 755, 803, 811, 829, 903, 930, 943, 972, 984, 989]
let p95 = sorted(latencies)[index] // 972
```

</details>
