---
layout:     post
title:      "CSAW CTF Qualification Round 2022 Writeup(Crypto)"
subtitle:   "CTF"
description: "CTF"
date:     2022-09-17
published: true
author:  Jacky Tang
published: true
categories: [ "Computer Science", "Information Security"]
tags:
    - Information Security
    - CTF
    - Cryptography
URL: "/2022/09/17/csaw-ctf-qualification-2022-crypto/"
katex: true
---

<!--more-->
This contest was held from Fri, 09 Sept. 2022, 00 am HKT — Sun, 11 Sept. 2022, 00 am HKT
My belonged team [NuttyShell](https://ctftime.org/team/72265) was ranked 40 over 884 teams with 4993 points, whom seems the highest ranked team
in Hong Kong SAR, China and second highest team in the APAC region.Now, I did some writeup for the Crypto problems of the contest.

   ## Gotta Crack Them All
I know there is a password leaked and its plaintext is "Cacturne-Grass-Dark".I then used netcat to connect to its server and had a look on its ciphertext.
```
nc crypto.chal.csaw.io 5002

You can encrypt a pre-approved password using this service.

What is the password you would like to encrypt?

>> Cacturne-Grass-Dark
The encrypted password is: b ' kz\xc6\xb9\xd9Du\xcb\x8a\x9e\xe0\x9d\xbeo\xee\x03\xcf\xddd ' 
Would you like to go again? ( Y/N )
```

We now have a pair of plaintext and ciphertext under the simple XOR encryption scheme, we may just simply use the properties of XOR
to recover the key.Then, we use the acquired key to decrypt the encryted password lists:
encrypted_passwords.txt
```
crËªÀSiƒð¸æ™¿
lz×¦ÞWrƒã¸à—
ksÌ£ËZrÀÀôÂ´«.Í
`zÕ½ÅXbƒé¶à‘¬p
kwÄºÅBaËÕôÅ¹y±
kzÆ¹ÙDuËŠžà¾oîÏÝd
{wÊºÇ_uÉŠ‰ý•¾s­jþÜvöäÒª
{uÀ¬ßSwƒã¸à—àU "
`tÊ½ÍKÝÞºú•®1„/ÁÜ{
zsÜ½ÉDrÁÕôÕŽ¢i­#ƒý`öç
{~À©ÃB6éÕ¸á
ksÌ£Ï^tÛŠŽóˆ¨nîÂÊláþÒª
|hÄ¿ÉSuÏŠžà¾o
mcÆ¬ÈDrÂËôÕŽ¢i­#ƒü{ðé×
onÈ¾ÄYtÝŠ—ýŽ }¯
ciÌ®ÇSoÛÉ¼¿¾¸{
lz×¹Þ_cƒà«ó¾1…+×Æaò
xrÎ¤ÜSpƒé¶à‘¬pîÂÖfûë
lnÂ¹Þ_tƒà«ý‰£xîÚÊjù
jzÖ®ÙZrÀŠŽóˆ¨n
`rÕ½ÃAÁÉôÕŽ¢i­#
|tÂ¨Ø_xƒá¸ûŽ´1…+×Æaò
nrË£ÉYuƒð¸æ™¿
zrÊ¡Ù]ÇÀ±æ•£{
muÑ¨Å]ÇÕ¼
{k×¤ØL~ËŠŸó•¿e
ezË¹ÅX~ƒð¸æ™¿1…+×Æaò
{rÉ»ÍZw×Š—ýŽ }¯
j~É¡ßFiÁÒ­¿»¿}°4ƒÿ`üÿÔ§
b×©ÉSiƒé¶à‘¬pîÝÖlýåØ
ez×¤ÀZ6ùÆ­÷ŽàZ¢.ÜÖ
`~×©ÅSiƒé¶à‘¬p
iwÑ¬Þ_zƒã«ó›¢rîÂÖfûë
|sÒ¬Ï]~×Šžà¾o
{kÀºÜW6ìÒ¾
jiÊ£ÖYuÉŠŠæ™¨pîÝÖlýåØ
`zÎ¬ÁY6ÁŠàªs­jèÆhýøÒ§œ
ksÀ¾Ü_uƒà«ó¾
ei‹íá_vËŠ‰á…®tª$ƒénüþÂ
|t×£ÍRnÝŠŸþ…¤r¤
xnÕ¤ØWiƒõ¶ñ—à[±(ÛÁk
ktÈ¯ÙEpËÉôÔ•¿yîÇÈgáåÕ®
onß·ÀYiÊŠóŽ¦1‡5ÏÈ`û
kz×£Å@rÀÂôÕŽ¬o°
oiÊºÀ_oÆÂôÔ•¿y
oiÐ¯Î_uƒå¬õ
ozÖ¹ÞYÁÉôÅ¹y±jéÝ`àâß
otÊ Õ_ÜÆ¾ý’
|sÌ¨ÚCwƒã¸à—
uþÏC)’î Ïùq vÞÇ<§
{~Ä©ÞW6ùÆ­÷Ž
```
I wrote the following Python Script:
```
cstr=b'kz\xc6\xb9\xd9Du\xcb\x8a\x9e\xe0\x9d\xbeo\xee\x03\xcf\xddd'
pstr = "Cacturne-Grass-Dark"
key=[]
for (x,y) in zip(pstr, cstr):
    key.append((ord(x) ^ y))
print(key)

def decrypt(c):
    pt = ""
    for (x,y) in zip(c,key):
       pt += chr(x ^ y)
    return pt
keys=[]
with open('encrypted_passwords.txt','rb') as f:
   for ct in f.readlines():
      print(decrypt(ct))

```
and it gives us the following result:
```
Kingler-Water▬
Darkrai-DarkÇ
Chingling-Psychic¥
Happiny-NormalÉ
Clawitzer-WaterM
Cacturne-Grass-Dark
Slowking-Poison-Psy
Sneasel-Dark-Ice¤
Hoopa-Psychic-Ghost
Rhyperior-Ground-Ro
Seedot-GrassÇ
Chinchou-Water-Elec
Tsareena-GrassÉ
Excadrill-Ground-St
Gumshoos-NormalM
Kricketune-BugÉ
Dartrix-Grass-Flyin
Pikipek-Normal-Flyi
Dugtrio-Ground-Stee
Basculin-WaterÉ
Hippowdon-Ground¤
Togetic-Fairy-Flyin
Finneon-Water▬
Riolu-FightingÉ
Entei-Fire
Spritzee-FairyÉ
Mantine-Water-Flyin
Silvally-NormalM
Bellsprout-Grass-Po
Wyrdeer-Normal-Psyc
Marill-Water-Fairy♣
Herdier-NormalÉ
Altaria-Dragon-Flyi
Thwackey-GrassÉ
Spewpa-Bug
Bronzong-Steel-Psyc
Hakamo-o-Dragon-Fig
Chespin-Grass▬
Mr. Mime-Psychic-Fa
Tornadus-FlyingM
Pupitar-Rock-Ground
Combusken-Fire-Figh
Guzzlord-Dark-Drago
Carnivine-GrassM
Growlithe-FireÉ
Grubbin-Bugö
Gastrodon-Water-Gro
Goomy-DragonÇ
Thievul-DarkÇ
1n53cu2357234mc1ph3
Seadra-Water
```
Its obvious to see that the key length is insufficent and we need to guess the later part of the key.Fortunately, our flag is 1n53cu2357234mc1ph3
and we just need to test 1n53cu2357234mc1ph32 or 1n53cu2357234mc1ph3r to see which one is the correct flag.

The flag is ```1n53cu2357234mc1ph32```

   ## Phi Too Much In Common
This problem shoud be first solved by RSA common modulus attack, we can first netcat to the server and found the valus of N, e, c.
We found the same Modulus being used for several times, eg
```
N1 = 75461601146977109505051863300570306161751276563121786104437301866642155784175317254260494775311634797488558805520781121132364962108616459254202910416468092927002459487502736154990706830790833888066192035302455290265424729625646904256394000816219726781302373964930663736507000644914110676175191362589865832223
e1 = 16027876300415011209350679787945536513670825518312504500575855876884920273789
c1 = 38398274931301082430049230413455210761450152861351311310108492644984625556327846433701547302910435614732671163268334350697059111950843010179917520114123694620040677010228591019034301817871559790724614491548290734409599718350812994593499369547917475837244937815545407401237410621313354091937639186609861495953

N2 = 75461601146977109505051863300570306161751276563121786104437301866642155784175317254260494775311634797488558805520781121132364962108616459254202910416468092927002459487502736154990706830790833888066192035302455290265424729625646904256394000816219726781302373964930663736507000644914110676175191362589865832223
e2 = 11103785570909949258170003668915847310505685186530595160788875241088558386189
c2 = 22436795245496194744548325517069696567584643054341081729351610630647239074105589721394729652691672147667890911058149512706659340256588257480919473904146480483386290146004514111882362347004711010567996849639919033758847016434752956734961294682418097149089683186838341975712255263460555144789924822789073258149
```
Then, we just need to do the RSA common modulus attack to retrieve the plaintext m by the following script:
```
import gmpy2
import libnum
N1 = 75461601146977109505051863300570306161751276563121786104437301866642155784175317254260494775311634797488558805520781121132364962108616459254202910416468092927002459487502736154990706830790833888066192035302455290265424729625646904256394000816219726781302373964930663736507000644914110676175191362589865832223
e1 = 16027876300415011209350679787945536513670825518312504500575855876884920273789
c1 = 38398274931301082430049230413455210761450152861351311310108492644984625556327846433701547302910435614732671163268334350697059111950843010179917520114123694620040677010228591019034301817871559790724614491548290734409599718350812994593499369547917475837244937815545407401237410621313354091937639186609861495953

N2 = 75461601146977109505051863300570306161751276563121786104437301866642155784175317254260494775311634797488558805520781121132364962108616459254202910416468092927002459487502736154990706830790833888066192035302455290265424729625646904256394000816219726781302373964930663736507000644914110676175191362589865832223
e2 = 11103785570909949258170003668915847310505685186530595160788875241088558386189
c2 = 22436795245496194744548325517069696567584643054341081729351610630647239074105589721394729652691672147667890911058149512706659340256588257480919473904146480483386290146004514111882362347004711010567996849639919033758847016434752956734961294682418097149089683186838341975712255263460555144789924822789073258149

print(gmpy2.gcd(e1, e2))
gcd, s1, s2 = gmpy2.gcdext(e1, e2)
m = pow(c1, s1, N1) if s1 > 0 else pow(gmpy2.invert(c1, N1), -s1, N1)
m *= pow(c2, s2, N2) if s2 >0 else pow(gmpy2.invert(c2, N2), -s2, N2)

print(libnum.n2s(int(m % N1)))
```
And then we can retrieve the plaintext b'd0nt_reUs3_c0mm0n_m0duLus_iN_RSA'.Secondly, we are given the N, e, d values and we are required
to calculate the phi(N) in RSA scheme.We then use the following script to decompose N into p and q and calculate its phi value:
```
import random
def gcd(a, b):
   if a < b:
     a, b = b, a
   while b != 0:
     temp = a % b
     a = b
     b = temp
   return a


def getpq(n,e,d):
    p = 1
    q = 1
    while p==1 and q==1:
        k = d * e - 1
        g = random.randint ( 0 , n )
        while p==1 and q==1 and k % 2 == 0:
            k //= 2
            y = pow(g,k,n)
            if y!=1 and gcd(y-1,n)>1:
                p = gcd(y-1,n)
                q = n/p
    return p,q

N = 125535360578582885358925401622831769891756989689778095588550262145766934912149587131120727805018528534189308002509514461355090953271290001724340657510312011309112446260082062295297277301412646909212912135861443246171871415174358648364026413664015381040614642208246598313957374669706586657370766575064464236851

e = 4144822488777579816294127415797245167222066715944350099281978078143859028277

d = 114713998493458087534975565635404314926557011148174308476483721959506913574194252039380511767192732941443437395188517640316536490549833375058695094803108196675233396944212368751909540908176197093226163679971469754678763662317841961755736595377614585876016968477452067049948316637263983437505604592570742367157

p,q = getpq(N,e,d)
print(p, q)
phi_n = (p - 1) * (q - 1)
print(phi_n)
``` 

Finally, the flag is ```flag{aR3nT_U_tH3_RSA_ninJA}```

  ## Not Too Taxing
For this problem, we just need to perform the known plaintext attack for zip file.

By the tool AZPR, we can recover the 3 encrypted keys:
![1](/img/CSAW-ctf-qualification-round2022/1.png)
Then, by using bkcrack:
```
./bkcrack -C Tax_Ret_Form_Nov_2021.zip -c Tax_Ret_Form_Nov_2021.pdf -k b2c4a24e f036ff3a 998f6727 -d Tax_Ret_Form_Nov_2021.pdf
```
We then open the extracted Tax_Ret_Form_Nov_2021.pdf with PDFStreamDumper and look at each object.

The flag is  ```flag{1f_y0u_u53_z1pcryp70_4ny0n3_c4n_aud17_y0u}```
