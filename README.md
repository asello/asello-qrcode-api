# asello-qrcode-api

import data to asello by QR codes from upstream systems

# prerequisites

* asello WinApp (from https://asello.at/apps)
* 2D-Scanner (Honeywell voyage 1400g USB)
* QR-Code with the following format

# format

The data within the QR code has to be formatted according to the following text-format. Each qr code starts with a prefix '!!_' and end with a suffix '_!!'. The commands are separated with ';'.

```
<prefix><command1>;<command2>;...;<commandN><suffix>
```

# commands

A command contains a action, executed in asello. The commands consists of a command name, a following ':' and n-parameters. The parameters are separated with ','.

```
<command-name>:<parameter1>,<parameter2>,...,<parameterN>
```

## command: add position

|||||
---|---|---|---|---|
command name | i ||||
parameter 1 | position name | string | ```"Position 1"```||
parameter 2 | unit net price | number | ```15.12```||
parameter 3 | ust rate | number | ```20.0```||
parameter 4 | quantity | number | ```1```||

Example:
```
i:Position 1,15.12,20.0,1
```

## command: customer

|||||
---|---|---|---|---|
command name | c ||||
parameter 1 | salutation | string('Mister', 'Miss', 'Company' | ```"Mister"```||
parameter 2 | name | string | ```"Mustermann"```||
parameter 3 | firstname | string | ```"Max"```||
parameter 4 | attention | string | ```"z.B. Miss Mustermann"```||
parameter 5 | street | string | ```"Musterstraße 1"```||
parameter 6 | zip code | string | ```"A-1234"```||
parameter 7 | city | string | ```"Musterstaft"```||

Example:
```
c:,Mustermann,Max,,,,
```

## command: payment method
|||||
---|---|---|---|---|
command name | p ||||
parameter 1 | method | string('Cash', 'CreditCard', 'CashCard') | ```"CashCard"```||

Example:
```
p:CashCard
```

## command: reference number
|||||
---|---|---|---|---|
command name | r ||||
parameter 1 | reference number | string | ```"R12345678"```||

Example:
```
r:R12345678
```

## command: action
|||||
---|---|---|---|---|
command name | a ||||
parameter 1 | name | string('print') | ```"CashCard"```||

Example:
```
a:print
```

# Example

```
!!_i:Position 1,15.12,20.0,1;c:,Mustermann,Max,,,,;p:CashCard;a:print_!!
```

![Example QR Code](https://github.com/asello/asello-qrcode-api/blob/master/example-qr-code.png?raw=true)
