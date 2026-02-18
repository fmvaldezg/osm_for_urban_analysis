---
theme: seriph
background: /assets/cover.gif
title: Using OpenStreetMap for Urban Spatial Analysis
class: text-center
transition: slide-left
mdc: true
duration: 60min
controls: true
presenter: false      
remote: false         
selectable: false     
monaco: false
info: false
drawings:
  enabled: false
contextMenu: false
---

<div class="overlay"></div>

<div class="content-wrapper">

# Using OpenStreetMap 

<span class="text-3xl">for Urban Spatial Analysis</span>

<div @click="$slidev.nav.next" class="mt-12 py-1 text-xs" hover:bg="white op-10">
  Press Space for next page <carbon:arrow-right />
</div>

</div>

<img 
  src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/b0/Openstreetmap_logo.svg/1280px-Openstreetmap_logo.svg.png" 
  class="absolute"
  style="left: 700px; top: 320px; width:130px; background-color: rgba(255, 255, 255, 0); padding: 10px; border-radius: 8px;"
  alt="OSM logo"
/>

<img 
  src="/assets/librarylogo.png" 
  class="absolute"
  style="left: 70px; top: 300px; width:300px; background-color: rgba(255, 255, 255, 0); padding: 10px; border-radius: 8px;"
  alt="OSM logo"
/>

<div class="abs-br m-6 text-xl">
  <a href="https://openstreetmap.org" target="_blank" class="slidev-icon-btn">
    <carbon:earth-filled />
  </a>
  <a href="https://library.temple.edu/services/support-for-gis-mapping" target="_blank" class="slidev-icon-btn">
    <carbon:information-filled />
  </a>
</div>

<style>
.overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.4);
  z-index: 1;
  pointer-events: none;
}

.content-wrapper {
  position: relative;
  z-index: 2;
}

.abs-br {
  position: absolute !important;
  bottom: 0.5rem !important;
  right: 0.5rem !important;
  z-index: 10 !important;
}
</style>

---
transition: slide-up
---

# Workshop agenda

<div class="text-sm">

| Time   | Topic                           | Description |
|--------|---------------------------------|-------------|
| 2 min  | Welcome & Setup                 | Introductions, goals, software check |
| 8 min | Introduction to OpenStreetMap   | OSM data model, tagging |
| 10 min | Exploring the OSM Ecosystem     | Live demo of openstreetmap.org, contributions |
| 15 min | Querying OSM Data            | Hands-on: Overpass Turbo queries for study area |
| 15 min | Alternative Visualization Methods | Overpass-ultra styling|
| 5 min | Working with OSM Data in GIS    | QuickOSM |
| 5 min | Contributing to OSM             | Hands-on: Create account, use iD editor |

</div>

---
level: 2
---

# Learning objectives


<br>
<br>

- 📝 Understand the OSM **data model**, including `nodes`, `ways`, `relations`, and the tagging schema
- ⚙️ Write **OverpassQL queries** to extract targeted urban datasets (roads, buildings, amenities, land use)
- 🧑‍💻 Use **Overpass Turbo** and **Overpass-ultra** to download and script OSM data extraction workflows
- 🗺️ Import OSM data into **QGIS** for spatial analysis and visualization
- 🌎 Create an OSM account and contribute edits using the **iD web editor**
- 🔬 Identify **research applications** of OSM data 

<br>
<br>


<!--
You can have `style` tag in markdown to override the style for the current page.
Learn more: https://sli.dev/features/slide-scope-style
-->

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

<!--
Here is another comment.
-->


---
transition: slide-up
layout: image-right
image: /assets/intro.gif
---

# What is OpenStreetMap?
Is a free, open, and collaborative map of the world that is created and maintained by volunteers.

<img src="/assets/stats.png">

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---
transition: slide-up
layout: image-right
level: 2
image: /assets/comparisson3.png
backgroundSize: contain
---

# Why use OpenStreetMap?

- Free and Open
- Global Reach
- Local Knowledge
- Continuous Updates
- Agency
- Giving Back
  

<div class="absolute" style="right: 280px; top: 230px;">
  <span v-mark.circle.orange="1" class="invisible">Mark</span>
</div>

<div class="absolute" style="right: 280px; bottom: 20px;">
  <span v-mark.circle.red="2" class="invisible">Mark</span>
</div>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---
transition: slide-up
layout: two-cols
level: 2
---

# How OSM works?

<div v-click>

## The Elements
</div>

<div class="space-y-4 text-base">

<div v-click>
<div><img src="https://wiki.openstreetmap.org/w/images/thumb/7/76/Osm_element_node.svg/256px-Osm_element_node.svg.png" class="inline w-6 h-6 mr-2" /> <strong>Nodes</strong> are dots used to mark locations.</div></div>

<div v-click>
<div><img src="https://wiki.openstreetmap.org/w/images/thumb/e/ee/Osm_element_way.svg/256px-Osm_element_way.svg.png" class="inline w-6 h-6 mr-2" /> <strong>Ways</strong> are connected lines of nodes (roads, rivers.)</div></div>

<div v-click>
<div><img src="https://wiki.openstreetmap.org/w/images/thumb/3/38/Osm_element_closedway.svg/40px-Osm_element_closedway.svg.png" class="inline w-6 h-6 mr-2" /> <strong>Closed ways</strong> are ways that form a closed loop.</div></div>

<div v-click>
<div><img src="https://wiki.openstreetmap.org/w/images/thumb/e/e6/Osm_element_area.svg/256px-Osm_element_area.svg.png" class="inline w-6 h-6 mr-2" /> <strong>Areas</strong> are closed ways which are also filled. </div></div>

<div v-click>
<div><img src="https://wiki.openstreetmap.org/w/images/thumb/4/48/Osm_element_relation.svg/256px-Osm_element_relation.svg.png" class="inline w-6 h-6 mr-2" /> <strong>Relations</strong> create complex shapes or represent related but not physically connected elements.</div></div>

</div>


::right::

<div v-click>

## Tags System

<div class="bg-gray-50 p-4 rounded-lg mb-4 border-l-4 border-green-500">
<div class="flex items-center mb-2">
<img src="https://wiki.openstreetmap.org/w/images/thumb/0/0d/Mf_tag.svg/240px-Mf_tag.svg.png" class="w-6 h-6 mr-2" />
<div class="text-sm font-semibold text-gray-700">key=value pairs describing elements</div>
</div>
<div class="font-mono text-green-600">amenity=library</div>
<div class="font-mono text-green-600">name=Charles Library</div>
</div>
</div>

<div v-click>

**Examples:**

<div class="space-y-2 text-sm">

- **Parking lot:** <code class="bg-gray-100 px-2 py-1 rounded">amenity=parking</code>

- **Building:** <code class="bg-gray-100 px-2 py-1 rounded">building=yes</code>

- **Residential road:** <code class="bg-gray-100 px-2 py-1 rounded">highway=residential</code>

- **McDonald's:** <code class="bg-gray-100 px-2 py-1 rounded text-xs">amenity=fast_food, brand=McDonald's, name=McDonald's</code>

</div>
</div>



<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}

h2 {
  color: #148c6e;
  border-bottom: 2px solid #e5e7eb;
  padding-bottom: 0.5rem;
  margin-bottom: 1rem;
}

.bg-gray-50 {
  background-color: #f9fafb;
}

code {
  font-size: 0.85em;
}
</style>

---
layout: image
level: 2
image: /assets/tags.png
--- 

---
layout: section
--- 

# Demo 1
Interacting with OpenStreetMap

<style>
.slidev-layout {
  background-image: url('/assets/demo1.gif');
  background-size: contain;
  background-position: center;
  background-repeat: no-repeat;
}

h1 {
  background-color: rgba(255, 255, 255, 0.5);
  color: #146b8c;
  padding: 1rem 2rem;
  border-radius: 12px;
  margin-bottom: 1.5rem;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
  backdrop-filter: blur(4px);
  font-weight: bold;
}

.slidev-layout p {
  background-color: rgba(255, 255, 255, 0.85);
  padding: 0.75rem 1.5rem;
  border-radius: 8px;
  margin: 0 auto;
  max-width: fit-content;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.15);
  backdrop-filter: blur(2px);
  font-size: 2rem;
}
</style>

---
layout: section
---

# Hands on:
OverpassQL queries



<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}

p {
  font-size: 1.7rem;
}
</style>

---
layout: default
level: 2
---

# [What is OverpassQL?](https://wiki.openstreetmap.org/wiki/Overpass_API/Overpass_QL)
OverpassQL is a procedural, imperative query language that lets you search the OSM database and get back exactly the features you want.

The code is divided into **statements**, each ending with a semicolon `;`. 

Statements execute sequentially, and each one changes the process's "execution state" — mainly by writing results into **sets**.
```ts {all|1|2|3}
[out:json][timeout:25];
node[amenity=drinking_water](39.88,-75.27,40.05,-75.02);
out;
```

<div class="relative min-h-48">

<div v-click="[1,2]" class="absolute top-0 left-0 w-full">

#### Line 1: Settings

<div class="bg-gray-50 p-4 rounded-lg mb-4 border-l-4 border-green-200">
<div class="flex items-center mb-2">
<div class="text-xs font-semibold text-gray-700">[name:value]</div>
</div>
<div class="font-mono text-green-600">[out:json]</div> Sets the output format
<div class="font-mono text-green-600">[timeout:25]</div> gives the server 25 seconds to respond
</div>

</div>

<div v-click="[2,3]" class="absolute top-0 left-0 w-full">

#### Line 2: Query

<div class="bg-gray-50 p-4 rounded-lg mb-4 border-l-4 border-green-200">
<div class="font-mono text-green-600">node</div> Requests point features
<div class="font-mono text-green-600">[amenity=drinking_water]</div> only return nodes with this **tag**
<div class="font-mono text-green-600">(39.95,-75.17,39.96,-75.16)</div> bounding box (south, west, north, east)
</div>

</div>

<div v-click="3" class="absolute top-0 left-0 w-full">

#### Line 3: Output

<div class="bg-gray-50 p-4 rounded-lg mb-4 border-l-4 border-green-200">
<div class="font-mono text-green-600">out;</div> Prints the results
<div> It can be <code>ids</code>, <code>skel</code>, <code>body</code>, <code>tags</code> or <code>meta</code>.</div>
</div>

</div>

</div>

---
layout: image-right
level: 2
image: /assets/query1.gif
backgroundSize: contain
---

# Lets run the first query

```ts
[out:json][timeout:25];
node[amenity=hospital](39.88,-75.27,40.05,-75.02);
out;
```
<v-clicks>

1. Copy the query
2. Got to [https://overpass-turbo.eu/](https://overpass-turbo.eu/)
3. Search and zoom in to Philadelphia, PA
4. Paste the query on the text area on the left
5. Click the run button <img src="/assets/run.png" width="50px">
</v-clicks>

---
layout: image-right
level: 2
image: /assets/query2.gif
backgroundSize: contain
clicks: 6
---

# Wait! 
Where are all the hospitals in Philly?

<div v-click="[1,3]">
```ts {all|all|2}
[out:json][timeout:25];
node[amenity=hospital](39.88,-75.27,40.05,-75.02);
out;
```

</div>

<div v-click="[2,3]">we only query <code>nodes</code> from the data set</div>

<div v-click="3">
```ts {all|all|2|3|all}
[out:json][timeout:25];
nwr[amenity=hospital](39.88,-75.27,40.05,-75.02);
out center;
```
<div v-click="[3,5]">we can replace <code>node</code> with <code>nwr</code> to query all types</div>

<div v-click="[5,6]">we have to add <code>center</code> to the <code>out;</code> statement to get a point on every element</div>

<div v-click="6">Re-run the query
<img src="/assets/run.png" width="50px">
</div>

</div>

---
layout: iframe
url: https://overpass-turbo.eu/s/2kI3
backgroundSize: contain
--- 

---
layout: default
level: 2
---

# Summing up
The anatomy of a query


```ts {all|1|2|3}
[out:json][timeout:25];
nwr[amenity=hospital](39.88,-75.27,40.05,-75.02);
out center;
```

<div class="relative min-h-48">

<div v-click="[1,2]" class="absolute top-0 left-0 w-full">

#### Line 1: Settings

<div class="bg-gray-50 p-4 rounded-lg mb-4 border-l-4 border-green-200">
<div class="font-mono text-green-600">[out:json]</div> Output format
<div class="font-mono text-green-600">[timeout:25]</div> server response time
<br>
<br>
<div class="font-times text-blue-700">Learn more about the settings <a target="_blank" href="https://wiki.openstreetmap.org/wiki/Overpass_API/Overpass_QL#Settings">here</a></div>

</div>

</div>

<div v-click="[2,3]" class="absolute top-0 left-0 w-full">

#### Line 2: Query statement

<div class="bg-gray-50 p-4 rounded-lg mb-4 border-l-4 border-green-200">
<div class="font-mono text-green-600"><code>node</code>or<code>way</code>or<code>nwr</code></div> type requested
<div class="font-mono text-green-600">[amenity=hospital]</div> tag requested
<div class="font-mono text-green-600">(39.95,-75.17,39.96,-75.16)</div> bounding box (south, west, north, east)
<br>
<br>
<div class="font-times text-blue-700">Learn more about tags <a target="_blank" href="https://wiki.openstreetmap.org/wiki/Map_features">here</a></div>
</div>

</div>

<div v-click="3" class="absolute top-0 left-0 w-full">

#### Line 3: Output

<div class="bg-gray-50 p-4 rounded-lg mb-4 border-l-4 border-green-200">
<div class="font-mono text-green-600">out center;</div> Prints the results
<br>
<br>
<div class="font-times text-blue-700">Learn more about results <a target="_blank" href="https://wiki.openstreetmap.org/wiki/Overpass_API/Overpass_QL#out">here</a></div>
</div>
</div>
</div>

---
layout: image-right
level: 2
image: /assets/query3.gif
backgroundSize: contain
clicks: 3
---

# Try it out!
Create a new query using a different tag.

<div class="relative min-h-48">

<div v-click="[1,2]">
```ts {2}
[out:json][timeout:25];
nwr[internet_access=wlan](39.88,-75.27,40.05,-75.02);
out center;
```
</div>

<div v-click="[1,2]">all places that have internet access wlan</div>

<div v-click="[2,3]">
```ts {2}
[out:json][timeout:25];
nwr[leisure=park](39.88,-75.27,40.05,-75.02);
out center;
```
</div>

<div v-click="[2,3]">all the parks</div>

<div v-click="3">
```ts {2}
[out:json][timeout:25];
nwr[railway=station](39.88,-75.27,40.05,-75.02);
out center;
```
</div>

<div v-click="3">all railway stations</div>

</div>

---
layout: image-right
level: 2
image: /assets/query4.gif
backgroundSize: contain
clicks: 3
---

# Combine tags
You can combine multiple tags in a single statement. They will work as an AND connector.

<div class="relative min-h-48">

<div v-click="[1,2]">
```ts {2}
[out:json][timeout:25];
nwr["internet_access"="wlan"]["internet_access:fee"="no"](39.88,-75.27,40.05,-75.02);
out center;
```
</div>

<div v-click="[1,2]">all places that have internet access wlan</div>
<div v-click="[1,2]">AND are free to use</div>

<div v-click="[2,3]">
```ts {2}
[out:json][timeout:25];
nwr["leisure"="park"]["dog"](39.88,-75.27,40.05,-75.02);
out center;
```
</div>

<div v-click="[2,3]">all the parks</div>
<div v-click="[2,3]">that include a <code>dog</code> tag</div>

<div v-click="3">
```ts {2}
[out:json][timeout:25];
nwr["railway"="station"]["subway"="yes"](39.88,-75.27,40.05,-75.02);
out center;
```
</div>

<div v-click="3">all railway stations</div>
<div v-click="3">from the subway system</div>

</div>

---
transition: slide-up
layout: default
level: 2
---

# Tag Filtering with Brackets
<div class="text-base mb-4">Tags are filtered using brackets. Here are the main patterns:</div>

<div class="grid grid-cols-1 gap-3 text-xs">

<div class="bg-blue-50 p-3 rounded-lg border-l-4 border-blue-400">
<div class="font-semibold text-blue-800 mb-2 text-sm">Basic Patterns</div>
<div class="space-y-1 font-mono">
<div><span class="text-green-600">node[amenity=restaurant];</span> <span class="text-gray-600 font-sans">// Exact match</span></div>
<div><span class="text-green-600">node[name];</span> <span class="text-gray-600 font-sans">// Key exists</span></div>
<div><span class="text-green-600">node[!name];</span> <span class="text-gray-600 font-sans">// Key does NOT exist</span></div>
<div><span class="text-green-600">node[amenity!=restaurant];</span> <span class="text-gray-600 font-sans">// Not equal</span></div>
</div>
</div>

<div class="bg-purple-50 p-3 rounded-lg border-l-4 border-purple-400">
<div class="font-semibold text-purple-800 mb-2 text-sm">Regular Expressions</div>
<div class="space-y-1 font-mono">
<div><span class="text-green-600">node[name~"^Starbucks"];</span> <span class="text-gray-600 font-sans">// Regex match</span></div>
<div><span class="text-green-600">node[name~"starbucks",i];</span> <span class="text-gray-600 font-sans">// Case insensitive</span></div>
<div><span class="text-green-600">node[~"addr:.*"~".*Philly.*"];</span> <span class="text-gray-600 font-sans">// Key AND value</span></div>
</div>
</div>

<div class="bg-green-50 p-3 rounded-lg border-l-4 border-green-400">
<div class="font-semibold text-green-800 mb-2 text-sm">Multiple Conditions (AND)</div>
<div class="font-mono mb-1">
<span class="text-green-600">node[amenity=restaurant][cuisine=mexican];</span>
</div>
<div class="text-gray-700 text-xs">Finds restaurants AND Mexican cuisine</div>
</div>

</div>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---
transition: slide-up
layout: default
level: 2
---

# Spatial Filters (Where to Search)

<div class="grid grid-cols-1 gap-3 text-xs">

<div class="bg-blue-50 p-3 rounded-lg border-l-3 border-blue-500">
<div class="flex items-center mb-2">
<div class="bg-blue-500 text-white px-2 py-1 rounded-full text-xs font-semibold mr-2">1</div>
<div class="font-semibold text-blue-800 text-sm">Bounding Box</div>
</div>
<div class="text-gray-700 mb-2">Four coordinates directly after the type:</div>
<div class="bg-gray-800 p-2 rounded font-mono text-green-400 text-xs">
node[amenity=cafe](39.94,-75.18,39.96,-75.16);
</div>
</div>

<div class="bg-green-50 p-3 rounded-lg border-l-3 border-green-500">
<div class="flex items-center mb-2">
<div class="bg-green-500 text-white px-2 py-1 rounded-full text-xs font-semibold mr-2">2</div>
<div class="font-semibold text-green-800 text-sm">Named Area</div>
</div>
<div class="text-gray-700 mb-2">Search by area name:</div>
<div class="bg-gray-800 p-2 rounded font-mono text-green-400 text-xs space-y-0.5">
<div>area[name="Philadelphia"]->.searchArea;</div>
<div>node[amenity=cafe](area.searchArea);</div>
</div>
<div class="text-xs text-gray-600 mt-1 italic">
Line 1 finds Philadelphia → stores in searchArea. Line 2 queries cafes within that area.
</div>
</div>

<div class="bg-purple-50 p-3 rounded-lg border-l-3 border-purple-500">
<div class="flex items-center mb-2">
<div class="bg-purple-500 text-white px-2 py-1 rounded-full text-xs font-semibold mr-2">3</div>
<div class="font-semibold text-purple-800 text-sm">Proximity (Around)</div>
</div>
<div class="text-gray-700 mb-2">Find features within radius (meters) of others:</div>
<div class="bg-gray-800 p-2 rounded font-mono text-green-400 text-xs space-y-0.5">
<div>node[amenity=hospital](area.searchArea);</div>
<div>node[amenity=pharmacy](around:500);</div>
</div>
<div class="text-xs text-gray-600 mt-1 italic">Finds pharmacies within 500m of hospitals</div>
</div>

</div>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---
layout: image-right
level: 2
image: /assets/query5.png
backgroundSize: contain
---

# Lets try something out
Find pharmacies within 1km from hospitals

```ts {all|2|5|8|all}
[out:json][timeout:25];
area[name="Philadelphia"]->.a;

// Find all hospitals
nwr["amenity"="hospital"](area.a)->.hospitals;

// Find pharmacies within 1km of those hospitals
nwr["amenity"="pharmacy"](around.hospitals:1000)->.nearby_pharmacies;

// Output just the pharmacies
.nearby_pharmacies out center;
```
<v-clicks>

1. Copy the query
2. Got to [https://overpass-turbo.eu/](https://overpass-turbo.eu/)
3. Search and zoom in to Philadelphia, PA
4. Paste the query on the text area on the left
5. Click the run button <img src="/assets/run.png" width="50px">
</v-clicks>

---
layout: image-right
level: 2
image: /assets/query6.png
backgroundSize: contain
---

# Lets try something out
Change the area `name`

```ts {2}
[out:json][timeout:25];
area[name="Camden"]->.a;

// Find all hospitals
nwr["amenity"="hospital"](area.a)->.hospitals;

// Find pharmacies within 1km of those hospitals
nwr["amenity"="pharmacy"](around.hospitals:1000)->.nearby_pharmacies;

// Output just the pharmacies
.nearby_pharmacies out center;
```

---
layout: image-right
level: 2
image: /assets/query7.png
backgroundSize: contain
---

# Once again
New area, new elements, new distance threshold

```ts {all|2|5|8|all}
[out:json][timeout:25];
area[name="North Philadelphia"]->.a;

// Find all railway stations
nwr["railway"="station"](area.a)->.stations;

// Find parks within 200m of those stations
nwr["leisure"="park"](around.stations:200)->.nearby_parks;

// Output just the pharmacies
.nearby_parks out center;
```

---
layout: image-right
level: 2
image: /assets/query8.png
backgroundSize: contain
---

# Share and Export
You can share and export the results in multple ways:

1. Share as a link
2. Export the data as: `geojson` `GPX` `KML` `raw`
3. Export as an image
4. Download/copy the query


---
layout: section
---

# More styling options:
Use Overpass Ultra

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}

p {
  font-size: 1.7rem;
}
</style>

---
layout: image-right
level: 2
image: /assets/query9.gif
backgroundSize: contain
---

# Overpass Ultra query

```yml
---
server: https://overpass-api.de/api/interpreter
style:
  layers:
    - type: heatmap
      paint:
        heatmap-opacity: 0.5
        heatmap-intensity: 1
        heatmap-radius: 5
  extends: https://api.protomaps.com/styles/v5/grayscale/en.json?key=f8eceeaad6896c92
options:
  zoom: 11
  center: [-75.1293, 39.9822]
---
[bbox:{{bbox}}];
nwr['leisure'="swimming_pool"];
out center;
```

<div text-sm>
<v-clicks>

1. Go to [https://overpass-ultra.us/](https://overpass-ultra.us/)
2. Create a query (or paste one you already created in turbo)
3. Pick a different basemap style
4. Add more styling using the YAML frontmatter
</v-clicks>
</div>

---
layout: iframe
url: https://overpass-ultra.us/#map&m=11.06/39.9822/-75.1293&q=LQhQGcFMCcDcYFwAIAWAXNAHcCD0uB7eaTAQ3HGFMwEsA6AE0l2ptxoDs0ZNpJvoENAE8ANpASgkSUaWEwcU6UmBIRmCakik0AW2pLlSMpzSSjRlNr3VgBMgGMaI5AAY6AVkMWrO-ZmBTSA5wZ2FkAEZvS2t-YGhSBhoAVxwkL2lIAA9uDgY09CwcfFY6XgI0An9wOgcq3HARcXBcWA9cAHME4XAHUnFcYLoAK3ACDgB+AGtIYQBeADMADkgHSG1EgDYlgE5Nhx2AJlB7NBpxxWkALwIqyKjpNa5EJABtYAB2DzoIw52AZgANEh-js6DslodDgBdUAgYCgV4AIyRBCyCAA3hiUWiAL646EAblAHAA7tBXgBycQ0cDJPiUuYAInApJoul0nA6AH1MLdREyiSdkmgkE8BISgA
backgroundSize: contain
--- 

---
level: 2
---

# Styling on Ultra
Step-by-step

````md magic-move {lines: true}
```js
//Step 1: add an Overpass Query
[bbox:{{bbox}}];
nwr['leisure'="swimming_pool"];
out center;
```

```js {1-4}
//Step 2: add a YAML front matter
---

---
[bbox:{{bbox}}];
nwr['leisure'="swimming_pool"];
out center;
```

``js {3|4-5|6-9|10|*}
//Step 3: add a specific style
---
style:
  layers:
    - type: heatmap
      paint:
        heatmap-opacity: 0.5
        heatmap-intensity: 1
        heatmap-radius: 5
  extends: https://api.protomaps.com/styles/v5/grayscale/en.json?key=f8eceeaad6896c92
---
[bbox:{{bbox}}];
nwr['leisure'="swimming_pool"];
out center;
```

```js {1,11|1,12|1,13|*}
//Step 4: add a center and a zoom
---
style:
  layers:
    - type: heatmap
      paint:
        heatmap-opacity: 0.5
        heatmap-intensity: 1
        heatmap-radius: 5
  extends: https://api.protomaps.com/styles/v5/grayscale/en.json?key=f8eceeaad6896c92
options:
  zoom: 11
  center: [-75.1293, 39.9822]
---
[bbox:{{bbox}}];
nwr['leisure'="swimming_pool"];
out center;
```
````

---
layout: image
transition: slide-up
image: /assets/workshoppromo.png
--- 

--- 
layout: end
---

Contact us at:\
felipe.valdez@temple.edu \
<br>
Visit our guides:\
https://guides.temple.edu/gis-mapping

<style>
.slidev-layout.end {
  background: linear-gradient(135deg, rgb(164, 30, 53) 0%, rgb(149, 56, 71) 100%);
}
</style>