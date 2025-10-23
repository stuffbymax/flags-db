# 🌍 Flags Database

A simple and open JSON database of world flags — including names, creation dates, designers, and image links.

📦 Data Source: [flags-db](https://github.com/stuffbymax/flags-db)  
📄 JSON URL: [Raw Data](https://raw.githubusercontent.com/stuffbymax/flags-db/refs/heads/main/contry-db.json)

---

## Usage

## java script Example

```js
// Fetch and display flags
fetch('https://raw.githubusercontent.com/stuffbymax/flags-db/refs/heads/main/contry-db.json')
  .then(response => response.json())
  .then(data => {
    console.log('Flags:', data.flags);
    data.flags.forEach(flag => console.log(flag.name, flag.image));
  })
  .catch(error => console.error('Error fetching flags:', error));
```

---

## React Example
```
import React, { useEffect, useState } from "react";

export default function FlagsList() {
  const [flags, setFlags] = useState([]);

  useEffect(() => {
    fetch("https://raw.githubusercontent.com/stuffbymax/flags-db/refs/heads/main/contry-db.json")
      .then(res => res.json())
      .then(data => setFlags(data.flags))
      .catch(console.error);
  }, []);

  return (
    <div className="p-6 grid gap-4 sm:grid-cols-2 md:grid-cols-3">
      {flags.map(flag => (
        <div key={flag.id} className="rounded-xl border p-4 shadow-sm">
          <img
            src={flag.image}
            alt={flag.name}
            className="w-full h-32 object-contain mb-3"
          />
          <h2 className="text-lg font-semibold">{flag.name}</h2>
          <p className="text-sm text-gray-500">{flag.description}</p>
        </div>
      ))}
    </div>
  );
}
```
---

## Python Example

```py
import requests

url = "https://raw.githubusercontent.com/stuffbymax/flags-db/refs/heads/main/contry-db.json"
response = requests.get(url)
data = response.json()

for flag in data["flags"]:
    print(flag["name"], "-", flag["image"])

```

---

| Field         | Type   | Description                      |
| ------------- | ------ | -------------------------------- |
| `id`          | string | Unique identifier                |
| `name`        | string | Country or flag name             |
| `createdAt`   | string | ISO date of adoption             |
| `designer`    | string | Designer name (if known)         |
| `image`       | string | Link to the flag image (SVG/PNG) |
| `description` | string | Short description of the entity  |
| `country`     | string | Related country name             |
