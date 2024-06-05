```mermaid
flowchart LR
    id0(((START)))
    id1["`**Player Character**`"]
    id1a[Perk Modifier]

    id2[Choices]
    id3[Enemy Attacks]

    id2a[Fight]
    id2aa[Brawl]
    id2ab[Melee]
    id2ac[Ranged]

    id2c[Item]
    id2cb["`List of Items`"]

    id2d[Flee]


    id3a[Dodge]
    id3b[Fight Back]
    id4["`**Resolve**`"]
    id5[Player HP > 0]
    id6[Player HP = 0]
    id7(((Game Over)))
    id8[Perk Modifier]
    id9{{Enemy Fights Back}}
    id10{ENEMY}

    id0-->id1
    id1-->id1a
    id1a-- if DEX higher than enemy -->id2
    id1a-- if DEX lower than enemy -->id3
    id2-->id2a
    id2-->id2c
    id2-->id2d

    id2a-->fight
    subgraph fight
   id2aa
   id2ab
   id2ac
    end

    fight-->id8
    id8-->id9
    id9-- enemy fight back fails -->id10

    id2c--> Items
    subgraph Items
    id2cb
    end

    Items-- after using item on self-->id3
    



    id3---id3a-->id4
    id3---id3b-->id4
    id4-->id5
    id4-->id6
    id5-->id2
    id6-->id7
```