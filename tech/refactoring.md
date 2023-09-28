---
cards-deck: tech::refactoring
---

# SOLID
#card
S: Single Responsibility Principle
O: Open/Close Principle
L: Liskov Substitution Principle
I: Interface Segregation Principle
D: Dependency Invesion Principle

## single responsibilitty principle
#card
每個模塊或者類只應該有一種功能

## open/close principle
#card
實體應開放擴展，關閉修改

## liskov substitution principle
#card
可以在不破壞系統的情況下，用子類代替父類

## interface segregation principle
#card
不應強迫客戶端依賴它不使用的方法

## dependency inversion principle
#card
高級模塊不應該依賴低級實現

# DRY prinple
#card
do not repeat yourself

# refactor
## when
#card
rule of three
add new features
fixing bugs
code reviews

### rule of three
#card
when code have three clients, start refactoring

## checklist
#card
code should be cleaner
no new features
all tests passed

## smell
#card
bloaters
object-oriented abuser
change preventer
couplers

### bloater
#card
long methods
large classes
primitive obsession
long param list

#### long methods
#card
rule of thumb, if you need inline comments, deserve a new method

#### object-oriented abuser
#card
switch statement (consider polymorphism)
temp fields
refused bequest

#### change preventer
#card
divergent change
shotgun surgery
parallel inheritance hierachies

#### coupler
#card
feature envy
inappropiate intimacy
message chains
middle man

# BDD
#card
behavior driven development/test (avoid writing untestable code)

# Tell Don't Ask
#card
don't ask object for data, tell object what to do
https://martinfowler.com/bliki/TellDontAsk.html

# Separation queries from updates
#card
do not allow code in same methods/classes to request data and act on it.
