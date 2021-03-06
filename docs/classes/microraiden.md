[microraiden](../README.md) > [MicroRaiden](../classes/microraiden.md)



# Class: MicroRaiden


Main MicroRaiden client class

Contains all methods to interact with a MicroRaiden channel through a web3 instance.

## Index

### Constructors

* [constructor](microraiden.md#constructor)


### Properties

* [challenge](microraiden.md#challenge)
* [channel](microraiden.md#channel)
* [contract](microraiden.md#contract)
* [decimals](microraiden.md#decimals)
* [token](microraiden.md#token)
* [web3](microraiden.md#web3)


### Methods

* [buyToken](microraiden.md#buytoken)
* [closeChannel](microraiden.md#closechannel)
* [confirmPayment](microraiden.md#confirmpayment)
* [forgetStoredChannel](microraiden.md#forgetstoredchannel)
* [getAccounts](microraiden.md#getaccounts)
* [getChallengePeriod](microraiden.md#getchallengeperiod)
* [getChannelInfo](microraiden.md#getchannelinfo)
* [getTokenInfo](microraiden.md#gettokeninfo)
* [incrementBalanceAndSign](microraiden.md#incrementbalanceandsign)
* [isChannelValid](microraiden.md#ischannelvalid)
* [loadChannelFromBlockchain](microraiden.md#loadchannelfromblockchain)
* [loadStoredChannel](microraiden.md#loadstoredchannel)
* [num2tkn](microraiden.md#num2tkn)
* [openChannel](microraiden.md#openchannel)
* [setBalance](microraiden.md#setbalance)
* [setChannel](microraiden.md#setchannel)
* [settleChannel](microraiden.md#settlechannel)
* [signMessage](microraiden.md#signmessage)
* [signNewProof](microraiden.md#signnewproof)
* [tkn2num](microraiden.md#tkn2num)
* [topUpChannel](microraiden.md#topupchannel)
* [verifyProof](microraiden.md#verifyproof)



---
## Constructors
<a id="constructor"></a>


### ⊕ **new MicroRaiden**(web3: *`string`⎮`object`*, contractAddr: *`string`*, contractABI: *`any`[]*, tokenAddr: *`string`*, tokenABI: *`any`[]*): [MicroRaiden](microraiden.md)


*Defined in [index.ts:189](https://github.com/andrevmatos/microraiden/blob/0546d77/microraiden/microraiden/webui/microraiden/src/index.ts#L189)*



MicroRaiden constructor


**Parameters:**

| Param | Type | Description |
| ------ | ------ | ------ |
| web3 | `string`⎮`object`   |  Web3 http url, or object with currentProvider property |
| contractAddr | `string`   |  Channel manager contract address |
| contractABI | `any`[]   |  Channel manager ABI |
| tokenAddr | `string`   |  Token address, must be the same setup in channel manager |
| tokenABI | `any`[]   |  Token ABI |





**Returns:** [MicroRaiden](microraiden.md)

---


## Properties
<a id="challenge"></a>

###  challenge

**●  challenge**:  *`number`* 

*Defined in [index.ts:189](https://github.com/andrevmatos/microraiden/blob/0546d77/microraiden/microraiden/webui/microraiden/src/index.ts#L189)*



Challenge period for uncooperative close, setup in channel manager




___

<a id="channel"></a>

###  channel

**●  channel**:  *[MicroChannel](../interfaces/microchannel.md)* 

*Defined in [index.ts:173](https://github.com/andrevmatos/microraiden/blob/0546d77/microraiden/microraiden/webui/microraiden/src/index.ts#L173)*



Currently set channel info. May be loaded through [loadStoredChannel](microraiden.md#loadstoredchannel), [loadChannelFromBlockchain](microraiden.md#loadchannelfromblockchain), or stored and set manually with [setChannel](microraiden.md#setchannel)




___

<a id="contract"></a>

###  contract

**●  contract**:  *`Web3.ContractInstance`* 

*Defined in [index.ts:181](https://github.com/andrevmatos/microraiden/blob/0546d77/microraiden/microraiden/webui/microraiden/src/index.ts#L181)*



Channel manager contract instance




___

<a id="decimals"></a>

###  decimals

**●  decimals**:  *`number`*  = 0

*Defined in [index.ts:185](https://github.com/andrevmatos/microraiden/blob/0546d77/microraiden/microraiden/webui/microraiden/src/index.ts#L185)*



Token decimals




___

<a id="token"></a>

###  token

**●  token**:  *`Web3.ContractInstance`* 

*Defined in [index.ts:177](https://github.com/andrevmatos/microraiden/blob/0546d77/microraiden/microraiden/webui/microraiden/src/index.ts#L177)*



Token contract instance




___

<a id="web3"></a>

###  web3

**●  web3**:  *`Web3`* 

*Defined in [index.ts:168](https://github.com/andrevmatos/microraiden/blob/0546d77/microraiden/microraiden/webui/microraiden/src/index.ts#L168)*



Web3 instance




___


## Methods
<a id="buytoken"></a>

###  buyToken

► **buyToken**(account: *`string`*): `Promise`.<`Web3.TransactionReceipt`>



*Defined in [index.ts:1019](https://github.com/andrevmatos/microraiden/blob/0546d77/microraiden/microraiden/webui/microraiden/src/index.ts#L1019)*



For testing. Send 0.1 ETH to mint method of contract. On TKN tests, it'll issue 50 TKNs to the sender's account.


**Parameters:**

| Param | Type | Description |
| ------ | ------ | ------ |
| account | `string`   |  Sender's account address |





**Returns:** `Promise`.<`Web3.TransactionReceipt`>
Promise to mint tx receipt






___

<a id="closechannel"></a>

###  closeChannel

► **closeChannel**(closingSig?: *`string`*): `Promise`.<`string`>



*Defined in [index.ts:728](https://github.com/andrevmatos/microraiden/blob/0546d77/microraiden/microraiden/webui/microraiden/src/index.ts#L728)*



Close current channel

Optional parameter is signed cooperative close from receiver, if available. If cooperative close was successful, channel is already settled after this method is resolved. Else, it enters 'closed' state, and should be settled after settlement period, configured in contract.


**Parameters:**

| Param | Type | Description |
| ------ | ------ | ------ |
| closingSig | `string`   |  Cooperative-close signature from receiver |





**Returns:** `Promise`.<`string`>
Promise to closing tx hash






___

<a id="confirmpayment"></a>

###  confirmPayment

► **confirmPayment**(proof: *[MicroProof](../interfaces/microproof.md)*): `void`



*Defined in [index.ts:944](https://github.com/andrevmatos/microraiden/blob/0546d77/microraiden/microraiden/webui/microraiden/src/index.ts#L944)*



Persists [MicroChannel.next_proof](../interfaces/microchannel.md#next_proof) to [MicroChannel.proof](../interfaces/microchannel.md#proof)

This method must be used after successful payment request, or right after [signNewProof](microraiden.md#signnewproof) is resolved, if implementation don't care for request status


**Parameters:**

| Param | Type | Description |
| ------ | ------ | ------ |
| proof | [MicroProof](../interfaces/microproof.md)   |  - |





**Returns:** `void`





___

<a id="forgetstoredchannel"></a>

###  forgetStoredChannel

► **forgetStoredChannel**(): `void`



*Defined in [index.ts:361](https://github.com/andrevmatos/microraiden/blob/0546d77/microraiden/microraiden/webui/microraiden/src/index.ts#L361)*



Forget current channel and remove it from localStorage, if available




**Returns:** `void`





___

<a id="getaccounts"></a>

###  getAccounts

► **getAccounts**(): `Promise`.<`string`[]>



*Defined in [index.ts:491](https://github.com/andrevmatos/microraiden/blob/0546d77/microraiden/microraiden/webui/microraiden/src/index.ts#L491)*



Get available accounts from web3 providers




**Returns:** `Promise`.<`string`[]>
Promise to accounts addresses array






___

<a id="getchallengeperiod"></a>

###  getChallengePeriod

► **getChallengePeriod**(): `Promise`.<`number`>



*Defined in [index.ts:314](https://github.com/andrevmatos/microraiden/blob/0546d77/microraiden/microraiden/webui/microraiden/src/index.ts#L314)*



Get contract's configured challenge's period

As it calls the contract method, can be used for validating that contract's address has code in current network




**Returns:** `Promise`.<`number`>
Promise to challenge period number, in blocks






___

<a id="getchannelinfo"></a>

###  getChannelInfo

► **getChannelInfo**(channel?: *[MicroChannel](../interfaces/microchannel.md)*): `Promise`.<[MicroChannelInfo](../interfaces/microchannelinfo.md)>



*Defined in [index.ts:521](https://github.com/andrevmatos/microraiden/blob/0546d77/microraiden/microraiden/webui/microraiden/src/index.ts#L521)*



Get channel details such as current state (one of opened, closed or settled), block in which it was set and current deposited amount


**Parameters:**

| Param | Type | Description |
| ------ | ------ | ------ |
| channel | [MicroChannel](../interfaces/microchannel.md)   |  Channel to get info from. Default to [channel](microraiden.md#channel) |





**Returns:** `Promise`.<[MicroChannelInfo](../interfaces/microchannelinfo.md)>
Promise to [[MicroChannelInfo]] data






___

<a id="gettokeninfo"></a>

###  getTokenInfo

► **getTokenInfo**(account?: *`string`*): `Promise`.<[MicroTokenInfo](../interfaces/microtokeninfo.md)>



*Defined in [index.ts:503](https://github.com/andrevmatos/microraiden/blob/0546d77/microraiden/microraiden/webui/microraiden/src/index.ts#L503)*



Get token details such as name, symbol and decimals.

If account is provided, returns also account balance for this token.


**Parameters:**

| Param | Type | Description |
| ------ | ------ | ------ |
| account | `string`   |  Address to be queried for current token balance |





**Returns:** `Promise`.<[MicroTokenInfo](../interfaces/microtokeninfo.md)>
Promise to [[MicroTokenInfo]] data






___

<a id="incrementbalanceandsign"></a>

###  incrementBalanceAndSign

► **incrementBalanceAndSign**(amount: *`BigNumber`*): `Promise`.<[MicroProof](../interfaces/microproof.md)>



*Defined in [index.ts:918](https://github.com/andrevmatos/microraiden/blob/0546d77/microraiden/microraiden/webui/microraiden/src/index.ts#L918)*



Ask user for signing a payment, which is previous balance incremented of amount.

Warnings from [signNewProof](microraiden.md#signnewproof) applies


**Parameters:**

| Param | Type | Description |
| ------ | ------ | ------ |
| amount | `BigNumber`   |  Amount to increment in current balance |





**Returns:** `Promise`.<[MicroProof](../interfaces/microproof.md)>
Promise to signature






___

<a id="ischannelvalid"></a>

###  isChannelValid

► **isChannelValid**(channel?: *[MicroChannel](../interfaces/microchannel.md)*): `boolean`



*Defined in [index.ts:474](https://github.com/andrevmatos/microraiden/blob/0546d77/microraiden/microraiden/webui/microraiden/src/index.ts#L474)*



Health check for currently configured channel info


**Parameters:**

| Param | Type | Description |
| ------ | ------ | ------ |
| channel | [MicroChannel](../interfaces/microchannel.md)   |  Channel to test. Default to [channel](microraiden.md#channel) |





**Returns:** `boolean`
True if channel is valid, false otherwise






___

<a id="loadchannelfromblockchain"></a>

###  loadChannelFromBlockchain

► **loadChannelFromBlockchain**(account: *`string`*, receiver: *`string`*): `Promise`.<[MicroChannel](../interfaces/microchannel.md)>



*Defined in [index.ts:384](https://github.com/andrevmatos/microraiden/blob/0546d77/microraiden/microraiden/webui/microraiden/src/index.ts#L384)*



Scan the blockchain for an open channel, and load it with 0 balance

The 0 balance may be overwritten with [setBalance](microraiden.md#setbalance) if server replies with a updated balance on first request. It should ask user for signing the zero-balance proof Throws/reject if no open channel was found


**Parameters:**

| Param | Type | Description |
| ------ | ------ | ------ |
| account | `string`   |  Sender/client's account address |
| receiver | `string`   |  Receiver/server's account address |





**Returns:** `Promise`.<[MicroChannel](../interfaces/microchannel.md)>
Promise to channel info, if a channel was found






___

<a id="loadstoredchannel"></a>

###  loadStoredChannel

► **loadStoredChannel**(account: *`string`*, receiver: *`string`*): `boolean`



*Defined in [index.ts:335](https://github.com/andrevmatos/microraiden/blob/0546d77/microraiden/microraiden/webui/microraiden/src/index.ts#L335)*



If localStorage is available, try to load a channel from it

Indexed by given account and receiver


**Parameters:**

| Param | Type | Description |
| ------ | ------ | ------ |
| account | `string`   |  Sender/client's account address |
| receiver | `string`   |  Receiver/server's account address |





**Returns:** `boolean`
True if a channel data was found, false otherwise






___

<a id="num2tkn"></a>

###  num2tkn

► **num2tkn**(value?: *`number`⎮`string`*): `BigNumber`



*Defined in [index.ts:232](https://github.com/andrevmatos/microraiden/blob/0546d77/microraiden/microraiden/webui/microraiden/src/index.ts#L232)*



Convert number to BigNumber

Takes into account configured token, taking in account the token decimals


**Parameters:**

| Param | Type | Description |
| ------ | ------ | ------ |
| value | `number`⎮`string`   |  Number or numeric-string to be converted |





**Returns:** `BigNumber`
BigNumber representation of value * 10^decimals






___

<a id="openchannel"></a>

###  openChannel

► **openChannel**(account: *`string`*, receiver: *`string`*, deposit: *`BigNumber`*): `Promise`.<[MicroChannel](../interfaces/microchannel.md)>



*Defined in [index.ts:598](https://github.com/andrevmatos/microraiden/blob/0546d77/microraiden/microraiden/webui/microraiden/src/index.ts#L598)*



Open a channel for account to receiver, depositing some tokens on it

Should work with both ERC20/ERC223 tokens. Replaces current [channel](microraiden.md#channel) data


**Parameters:**

| Param | Type | Description |
| ------ | ------ | ------ |
| account | `string`   |  Sender/client's account address |
| receiver | `string`   |  Receiver/server's account address |
| deposit | `BigNumber`   |  Tokens to be initially deposited in the channel |





**Returns:** `Promise`.<[MicroChannel](../interfaces/microchannel.md)>
Promise to [[MicroChannel]] info object






___

<a id="setbalance"></a>

###  setBalance

► **setBalance**(value: *`BigNumber`*): `void`



*Defined in [index.ts:968](https://github.com/andrevmatos/microraiden/blob/0546d77/microraiden/microraiden/webui/microraiden/src/index.ts#L968)*



Reset the current channel balance.

Used mainly when server replies a balance out-of-sync with current state Caution: it sets the balance without verifying it. If possible, prefer [verifyProof](microraiden.md#verifyproof)


**Parameters:**

| Param | Type | Description |
| ------ | ------ | ------ |
| value | `BigNumber`   |  Balance value to be set |





**Returns:** `void`





___

<a id="setchannel"></a>

###  setChannel

► **setChannel**(channel: *[MicroChannel](../interfaces/microchannel.md)*): `void`



*Defined in [index.ts:460](https://github.com/andrevmatos/microraiden/blob/0546d77/microraiden/microraiden/webui/microraiden/src/index.ts#L460)*



Set [channel](microraiden.md#channel) info

Can be used to externally [re]store an externally persisted channel info


**Parameters:**

| Param | Type | Description |
| ------ | ------ | ------ |
| channel | [MicroChannel](../interfaces/microchannel.md)   |  Channel info to be set |





**Returns:** `void`





___

<a id="settlechannel"></a>

###  settleChannel

► **settleChannel**(): `Promise`.<`string`>



*Defined in [index.ts:782](https://github.com/andrevmatos/microraiden/blob/0546d77/microraiden/microraiden/webui/microraiden/src/index.ts#L782)*



If channel was not cooperatively closed, and after settlement period, this function settles the channel, distributing the tokens to sender and receiver.




**Returns:** `Promise`.<`string`>
Promise to settlement tx hash






___

<a id="signmessage"></a>

###  signMessage

► **signMessage**(msg: *`string`*): `Promise`.<`string`>



*Defined in [index.ts:811](https://github.com/andrevmatos/microraiden/blob/0546d77/microraiden/microraiden/webui/microraiden/src/index.ts#L811)*



Ask user for signing a string with (personal|eth)_sign


**Parameters:**

| Param | Type | Description |
| ------ | ------ | ------ |
| msg | `string`   |  Data to be signed |





**Returns:** `Promise`.<`string`>
Promise to signature






___

<a id="signnewproof"></a>

###  signNewProof

► **signNewProof**(proof?: *[MicroProof](../interfaces/microproof.md)*): `Promise`.<[MicroProof](../interfaces/microproof.md)>



*Defined in [index.ts:849](https://github.com/andrevmatos/microraiden/blob/0546d77/microraiden/microraiden/webui/microraiden/src/index.ts#L849)*



Ask user for signing a channel balance

Notice it's the final balance, not the increment, and that the new balance is set in [MicroChannel.next_proof](../interfaces/microchannel.md#next_proof), requiring a [confirmPayment](microraiden.md#confirmpayment) call to persist it, after successful request. Implementation can choose to call confirmPayment right after this call resolves, assuming request will be successful after payment is signed. Tries to use eth_signTypedData (from EIP712), tries to use personal sign if it fails.


**Parameters:**

| Param | Type | Description |
| ------ | ------ | ------ |
| proof | [MicroProof](../interfaces/microproof.md)   |  Balance proof to be signed |





**Returns:** `Promise`.<[MicroProof](../interfaces/microproof.md)>
Promise to signature






___

<a id="tkn2num"></a>

###  tkn2num

► **tkn2num**(bal: *`BigNumber`*): `number`



*Defined in [index.ts:245](https://github.com/andrevmatos/microraiden/blob/0546d77/microraiden/microraiden/webui/microraiden/src/index.ts#L245)*



Convert BigNumber to number

Takes into account configured token, taking in account the token decimals Caution: it may add imprecisions due to javascript's native number limitations


**Parameters:**

| Param | Type | Description |
| ------ | ------ | ------ |
| bal | `BigNumber`   |  Value to be converted |





**Returns:** `number`
JS's native number representation of bal






___

<a id="topupchannel"></a>

###  topUpChannel

► **topUpChannel**(deposit: *`BigNumber`*): `Promise`.<`string`>



*Defined in [index.ts:667](https://github.com/andrevmatos/microraiden/blob/0546d77/microraiden/microraiden/webui/microraiden/src/index.ts#L667)*



Top up current channel, by depositing some [more] tokens to it

Should work with both ERC20/ERC223 tokens


**Parameters:**

| Param | Type | Description |
| ------ | ------ | ------ |
| deposit | `BigNumber`   |  Tokens to be deposited in the channel |





**Returns:** `Promise`.<`string`>
Promise to tx hash






___

<a id="verifyproof"></a>

###  verifyProof

► **verifyProof**(proof: *[MicroProof](../interfaces/microproof.md)*): `boolean`



*Defined in [index.ts:989](https://github.com/andrevmatos/microraiden/blob/0546d77/microraiden/microraiden/webui/microraiden/src/index.ts#L989)*



Verify and set given proof as current, if valid

Used mainly when server replies with an updated balance proof.


**Parameters:**

| Param | Type | Description |
| ------ | ------ | ------ |
| proof | [MicroProof](../interfaces/microproof.md)   |  Balance proof, containing balance and signatue |





**Returns:** `boolean`
True if balance is valid and correct, false otherwise






___


