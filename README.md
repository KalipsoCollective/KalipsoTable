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
  <script src="l10n/[lang].js">
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
    language: "tr",
    // server: true, // SERVER-SIDE
    // source: 'http://webaddress.com/list',
    server: false, // CLIENT-SIDE
    source: [
      {id: 1, u_name: 'alonzo', name: 'Alonzo Forza', email: 'alonzof@gmail.com', birth_date: '1996.08.14', role: 'admin', created: '2022.05.05', updated: '2022.05.05', status: 'active', action: '<button class="btn btn-danger btn-sm">Delete</button>'},
      {id: 2, u_name: 'carlb', name: 'Carl Ben', email: 'carlb@gmail.com', birth_date: '1996.08.14', role: 'admin', created: '2022.05.06', updated: '2022.05.05', status: 'passive', action: '<button class="btn btn-danger btn-sm">Delete</button>'},
      {id: 3, u_name: 'dan14edward', name: 'Dan Edward', email: 'dan14edward@outlook.com', birth_date: '1996.08.14', role: 'admin', created: '2022.05.08', updated: '2022.05.05', status: 'active', action: '<button class="btn btn-danger btn-sm">Delete</button>'},
      {id: 4, u_name: 'hankfrank', name: 'Frank Hank', email: 'hankfrank@gmail.com', birth_date: '1996.08.14', role: 'admin', created: '2022.05.09', updated: '2022.05.05', status: 'active', action: '<button class="btn btn-danger btn-sm">Delete</button>'},
      {id: 5, u_name: 'thomopeter22', name: 'Thomas Peter', email: 'thomopeter@hotmail.com', birth_date: '1996.08.14', role: 'admin', created: '2022.08.22', updated: '2022.05.05', status: 'passive', action: '<button class="btn btn-danger btn-sm">Delete</button>'},
      {id: 6, u_name: 'time', name: 'Edward Tim', email: 'tim.edward@gmail.com', birth_date: '1996.08.14', role: 'admin', created: '2021.04.13', updated: '2022.05.05', status: 'active', action: '<button class="btn btn-danger btn-sm">Delete</button>'},
      {id: 7, u_name: 'wm', name: 'Walter Monte', email: 'waltermontee@outlook.com', birth_date: '1996.08.14', role: 'admin', created: '2021.09.10', updated: '2022.05.05', status: 'active', action: '<button class="btn btn-danger btn-sm">Delete</button>'},
      {id: 8, u_name: 'george.c', name: 'George Corte', email: 'george.c@gmail.com', birth_date: '1996.08.14', role: 'admin', created: '2022.07.12', updated: '2022.05.05', status: 'deleted', action: ''},
      {id: 9, u_name: 'hi.ben', name: 'Ben Thomas', email: 'ben_thomas@gmail.com', birth_date: '1996.08.14', role: 'admin', created: '2020.05.24', updated: '2022.05.05', status: 'active', action: '<button class="btn btn-danger btn-sm">Delete</button>'},
      {id: 10, u_name: 'otto_dan', name: 'Dan Otto', email: 'otto_dan@gmail.com', birth_date: '1996.08.14', role: 'admin', created: '2022.03.28', updated: '2022.05.05', status: 'deleted', action: ''},
      {id: 11, u_name: 'kotto_dan', name: 'Kenau Dan Otto', email: 'kotto_dan@gmail.com', birth_date: '1996.08.14', role: 'admin', created: '2022.03.28', updated: '2022.05.05', status: 'deleted', action: ''}
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
          "maxlength": 50
        },
        "orderable": true,
        "title": "Kullanıcı Adı",
        "key": "u_name"
      },
      {
        "searchable": {
          "type": "text",
          "maxlength": 50
        },
        "orderable": true,
        "title": "Ad",
        "key": "name"
      },
      {
        "searchable": {
          "type": "text",
          "maxlength": 50
        },
        "orderable": true,
        "title": "Eposta Adresi",
        "key": "email"
      },
      {
        "searchable": {
          "type": "date",
        },
        "orderable": true,
        "title": "Doğum Tarihi",
        "key": "birth_date"
      },
      {
        "searchable": {
          "type": "text",
          "maxlength": 50
        },
        "orderable": true,
        "title": "Rol",
        "key": "role"
      },
      {
        "searchable": {
          "type": "date",
          "maxlength": 50
        },
        "orderable": true,
        "title": "Eklenme",
        "key": "created"
      },
      {
        "searchable": {
          "type": "date",
          "maxlength": 50
        },
        "orderable": true,
        "title": "Güncellenme",
        "key": "updated"
      },
      {
        "searchable": {
          "type": "select",
          "datas": [
            {"value": 'active', "name": "Aktif"},
            {"value": 'passive', "name": "Pasif"},
            {"value": 'deleted', "name": "Silinmiş"}
          ],
        },
        "orderable": true,
        "title": "Durum",
        "key": "status"
      },
      {
        "searchable": false,
        "orderable": false,
        "title": "İşlem",
        "key": "action"
      }
    ],
    customize: {
      tableWrapClass: "table-responsive",
      tableClass: "table table-bordered",
      inputClass: "form-control form-control-sm",
      selectClass: "form-control form-control-sm",
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

### Server-side and KalipsoTable PHP Class

Requests made on the server side are thrown with the GET method. The version information of KalipsoTable is carried in the header with the definition of X-KALIPSOTABLE. 
You can use the KalipsoTable class written in PHP for server-side data manipulation and output.

#### Server-side Request
- per_page: ex. 5 || 10 || 100
- order: ex. id,desc (with comma)
- full_search: ex. Alex
- search: ex: {"name": "Alex", "status", "active"} (as url encoded json)

#### Server-side Response
- current_page: 1
- filtered_count: 10
- record_count: 325
- records: [{id: "207", u_name: "jack-joe_25415", name: "Joe Jack", email: "jack-joe_25415@outlook.com",…},…]
- total_page: 33