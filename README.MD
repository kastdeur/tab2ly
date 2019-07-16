# Tab2Ly
A utility to process textual tablature into a lilypond score.


For example, the bass riff from Feel Good Inc. by Gorillaz
```
Gs|-----------------|-----------------|-----------------|-----------------||
Ds|-----------------|-----------------|-----------------|-----------------||
As|---------------3-|---2-------------|-0-----0-3-2-----|-----------------||
Es|-0-----0-2-3-----|-----------------|---------------3-|---0---9/12------||
    1 a 2 a 3 a 4 a | 1 a 2 a 3 a 4 a | 1 a 2 a 3 a 4 a | 1 a 2 a 3 a 4 a ||
```
should turn into
```lilypond

tabMusic = \relative es,, {
	\cadenzaOn 
	es8\4 r8    r8 es8\4    f8\4 fis8\4 r8 b8\3 \bar "|"
	r8 bes8~\3   bes2.\3 \bar "|"
	as8\3 r8    r8 as8\3  b8\3 bes8\3 r8 fis8\4 \bar "|"
	r8 es4\4      c'8\4\glissando es4\4 r4  \bar "||"
}
\new TabStaff \with {
	stringTunings = \stringTuning <e,, a,, d, g,>
} {
	\tabMusic
}
```
