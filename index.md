## Welcome to US Currency Exchange 

This is a BCT project to simulate the Currency Exchange service.

### Case Scenario

In this project we are simulating the working of currency exchange service. Following project we have used few assumptions.
1. The Currency exchange service is limited to USA currency in Dollars and Indian Currency in Rupees.
2. Exchange Value 1 Dollar = 73 Rupees.

### Implementation 

`
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
`



Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/rahulCSENITTE/US_Currency_Exchange/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
