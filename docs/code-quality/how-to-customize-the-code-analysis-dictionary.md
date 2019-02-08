---
title: 'Instrukcje: Dostosowywanie słownika analizy kodu'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code analysis dictionary
- custom dictionary, code analysis
- dictionary, code analysis
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 71ba70f536074365b3b0ead56b845216918f1a6f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55919849"
---
# <a name="how-to-customize-the-code-analysis-dictionary"></a>Instrukcje: Dostosowywanie słownika analizy kodu
Analiza kodu użyto słownika wbudowanego do sprawdzenia identyfikatorów w kodzie w poszukiwaniu błędów pisowni, gramatyki wielkości liter i innych konwencje nazewnictwa wytycznych programu .NET Framework. Można utworzyć słownika niestandardowego pliku Xml, aby dodać, usunąć lub zmodyfikować warunki, skróty i akronimów do wbudowanych słownika.

 Załóżmy, że Twój kod zawiera klasę o nazwie **DoorKnokker**. Analiza kodu będzie identyfikować nazwę jako złożonej z dwóch słów: **drzwi** i **knokker**. Wywołałby ostrzeżenie, **knokker** nie została wpisana poprawnie. Aby wymusić analizy kodu, rozpoznawał pisowni, należy dodać termin **knokker** do słownika niestandardowego.

## <a name="to-create-a-custom-dictionary"></a>Aby utworzyć słownik niestandardowy
 Utwórz plik o nazwie **CustomDictionary.xml**.

 Zdefiniuj swoje podasz niestandardowe wyrazy, korzystając z następującej struktury XML:

```
<Dictionary>
      <Words>
         <Unrecognized>
            <Word>knokker</Word>
         </Unrecognized>
         <Recognized>
            <Word></Word>
         </Recognized>
         <Deprecated>
            <Term PreferredAlternate=""></Term>
         </Deprecated>
         <Compound>
            <Term CompoundAlternate=""></Term>
         </Compound>
         <DiscreteExceptions>
            <Term></Term>
         </DiscreteExceptions>
      </Words>
      <Acronyms>
         <CasingExceptions>
            <Acronym></Acronym>
         </CasingExceptions>
      </Acronyms>
   </Dictionary>
```

## <a name="custom-dictionary-elements"></a>Słownik niestandardowy elementów
 Można zmodyfikować zachowanie słownika analizy kodu, dodając warunki jako tekst wewnętrzny z następujących elementów do słownika:

- [Słownik/słów/rozpoznane/programu Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)

- [Słownik/słów/nierozpoznany/programu Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)

- [Słownik/słów/przestarzałe/termin [@PreferredAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)

- [Słownik/słów/złożone/termin [@CompoundAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)

- [Słownik/słów/DiscreteExceptions/termin](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)

- [Słownik/akronimów/CasingExceptions/akronim](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)

###  <a name="BKMK_DictionaryWordsRecognizedWord"></a> Słownik/słów/rozpoznane/programu Word
 Aby uwzględnić termin na liście terminów, które identyfikują analizy kodu jako poprawnie zapisany, należy dodać termin jako tekst wewnętrzny elementu słownik/słów/Recognized/programu Word. Warunki w elementach słownik/słów/Recognized/słowa nie jest rozróżniana wielkość liter.

 **Przykład**

```
<Dictionary>
      <Words>
         <Recognized>
            <Word>knokker</Word>
            ...
         </Recognized>
         ...
      </Words>
      ...
</Dictionary>
```

 Warunki w węzłach słów/słownik/Recognized są stosowane do następujących reguł analizy kodu:

-   [CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702: Wyrazy złożone powinny mieć prawidłową wielkość liter](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

-   [CA1703: Ciągi zasobów, które powinny być zapisane poprawnie](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

-   [CA1704: Identyfikatory powinny być zapisane poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

-   [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

-   [CA1726: Używaj preferowanych terminów](../code-quality/ca1726-use-preferred-terms.md)

-   [CA2204: Literały powinny być zapisane poprawnie](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

###  <a name="BKMK_DictionaryWordsUnrecognizedWord"></a> Słownik/słów/nierozpoznany/programu Word
 Aby wykluczyć termin z listy terminów, które identyfikują analizy kodu jako poprawnie zapisany, Dodaj wyrażenie, aby wykluczyć je jako tekst wewnętrzny elementu słownik/słów/nierozpoznane/programu Word. Warunki w elementach słownik/słów/nierozpoznane/słowa nie jest rozróżniana wielkość liter.

 **Przykład**

```
<Dictionary>
      <Words>
         <Unrecognized>
            <Word>meth</Word>
            ...
         </Unrecognized>
         ...
      </Words>
      ...
</Dictionary>
```

 Warunki w węźle słów/słownik/nierozpoznane są stosowane do następujących reguł analizy kodu:

-   [CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702: Wyrazy złożone powinny mieć prawidłową wielkość liter](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

-   [CA1703: Ciągi zasobów, które powinny być zapisane poprawnie](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

-   [CA1704: Identyfikatory powinny być zapisane poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

-   [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

-   [CA1726: Używaj preferowanych terminów](../code-quality/ca1726-use-preferred-terms.md)

-   [CA2204: Literały powinny być zapisane poprawnie](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

###  <a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a> Słownik/słów/przestarzałe/termin [@PreferredAlternate]
 Aby dołączyć termin na liście warunków, które identyfikują analizy kodu, jako przestarzałe, należy dodać termin jako tekst wewnętrzny elementu słownik/słów/przestarzałe/termin. Przestarzałe termin jest programu word, która została wpisana poprawnie, ale nie powinny być używane.

 Aby dołączyć proponowany termin alternatywny ostrzeżenia, należy określić alternatywna w atrybucie PreferredAlternate elementu terminu. Wartość atrybutu można pozostawić puste, jeśli nie chcesz sugerować alternatywne.

- Przestarzałe termin w słownika / / element uznane za przestarzałe/termin nie jest rozróżniana wielkość liter.

- Wartość atrybutu PreferredAlternate jest rozróżniana wielkość liter. Użyj pisanymi wielkimi literami dla złożonych alternatyw.

  **Przykład**

```
<Dictionary>
      <Words>
         <Deprecated>
            <Term PreferredAlternate="LogOn">login</Term>
            ...
         </Deprecated>
         ...
      </Words>
      ...
</Dictionary>
```

 Warunki w węźle słów/słownik/przestarzałe, są stosowane do następujących reguł analizy kodu:

-   [CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702: Wyrazy złożone powinny mieć prawidłową wielkość liter](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

-   [CA1703: Ciągi zasobów, które powinny być zapisane poprawnie](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

-   [CA1704: Identyfikatory powinny być zapisane poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

-   [CA1726: Używaj preferowanych terminów](../code-quality/ca1726-use-preferred-terms.md)

###  <a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a> Słownik/słów/złożone/termin [@CompoundAlternate]
 Słownik wbudowany identyfikuje niektóre terminy jako pojedynczy, odrębny terminy zamiast złożone termin. Dołącz termin do listy warunków, które identyfikują analizy kodu, jako wyraz złożony i określ poprawny wielkość liter w wyrazie termin, należy dodać termin jako tekst wewnętrzny elementu słownik/słów/złożone/termin. W atrybucie CompoundAlternate elementu terminu Określ poszczególnych wyrazów składających się termin złożone przez pierwszą literę poszczególnych wyrazów (pisanymi wielkimi literami). Należy pamiętać, że okres określony w tekst wewnętrzny jest automatycznie dodawany do listy słów/słownik/DiscreteExceptions.

- Przestarzałe termin w słownika / / element uznane za przestarzałe/termin nie jest rozróżniana wielkość liter.

- Wartość atrybutu PreferredAlternate jest rozróżniana wielkość liter. Użyj pisanymi wielkimi literami dla złożonych alternatyw.

  **Przykład**

```
<Dictionary>
      <Words>
         <Compound>
            <Term CompoundAlternate="CheckBox">checkbox</Term>
            ...
         </Compound>
         ...
      </Words>
      ...
</Dictionary>
```

 Warunki w węźle słów/słownik/złożone są stosowane do następujących reguł analizy kodu:

-   [CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702: Wyrazy złożone powinny mieć prawidłową wielkość liter](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

-   [CA1703: Ciągi zasobów, które powinny być zapisane poprawnie](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

-   [CA1704: Identyfikatory powinny być zapisane poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

###  <a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a> Słownik/słów/DiscreteExceptions/termin
 Aby wykluczyć termin na liście warunków, które identyfikują analizy kodu, jako pojedynczy, odrębny programu word, gdy wyrażenie jest sprawdzana przez reguł stosowania wielkości liter dla wyrazy złożone, Dodaj termin jako tekst wewnętrzny elementu słownik/słów/DiscreteExceptions/termin. Termin w elemencie słownik/słów/DiscreteExceptions/termin nie jest rozróżniana wielkość liter.

 **Przykład**

```
<Dictionary>
      <Words>
         <DiscreteExceptions>
            <Term>checkbox</Term>
            ...
         </DiscreteExceptions>
         ...
      </Words>
      ...
</Dictionary>
```

 Warunki w węźle słów/słownik/DiscreteExceptions są stosowane do następujących reguł analizy kodu:

-   [CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

-   [CA1702: Wyrazy złożone powinny mieć prawidłową wielkość liter](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

###  <a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a> Słownik/akronimów/CasingExceptions/akronim
 Dołącz akronim listy warunków, które identyfikują analizy kodu, co to jest poprawna i wskazują, jak zasady akronim, gdy wyrażenie jest sprawdzana przez wielkość liter w wyrazie wyrazy złożone, Dodaj termin jako tekst zawarty wewnątrz słownik/akronimów/CasingExceptions / Acronym element. Akronimem w elemencie słownik/akronimów/CasingExceptions/akronim jest uwzględniana wielkość liter.

 **Przykład**

```
<Dictionary>
      <Acronyms>
         <CasingExceptions>
            <Acronym>NESW</Acronym>   <!-- North East South West -->
            ...
         </CasingExceptions>
         ...
      </Acronyms>
      ...
</Dictionary>
```

 Warunki w węźle akronimów/słownik/CasingExceptions są stosowane do następujących reguł analizy kodu:

-   [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

##  <a name="BKMK_ToApplyACustomDictionaryToAProject"></a> Aby zastosować słownika niestandardowego do projektu

1.  W **Eksploratora rozwiązań**, użyj jednej z następujących procedur:

2.  Aby dodać słownika do pojedynczego projektu, kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij przycisk **Dodaj istniejący element**. Określ plik w **Dodaj istniejący element** okno dialogowe.

3.  Aby dodać słownika, która jest współużytkowana przez dwa lub więcej projektów, Znajdź plik do udziału w **Dodaj istniejący element** okna dialogowego kliknij strzałkę w dół na **Dodaj** przycisk, a następnie kliknij przycisk **Dodaj jako łącze** .

4.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **CustomDictionary.xml** nazwę pliku i kliknij przycisk **właściwości**.

5.  Z **Build Action** listy wybierz **CodeAnalysisDictionary**.

6.  Z **Kopiuj do katalogu wyjściowego** listy wybierz **nie Kopiuj**.