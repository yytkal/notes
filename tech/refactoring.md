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
^1610505049767

## single responsibilitty principle
#card
每個模塊或者類只應該有一種功能
^1610505049777

## open/close principle
#card
實體應開放擴展，關閉修改
^1610505049784

## liskov substitution principle
#card
可以在不破壞系統的情況下，用子類代替父類
^1610505049790

## interface segregation principle
#card
不應強迫客戶端依賴它不使用的方法
^1610505049799

## dependency inversion principle
#card
高級模塊不應該依賴低級實現
^1610505049807

# DRY prinple
#card
do not repeat yourself
^1610505049815

# refactor
## when
#card
rule of three
add new features
fixing bugs
code reviews
^1610505049823

### rule of three
#card
when code have three clients, start refactoring
^1610505049829

## checklist
#card
code should be cleaner
no new features
all tests passed
^1610505049835

## smell
#card
bloaters
object-oriented abuser
change preventer
couplers
^1610505049842

### bloater
#card
long methods
large classes
primitive obsession
long param list
^1610505049850

#### long methods
#card
rule of thumb, if you need inline comments, deserve a new method
^1610505049856

#### object-oriented abuser
#card
switch statement (consider polymorphism)
temp fields
refused bequest
^1610505049864

#### change preventer
#card
divergent change
shotgun surgery
parallel inheritance hierachies
^1610505049871

#### coupler
#card
feature envy
inappropiate intimacy
message chains
middle man
^1610505049880

# BDD
#card
behavior driven development/test (avoid writing untestable code)
^1610505049887

# Tell Don't Ask
#card
don't ask object for data, tell object what to do
https://martinfowler.com/bliki/TellDontAsk.html
^1611302987692

# Separation queries from updates
#card
do not allow code in same methods/classes to request data and act on it.
^1611302987701
