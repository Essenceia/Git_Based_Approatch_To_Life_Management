# Chiplets

Instead of having one "big" monolitic chip : break the design up into seperate smaller 
chips that are to be assembled.
** Each individual chiplet is not a complete SOC ** 

## Agruments in favor

### Percived adventages

- yield due to smalled individual chiplets
- node diversity possible
- faster time to market ( re-usablility )
- cheaper / simpler process 

### Arguments agains current node scalling 

- exponenciel cost for new nodes ( 7nm )
- low yields

## Challenges 

### Routing 

This gets complicated on multiple levels. â"You could have half a dozen chiplets, 
you might have different types of memory, be it stacked or side-by-side, and you may be 
looking at using an interposer or an embedded interposer bridge, " adds Felton. 
â"You are basically dealing with multiple levels of substrate integration, 
side-by-side, stacked, embedded, and you need an environment where you can quickly 
evaluate these different scenarios to see what they give you in terms of the overall 
goals.â"

- static time analysis
- parasitic extraction 
- design rule checking ( DRC ) 
- LVS
- timing closure across two chips


---

Market leaders always have been the first to move to the latest node because it 
provided them with scaling, power and performance advantages needed to maintain their 
competitive edge. â"Monolithic scaling is coming to the end of its life for most 
people,â"  says Keith Felton, product marketing manager in the Board System Division 
of Mentor, A Siemens Business. â" 7nm is wickedly expensive, the yield per wafer is 
not that good, and you have to make millions of them in order to cover the NRE. When 
you have a chip that large, you are often better off breaking the design up into 
smaller blocks where you can use the appropriate node point or technology for that part 
of the chip, and then integrate it together on a silicon interposer. You get something 
that is much cheaper. You can bring to market faster. And if you want to do an update, 
you can just replace one or two of the chiplets and have a new product rather than 
having to respin a whole new SoC."

## Sources

https://semiengineering.com/design-for-advanced-packaging/
https://www.computermachines.org/joe/publications/pdfs/hpca2017_exascale_apu.pdf
