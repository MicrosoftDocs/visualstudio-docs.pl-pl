---
title: 'Porady: dostosowywanie słownika analizy kodu'
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
ms.openlocfilehash: 5ec2afbdad9e68de38fcee8e4477a73851718e9d
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72535841"
---
# <a name="how-to-customize-the-code-analysis-dictionary"></a>Porady: dostosowywanie słownika analizy kodu

Analiza kodu używa wbudowanego słownika do sprawdzania identyfikatorów w kodzie pod kątem błędów w pisowni, przypadku gramatyki i innych konwencji nazewnictwa w wytycznych dotyczących projektowania platformy .NET. Możesz utworzyć niestandardowy plik XML słownika, aby dodać, usunąć lub zmodyfikować terminy, skróty i akronimy do wbudowanego słownika.

Załóżmy na przykład, że kod zawiera klasę o nazwie **DoorKnokker**. Analiza kodu powinna identyfikować nazwę jako związek dwóch wyrazów: **drzwi** i **knokker**. Następnie zostanie zgłoszone ostrzeżenie, że **knokker** nie został wpisany poprawnie. Aby wymusić rozpoznanie pisowni przez analizę kodu, możesz dodać termin **knokker** do słownika niestandardowego.

## <a name="to-create-a-custom-dictionary"></a>Aby utworzyć słownik niestandardowy

Utwórz plik o nazwie **CustomDictionary. XML**.

Zdefiniuj niestandardowe słowa przy użyciu następującej struktury XML:

```xml
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

## <a name="custom-dictionary-elements"></a>Elementy słownika niestandardowego

Możesz zmodyfikować zachowanie słownika analizy kodu, dodając warunki jako tekst wewnętrzny następujących elementów w słowniku niestandardowym:

- [Słownik/wyrazy/rozpoznane/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)

- [Słownik/wyrazy/nierozpoznane/słowo](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)

- [Słownik/wyrazy/przestarzałe/termin [@PreferredAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)

- [Słownik/wyrazy/związek/wyrażenie [@CompoundAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)

- [Słownik/wyrazy/DiscreteExceptions/Term](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)

- [Słownik/akronimy/CasingExceptions/akronim](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)

### <a name="BKMK_DictionaryWordsRecognizedWord"></a>Słownik/wyrazy/rozpoznane/Word

Aby uwzględnić termin na liście warunków identyfikowanych przez analizę kodu jako prawidłowo wpisany, należy dodać termin jako tekst wewnętrzny słownika/wyrazów/rozpoznany/wyraz. W przypadku wyrazów/słów/rozpoznaje/elementy słowa nie jest rozróżniana wielkość liter.

**Przykład**

```xml
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

Warunki dotyczące słownika/słów/rozpoznanych węzłów są stosowane do następujących reguł analizy kodu:

- [CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter](../code-quality/ca1701.md)

- [CA1702: W wyrazach złożonych należy poprawnie używać wielkości liter](../code-quality/ca1702.md)

- [CA1703: Ciągi zasobu powinny być zapisane poprawnie](../code-quality/ca1703.md)

- [CA1704: Identyfikatory powinny być zapisane poprawnie](../code-quality/ca1704.md)

- [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709.md)

- [CA1726: Używaj preferowanych terminów](../code-quality/ca1726.md)

- [CA2204: Literały powinny być zapisane poprawnie](../code-quality/ca2204.md)

### <a name="BKMK_DictionaryWordsUnrecognizedWord"></a>Słownik/wyrazy/nierozpoznane/słowo

Aby wykluczyć termin z listy warunków identyfikowanych przez analizę kodu jako prawidłowo wpisany, Dodaj termin do wykluczenia jako tekst wewnętrzny słownika/słów/nierozpoznanego/słowa. W warunkach słownika/słów/nierozpoznawalnych/nierozpoznanych elementów słowa nie jest rozróżniana wielkość liter.

**Przykład**

```xml
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

Warunki w słowniku/słowach/nierozpoznanym węźle są stosowane do następujących reguł analizy kodu:

- [CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter](../code-quality/ca1701.md)

- [CA1702: W wyrazach złożonych należy poprawnie używać wielkości liter](../code-quality/ca1702.md)

- [CA1703: Ciągi zasobu powinny być zapisane poprawnie](../code-quality/ca1703.md)

- [CA1704: Identyfikatory powinny być zapisane poprawnie](../code-quality/ca1704.md)

- [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709.md)

- [CA1726: Używaj preferowanych terminów](../code-quality/ca1726.md)

- [CA2204: Literały powinny być zapisane poprawnie](../code-quality/ca2204.md)

### <a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a>Słownik/wyrazy/przestarzałe/termin [@PreferredAlternate]

Aby uwzględnić termin na liście warunków identyfikowanych jako przestarzałe przez analizę kodu, Dodaj termin jako tekst wewnętrzny słownika/wyrazów/przestarzałych/terminowych. Przestarzały termin to wyraz, który jest wpisany prawidłowo, ale nie powinien być używany.

Aby w ostrzeżeniu uwzględnić sugerowany termin alternatywny, określ alternatywę w atrybucie PreferredAlternate elementu Term. Wartość atrybutu można pozostawić pustą, jeśli nie chcesz, aby zasugerować alternatywę.

- Jako przestarzały termin w słowniku/słowach/przestarzały element/wyrażenie nie jest rozróżniana wielkość liter.

- W wartości atrybutu PreferredAlternate jest rozróżniana wielkość liter. Użyj przypadku w języku Pascal dla alternatywnych odmian.

**Przykład**

```xml
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

Warunki w słowniku/słowach/przestarzałych węzłach są stosowane do następujących reguł analizy kodu:

- [CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter](../code-quality/ca1701.md)

- [CA1702: W wyrazach złożonych należy poprawnie używać wielkości liter](../code-quality/ca1702.md)

- [CA1703: Ciągi zasobu powinny być zapisane poprawnie](../code-quality/ca1703.md)

- [CA1704: Identyfikatory powinny być zapisane poprawnie](../code-quality/ca1704.md)

- [CA1726: Używaj preferowanych terminów](../code-quality/ca1726.md)

### <a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a>Słownik/wyrazy/związek/wyrażenie [@CompoundAlternate]

Wbudowany słownik identyfikuje niektóre terminy jako pojedyncze, osobne warunki, a nie termin złożony. Aby uwzględnić termin na liście warunków identyfikowanych przez analizę kodu jako wyraz złożony i aby określić poprawną wielkość liter w danym okresie, Dodaj termin jako wewnętrzny tekst słownika/wyrazów/elementu złożonego/terminu. W atrybucie CompoundAlternate elementu Term Określ poszczególne wyrazy, które składają się na termin złożony, wielką literą pojedynczych wyrazów (przypadek Pascal). Należy zauważyć, że termin określony w tekście wewnętrznym jest automatycznie dodawany do listy słownik/wyrazy/DiscreteExceptions.

- W warunku złożonym w słowniku/słowach/elemencie złożonym/Term nie jest rozróżniana wielkość liter.

- W wartości atrybutu CompoundAlternate jest rozróżniana wielkość liter. Użyj przypadku w języku Pascal dla alternatywnych odmian.

**Przykład**

```xml
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

Warunki w słowniku/słowach/węźle złożonym są stosowane do następujących reguł analizy kodu:

- [CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter](../code-quality/ca1701.md)

- [CA1702: W wyrazach złożonych należy poprawnie używać wielkości liter](../code-quality/ca1702.md)

- [CA1703: Ciągi zasobu powinny być zapisane poprawnie](../code-quality/ca1703.md)

- [CA1704: Identyfikatory powinny być zapisane poprawnie](../code-quality/ca1704.md)

### <a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a>Słownik/wyrazy/DiscreteExceptions/Term

Aby wykluczyć termin z listy warunków, które Analiza kodu identyfikuje jako pojedynczy, odrębny wyraz, gdy termin jest sprawdzany przez reguły wielkości liter dla wyrazów złożonych, Dodaj termin jako tekst wewnętrzny słownika/wyrazów/DiscreteExceptions/Term. W warunku słownika/słów/DiscreteExceptions/Term nie jest rozróżniana wielkość liter.

**Przykład**

```xml
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

Warunki w węźle słownik/wyrazy/DiscreteExceptions są stosowane do następujących reguł analizy kodu:

- [CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter](../code-quality/ca1701.md)

- [CA1702: W wyrazach złożonych należy poprawnie używać wielkości liter](../code-quality/ca1702.md)

### <a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a>Słownik/akronimy/CasingExceptions/akronim

Aby dołączyć akronim na liście warunków identyfikowanych przez analizę kodu jako prawidłowo wpisany i aby wskazać, jak akronim ma być sprawdzany przez reguły wielkości liter dla wyrazów złożonych, Dodaj termin jako tekst wewnętrzny słownika/akronimów/CasingExceptions/ Akronim elementu. Akronim w elemencie dictionary/Akronims/CasingExceptions/akronim jest uwzględniana wielkość liter.

**Przykład**

```xml
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

Warunki w węźle słownik/akronimy/CasingExceptions są stosowane do następujących reguł analizy kodu:

- [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709.md)

## <a name="BKMK_ToApplyACustomDictionaryToAProject"></a>Aby zastosować słownik niestandardowy do projektu

1. W **Eksplorator rozwiązań**Użyj jednej z następujących procedur:

2. Aby dodać słownik do pojedynczego projektu, kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij pozycję **Dodaj istniejący element**. Określ plik w oknie dialogowym **Dodaj istniejący element** .

3. Aby dodać słownik współużytkowany przez dwa lub więcej projektów, zlokalizuj plik do udostępnienia w oknie dialogowym **Dodaj istniejący element** , kliknij strzałkę w dół na przycisku **Dodaj** , a następnie kliknij przycisk **Dodaj jako link**.

4. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy nazwę pliku **CustomDictionary. XML** i kliknij polecenie **Właściwości**.

5. Z listy **Akcja kompilacji** wybierz pozycję **CodeAnalysisDictionary**.

6. Z listy **Kopiuj do katalogu wyjściowego** wybierz pozycję nie **Kopiuj**.
