100*("insediamenti-prossimita@1">6000) 
+ 
50*("insediamenti-prossimita@1">1000) * ("insediamenti-prossimita@1"<=6000)
+
10*("insediamenti-prossimita@1"<1000)


----
Eg.:

- `10` (10m dall'insediamento)= 100 x 0 + 50x0x1 + 10x1 = 10
- `5000` (5 km dall'insediamento)= 100 x 0 + 50x1x1 +10x0= 50
- `7000` (7 km dall'insedimento) =100


# Idrografia
## Lineare
**10-50-100**
```
100*("idrografia-prossimita@1">6000) 
+
50*("idrografia-prossimita@1">1000) * ("idrografia-prossimita@1"<=6000) 
+
10*("idrografia-prossimita@1"<1000)

## Gaussiana
**10-100-10**
```

```
10*("idrografia-prossimita@1">6000) 
+
100*("idrografia-prossimita@1">1000) * ("idrografia-prossimita@1"<=6000) 
+
10*("idrografia-prossimita@1"<1000)
```