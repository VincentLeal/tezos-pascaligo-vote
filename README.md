# tezos-pascaligo-vote 
Simple Smart Contract for voting, written in PascaLIGO, for Tezos DLT Blockchain.

## Goals:
Write a smart voting contract (in LIGO):
+ 2 vote options possible ("yes" or "no")
+ any user has the right to vote
+ a user can only vote once
+ the administrator is defined during the deployment of the smart contract
    + the administrator does not have the right to vote 
+ the smart contract is paused if at least 10 people have voted
    + when the smart contract is paused, the result of the vote must be available (the result is stored in the storage of the smart contract) 
    + an administrator must be able to reset all votes (and remove the pause => make it active again)
+ the smart contract should have unit tests

## Usage:
First, make sure you have LIGO installed and correctly set up :
+ [Tezos - Installation](https://tezos.gitlab.io/introduction/howtoget.html#build-from-sources)
+ [LIGO Lang - Installation](https://ligolang.org/docs/intro/installation/)

Then, copy the contents of this repo and compile, dry-run, and deploy the contract `votingContract.ligo` :
```
ligo compile-contract votingContract.ligo main > votingContract.tz
```
```
ligo compile-storage votingContract.ligo main 'record admin = ("tz1LKe9GQfF4wfob11YjH9grP1YdEWZtPe9W": address); paused = False; votes = (map[] : map(address, bool)); end'
```
```
ligo compile-parameter votingContract.ligo main "Vote(record vote = False; end)" 
ligo compile-parameter votingContract.ligo main "Reset(0)"
```
```
pytest pyTestContract.py
```

## Known Issues:
```
No function for returning the value of present votes is implemented yet... coming soon!
```
