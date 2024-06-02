# NextUI Cheat Shee





# Templates

<br><br>
<br><br>


## Dashboard
- https://github.com/Siumauricio/nextui-dashboard-template









<br><br>
____________________________________________
____________________________________________

<br><br>

# Customization

<br><br>

## Colors
- NextUI's plugin enables you to personalize the semantic colors of the theme such as primary, secondary, success, etc.
- tailwind.config.js

<br><br>
<br><br>

### Default colors
- https://nextui.org/docs/customization/colors#default-colors
- Common colors, like TailwindCSS colors, remain consistent regardless of the theme. To prevent conflicts with TailwindCSS colors, common colors are initially disabled but can be activated with the addCommonColors option.


<br><br>
<br><br>

### Semantic Colors
- Semantic colors adapt with the theme, delivering meaning and reinforcing your brand identity. For an effective palette, we recommend using color ranges from 50 to 900. You can use tools like Eva Design System, Smart Watch, Palette or Color Box to generate your palette.



















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
- https://nextui.org/docs/components/modal

<br><br>

## Open on Button click
```javascript
/ ==== NEXT UI ====
import {Modal, ModalContent, ModalHeader, ModalBody, ModalFooter, Button, useDisclosure} from "@nextui-org/react";

export default function TransactionsTable() {
	const { isOpen, onOpen, onOpenChange } = useDisclosure()
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
}
```

<br><br>
<br><br>

## Open at load when some condition is not filled
```typescript
/ ==== NEXT UI ====
import {Modal, ModalContent, ModalHeader, ModalBody, ModalFooter, Button, useDisclosure} from "@nextui-org/react";

export default function TransactionsTable() {
    const { isOpen, onOpen, onOpenChange } = useDisclosure()
}

// State to store and show the connected account
const [connectedAccount, setConnectedAccount] = useState('null')


useEffect(() => {
	const checkAccount = async() => {
	    if (window.ethereum) {
		// Instantiate Web3 with the injected provider
		const web3 = new Web3(window.ethereum)
	
		// Get the connected accounts
		const accounts = await web3.eth.getAccounts()
		console.log('checkAccount() -> accounts: ', accounts)
	
		if (_.isEmpty(accounts)) {
		    onOpen()
		}
	
		// Show the first connected account in the react page
		setConnectedAccount(accounts[0])
	    }
	}
	
	checkAccount()
}, [onOpen])

const metaMaskNotFoundModal = (
        <Modal 
            isOpen={isOpen} onOpenChange={onOpenChange}
        >
            <ModalContent>
                {onClose => (
                    <>
                        <ModalHeader className="flex flex-col gap-1">
                            <div className="flex items-center gap-2">
                                <MetaMaskIcon />
                                <h2 className="text-3xl font-bold">MetaMask not connected..</h2>
                            </div>
                        </ModalHeader>

                        <ModalBody>
                            <p className="text-lg">
                                Please connect to the MetaMask extension.
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

    if (!connectedAccount) {
        return (
            <>
                {metaMaskNotFoundModal}
            </>
        )
    }
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
