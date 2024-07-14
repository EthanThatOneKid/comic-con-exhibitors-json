# comic-con-exhibitors-json

List of San Diego Comic-Con exhibitors in JSON format.

## Data

Get the exhibitors data from the following list of JSON files:

- [2024 exhibitors](2024.json)

## Method

**1\.** Visit <https://www.comic-con.org/cc/things-to-do/exhibit-hall/exhibitors/> website.

**2\.** Open the browser console.

**3\.** Run the following script:

```js
function scrapeTableData(tableId) {
  const table = document.getElementById(tableId);
  if (!table) {
    return console.error("Table not found!");
  }

  const tableData = [];
  const rows = table.querySelectorAll("tbody tr");

  for (const row of rows) {
    const companyCell = row.querySelector("td:nth-child(2) a");
    const locationCell = row.querySelector("td:nth-child(3) a");

    if (companyCell && locationCell) {
      tableData.push({
        company: companyCell.textContent.trim(),
        location: locationCell.textContent.trim(),
      });
    }
  }

  return tableData;
}

// Example usage
const scrapedData = scrapeTableData("1000020");
console.log(JSON.stringify(scrapedData, null, 2));
```

---

Scraped with ❤️ by [**@EthanThatOneKid**](https://etok.codes/)
