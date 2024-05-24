# NextUI Cheat Shee










<br><br>
____________________________________________
____________________________________________

<br><br>

## Table


<br><br>
<br><br>

### Rows

#### Color

##### Change selected row color
```
<Table
   color="secondary"
>
```


<br><br>
<br><br>

#### Change initial display columns

#### Out of the box
```
const INITIAL_VISIBLE_COLUMNS = ['name', 'role', 'status', 'actions']
```

#### Custom:
```
{headerColumns.map((column: {
    uid: string
    name: string
    sortable: boolean
}) => {
    console.log('headerColumns: ', headerColumns)
    console.log('column: ', column)
    return <TableCell key={column.uid}>{renderCell(item, column.uid)}</TableCell>
})}
```
