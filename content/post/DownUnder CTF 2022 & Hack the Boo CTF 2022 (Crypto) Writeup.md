---
layout:     post
title:      "DownUnder CTF 2022 & Hack the Boo CTF 2022 (Crypto) Writeup"
subtitle:   ""
description: ""
date:     2022-11-15
published: true
author:  Jacky Tang
published: true
categories: [ "Computer Science", "Information Security"]
tags:
    - Information Security
    - CTF
    - Cryptography
URL: "/2022/11/15/ctfs-2022-crypto/"
katex: true
---

<!--more-->
   
   ##DownUnder CTF 2022

DownUnderCTF is the largest online Australian run Capture The Flag (CTF) competition with over 4000+ registered users and over 2100+ registered teams (2021).
This contest was held from Fri, 23 Sept. 2022, 17:30 HKT — Sun, 25 Sept. 2022, 17:30 HKT
My belonged team [NuttyShell](https://ctftime.org/team/72265) was ranked 65 over 1407 teams.Now, I did some writeups for the Crypto problems of the contest.

   ## Baby ARX
Description:
I heard that add-rotate-xor are good operations for a cipher so I tried to make my own...

The Challenge Script:
```
class baby_arx():
    def __init__(self, key):
        assert len(key) == 64
        self.state = list(key)

    def b(self):
        b1 = self.state[0]
        b2 = self.state[1]
        b1 = (b1 ^ ((b1 << 1) | (b1 & 1))) & 0xff
        b2 = (b2 ^ ((b2 >> 5) | (b2 << 3))) & 0xff
        b = (b1 + b2) % 256
        self.state = self.state[1:] + [b]
        return b

    def stream(self, n):
        return bytes([self.b() for _ in range(n)])


FLAG = open('./flag.txt', 'rb').read().strip()
cipher = baby_arx(FLAG)
out = cipher.stream(64).hex()
print(out)

# cb57ba706aae5f275d6d8941b7c7706fe261b7c74d3384390b691c3d982941ac4931c6a4394a1a7b7a336bc3662fd0edab3ff8b31b96d112a026f93fff07e61b
```

I wrote the following Python Script:
```
chex = "cb57ba706aae5f275d6d8941b7c7706fe261b7c74d3384390b691c3d982941ac4931c6a4394a1a7b7a336bc3662fd0edab3ff8b31b96d112a026f93fff07e61b"
c = bytes.fromhex(chex)
print(c)
b = 0xcb
flag = ""
for b1 in range(256):
    for b2 in range(256):
        nb1 = (b1 ^ ((b1 << 1) | (b1 & 1))) & 0xff
        nb2 = (b2 ^ ((b2 >> 5) | (b2 << 3))) & 0xff
        if b == (nb1 + nb2) % 256 and b1==ord("D") and b2==ord("U"):
           i1 = b2
           flag += chr(b1)
           flag +=  chr(b2)
           i1_new = (i1 ^ ((i1 << 1) | (i1 & 1))) & 0xff
           for i in range(2, len(chex), 2):
               for i2 in range(1024):
                 i2_new = i2 ^ ((i2 >> 5) | (i2 << 3)) & 0xff
                 if (i1_new  + i2_new) % 256 == int(chex[i:i+2], 16):
                     flag += chr(i2)
                     i1 = i2
                     i1_new = (i1 ^ ((i1 << 1) | (i1 & 1))) & 0xff
                     break
print(flag)

```
and it gives us the foillowing result:
```
DUCTF{i_d0nt_th1nk_th4ts_h0w_1t_w0rks_actu4lly_92f45fb961ecf420}
```

The flag is ```DUCTF{i_d0nt_th1nk_th4ts_h0w_1t_w0rks_actu4lly_92f45fb961ecf420}```

   ##Hack the Boo CTF 2022
 
 Hack The Boo CTF competition 2022 was organized by Hack The Box.This contest was held from Sat, 22 Oct. 2022, 21:00 HKT — Thu, 27 Oct. 2022, 21:59 HKT.
 Coached by the PolyU EIE mphil student Hopkins Kong, I was responsible for helping to solve the majorities of Crypto challenges during the contest.Our team
 [NuttyShell](https://ctftime.org/team/72265) was ranked 1 over 6350+ teams from worldwide([News](https://www.polyu.edu.hk/eie/news-and-events/news/2022/2022-11-09-champion-of-hacktheboo-ctf/)).
 and also the fastest team to solve all the challenges during th4e contest.
   
   ##Gonna-Lift-Em-All
 We are given the following challenge script:
 
```
import random
 
FLAG = b'HTB{??????????????????????????????????????????????????????????????????????}'
 
def gen_params():
  p = getPrime(1024)
  g = random.randint(2, p-2)
  x = random.randint(2, p-2)
  h = pow(g, x, p)
  return (p, g, h), x
 
def encrypt(pubkey):
  p, g, h = pubkey
  m = bytes_to_long(FLAG)
  y = random.randint(2, p-2)
  s = pow(h, y, p)
  return (g * y % p, m * s % p)
 
def main():
  pubkey, privkey = gen_params()
  c1, c2 = encrypt(pubkey)
 
  with open('data.txt', 'w') as f:
    f.write(f'p = {pubkey[0]}\ng = {pubkey[1]}\nh = {pubkey[2]}\n(c1, c2) = ({c1}, {c2})\n')
 
 
if __name__ == "__main__":
  main()
```
By the2 equations: c1 = g*y %p; c2 = m*pow(h,y,p)%p where p, g, h, c1, c2 are known, we can then get y through the first formula and then through the second formula get m

```
from Crypto.Util.number import *
import gmpy2
p = 163096280281091423983210248406915712517889481034858950909290409636473708049935881617682030048346215988640991054059665720267702269812372029514413149200077540372286640767440712609200928109053348791072129620291461211782445376287196340880230151621619967077864403170491990385250500736122995129377670743204192511487
g = 90013867415033815546788865683138787340981114779795027049849106735163065530238112558925433950669257882773719245540328122774485318132233380232659378189294454934415433502907419484904868579770055146403383222584313613545633012035801235443658074554570316320175379613006002500159040573384221472749392328180810282909
h = 36126929766421201592898598390796462047092189488294899467611358820068759559145016809953567417997852926385712060056759236355651329519671229503584054092862591820977252929713375230785797177168714290835111838057125364932429350418633983021165325131930984126892231131770259051468531005183584452954169653119524751729
(c1, c2) = (159888401067473505158228981260048538206997685715926404215585294103028971525122709370069002987651820789915955483297339998284909198539884370216675928669717336010990834572641551913464452325312178797916891874885912285079465823124506696494765212303264868663818171793272450116611177713890102083844049242593904824396, 119922107693874734193003422004373653093552019951764644568950336416836757753914623024010126542723403161511430245803749782677240741425557896253881748212849840746908130439957915793292025688133503007044034712413879714604088691748282035315237472061427142978538459398404960344186573668737856258157623070654311038584)

y = gmpy2.divm(c1, g, p)
s = pow(h, y, p)
m = gmpy2.divm(c2, s, p)
print(long_to_bytes(m))
```
Hence, the flag for this challenge is ```HTB{b3_c4r3ful_wh3n_1mpl3m3n71n6_cryp705y573m5_1n_7h3_mul71pl1c471v3_6r0up}```

   ##Fast Carmichael

```
from secret import FLAG
from Crypto.Util.number import isPrime
import socketserver
import signal
 
class Handler(socketserver.BaseRequestHandler):
 
    def handle(self):
        signal.alarm(0)
        main(self.request)
 
 
class ReusableTCPServer(socketserver.ForkingMixIn, socketserver.TCPServer):
    pass
 
 
def sendMessage(s, msg):
    s.send(msg.encode())
 
 
def receiveMessage(s, msg):
    sendMessage(s, msg)
    return s.recv(4096).decode().strip()
 
 
def generate_basis(n):
    basis = [True] * n
 
    for i in range(3, int(n**0.5) + 1, 2):
        if basis[i]:
            basis[i * i::2 * i] = [False] * ((n - i * i - 1) // (2 * i) + 1)
 
    return [2] + [i for i in range(3, n, 2) if basis[i]]
 
 
def millerRabin(n, b):
    basis = generate_basis(300)
    if n == 2 or n == 3:
        return True
 
    if n % 2 == 0:
        return False
 
    r, s = 0, n - 1
    while s % 2 == 0:
        r += 1
        s //= 2
    for b in basis:
        x = pow(b, s, n)
        if x == 1 or x == n - 1:
            continue
        for _ in range(r - 1):
            x = pow(x, 2, n)
            if x == n - 1:
                break
        else:
            return False
    return True
 
 
def _isPrime(p):
    if p < 1:
        return False
    if (p.bit_length() <= 600) and (p.bit_length() > 1500):
        return False
    if not millerRabin(p, 300):
        return False
 
    return True
 
 
def main(s):
    p = receiveMessage(s, "Give p: ")
 
    try:
        p = int(p)
    except:
        sendMessage(s, "Error!")
 
    if _isPrime(p) and not isPrime(p):
        sendMessage(s, FLAG)
    else:
        sendMessage(s, "Conditions not satisfied!")
 
 
if __name__ == '__main__':
    socketserver.TCPServer.allow_reuse_address = True
    server = ReusableTCPServer(("0.0.0.0", 1337), Handler)
    server.serve_forever()
```
To bypass the server's condition, we need to generate a pesduorandom number with bits length from 600 to 1500.By reading the 
[souce code searched from Internet](https://gist.github.com/keltecc/b5fbd533d2f203e810b43c26ff9d17cc) based on the [research paper by (François Arnault. 1995.)](https://doi.org/10.1006/jsco.1995.1042),
 we can then immediately construct a carmichael number which are Strong Pseudoprimes to Several Bases and we just need to send it to the server to get the flag.
```99597527340020670697596886062721977401836948352586238797499761849061796816245727295797460642211895009946326533856101876592304488359235447755504083536903673408562244316363452203072868521183142694959128745107323188995740668134018742165409361423628304730379121574707411453909999845745038957688998441109092021094925758212635651445626620045726265831347783805945477368631216031783484978212374792517000073275125176790602508815912876763504846656547041590967709195413101791490627310943998497788944526663960420235802025853374061708569334400472016398343229556656720912631463470998180176325607452843441554359644313713952036867```

   ##Whole Lotta Candy

Two programs are given, one is server and the other is AES encrypt, where the server can choose the encryption mode to encrypt and get the encrypted flag:

```
from encrypt import Encryptor
from secret import FLAG
import socketserver
import random
import signal
import json
 
MODES = ['ECB', 'CBC', 'CFB', 'OFB', 'CTR']
 
 
class Handler(socketserver.BaseRequestHandler):
 
    def handle(self):
        signal.alarm(0)
        main(self.request)
 
 
class ReusableTCPServer(socketserver.ForkingMixIn, socketserver.TCPServer):
    pass
 
 
def sendMessage(s, msg):
    s.send(msg.encode())
 
 
def receiveMessage(s, msg):
    sendMessage(s, msg)
    return s.recv(4096).decode().strip()
 
 
def main(s):
    mode = random.choice(MODES)
    enc = Encryptor()
    while True:
        try:
            sendMessage(s,
                        f"Please interact with the server using json data!\n")
            sendMessage(s, f"Selected mode is {mode}.\n")
            payload = receiveMessage(
                s,
                "\nOptions:\n\n1.Encrypt flag\n2.Encrypt plaintext\n3.Change mode\n4.Exit\n\n> "
            )
            payload = json.loads(payload)
            option = payload["option"]
            if option == "1":
                ciphertext = enc.encrypt(FLAG, mode).hex()
                response = json.dumps({
                    "response": "encrypted",
                    "ciphertext": ciphertext
                })
                sendMessage(s, "\n" + response + "\n")
            elif option == "2":
                payload = receiveMessage(s, "Enter plaintext: \n")
                payload = json.loads(payload)
                plaintext = payload['plaintext'].encode()
                ciphertext = enc.encrypt(plaintext, mode).hex()
                response = json.dumps({
                    "response": "encrypted",
                    "ciphertext": ciphertext
                })
                sendMessage(s, "\n" + response + "\n")
            elif option == "3":
                response = json.dumps({"modes": MODES})
                sendMessage(
                    s, "These are the supported modes\n" + response + "\n")
                payload = receiveMessage(s, "Expecting modes: \n")
                payload = json.loads(payload)
                mode = random.choice(payload['modes'])
            elif option == "4":
                sendMessage(s, "Bye bye\n")
                exit()
        except Exception as e:
            response = json.dumps({"response": "error", "message": str(e)})
            sendMessage(s, "\n" + response + "\n")
            exit()
 
 
if __name__ == "__main__":
    socketserver.TCPServer.allow_reuse_address = True
    server = ReusableTCPServer(("0.0.0.0", 1337), Handler)
    server.serve_forever()
```
Here, only the CTR mode is required to be selected for solving the challenge.
The loophole is that when selecting the encryption mode, the optional items are input by the user, so that the CTR encryption mode can be selected. In the CTR encryption, z0, z1... are first generated, and then XORed with the plaintext to obtain the ciphertext. In this way, you only need to input a plaintext to get the encrypted result, and then get z and XOR it with the ciphertext of flag. Here, I just entered several zeros
and sent the json to the server.

I then wrote the following script:
```
from pwn import xor
import binascii
test="000000000000000000000000000000000000000000000000"
encrypted_test =binascii.unhexlify("3c67df24ac9b439824030d9198f1aaa846c958c42d7c48b7e55c8528075983ea37a04ee031ad5e4b563612e2de8377699b5946c78eaf8f46d186017a44f54b2e")
encrypted_flag = binascii.unhexlify("4403ad6fd7c53cff5a6c4dcdc9f0d4af45ce10c3422d4fb0b42fde475b588ab230a521e749ae310c275f7de586c1280cb20109badff1e6098cf975592e98593c")
blob = xor(encrypted_test , encrypted_flag)
flag = xor(blob, test)
print(flag)
```

The flag is ```HTB{KnOWN_pla1N737x7_a77aCk_l19h75_7H3_wAY_7hroU9H_mANy_Mod3z}```