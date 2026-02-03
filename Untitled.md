```
trim(
	string_to_array(
		"snippet" ,
		';'
	)
	[0]
)
```


```
trim(
 string_to_array( "cronologia", '-')[1]
)
```

**Seleziona a mano gli `AD`**
```
 to_int( 
	trim(
	 replace( "crono_da", 'AD', '')
	 )
 )
```

**Seleziona a mano gli `BC`**
```
 to_int( 
	trim(
	 replace( "crono_da", 'BC', '')
	 )
 )*-1

**Su tutti i campi**
```
if(
	strpos(
		string_to_array(  "cronologia" , ' - ')[0],
		'AD'
	) > 0,
	 to_int(replace(
	   string_to_array(  "cronologia" , ' - ')[0],
	   'AD ',
	   ''
	 )),
	to_int(replace(
	   string_to_array(  "cronologia" , ' - ')[0],
	   ' BC',
	   ''
	 ))*-1
)
```