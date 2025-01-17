# Shop

Category: Reverse Engineering

Source: picoCTF 2021

Author: THELSHELL

Score: 5

## Description

Best Stuff - Cheap Stuff, Buy Buy Buy... Store Instance: [source](https://mercury.picoctf.net/static/e8e966fcaa1ff5ea48574046d0cf9c19/source). The shop is open for business at `nc mercury.picoctf.net 37799`.

## Hints

Always check edge cases when programming

## Approach

I connected to `nc mercury.picoctf.net 34938` and played around for a bit. There's only 40 coins in circulation which means the 100 coin flag is not something that can be bought.

```
You have 40 coins
        Item            Price   Count
(0) Quiet Quiches       10      12
(1) Average Apple       15      8
(2) Fruitful Flag       100     1
(3) Sell an Item
(4) Exit
Choose an option:
```

After playing around for a bit, I sold a negative number of item.... and ended up with a negative value for money. Through this I realized I should also be able to buy negative numbers of items since the shop probably only checks if there are less than how many items are in their stock. I bought a negative number of items and sure enough, ended up with a large enough sum of coins to buy a flag.

```
Flag is:  [112 105 99 111 67 84 70 123 98 52 100 95 98 114 111 103 114 97 109 109 101 114 95 98 97 54 98 56 99 100 102 125]
```

This looks like ascii so I wrote a quick [Python script](https://github.com/vivian-dai/PicoCTF2021-Writeup/blob/main/Reverse Engineering/Shop/script.py) to get the flag

## Flag

picoCTF{b4d_brogrammer_ba6b8cdf}

## Reference

Writeup from https://github.com/vivian-dai/PicoCTF2021-Writeup/blob/main/Reverse%20Engineering/Shop/Shop.md

