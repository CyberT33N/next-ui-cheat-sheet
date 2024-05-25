# NextUI Cheat Shee

















<br><br>
____________________________________________
____________________________________________

<br><br>

# Avatar
- You can use images from your public folder for src
```javascript
import {Avatar} from "@nextui-org/react";

 <NavbarItem className="hidden lg:flex">{searchInput}</NavbarItem>
	{connectedAccount === 'null' ? (
	    <NavbarItem className="hidden lg:flex">{metamaskButton}</NavbarItem>
	) : (
	    <Avatar isBordered color="secondary" src="/avatar/wallet/robot-purple.jpeg" />
	)}
</NavbarContent>
```










<br><br>
____________________________________________
____________________________________________

<br><br>

# Modal
```javascript
const [connectedAccount, setConnectedAccount] = useState('null')

async function connectMetamask() {
     if (window.ethereum) {
        // ..
     } else {
         onOpen()
     }
 }

 const metamaskButton = (
	   <Button
		  className="text-sm font-normal text-default-600 bg-default-100"
		  onClick={connectMetamask}
		  startContent={<MetaMaskIcon/>}
		  variant="flat"
	   >
		  Connect
	   </Button>
)


const metaMaskNotFound = (
        <Modal isOpen={isOpen} onOpenChange={onOpenChange}>
            <ModalContent>
                {onClose => (
                    <>
                        <ModalHeader className="flex flex-col gap-1">
                            <div className="flex items-center gap-2">
                                <MetaMaskIcon />
                                <h2 className="text-3xl font-bold">MetaMask not found</h2>
                            </div>
                        </ModalHeader>

                        <ModalBody>
                            <p className="text-lg">
                                Please install the MetaMask extension.
                            </p>

                            <p className="text-lg">
                                You can download it from{' '}
                                <a
                                    href="https://metamask.io/"
                                    target="_blank"
                                    rel="noopener noreferrer"
                                    className="text-primary underline"
                                    style={{ fontWeight: 'bold' }}
                                >
                                    here
                                </a>
                                .
                            </p>
                        </ModalBody>
                        <ModalFooter>
                            <Button color="danger" variant="light" onPress={onClose}>
                                Close
                            </Button>
                        </ModalFooter>
                    </>
                )}
            </ModalContent>
        </Modal>
    )
```













<br><br>
____________________________________________
____________________________________________

<br><br>

# Table

## Default sort oder:
```javascript
 const [sortDescriptor, setSortDescriptor] = React.useState<SortDescriptor>({
        column: 'created',
        direction: 'descending'
    })
```







<br><br>
<br><br>

## Rows

### Color

#### Change selected row color
```
<Table
   color="secondary"
>
```


<br><br>
<br><br>

### Change initial display columns

### Out of the box
```
const INITIAL_VISIBLE_COLUMNS = ['name', 'role', 'status', 'actions']
```

### Custom:
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
