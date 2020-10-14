# Welcome to US Currency Exchange 

This is a BCT project to simulate the Currency Exchange service.

## Authors
1. Rahul S (4NM17CS141)
2. Raksha D Shetty (4NM17CS142)
3. Rushali Shetty (4NM17CS152)

## Case Scenario

In this project we are simulating the working of currency exchange service. Following project we have used few assumptions.
1. The Currency exchange service is limited to USA currency in Dollars and Indian Currency in Rupees.
2. Exchange Value 1 Dollar = 73 Rupees.

## Implementation 

```markdown 
    pragma solidity ^0.5.0;
    contract Currencyconverter{
    mapping(address=>uint) private balances;
    address public owner;

    uint Dollar_value=73;
    
    function deposite_inr()public payable returns (uint){
        require((msg.sender.balance+(msg.value))>=msg.sender.balance);
        balances[msg.sender]+=msg.value;
        return balances[msg.sender];
    }
    
    function deposite_dollars()public payable returns (uint){
        require((balances[msg.sender]+(msg.value*Dollar_value))>=balances[msg.sender]);
        balances[msg.sender]+=msg.value*Dollar_value;
        return msg.sender.balance;
    }
    
    function withdraw_dollars() public payable returns (uint remainingBal){
        require(msg.value*Dollar_value <= balances[msg.sender]);
        balances[msg.sender]-=msg.value*Dollar_value;
        return msg.sender.balance;
    }
    
    function dollar_to_rupees(uint checkAmount) view public returns (uint) {
        return (checkAmount*Dollar_value);
    }  
    
    function rupees_to_dollars(uint checkAmount) view public returns (uint) {
        return (checkAmount/Dollar_value);
    }

    function balance() view public returns (uint){
        return balances[msg.sender];
    }
    }
```

## Money Deposit to Account

In this, we assume that the end user need to have and an account in US Exchange and if he/she needs Indian Rupees to be converted to USA Dollars it will be deducted from this Account.

To add money we have two functions 
1. deposite_inr
2. deposite_dollars

### Function: deposite_inr()

```markdown 
 function deposite_inr()public payable returns (uint){
        require((msg.sender.balance+(msg.value))>=msg.sender.balance);
        balances[msg.sender]+=msg.value;
        return balances[msg.sender];
    }
```
In this, function deposit is done to the account from Indian Rupee to Indian Rupee(No conversion takes place).

### Function: deposite_dollars()

```markdown 
  function deposite_dollars()public payable returns (uint){
        require((balances[msg.sender]+(msg.value*Dollar_value))>=balances[msg.sender]);
        balances[msg.sender]+=msg.value*Dollar_value;
        return msg.sender.balance;
    }
```
In this function, deposit is done to the account from USA Dollars to Indian Rupees(Conversion takes place).

## Get Rupees in Dollars

In this, we convert the given input USA Dollars to Indian Rupees and deduct the same from the account. If the balance is insufficient transaction will not proceed.
```markdown
   function withdraw_dollars() public payable returns (uint remainingBal){
        require(msg.value*Dollar_value <= balances[msg.sender]);
        balances[msg.sender]-=msg.value*Dollar_value;
        return msg.sender.balance;
    }
```

##  Balance Check

In this we check the current balance in account in Indian Rupees.

```markdown
function balance() view public returns (uint){
        return balances[msg.sender];
    }
```

## Conversion Rates

In this we assume that 1 Dollar = 73 Rupees and provide real time conversions.
It has two functions

### Function: dollar_to_rupees()
```markdown
 function dollar_to_rupees(uint checkAmount) view public returns (uint) {
        return (checkAmount*Dollar_value);
    }
```
In this function for given parameter it converts that to Indian Rupees.

### Function: rupees_to_dollars()
```markdown    
    function rupees_to_dollars(uint checkAmount) view public returns (uint) {
        return (checkAmount/Dollar_value);
    }
```

In this function for given parameter it converts that to Dollar Rupees.
