## Morpheus MRC-44: Compute Lending Protocol

---

## Status
**July 10, 2024: Proposed**

---

## Summary
As Smart Agents are developed within the Morpheus ecosystem, there will be a high demand for compute. This technology creates a marketplace to “lend” and “borrow” MOR tokens to utilize the compute at a low cost. 

---

## Rationale & Value Proposition
Smart Agent developers must acquire compute through holding MOR tokens, or by purchasing compute directly [need to clarify this existing mechanism]. These developers may not be interested in a large monetary exposure to MOR tokens to access the compute required for their agent, and will attempt to find other mechanisms to access compute without large initial investment, at a low cost. MOR holders who are not utilizing compute will be interested in “lending” their compute to create a revenue stream. MOR Borrowers: Borrowing MOR to access the compute. MOR Lenders: Lending MOR to monetize their unused compute allocation. MOR Protocol: x basis points of reward amount will be paid to the Morpheus ecosystem

---

## Mechanism & Capabilities
A smart contract template will be developed, similar to the MOR20 form, that will provide the following capabilities: 1) “Owner”, which will be the Smart Agent Developer, 2) “Reward Currency”, what currency will the lender be compensated in, 3) “Reward Amount”, how much will the lender be compensated per locked MOR, per day, 4) “Period”, the amount of time that lenders will lock their MOR within the contract, 5) “Borrow Amount”, the amount of MOR the developer is interested in borrowing, 6) “Assignment”, the address where the MOR compute earned within the contract will be assigned, 7) “Withdraw Excess”, the developer can withdraw any unused reward to compensate the lenders, 8) “Withdraw MOR”, the lenders can withdraw the MOR at the end of the “Period”, 9) “Withdraw Reward”, the lender can withdraw their reward that has been earned at any point in time, 10) “Morpheus Fee”, this will be calculated as x basis points of the “Reward Amount”, paid directly to Morpheus Protocol. 11) “Lend”, where the lender can deposit their MOR in the contract. When deploying the contract, the Smart Agent Developer must deposit the full “Reward Amount” that will be used to compensate Lenders across the entire “Period”. The only modifiable function within the contract will be the “Assignment”, as the Smart Agent Developer can change where the borrowed compute is utilized. 

---

## Dependencies
The key dependencies to this are the ability to assign MOR compute from one address to another, and the development of the smart contract. 


---

## Deliverables
P0: Smart Contract Development to support the borrowing and lending defined above
P1: Form to support the simple deployment of the smart contract, similar to the MOR20 form
P2: Marketplace that shows all of the smart contracts that have been deployed, their Reward Currency, Amount and Period, as well as the remaining amount that can be lent.  