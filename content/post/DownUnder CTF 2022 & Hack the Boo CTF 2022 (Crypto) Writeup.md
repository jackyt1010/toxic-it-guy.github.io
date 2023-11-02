---
layout:post
title:"DownUnderCTF2022&HacktheBooCTF2022(Crypto)Writeup"
subtitle:""
description:""
date:2022-11-15
published:true
author: JackyTang
published:true
categories:["ComputerScience","InformationSecurity"]
tags:
-InformationSecurity
-CTF
-Cryptography
URL:"/2022/11/15/ctfs-2022-crypto/"
katex:true
---

<!--more-->
#DownUnderCTF2022

DownUnderCTFisthelargestonlineAustralianrunCaptureTheFlag(CTF)competitionwithover4000+registeredusersandover2100+registeredteams(2021).
ThiscontestwasheldfromFri,23Sept.2022,17:30HKT—Sun,25Sept.2022,17:30HKT
Mybelongedteam[NuttyShell](https://ctftime.org/team/72265)wasranked65over1407teams.Now,IdidsomewriteupsfortheCryptoproblemsofthecontest.

##BabyARX
Description:
Iheardthatadd-rotate-xoraregoodoperationsforaciphersoItriedtomakemyown...

TheChallengeScript:
```
classbaby_arx():
def__init__(self,key):
assertlen(key)==64
self.state=list(key)

defb(self):
b1=self.state[0]
b2=self.state[1]
b1=(b1^((b1<<1)|(b1&1)))&0xff
b2=(b2^((b2>>5)|(b2<<3)))&0xff
b=(b1+b2)%256
self.state=self.state[1:]+[b]
returnb

defstream(self,n):
returnbytes([self.b()for_inrange(n)])


FLAG=open('./flag.txt','rb').read().strip()
cipher=baby_arx(FLAG)
out=cipher.stream(64).hex()
print(out)

#cb57ba706aae5f275d6d8941b7c7706fe261b7c74d3384390b691c3d982941ac4931c6a4394a1a7b7a336bc3662fd0edab3ff8b31b96d112a026f93fff07e61b
```

IwrotethefollowingPythonScript:
```
chex="cb57ba706aae5f275d6d8941b7c7706fe261b7c74d3384390b691c3d982941ac4931c6a4394a1a7b7a336bc3662fd0edab3ff8b31b96d112a026f93fff07e61b"
c=bytes.fromhex(chex)
print(c)
b=0xcb
flag=""
forb1inrange(256):
forb2inrange(256):
nb1=(b1^((b1<<1)|(b1&1)))&0xff
nb2=(b2^((b2>>5)|(b2<<3)))&0xff
ifb==(nb1+nb2)%256andb1==ord("D")andb2==ord("U"):
i1=b2
flag+=chr(b1)
flag+=chr(b2)
i1_new=(i1^((i1<<1)|(i1&1)))&0xff
foriinrange(2,len(chex),2):
fori2inrange(1024):
i2_new=i2^((i2>>5)|(i2<<3))&0xff
if(i1_new+i2_new)%256==int(chex[i:i+2],16):
flag+=chr(i2)
i1=i2
i1_new=(i1^((i1<<1)|(i1&1)))&0xff
break
print(flag)

```
anditgivesusthefoillowingresult:
```
DUCTF{i_d0nt_th1nk_th4ts_h0w_1t_w0rks_actu4lly_92f45fb961ecf420}
```

Theflagis```DUCTF{i_d0nt_th1nk_th4ts_h0w_1t_w0rks_actu4lly_92f45fb961ecf420}```

#HacktheBooCTF2022

HackTheBooCTFcompetition2022wasorganizedbyHackTheBox.ThiscontestwasheldfromSat,22Oct.2022,21:00HKT—Thu,27Oct.2022,21:59HKT.
CoachedbythePolyUEIEMPhilstudent[Mr.HopkinsKong](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwjThPqvxLD7AhXbd94KHbdyD44QFnoECBoQAQ&url=https%3A%2F%2Fhk.linkedin.com%2Fin%2Fhopkins-k-805ba615b%3Ftrk%3Dpublic_profile_browsemap_profile-result-card_result-card_full-click&usg=AOvVaw1KFc1fu1v9QRAoRj4-1YVw),IwasresponsibleforhelpingtosolvethemajoritiesofCryptochallengesduringthecontest.Ourteam
[NuttyShell](https://ctftime.org/team/72265)wasranked1over6350+teamsfromworldwide([News](https://www.polyu.edu.hk/eie/news-and-events/news/2022/2022-11-09-champion-of-hacktheboo-ctf/))
andalsothefastestteamtosolveallthechallengesduringthecontest.

##Gonna-Lift-Em-All
Wearegiventhefollowingchallengescript:

```
importrandom

FLAG=b'HTB{??????????????????????????????????????????????????????????????????????}'

defgen_params():
p=getPrime(1024)
g=random.randint(2,p-2)
x=random.randint(2,p-2)
h=pow(g,x,p)
return(p,g,h),x

defencrypt(pubkey):
p,g,h=pubkey
m=bytes_to_long(FLAG)
y=random.randint(2,p-2)
s=pow(h,y,p)
return(g*y%p,m*s%p)

defmain():
pubkey,privkey=gen_params()
c1,c2=encrypt(pubkey)

withopen('data.txt','w')asf:
f.write(f'p={pubkey[0]}\ng={pubkey[1]}\nh={pubkey[2]}\n(c1,c2)=({c1},{c2})\n')


if__name__=="__main__":
main()
```
Bythe2equations:c1=g*y%p;c2=m*pow(h,y,p)%pwherep,g,h,c1,c2areknown,wecanthengetythroughthefirstformulaandthenthroughthesecondformulagetm

```
fromCrypto.Util.numberimport*
importgmpy2
p=163096280281091423983210248406915712517889481034858950909290409636473708049935881617682030048346215988640991054059665720267702269812372029514413149200077540372286640767440712609200928109053348791072129620291461211782445376287196340880230151621619967077864403170491990385250500736122995129377670743204192511487
g=90013867415033815546788865683138787340981114779795027049849106735163065530238112558925433950669257882773719245540328122774485318132233380232659378189294454934415433502907419484904868579770055146403383222584313613545633012035801235443658074554570316320175379613006002500159040573384221472749392328180810282909
h=36126929766421201592898598390796462047092189488294899467611358820068759559145016809953567417997852926385712060056759236355651329519671229503584054092862591820977252929713375230785797177168714290835111838057125364932429350418633983021165325131930984126892231131770259051468531005183584452954169653119524751729
(c1,c2)=(159888401067473505158228981260048538206997685715926404215585294103028971525122709370069002987651820789915955483297339998284909198539884370216675928669717336010990834572641551913464452325312178797916891874885912285079465823124506696494765212303264868663818171793272450116611177713890102083844049242593904824396,119922107693874734193003422004373653093552019951764644568950336416836757753914623024010126542723403161511430245803749782677240741425557896253881748212849840746908130439957915793292025688133503007044034712413879714604088691748282035315237472061427142978538459398404960344186573668737856258157623070654311038584)

y=gmpy2.divm(c1,g,p)
s=pow(h,y,p)
m=gmpy2.divm(c2,s,p)
print(long_to_bytes(m))
```
Hence,theflagforthischallengeis```HTB{b3_c4r3ful_wh3n_1mpl3m3n71n6_cryp705y573m5_1n_7h3_mul71pl1c471v3_6r0up}```

##FastCarmichael

```
fromsecretimportFLAG
fromCrypto.Util.numberimportisPrime
importsocketserver
importsignal

classHandler(socketserver.BaseRequestHandler):

defhandle(self):
signal.alarm(0)
main(self.request)


classReusableTCPServer(socketserver.ForkingMixIn,socketserver.TCPServer):
pass


defsendMessage(s,msg):
s.send(msg.encode())


defreceiveMessage(s,msg):
sendMessage(s,msg)
returns.recv(4096).decode().strip()


defgenerate_basis(n):
basis=[True]*n

foriinrange(3,int(n**0.5)+1,2):
ifbasis[i]:
basis[i*i::2*i]=[False]*((n-i*i-1)//(2*i)+1)

return[2]+[iforiinrange(3,n,2)ifbasis[i]]


defmillerRabin(n,b):
basis=generate_basis(300)
ifn==2orn==3:
returnTrue

ifn%2==0:
returnFalse

r,s=0,n-1
whiles%2==0:
r+=1
s//=2
forbinbasis:
x=pow(b,s,n)
ifx==1orx==n-1:
continue
for_inrange(r-1):
x=pow(x,2,n)
ifx==n-1:
break
else:
returnFalse
returnTrue


def_isPrime(p):
ifp<1:
returnFalse
if(p.bit_length()<=600)and(p.bit_length()>1500):
returnFalse
ifnotmillerRabin(p,300):
returnFalse

returnTrue


defmain(s):
p=receiveMessage(s,"Givep:")

try:
p=int(p)
except:
sendMessage(s,"Error!")

if_isPrime(p)andnotisPrime(p):
sendMessage(s,FLAG)
else:
sendMessage(s,"Conditionsnotsatisfied!")


if__name__=='__main__':
socketserver.TCPServer.allow_reuse_address=True
server=ReusableTCPServer(("0.0.0.0",1337),Handler)
server.serve_forever()
```
Tobypasstheserver'scondition,weneedtogenerateapesduoprimenumberwithbitslengthfrom600to1500.Byreadingthe
[soucecodesearchedfromInternet](https://gist.github.com/keltecc/b5fbd533d2f203e810b43c26ff9d17cc)basedonthe[researchpaperby(FrançoisArnault.1995.)](https://doi.org/10.1006/jsco.1995.1042),
wecanthenimmediatelyconstructacarmichaelnumberwhichareStrongPseudoprimestoSeveralBasesandwejustneedtosendittotheservertogettheflag.

##WholeLottaCandy

Twoprogramsaregiven,oneisserverandtheotherisAESencrypt,wheretheservercanchoosetheencryptionmodetoencryptandgettheencryptedflag:

```
fromencryptimportEncryptor
fromsecretimportFLAG
importsocketserver
importrandom
importsignal
importjson

MODES=['ECB','CBC','CFB','OFB','CTR']


classHandler(socketserver.BaseRequestHandler):

defhandle(self):
signal.alarm(0)
main(self.request)


classReusableTCPServer(socketserver.ForkingMixIn,socketserver.TCPServer):
pass


defsendMessage(s,msg):
s.send(msg.encode())


defreceiveMessage(s,msg):
sendMessage(s,msg)
returns.recv(4096).decode().strip()


defmain(s):
mode=random.choice(MODES)
enc=Encryptor()
whileTrue:
try:
sendMessage(s,
f"Pleaseinteractwiththeserverusingjsondata!\n")
sendMessage(s,f"Selectedmodeis{mode}.\n")
payload=receiveMessage(
s,
"\nOptions:\n\n1.Encryptflag\n2.Encryptplaintext\n3.Changemode\n4.Exit\n\n>"
)
payload=json.loads(payload)
option=payload["option"]
ifoption=="1":
ciphertext=enc.encrypt(FLAG,mode).hex()
response=json.dumps({
"response":"encrypted",
"ciphertext":ciphertext
})
sendMessage(s,"\n"+response+"\n")
elifoption=="2":
payload=receiveMessage(s,"Enterplaintext:\n")
payload=json.loads(payload)
plaintext=payload['plaintext'].encode()
ciphertext=enc.encrypt(plaintext,mode).hex()
response=json.dumps({
"response":"encrypted",
"ciphertext":ciphertext
})
sendMessage(s,"\n"+response+"\n")
elifoption=="3":
response=json.dumps({"modes":MODES})
sendMessage(
s,"Thesearethesupportedmodes\n"+response+"\n")
payload=receiveMessage(s,"Expectingmodes:\n")
payload=json.loads(payload)
mode=random.choice(payload['modes'])
elifoption=="4":
sendMessage(s,"Byebye\n")
exit()
exceptExceptionase:
response=json.dumps({"response":"error","message":str(e)})
sendMessage(s,"\n"+response+"\n")
exit()


if__name__=="__main__":
socketserver.TCPServer.allow_reuse_address=True
server=ReusableTCPServer(("0.0.0.0",1337),Handler)
server.serve_forever()
```
	

Here,onlytheCTRmodeisrequiredtobeselectedforsolvingthechallenge.
Theloopholeisthatwhenselectingtheencryptionmode,theoptionalitemsareinputbytheuser,sothattheCTRencryptionmodecanbeselected.IntheCTRencryption,z0,z1...arefirstgenerated,andthenXORedwiththeplaintexttoobtaintheciphertext.Inthisway,youonlyneedtoinputaplaintexttogettheencryptedresult,andthengetzandXORitwiththeciphertextofflag.Here,Ijustenteredseveralzeros
andsentthejsontotheserver.

Ithenwrotethefollowingscript:
```
frompwnimportxor
importbinascii
test="000000000000000000000000000000000000000000000000"
encrypted_test=binascii.unhexlify("3c67df24ac9b439824030d9198f1aaa846c958c42d7c48b7e55c8528075983ea37a04ee031ad5e4b563612e2de8377699b5946c78eaf8f46d186017a44f54b2e")
encrypted_flag=binascii.unhexlify("4403ad6fd7c53cff5a6c4dcdc9f0d4af45ce10c3422d4fb0b42fde475b588ab230a521e749ae310c275f7de586c1280cb20109badff1e6098cf975592e98593c")
blob=xor(encrypted_test,encrypted_flag)
flag=xor(blob,test)
print(flag)
```

Theflagis```HTB{KnOWN_pla1N737x7_a77aCk_l19h75_7H3_wAY_7hroU9H_mANy_Mod3z}```