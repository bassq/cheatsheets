# AWK cheatsheet

|   VAR |||
|------:|---|---|
| ` NF` | Number of Fields | `$NF` is tail field=column content |
| ` NR` | Number of Record | `wc -l` : `awk 'END{print NR}'` |
| ` FS` | Field  Separator | `awk -F 'regex char'` |
| ` RS` | Record Separator | `awk -v RS="\r\n"` |
| `OFS` | Output FS        | |
| `ORS` | Output RS        | |

## common usage
* CSV subtotal : `awk -F, '{sum+=$2}END{print sum}' table.csv`

## filter One Liner
* `head` : `awk 'NR<=5{print}'`
* `cat -n` : `awk '{print FNR "\t" $0}'`
* `grep -A 2` : `awk '/regex/{i=2+1}{if(i){i--;print}}'`
* `tail -n 1` : `awk 'END{print}'`

## tail
```awk
{ line[NR%5] = $0 }
END { for( i=1; i<=5; i++){ print line[(NR+i)%5] } }
```

## ascii char code
```awk
BEGIN { for( i=32; i<128; i++){ codeOf[sprintf("%c", i)] = i }
{ print codeOf[$0] }
```
## CSV/TSV to html
```awk
#!/usr/bin/awk -f
BEGIN {
	FS = "[,\t]";
	print "<table>";
}
{
	printf "<tr>";
	for( i=1; i<=NF; i++){ printf "<td>%s</td>", $i };
	printf "</tr>\n"
}
END { print "</table>"; }
```
