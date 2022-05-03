# KalipsoTable
Pure JS data table library.

## Usage

Just include the script and style file in the page and set the options block.

```html
<head>
  <link rel="stylesheet" type="text/css" href="kalipso.table.css">
  <script src="kalipso.table.js">
</head>
```

### Localization

If you want to use it with an external language, you must include the relevant language file before including the resources.

```html
<head>
  <script src="kalipso.table.js">
  ...
</head>
```
### Prepare

First, let's set the DOM element for which the table will be created.
```html
<div id="usersTable"></div>
```

You can trigger the KalipsoTable with the following setting block.
```js
  const options = {
    selector: "#usersTable",
    language: "en",
    source: [
      {
        "id": 1,
        "username": "test1",
        "email": "test1@example.com",
        "birthday": "07.07.2021",
        "status": "active",
        "action": "action"
      },
      {
        "id": 5,
        "username": "test5",
        "email": "test5@example.com",
        "birthday": "01.01.2021",
        "status": "passive",
        "action": "action"
      },
      {
        "id": 4,
        "username": "test4",
        "email": "test4@example.com",
        "birthday": "05.05.2021",
        "status": "deleted",
        "action": "action"
      },
      {
        "id": 2,
        "username": "test2",
        "email": "test2@example.com",
        "birthday": "09.12.2021",
        "status": "active",
        "action": "action"
      },
      {
        "id": 3,
        "username": "<div>test3</div>",
        "email": "test3@example.com",
        "birthday": "10.12.2021",
        "status": "passive",
        "action": "action"
      }
    ],
    columns: [ 
      {
        "searchable": {
          "type": "number",
          "min": 1,
          "max": 999
        },
        "orderable": true,
        "title": "#",
        "key": "id"
      },
      {
        "searchable": {
          "type": "text",
          "maxlenght": 50
        },
        "orderable": true,
        "title": "Username",
        "key": "username"
      },
      {
        "searchable": {
          "type": "text",
          "maxlenght": 50
        },
        "orderable": true,
        "title": "Email",
        "key": "email"
      },
      {
        "searchable": {
          "type": "text",
          "maxlenght": 50
        },
        "orderable": true,
        "title": "Birthday",
        "key": "birthday"
      },
      {
        "searchable": {
          "type": "select",
          "datas": [
            {"value": 'active', "name": "Active"},
            {"value": 'passive', "name": "Passive"},
            {"value": 'deleted', "name": "Deleted"}
          ],
        },
        "orderable": true,
        "title": "Status",
        "key": "status"
      },
      {
        "searchable": false,
        "orderable": false,
        "title": "",
        "key": "action"
      }
    ],
    lengthOptions: [
      {
        "name": "10",
        "value": 10,
      },
      {
        "name": "1",
        "value": 1,
      },
      {
        "name": "50",
        "value": 50,
      },
      {
        "name": "100",
        "value": 100,
        "default": true
      },
      {
        "name": "All",
        "value": 0,
      }
    ],
    customize: { // The example class definitions assume use with Bootstrap.
      tableWrapClass: "table-responsive",
      tableClass: "table table-bordered",
      tableHeadClass: "",
      tableBodyClass: "",
      tableFooterClass: "",
      inputClass: "form-control form-control-sm",
      selectClass: "form-control form-control-sm",
      paginationUlClass: null,
      paginationLiClass: null,
      paginationAClass: null
    },
    tableHeader: {
      searchBar: true
    },
    tableFooter: {
      visible: true,
      searchBar: true
    }
  };
  new KalipsoTable(options);
```