# salve , io uso per fare delle prove con GNU Awk 3.1.3<br />
# del pacchetto <a href="http://unxutils.sourceforge.net/">UnxUtils</a> su xp sp2 con path:....<br />
# C:\Documents and Settings\danilo\Documenti\my_proces\UnxUtils\usr\local\bin;<br />
# C:\Documents and Settings\danilo\Documenti\my_proces\UnxUtils\usr\local\lib;<br />
# questa è una raccolta di esercizi tratti dal <a href="http://www.gnu.org/software/gawk/manual/gawk.pdf">manuale</a><a href="http://www.gnu.org/software/gawk/manual/gawk.pdf"></a><br />
# editor <a href="http://poldovim.blogspot.com/">vim</a><br />
# sono in ordine di testo<br />
#argomenti: formatazione, ricerca, operazioni, comparazione, stringhe, system<br />
<br />
### formatazione ###<br />
<br />
# gawk "{ a[$1]++ } END { for (c in a) print c, a[c]}" myfile<br />
# expand data  gawk "{ if ( x &lt; x =" length()"&gt; 0 " BBS-list<br />
# gawk "BEGIN { OFS = \";\"; ORS = \"\n\n\" } { print $1, $2 }" BBS-list<br />
# gawk "BEGIN { OFMT = \"%.0f\" ; print 17.23 , 17.54 }" ()<br />
# gawk "BEGIN { printf \" %2$s %1$s \n\", \"don't\" , \"panic\" }"<br />
# gawk "BEGIN { printf \" %.2s\" \"panic\" }"<br />
# pa<br />
<br />
### ricerca ###<br />
<br />
# gawk "BEGIN { w = 5 ; p = 3 ; s = \"abcdefg\" ; printf \"%*.*s\n\",w,p,s }"<br />
# gawk "BEGIN { s = \"abcdefg\" ; printf \"%5.3s\n\",s }"<br />
# abc<br />
<br />
# gawk "BEGIN { print $1 &gt; \"names.unsorted\" ; command = # UNIX CMD<br />
# \"sort-r &gt; names.sorted\" ; print $1  command } " BBS-list<br />
<br />
# gawk " { nome = $1 ; nomi = sort -r nome ; print nomi } " BBS-list<br />
# gawk "BEGIN { printf(\"mv %s %s\n\", $0, tolupper($0))  system(\"sh\") } END{ close(\"sh\") }" BBS-list # unix cmd<br />
<br />
# ls -l  | gawk " $6 == \"Sep\" { sum += $5 } END { print sum }"<br />
# 132644<br />
# ls -l  | gawk " $6 == \"Sep\" { sum += $2 } END { print sum }"<br />
# 17<br />
# ls -l  | grep "Sep"  | wc -l<br />
# 17<br />
<br />
# gawk " BEGIN { digits_regexp = \"[[:digit:]]+\" } ; $0 ~ digits_regexp { print } " check.conf.txt<br />
<br />
# gawk "$0 ~ /[ \t\n]/" check.conf.txt<br />
# gawk "BEGIN { RS=\"/\" } ; { print $0 }" BBS-list<br />
# gawk "{ print $0 }" RS="/" BBS-list<br />
<br />
# gawk "BEGIN { printf \"%d, %d, %d\n\", 011, 11, 0x11 }"<br />
# gawk " { if( $0 ~ /barfly/  $0 ~ /camelot/) print \"ok\" } " sh<br />
# gawk "{ print $n }" n=4 inventory-shipped n=2 BBS-list<br />
<br />
### operazioni ###<br />
<br />
# gawk "BEGIN{ two=2 ; three=3 ; print ( two three ) + 4 }"<br />
# gawk "{ sum = $2 + $3 + $4 ; avg = sum / 3 ; print $1, avg }" sh<br />
# gawk "BEGIN{ a = \"don't\" ; print(a \" \"(a=\"panic\")) }"<br />
# don't panic<br />
<br />
# gawk "BEGIN { print -12 \" \" -24 }"<br />
#-12-24<br />
# gawk "BEGIN { print -12 \" \" (-24) }"<br />
#-12 -24<br />
# gawk "BEGIN { b=6; b += b++ ; print b }"<br />
<br />
### comparazione ###<br />
<br />
# echo 1e2 3  | gawk "{ print ($1 &lt; $2) ? \"true\" : \"false\" ; print $1 \" \" $2 }"<br />
# echo 1e2 3  | gawk "{ print ($1 = $2) ? \"true\" : \"false\" ; print $1 \" \" $2 }"  <br />
<br />
# gawk "$1 ~ /foo/ { print $2 }" BBS-list<br />
# gawk "$1 == /foo/ { print $2 }" BBS-list<br />
# gawk "1200  /foo/ { print $2 }" BBS-list<br />
# gawk "2400 &amp;&amp; /foo/ { print $2 }" BBS-list<br />
# gawk "! /foo/ { print $2 }" BBS-list  <br />
<br />
# gawk "BEGIN { print \"Analysis of foo\" } /foo/ { ++n } END { print \"foo appears\", n, \"times.\" }" BBS-list <br />
# gawk "BEGIN{ for (i in ENVIRON) print i }"<br />
# gawk "BEGIN{ for (i in ENVIRON) system(\"echo %\" i \"%\") }"  <br />
<br />
### stringhe ### <br />
<br />
$echo &nbsp;1406+12233+370904+396851+221020+123508+765366 |&nbsp;awk -F"+" '{print NF" "NR" "FNR}'<br />
<br />
# more fsadm4.log  | gawk "{ for ( i=1 ; i &lt;= NF; i++ ) used[$i] = 1 } END { for ( x in used ) if ( length(x) &gt; 10 ) { ++num_long_words ; print x }<br />
print num_long_words, \"words longer than 10 characters\" }"<br />
<br />
# gawk "BEGIN { print index(\"peanut\", \"n\") }"<br />
# echo foooobazbarrrrr  | gawk "{ match($0, /(fo+).+(bar*)/, arr) ; print arr[1], arr[2] ; print arr[1, \"start\"], arr[1, \"length\"]}"<br />
<br />
# gawk "BEGIN { split(\"cul-de-sac\",a,\"-\") ; for ( c in a ) print c , a[c] }"<br />
# gawk "BEGIN { split(\"sac-cul-amen-de-loc\",a,\"-\") ; for ( c in a ) print c , a[c] ; asort(a) ; for (c=1; c<6 a="" br="" c="" print=""><br /># echo daabaaaa  | gawk "{ str = $1 ; sub( /a+/ , \"C%C\" , str ) ; print str }"<br /># echo daabaaaa  | gawk "{ str = $1 ; gsub( /a+/ , \"C*C\" , str ) ; print str }"<br /><br /># gawk "BEGIN { a = \"abc def\"; b = gensub(/(.+) (.+)/, \"\\2 \\1\", \"g\", a); print b }"<br /># echo a b c a b c  | gawk "{ print gensub(/a/, \"AA\", 2) }"<br /># echo a b c a b c  | gawk "{ print gensub(/a.b/, \"AA\", 2) }"<br /># echo a b c a b c  | gawk "{ print gensub(/a|b/, \"AA\", 2) }"<br /># echo abc  | gawk "{ gsub(/m*/, \"X\"); print }"<br /><br />### system ###<br /><br /># gawk "{ system( \"date /T\") }"<br /><br /># echo 0123 123 0x123  | gawk --non-decimal-data " { print $1, $2, $3 ; print $1 + 0, $2 + 0, $3 + 0 }"<!--6--><!--6--></6>
