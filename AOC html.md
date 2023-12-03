# This is a description of the html format used on the site Advent of code

The interesting stuff is inside the `<main>` element.
The two parts are in `<article>` elements.
A finished part is followed by a `<p>` containing your answer.

## Not logged in

```html
<article class="day-desc">
    ...
</article>
<p>To play, please identify yourself via one of these services:</p>
```

## New day

```html
<article class="day-desc">
    <h2>--- Day X: ... ---</h2>
    <p>...</p>
    <pre><code>...
...
</code></pre>
    <p>...</p>
    <ul>
        <li>... <code>...</code> ...</li>
    </ul>
    <p>...</p>
</article>
<p>To begin, <a href="https://adventofcode.com/2022/day/8/input" target="_blank">get your puzzle input</a>.</p>
<form method="post" action="https://adventofcode.com/2022/day/8/answer">
    <input type="hidden" name="level" value="1">
    <p>Answer: <input type="text" name="answer" autocomplete="off"> <input type="submit" value="[Submit]"></p>
</form>
```

## Partially completed day

```html
<article class="day-desc">
    <h2>--- Day X: ... ---</h2>
    ...
</article>
<p>Your puzzle answer was <code>1667443</code>.</p>
<p class="day-success">The first half of this puzzle is complete! It provides one gold star: *</p>
<article class="day-desc">
    <h2 id="part2">--- Part Two ---</h2>
    ...
</article>
<form method="post" action="https://adventofcode.com/2022/day/7/answer">
    <input type="hidden" name="level" value="2">
    <p>Answer: <input type="text" name="answer" autocomplete="off"> <input type="submit" value="[Submit]"></p>
</form>
<p>Although it hasn't changed, you can still <a href="https://adventofcode.com/2022/day/7/input" target="_blank">get your puzzle input</a>.</p>
```

## Fully completed day

```html
<article class="day-desc">
    <h2>--- Day X: ... ---</h2>
    ...
</article>
<p>Your puzzle answer was <code>xxx</code>.</p>
<p class="day-success">The first half of this puzzle is complete! It provides one gold star: *</p>
<article class="day-desc">
    <h2 id="part2">--- Part Two ---</h2>
    ...
</article>
<p>Your puzzle answer was <code>xxx</code>.</p>
<p class="day-success">Both parts of this puzzle are complete! They provide two gold stars: **</p>
<p>At this point, you should <a href="https://adventofcode.com/2023">return to your Advent calendar</a> and try another puzzle.</p>
<p>If you still want to see it, you can <a href="https://adventofcode.com/2023/day/2/input" target="_blank">get your puzzle input</a>.</p>
```
