---
title: "Welcome to Jekyll!"
date: 2019-04-18T15:34:30-04:00
categories:
  - blog
tags:
  - Jekyll
  - update
---

You'll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

```ruby
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
```


D3.js Example
Below is a simple example of a D3.js bar chart embedded directly into this post.

<div id="d3-container" style="width: 500px; height: 300px;">
  <svg width="500" height="300"></svg>
</div>
<script src="https://d3js.org/d3.v7.min.js"></script>
<script>
  const data = [10, 20, 30, 40, 50];
  
  const svg = d3.select("svg"),
        margin = {top: 20, right: 30, bottom: 40, left: 40},
        width = +svg.attr("width") - margin.left - margin.right,
        height = +svg.attr("height") - margin.top - margin.bottom,
        g = svg.append("g").attr("transform", `translate(${margin.left},${margin.top})`);

  const x = d3.scaleBand().rangeRound([0, width]).padding(0.1).domain(data.map((d, i) => i)),
        y = d3.scaleLinear().rangeRound([height, 0]).domain([0, d3.max(data, d => d)]);

  g.append("g")
   .attr("class", "axis axis--x")
   .attr("transform", `translate(0,${height})`)
   .call(d3.axisBottom(x));

  g.append("g")
   .attr("class", "axis axis--y")
   .call(d3.axisLeft(y).ticks(10));

  g.selectAll(".bar")
   .data(data)
   .enter().append("rect")
   .attr("class", "bar")
   .attr("x", (d, i) => x(i))
   .attr("y", d => y(d))
   .attr("width", x.bandwidth())
   .attr("height", d => height - y(d));
</script>


First, let's create an interactive bar chart using Chart.js:

<div style="width: 500px; height: 300px;">
  <canvas id="chartjs-bar"></canvas>
</div>

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<script>
  const ctx = document.getElementById('chartjs-bar').getContext('2d');
  const chart = new Chart(ctx, {
      type: 'bar',
      data: {
          labels: ['Red', 'Blue', 'Yellow', 'Green', 'Purple', 'Orange'],
          datasets: [{
              label: '# of Votes',
              data: [12, 19, 3, 5, 2, 3],
              backgroundColor: [
                  'rgba(255, 99, 132, 0.2)',
                  'rgba(54, 162, 235, 0.2)',
                  'rgba(255, 206, 86, 0.2)',
                  'rgba(75, 192, 192, 0.2)',
                  'rgba(153, 102, 255, 0.2)',
                  'rgba(255, 159, 64, 0.2)'
              ],
              borderColor: [
                  'rgba(255, 99, 132, 1)',
                  'rgba(54, 162, 235, 1)',
                  'rgba(255, 206, 86, 1)',
                  'rgba(75, 192, 192, 1)',
                  'rgba(153, 102, 255, 1)',
                  'rgba(255, 159, 64, 1)'
              ],
              borderWidth: 1
          }]
      },
      options: {
          scales: {
              y: {
                  beginAtZero: true
              }
          }
      }
  });
</script>

### Animated P5.js Graph

Next, let's add an animated graph using P5.js. This example creates a simple animated sine wave:

<div id="p5-container" style="width: 500px; height: 300px;"></div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.4.0/p5.js"></script>
<script>
  function setup() {
    let canvas = createCanvas(500, 300);
    canvas.parent('p5-container');
  }

  function draw() {
    background(255);
    let x = width * 0.5;
    let y = height * 0.5;
    let amplitude = 50;
    let period = 100;
    let angle = frameCount * 0.05;
    let sineValue = amplitude * sin(angle * TWO_PI / period);

    fill(150, 50, 250);
    ellipse(x + sineValue, y, 50, 50);
  }
</script>

For more details on how to integrate JavaScript visualizations in your Jekyll posts, check out the [Jekyll docs][jekyll-docs].

[jekyll-docs]: https://jekyllrb.com/docs/home

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
