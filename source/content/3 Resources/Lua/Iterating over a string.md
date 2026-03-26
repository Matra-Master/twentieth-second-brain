---
created: 20251206-1120
tags:
  - programming
  - lua
---

https://stackoverflow.com/questions/829063/how-to-iterate-individual-characters-in-lua-string

Some commenter on stack overflow made a great benchmark for iteration over strings

>How many times you'll need to iterate over characters in string?
>    If the answer is "once", than you should look up first part of the banchmark ("raw speed").
>    Otherwise, the second part will provide more precise estimation, because it parses the string into the table, which is much faster to iterate over. You should also consider writing a simple function for this, like @Jarriz suggested.
>
> Result:
> In my case, the string.byte and string.sub were fastest in terms of raw speed. When using cache table and reusing it 10 times per loop, the string.byte version was fastest even when converting charcodes back to chars (which isn't always necessary and depends on usage).
> As you have probably noticed, I've made some assumptions based on my previous benchmarks and applied them to the code:
>
>     Library functions should be always localized if used inside loops, because it is a lot faster.
>     Inserting new element into lua table is much faster using tbl[idx] = value than table.insert(tbl, value).
>     Looping through table using for i = 1, #tbl is a bit faster than for k, v in pairs(tbl).
>     Always prefer the version with less function calls, because the call itself adds a little bit to the execution time.
> Hope it helps.

``` Lua
-- Source - https://stackoverflow.com/questions/829063/how-to-iterate-individual-characters-in-lua-string
-- Posted by Electrix, modified by community. See post 'Timeline' for change history
-- Retrieved 2025-12-06, License - CC BY-SA 3.0

-- Setup locals
local str = "Hello World!"
local attempts = 5000000
local reuses = 10 -- For the second part of benchmark: Table values are reused 10 times. Change this according to your needs.
local x, c, elapsed, tbl
-- "Localize" funcs to minimize lookup overhead
local stringbyte, stringchar, stringsub, stringgsub, stringgmatch = string.byte, string.char, string.sub, string.gsub, string.gmatch

print("-----------------------")
print("Raw speed:")
print("-----------------------")

-- Version 1 - string.sub in loop
x = os.clock()
for j = 1, attempts do
    for i = 1, #str do
        c = stringsub(str, i)
    end
end
elapsed = os.clock() - x
print(string.format("V1 string.sub: elapsed time: %.3f", elapsed))

-- Version 2 - string.gmatch loop
x = os.clock()
for j = 1, attempts do
    for c in stringgmatch(str, ".") do end
end
elapsed = os.clock() - x
print(string.format("V2 string.match: elapsed time: %.3f", elapsed))

-- Version 3 - string.gsub callback
x = os.clock()
for j = 1, attempts do
    stringgsub(str, ".", function(c) end)
end
elapsed = os.clock() - x
print(string.format("V3 string.gsub: elapsed time: %.3f", elapsed))

-- For version 4
local str2table = function(str)
    local ret = {}
    for i = 1, #str do
        ret[i] = stringsub(str, i) -- Note: This is a lot faster than using table.insert
    end
    return ret
end

-- Version 4 - function str2table
x = os.clock()
for j = 1, attempts do
    tbl = str2table(str)
    for i = 1, #tbl do -- Note: This type of loop is a lot faster than "pairs" loop.
        c = tbl[i]
    end
end
elapsed = os.clock() - x
print(string.format("V4 str2table: elapsed time: %.3f", elapsed))

-- Version 5 - string.byte
x = os.clock()
for j = 1, attempts do
    tbl = {stringbyte(str, 1, #str)} -- Note: This is about 15% faster than calling string.byte for every character.
    for i = 1, #tbl do
        c = tbl[i] -- Note: produces char codes instead of chars.
    end
end
elapsed = os.clock() - x
print(string.format("V5 string.byte: elapsed time: %.3f", elapsed))

-- Version 5b - string.byte + conversion back to chars
x = os.clock()
for j = 1, attempts do
    tbl = {stringbyte(str, 1, #str)} -- Note: This is about 15% faster than calling string.byte for every character.
    for i = 1, #tbl do
        c = stringchar(tbl[i])
    end
end
elapsed = os.clock() - x
print(string.format("V5b string.byte to chars: elapsed time: %.3f", elapsed))

print("-----------------------")
print("Creating cache table ("..reuses.." reuses):")
print("-----------------------")

-- Version 1 - string.sub in loop
x = os.clock()
for k = 1, attempts do
    tbl = {}
    for i = 1, #str do
        tbl[i] = stringsub(str, i) -- Note: This is a lot faster than using table.insert
    end
    for j = 1, reuses do
        for i = 1, #tbl do
            c = tbl[i]
        end
    end
end
elapsed = os.clock() - x
print(string.format("V1: elapsed time: %.3f", elapsed))

-- Version 2 - string.gmatch loop
x = os.clock()
for k = 1, attempts do
    tbl = {}
    local tblc = 1 -- Note: This is faster than table.insert
    for c in stringgmatch(str, ".") do
        tbl[tblc] = c
        tblc = tblc + 1
    end
    for j = 1, reuses do
        for i = 1, #tbl do
            c = tbl[i]
        end
    end
end
elapsed = os.clock() - x
print(string.format("V2: elapsed time: %.3f", elapsed))

-- Version 3 - string.gsub callback
x = os.clock()
for k = 1, attempts do
    tbl = {}
    local tblc = 1 -- Note: This is faster than table.insert
    stringgsub(str, ".", function(c)
        tbl[tblc] = c
        tblc = tblc + 1
    end)
    for j = 1, reuses do
        for i = 1, #tbl do
            c = tbl[i]
        end
    end
end
elapsed = os.clock() - x
print(string.format("V3: elapsed time: %.3f", elapsed))

-- Version 4 - str2table func before loop
x = os.clock()
for k = 1, attempts do
    tbl = str2table(str)
    for j = 1, reuses do
        for i = 1, #tbl do -- Note: This type of loop is a lot faster than "pairs" loop.
            c = tbl[i]
        end
    end
end
elapsed = os.clock() - x
print(string.format("V4: elapsed time: %.3f", elapsed))

-- Version 5 - string.byte to create table
x = os.clock()
for k = 1, attempts do
    tbl = {stringbyte(str,1,#str)}
    for j = 1, reuses do
        for i = 1, #tbl do
            c = tbl[i]
        end
    end
end
elapsed = os.clock() - x
print(string.format("V5: elapsed time: %.3f", elapsed))

-- Version 5b - string.byte to create table + string.char loop to convert bytes to chars
x = os.clock()
for k = 1, attempts do
    tbl = {stringbyte(str, 1, #str)}
    for i = 1, #tbl do
        tbl[i] = stringchar(tbl[i])
    end
    for j = 1, reuses do
        for i = 1, #tbl do
            c = tbl[i]
        end
    end
end
elapsed = os.clock() - x
print(string.format("V5b: elapsed time: %.3f", elapsed))
```
