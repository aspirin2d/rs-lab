
---
Original CoC Combat FlowChart
---

```mermaid
flowchart LR
    id1["`**Establish Order of Attack:**
    - Dex Ranking 
    - Highest Dex goes first
    - Readied Firearms: Dex + 50`"]

    id2["`**Surprise Attack**:
    - Target can make a skill roll to determine if they anticipate the attack: Spot Hidden, Listen, Psychology`"]

    id2a["`**Anticpated:**
    Use DEX order of combat`"]

    id2b["`**Unanticipated:**
    Auto-Hit or gain bonus die.`"]

    id3["`**Resolve in DEX order:**
    Attacker can: Attack, Maneuver, or Flee.
    Defender can: Dodge, Fight Back, or perform Maneuver.
    Attacker and defender make opposed roll.`"]

    id3a["`**Dodge:**
    **Higher** level of success wins.
    **Draw = Defender wins**
    **Both fail:** No damage inflicted`"]

    id3b["`**Fight Back:**
    **Higher** level of success wins.
    **Draw = Initiator wins.**
    **Both fail:** No damage inflicted`"]

    id3c["`**Maneuver:**
    Same as **Fight Back**, but apply the effect of maneuver instead.`"]

    id4["`**Maneuver:**
    If **initiator** has a **smaller** build difference of **1**, penalty die for **each point** of difference. 
    Difference of **3+** means the maneuver is **impossible.**`"]


    id1-->id2
    id2-->id2a
    id2-->id2b
    id1-->id3
    id3-->id3a
    id3-->id3b
    id3-->id3c
    id3-->id4
    id4-->id3c
```

---
Simplified Flowchart: Player's Perspective
---

```mermaid
flowchart LR
    id0(((START)))
    id1["`**Player Character**`"]

    id2[Battle Options]
    id3[Reaction]

    id2a[Fight]
    id2aa[Brawl]
    id2ab[Melee]
    id2ac[Ranged]

    id2b[Character Perk]

    id2c[Item]
    id2cb["`List of Items`"]

    id2d[Flee]


    id3a[Dodge]
    id3b[Fight Back]
    id4["`**Resolve**`"]

    id0-->id1
    id1-- if DEX higher than enemy -->id2
    id1-- if DEX lower than enemy -->id3
    id2-->id2a
    id2-->id2b
    id2-->id2c
    id2-->id2d

    id2a-->fight
    subgraph fight
   id2aa
   id2ab
   id2ac
    end


    id2c--> Items
    subgraph Items
    id2cb
    end
    



    id3---id3a-->id4
    id3---id3b-->id4
    id4-->id2
```

---
Simplified Flowchart: Flee Loop
---

```mermaid
flowchart LR
    id0(((START)))
    id1["`**Initiative**`"]

    id2[Battle Options]
    id3[Enemy Attacks]


    id2d[Flee]
    id2da["`**Resolve**`"]
    id2db((("`**Exit Battle**`")))


    id3a[Dodge Enemy]
    id3b[Fight Back Enemy]
    id4["`**Resolve**`"]







    id0-->id1
    id1-- if DEX higher -->id2
    id1-- if DEX lower -->id3
    
    id2-->id2d
    id2d-- Constitution Roll -->id2da
    id2da-- Success -->id2db
    id2da-- Fail -->id3


    id3---id3a-->id4
    id3---id3b-->id4
    id4-->id2
```

---
Simplified Flowchart: Fight Loop
---

```mermaid
flowchart LR
    id0(((START)))
    id1["`**Initiative**`"]

    id2[Battle Options]
    id3[Reaction]

    id2a[Fight]
    id2aa[Brawl]
    id2ab[Melee]
    id2ac[Ranged]


    id3a[Dodge]
    id3b[Fight Back]
    id4["`**Resolve**`"]
    id5["`**Resolve**`"]
    id6((("`**Exit Battle**`")))

    id0-->id1
    id1-- if DEX higher -->id2
    id1-- if DEX lower -->id3
    id2-->id2a



    id2a-->fight
    id2a-- if no melee or range equipped -->id5
    subgraph fight
   id2aa
   id2ab
   id2ac
    end

    fight-->id5

    id5 -- Enemy Dies --> id6

    id5-- Enemy Alive --> id3



    id3---id3a-->id4
    id3---id3b-->id4
    id4-->id2
```

---
Simplified Flowchart: Perk Loop
---

```mermaid
flowchart LR
    id0(((START)))
    id1["`**Initiative**`"]

    id2[Battle Options]
    id3[Reaction]


    id2b[Character Perk]
    id2ba["`**Resolve**`"]


    id3a[Dodge]
    id3b[Fight Back]
    id4["`**Resolve**`"]

    id5((("`**Exit Battle**`")))

    id0-->id1
    id1-- if DEX higher -->id2
    id1-- if DEX lower -->id3
    id2-->id2b

    id2b-->id2ba

    id2ba-- Kills Enemy --> id5
    id2ba-- Successful / Unsuccessful / Did not kill enemy -->id3
    id2ba-- spc.effect:stun success -->id2


    id3---id3a-->id4
    id3---id3b-->id4
    id4-->id2
```

---
Simplified Flowchart: Items Loop
---

```mermaid
flowchart LR
    id0(((START)))
    id1["`**Initiative**`"]

    id2[Battle Options]
    id3[Reaction]

    id2c[Item]
    id2ca[Backpack]
    id2cb["`List of Items`"]
    id2cc[Item Effect]

    id3a[Dodge]
    id3b[Fight Back]
    id4["`**Resolve**`"]


    id0-->id1
    id1-- if DEX higher -->id2
    id1-- if DEX lower -->id3
    id2-->id2c

    id2c--> Items
    subgraph Items
    id2ca-->id2cb
    end

    Items-- use items -->id2cc
    id2cc-->id3



    id3---id3a-->id4
    id3---id3b-->id4
    id4-->id2
