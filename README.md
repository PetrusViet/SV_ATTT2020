# SV_ATTT2020


## Crypto: Zozo

```python
from Crypto.Util.number import getPrime
from secret import flag
if __name__ == "__main__":
    p = getPrime(2020)
    q = getPrime(2020)
    n = p * q
    m = int.from_bytes(flag, "big")
    print("m_nbits =", m.bit_length())
    print("n =", n)
    print("c =", pow(m, 2020, n))
    print("a =", pow(2020, p + q, n))
    print("b =", pow(2020 + p, q, n))

 # Output:
 # m_nbits = 319
 # n = 6709908271017636273378655032643421210567975544297596915593470137128363891228419512657274114669011891942663090194905940777812561840118056588428615370768885092202739470181344818071226713472147749259310788573428481022337413249410993247950922905606644328528192943149444979234186887778743327152264963995552199639516334711772886596304023688804194352785222469981515261437190030385869298033630451369031363005751953854690763993170983549216454881262214787640404401540368982811803830518044862679244774316554303060596087036766585181264228754533884686157605874994816602077647771821154174017913840152663341574258319064731734285760120757142699366635818090921302212163494224026153096257118848542085578751569398418767290380960045993906298155744307585160054373394289318601600049110591936546458514375137447927136123305276472066985894412133850945593125430051050782975296823192677589524309974575965049652679106537699815859361332255355304073828912153633031918384020344454320846509291701047296552969792343877167445711589879582318737790689596530198981403204253053646510518423927646404039101183559872205057776835009335526749058360229304128875012756435061325738256749504976724101945923621936319816392889120956770374512063428722147098976329869
 # c = 5864224848711720820817211671704694778695905148173426478823772341754769520297436790151720178822600703359634349693051017219994907057376876420682144309079454049023976356544836505728317828461198527983277715566118420702752363857780547934544333993684124272218912250542205291534959151403509560016811650493184981511608683386142308504929435507931615262448404799085994422034724586629678554166350178079472940420236074564061155766530450893276418007617083241365348685146022947027279870389893842842614241511586881271858702844985097949892504390163623182619199573989321882518783794640005487714616634923991074288211103528655178494133088391737888436621251297706643777790612880535035200633789617808463268702449003376758757849721087341450984385511290854783178315821367126481676592169755994541387156782192827145938301269351351761757778187189555776815049743584913347828959463932827039920965698827045664624051911631548912462614658429336371605254382418714300094185931900084689915127987428492388032885236529440573162080413658116170946312622966085259442254980477576414261877472891280475076723292584965680453174928254104610632650756393979776626931043914335355823274523183066437816628018798318931084472527823444775310790650495948742550122666265
 # a = 980781179837305218885179206087048803444471590700302063643535018495693430724914030556245097393427260363913143528109538846693614829591697702120365428254385683345686839503177715773958743573268578603719463614159789566282009616211761285100706329150399807929446215401809997648819192178784790954736795499890038722047760536412541503802934220088682495579518726114052360115421374595601506367371502412838497878638171727147057117092423900868846945245783789452892823795098355454383460294933817930733670269626108689690340482888570822525974184471046978083084475955634871778999677709303300606494890899380058971976816822189144579808563376704948356613537488887920531445962766022108577853761563429626110136791087146101838675208582550451197200757032589215039999050104990561516363971216242857221975891670846525040094795082245693423133498139889346759731100028439885160329382113242431148999407896236749722176599862270989214245784974790773738512127225274712656701544006472542108326726757708387122994130188265336534967519742344235206902681790664982286969578284724535014551860462777351346235879265149601211212012635615413576036852957939185779471487479187069954869805725012786640528981369936114776694281309574922917292585167819126537098878393
# b = 4641216257378099057352381055721343077859730393779620957802677320836328299623919622682409180900043164006379743835208471861065322669689004219152209877688932161323939062172737862949209335612905959419049131122827606289833320132637091525870446228013750820759726221912426092978807761763953422452903897746886480698273729327700002205007278822192835444552715212503789831922772941247247255969897858427770953126012859725663442324952213635057881518395655943469500770643862064112328593634725795022717613503995768650624713368354255625278684619158673643673318377015067884394373976604294325761072623961601920844588611380160669668620997109083418668830300999523289352487100107863180219906337931959899035161077718190292946009520400669518771791347719094082165012180394779767868370586439398218340075663119372165826283115713174037872289972899332408490598997589851075336647868448921242054058992305185018532387107710133316926598562378231532319494830261025962503435937632030032541114261355373337463537885816018226679565761261843148303706086819008415654607508321193854761654672254054381663393374480552395442623530365395504895082051270910574308865251390812099708944795467910074283930491871014602632927379580666428504295668769812578759829434656
```


Theo đề ra ta có:
```
a = 2020**(p+q) mod n (1)
b = (2020+p)**q mod n (2)
```
Từ (2) ta có: 
```
b ≡ (2020+p)**q mod p (2) (Do n = p*q)
b ≡ 2020**q mod p
```
Theo định lý Fermat thì: "Nếu p là số nguyên tố và a là số nguyên không chia hết cho p thì a**(p-1) ≡ 1 mod p" thế nên ta có:
```
     b ≡ 2020**q * 2020**(p-1) mod p
2020*b ≡ 2020**(p+q) mod p (*)
```
Mặt khác, từ (1) ta có:
```
        a ≡ 2020**(p+q) mod p (do n = p*q)
(*)=>   2020*b ≡ a mod p
        (2020*b - a) ≡ 0 mod p (**)
```
ta cũng có:
```
        n = p*q
=>      n ≡ 0 mod p
(**)=>  GCD(n, (2020*b - a)) = p
```

Đến đây ta đã có được p và q. Thế nhưng vẫn chưa thể nào encrypt được, lý do là vì GCD(e, phi) = 4 nên không thể tìm được d sao cho e*d ≡ 1 mod phi. Vậy ta phải làm như thế nào???

Với dx sao cho (e/4)*dx ≡ 1 mod phi. Ta có:
```
Cx ≡ C**dx mod n
Cx ≡ M**(e*dx) mod n
Cx ≡ M**4 mod n
```
Do tác giả bài này thương tình nên M**4 < n tức là Cx chính bằng M**4 luôn, ta có thể lấy căn bậc 4 của Cx để tìm lại M. Trong trường hợp các bạn gặp phải M**x > n, các bạn có thể sử dụng thuật toán "Miller Rabin" để giải tiếp nhé.

Dưới đây là code để lấy flag:
```python
from Crypto.Util.number import *
import math
import sympy

n = 6709908271017636273378655032643421210567975544297596915593470137128363891228419512657274114669011891942663090194905940777812561840118056588428615370768885092202739470181344818071226713472147749259310788573428481022337413249410993247950922905606644328528192943149444979234186887778743327152264963995552199639516334711772886596304023688804194352785222469981515261437190030385869298033630451369031363005751953854690763993170983549216454881262214787640404401540368982811803830518044862679244774316554303060596087036766585181264228754533884686157605874994816602077647771821154174017913840152663341574258319064731734285760120757142699366635818090921302212163494224026153096257118848542085578751569398418767290380960045993906298155744307585160054373394289318601600049110591936546458514375137447927136123305276472066985894412133850945593125430051050782975296823192677589524309974575965049652679106537699815859361332255355304073828912153633031918384020344454320846509291701047296552969792343877167445711589879582318737790689596530198981403204253053646510518423927646404039101183559872205057776835009335526749058360229304128875012756435061325738256749504976724101945923621936319816392889120956770374512063428722147098976329869
c = 5864224848711720820817211671704694778695905148173426478823772341754769520297436790151720178822600703359634349693051017219994907057376876420682144309079454049023976356544836505728317828461198527983277715566118420702752363857780547934544333993684124272218912250542205291534959151403509560016811650493184981511608683386142308504929435507931615262448404799085994422034724586629678554166350178079472940420236074564061155766530450893276418007617083241365348685146022947027279870389893842842614241511586881271858702844985097949892504390163623182619199573989321882518783794640005487714616634923991074288211103528655178494133088391737888436621251297706643777790612880535035200633789617808463268702449003376758757849721087341450984385511290854783178315821367126481676592169755994541387156782192827145938301269351351761757778187189555776815049743584913347828959463932827039920965698827045664624051911631548912462614658429336371605254382418714300094185931900084689915127987428492388032885236529440573162080413658116170946312622966085259442254980477576414261877472891280475076723292584965680453174928254104610632650756393979776626931043914335355823274523183066437816628018798318931084472527823444775310790650495948742550122666265
a = 980781179837305218885179206087048803444471590700302063643535018495693430724914030556245097393427260363913143528109538846693614829591697702120365428254385683345686839503177715773958743573268578603719463614159789566282009616211761285100706329150399807929446215401809997648819192178784790954736795499890038722047760536412541503802934220088682495579518726114052360115421374595601506367371502412838497878638171727147057117092423900868846945245783789452892823795098355454383460294933817930733670269626108689690340482888570822525974184471046978083084475955634871778999677709303300606494890899380058971976816822189144579808563376704948356613537488887920531445962766022108577853761563429626110136791087146101838675208582550451197200757032589215039999050104990561516363971216242857221975891670846525040094795082245693423133498139889346759731100028439885160329382113242431148999407896236749722176599862270989214245784974790773738512127225274712656701544006472542108326726757708387122994130188265336534967519742344235206902681790664982286969578284724535014551860462777351346235879265149601211212012635615413576036852957939185779471487479187069954869805725012786640528981369936114776694281309574922917292585167819126537098878393
b = 4641216257378099057352381055721343077859730393779620957802677320836328299623919622682409180900043164006379743835208471861065322669689004219152209877688932161323939062172737862949209335612905959419049131122827606289833320132637091525870446228013750820759726221912426092978807761763953422452903897746886480698273729327700002205007278822192835444552715212503789831922772941247247255969897858427770953126012859725663442324952213635057881518395655943469500770643862064112328593634725795022717613503995768650624713368354255625278684619158673643673318377015067884394373976604294325761072623961601920844588611380160669668620997109083418668830300999523289352487100107863180219906337931959899035161077718190292946009520400669518771791347719094082165012180394779767868370586439398218340075663119372165826283115713174037872289972899332408490598997589851075336647868448921242054058992305185018532387107710133316926598562378231532319494830261025962503435937632030032541114261355373337463537885816018226679565761261843148303706086819008415654607508321193854761654672254054381663393374480552395442623530365395504895082051270910574308865251390812099708944795467910074283930491871014602632927379580666428504295668769812578759829434656



p = math.gcd(n, (2020*b -a))
q = n//p

dx = inverse(2020//4, (p-1)*(q-1))
Cx = pow(c, dx, n)
m = sympy.root(Cx,4)
print(long_to_bytes(m))
```

### Flag: ASCIS{pl4y1ng_w1th_p_4nd_q_1s_d4ng3r0us}
