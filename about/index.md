---
layout: page
title: About Ecology and Evolution Unit
tags: [about, Jekyll, theme, responsive]
comments: true
image:
  feature: oist2.jpg
---

The Ecology and Evolution research group is part of the <a href="http://www.oist.jp/" target="_blank">Okinawa Institute of Science and Technology Graduate University</a>.

<h3>Where Are Ecology and Evolution Unit Members From?</h3>
  <p>Geographic origins of Ecology and Evolution Unit members and visitors. Feel free to hover and zoom.</p>

<div id='convas'></div>
<div id="container"></div>
<script src="d3.css"></script>
<script src="http://d3js.org/topojson.v1.min.js"></script>
<script src="http://d3js.org/d3.v3.min.js"></script>
<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.11.1/jquery.min.js"></script>
<!-- <script src="https://dl.dropboxusercontent.com/u/5275622/lab%20map/zlib.js/bin/gunzip.min.js"></script>  -->
<script src="from github.com/imaya/zlib.js"></script>
<script>
d3.select(window).on("resize", throttle);

var zoom = d3.behavior.zoom()
    .scaleExtent([1, 9])
    .on("zoom", move);

var width = document.getElementById('container').offsetWidth;
var height = width / 2;

var topo,projection,path,svg,g;

var graticule = d3.geo.graticule();

var tooltip = d3.select("#container").append("div").attr("class", "tooltip hidden");

setup(width,height);

function setup(width,height){
  projection = d3.geo.mercator()
    .translate([(width/2), (height/2)])
    .center([5,0])
    .scale( width / 2 / Math.PI);

  path = d3.geo.path().projection(projection);

  svg = d3.select("#container").append("svg")
      .attr("width", width)
      .attr("height", height)
      .call(zoom)
      .on("click", click)
      .append("g");

  g = svg.append("g");

}

d3.json("json/world-topo-min.json", function(error, world) {

  var countries = topojson.feature(world, world.objects.countries).features;

  topo = countries;
  draw(topo);

});

function draw(topo) {

  svg.append("path")
     .datum(graticule)
     .attr("class", "graticule")
     .attr("d", path);

  g.append("path")
   .datum({type: "LineString", coordinates: [[-180, 0], [-90, 0], [0, 0], [90, 0], [180, 0]]})
   .attr("class", "equator")
   .attr("d", path);

  var country = g.selectAll(".country").data(topo);

  country.enter().insert("path")
      .attr("class", "country")
      .attr("d", path)
      .attr("id", function(d,i) { return d.id; })
      .attr("title", function(d,i) { return d.properties.name; })
      .style("fill", function(d, i) { return d.properties.color; });

  //Add data on people
  d3.json("json/members.json", function(err, people) {

    people.forEach(function(i){
      addpoint(i.longitude,i.latitude,  i.name , i.photo);
    });
  });

    //offsets for tooltips
  var offsetL = document.getElementById('container').offsetLeft+20;
  var offsetT = document.getElementById('container').offsetTop+10;


  country
    .on("mousemove", function(d,i) {

      var mouse = d3.mouse(svg.node()).map( function(d) { return parseInt(d); } );

      tooltip.classed("hidden", false)
             .attr("style", "left:"+(mouse[0]+offsetL)+"px;top:"+(mouse[1]+offsetT)+"px")
             .html(d.properties.name);

      })
      .on("mouseout",  function(d,i) {
        tooltip.classed("hidden", true);
      }); 



  //function to add points and text to the map (used in plotting capitals)
  function addpoint(lat,lon,text,photo) {

    var gpoint = g.append("g")
        .attr("class", "gpoint")
        .attr("title",text)
        .attr("photo",photo);

    var x = projection([lat,lon])[0];
    var y = projection([lat,lon])[1];

    gpoint.append("svg:circle")
          .attr("cx", x)
          .attr("cy", y)
          .attr("class","point")
          .attr("r", 5);

    gpoint.on("mouseover", onMouseOver)
          .on("mouseout", onMouseOut); 

    function onMouseOver () {

        var mouse = d3.mouse(svg.node()).map( function(d) { return parseInt(d); } );

        var display = "<center>" + this.getAttribute("title") + "</center>"+"<img src= " + this.getAttribute("photo") + " width=80 />";

        tooltip.classed("hidden", false)
               .attr("style", "left:"+(mouse[0]+offsetL)+"px;top:"+(mouse[1]+offsetT)+"px")
               .html(display);
               // .html(this.getAttribute("title"));

        d3.select(this).style("fill", "red");            
    };

    function onMouseOut () {

        tooltip.classed("hidden", true);
        d3.select(this).style("fill", "black");
    }

  }

}

function redraw() {
  width = document.getElementById('container').offsetWidth;
  height = width / 2;
  d3.select('svg').remove();
  setup(width,height);
  draw(topo);
}


function move() {

  var t = d3.event.translate;
  var s = d3.event.scale; 
  zscale = s;
  var h = height/4;


  t[0] = Math.min(
    (width/height)  * (s - 1), 
    Math.max( width * (1 - s), t[0] )
  );

  t[1] = Math.min(
    h * (s - 1) + h * s, 
    Math.max(height  * (1 - s) - h * s, t[1])
  );

  zoom.translate(t);
  g.attr("transform", "translate(" + t + ")scale(" + s + ")");

  //adjust the country hover stroke width based on zoom level
  d3.selectAll(".country").style("stroke-width", 1.5 / s);
  d3.selectAll(".point").attr("r", 5 / s);

}

var throttleTimer;
function throttle() {
  window.clearTimeout(throttleTimer);
    throttleTimer = window.setTimeout(function() {
      redraw();
    }, 200);
}

//geo translation on mouse click in map
function click() {
  var latlon = projection.invert(d3.mouse(this));
  console.log(latlon);
}
</script>


<!-- Load profiles -->
<script>
$(document).ready(function() { $('#people').load('profiles.html'); });
</script>
<div id="people"></div>
