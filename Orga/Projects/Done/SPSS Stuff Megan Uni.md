[Portfolio Google Drive](https://drive.google.com/drive/folders/1vhGEcWP3D9NnooH7KQCUhLfxVqdmiF6n)

Artefakt 3: Anwendung von statistischen/ experimentellen Methoden der Datenerhebung und -analyse (SPSS-Syntax & Lauftext mit Tabellen & Grafiken)

Folien: [SPSS-Übung für Artefakt 3](https://drive.google.com/file/d/1dnGiqqzoUhDeb7IUD9sqiaH82zVjYtjG/view?usp=sharing)

[Fragebogen](https://drive.google.com/file/d/1ZmP2MSUXS2G0j2nGwpmCClsfWcLvzUOz/view)

Anforderungen:

- Sorgfältige deskriptive Analysen
- Missing data? → Wie wurde damit umgegangen?
- Widersprüchliche oder unplausible Datenmuster? → Wie wurde damit umgegangen?
- Sind die Analysen gute theoretische begründet worden?
- Haben Sie alle Voraussetzungen der Verfahren geprüft?

Faktorenanalyse

- Stichprobeneignung nach KMO → Über 0.5
- Signifikanz nach Bartlett soll gegeben sein (0,000 ist sehr gut)
- Anti-Image-Korrelation unter 0.5 → Item raus und neu rechnen

Important: 145 How honest were you?

![Image.png](Orga/Projects/Done/SPSS%20Stuff%20Megan%20Uni.assets/Image.png)

96.2% somewhat usable

Alle unabhängigen Variablen zusammenfassen, alle abhängigen Variablen zusammenfassen. Dann ein Test machen!

Test, dass unabhängige Variablen im Zusammenhang stehen: Kovariate-Test

Pearson: 192-198

# Anleitung Setup

Anleitung:

- Setup Medialab
   - Anleitung: "202105_SPSS_Studierende_Anleitung_ServicePortal" in Ilias
   - Get Microsoft Remote Desktop
   - Add Workspace with Fresenius Email
   - Login

![Image.png](Orga/Projects/Done/SPSS%20Stuff%20Megan%20Uni.assets/Image%20(2).png)

- Upload files
   - Click "RDS Studierende"
   - Create folder and upload files (Cmd + C, then Cmd + V in RD)
      - AYS_2006_SoSe_MP2_Artefakt3_6April2022.sps
      - AYS_2006_SoSe_MP2_Artefakt3_upload.sav
- Tricks
   - Connections → Keyboard mode → Unicode
   - Dateneditor → Ansicht → Wertebeschreibungen
   - Ansicht → Variablen
   - Fenster → Hauptsyntax
   - Syntax-Editor: Bearbeiten → Optionen → Viewer → Befehle im Protokoll anzeigen

# Old hypothesis

## Definitions

U1: Question A: Persistent conflict between parents / caregivers and children

- 121 "People in my family often insult or yell at each other"
- 123 "We argue about the same things in my family over and over
- 138 "People in my family have serious arguments"

Question B: Drug and Alcohol abuse

- 95 "How many times 5+ alcoholic bev in a row"
- "Ho many" 0, 1-2, 3-5, 6-9, 10-19, 20-39, 40+
   - 52-77
   - Maybe max this and compare correlation?

Question C: Grades in school

- 20: Grades last year

Question D: Drug/Alcohol abuse in adults around

- 94

## Hyp 1

Persistent conflict between parents / caregivers and children raises the child's risk of drug and alcohol abuse

## Hyp 2

The more a child uses drugs and alcohol, the lower their grades will be in school

## Hyp 3

Children who live with or are exposed to adults who use drugs and alcohol are more likely to engage in drug and alcohol use

# Result Syntax + Output

```other
* Encoding: UTF-8.

DATASET ACTIVATE DataSet1.

*** Explorative Faktorenanalyse

FACTOR
  /VARIABLES q7a to q61 q64 to q144e
  /MISSING LISTWISE 
  /ANALYSIS q7a to q61 q64 to q144e
  /PRINT INITIAL KMO AIC EXTRACTION ROTATION
  /FORMAT SORT BLANK(0.3)
  /PLOT EIGEN
  /CRITERIA FACTORS(15) ITERATE(25)
  /EXTRACTION ML
  /CRITERIA ITERATE(25)
  /ROTATION VARIMAX.

*** Faktor 8 = Depression + Fights at home
    
*** F1 = Depression

COMPUTE f1 = (q45 + q46 + q47 + q48) / 4.
VARIABLE LABELS f1 'Geringes Selbstwertgefühl'.

*** F2 = Fights at home

COMPUTE f2 = (q121 + q123 + q138) / 3.
VARIABLE LABELS f2 'Streit im familiären Umfeld'.

*** Father lives with you - Recoded

COMPUTE q7f_boolean = q7f = 1.
VARIABLE LABELS q7f_boolean 'Father lives with you'.
ADD VALUE LABELS q7f_boolean 1 'Yes' 0 'No'.

*** Fehlende Werte abwählen

COMPUTE missing = nmiss(f1, f2, q7f) = 0.
FILTER OFF.
FILTER by missing.

EXECUTE.

*** Fehlende Werte doppel-checken

MULTIPLE IMPUTATION f1, f1, q7f /IMPUTE METHOD=NONE.

*** Normalverteilung der Variablen prüfen

GRAPH
  /HISTOGRAM(NORMAL)=f1.

GRAPH
  /HISTOGRAM(NORMAL)=f2.

*** Nicht normalverteilt, daher Spearman

NONPAR CORR
  /VARIABLES=f1 f2
  /PRINT=SPEARMAN TWOTAIL NOSIG LOWER
  /MISSING=PAIRWISE.

*** Vergleich mit q7f - Father lives with you

*** f2 ist normalverteilt, daher t-test

T-TEST GROUPS=q7f(1 2)
  /MISSING=ANALYSIS
  /VARIABLES=f2
  /ES DISPLAY(TRUE)
  /CRITERIA=CI(.95).

*** f1 ist nicht normalverteilt, daher Mann-Whitney-U-Test



NPTESTS 
  /INDEPENDENT TEST (f1) GROUP (q7f_boolean) 
  /MISSING SCOPE=ANALYSIS USERMISSING=EXCLUDE
  /CRITERIA ALPHA=0.05  CILEVEL=95.
```

Schritt 1 Faktorenanalyse:

![Image.png](Orga/Projects/Done/SPSS%20Stuff%20Megan%20Uni.assets/Image%20(3).png)

Fehlende Werte:

![Image.png](Orga/Projects/Done/SPSS%20Stuff%20Megan%20Uni.assets/Image%20(4).png)

Verteilung von F1 = Depression

![Image.png](Orga/Projects/Done/SPSS%20Stuff%20Megan%20Uni.assets/Image%20(5).png)

Verteilung von F2 = Fights

![Image.png](Orga/Projects/Done/SPSS%20Stuff%20Megan%20Uni.assets/Image%20(6).png)

Korrelation Spearman-Rho (nicht normalverteilt):

![Image.png](Orga/Projects/Done/SPSS%20Stuff%20Megan%20Uni.assets/Image%20(7).png)

Neuer Faktor: Father lives with you (q7f)

Normalverteilt: t-test f2 vs q7f

![Image.png](Orga/Projects/Done/SPSS%20Stuff%20Megan%20Uni.assets/Image%20(8).png)

Nicht normalverteilt: Mann-Whitney-U-Test f1 vs q7f

![Image.png](Orga/Projects/Done/SPSS%20Stuff%20Megan%20Uni.assets/Image%20(9).png)

Weitere Infos:

![Image.png](Image%20(10).png)

![Image.png](Image%20(11).png)

# Result Syntax + Output Marie

```other
FACTOR
  /VARIABLES q7a to q61 q64 to q144e
  /MISSING LISTWISE 
  /ANALYSIS q7a to q61 q64 to q144e
  /PRINT INITIAL KMO AIC EXTRACTION ROTATION
  /FORMAT BLANK(0.3)
  /PLOT EIGEN
  /CRITERIA FACTORS(15) ITERATE(25)
  /EXTRACTION ML
  /CRITERIA ITERATE(25)
  /ROTATION VARIMAX.

*** Substanzen (Faktor 2)
    
COMPUTE a1 = (SUM(q52 to q61) + sum(q64 to q77)) / 24.

*** Beziehung zur Familie (Faktor 4)

COMPUTE u1 = (q115 + q116 + SUM(q122 to q140)) / 21.

*** Einfach zu beschaffen (Angelehnt an Faktor 3)
    
COMPUTE u2 = (q90 + q91 + q93) / 3.

*** Substanzen ja/nein

COMPUTE u3 = a1 > 1.

*** Glücksspiel
 
 COMPUTE a2 = SUM(q142a to q142i) / 9.

*** Körperliche Auseinandersetzungen
    
COMPUTE a3 = (q39 + q40) / 2.

EXECUTE.

** -> Normalverteilt

GRAPH  /HISTOGRAM=a1.

** -> Normalverteilt

GRAPH  /HISTOGRAM=u1.

** -> Nicht Normalverteilt

GRAPH  /HISTOGRAM=u2.

** Boolean (nicht normalverteilt)

GRAPH  /HISTOGRAM=u3.

** Normalverteilt mit Spitze bei 1??

GRAPH  /HISTOGRAM=a2.

** Nicht normalverteilt

GRAPH  /HISTOGRAM=a3.
```

