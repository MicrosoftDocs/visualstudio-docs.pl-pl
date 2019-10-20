---
title: 'CA1704: Identyfikatory powinny być poprawnie napisane | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
helpviewer_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 56ac5e60964621859c77bf53dc4f6c14480b4a83
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669238"
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704: Identyfikatory powinny być napisane poprawnie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldBeSpelledCorrectly|
|CheckId|CA1704|
|Kategoria|Microsoft. nazewnictwo|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Nazwa identyfikatora zawiera jeden lub więcej wyrazów, które nie są rozpoznawane przez bibliotekę sprawdzania pisowni firmy Microsoft. Ta reguła nie sprawdza konstruktorów ani elementów członkowskich o specjalnej nazwie, takich jak metody dostępu get i Set.

## <a name="rule-description"></a>Opis reguły
 Ta reguła analizuje identyfikator w tokenach i sprawdza pisownię każdego tokenu. Algorytm analizy wykonuje następujące przekształcenia:

- Wielkie litery zaczynają nowy token. Na przykład MyNameIsJoe tokenizes do "my", "name", "is", "Jan".

- W przypadku wielu wielkich liter, Ostatnia Wielka litera zaczyna nowy token. Na przykład GUIEditor tokenizes do "GUI", "Edytor".

- Cudzysłowy wiodące i końcowe są usuwane. Na przykład "Sender" tokenizes do "Sender".

- Podkreślenia oznacza koniec tokenu i są usuwane. Na przykład hello_world tokenizes na "Hello", "World".

- Osadzone znaki handlowe są usuwane. Na przykład dla & mat tokenizes "format".

  Domyślnie używana jest wersja angielskojęzyczna (EN) modułu sprawdzania pisowni. Obecnie nie są dostępne żadne inne słowniki językowe.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Popraw pisownię wyrazu lub Dodaj słowo do słownika niestandardowego o nazwie CustomDictionary. XML. Umieść słownik w katalogu instalacyjnym narzędzia, katalogu projektu lub w katalogu, który jest skojarzony z narzędziem w profilu użytkownika (%USERPROFILE%\Application dane \\...). Aby dowiedzieć się, jak dodać słownik niestandardowy do projektu w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], zobacz [How to: Dostosowywanie słownika analizy kodu](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

- Dodaj wyrazy, które nie powinny spowodować naruszenia w ramach słownika/słów/rozpoznanej ścieżki.

- Dodaj wyrazy, które powinny spowodować naruszenie w przypadku słownika/słów/nierozpoznanej ścieżki.

- Dodaj wyrazy, które powinny być oflagowane jako przestarzałe w przypadku słownika/słów/przestarzałej ścieżki. Zobacz temat pokrewna reguła CA1726: Aby uzyskać więcej informacji, [Użyj preferowanych warunków](../code-quality/ca1726-use-preferred-terms.md).

- Dodaj wyjątki do reguł wielkości liter akronimu do słownika/akronimów/CasingExceptions ścieżki.

  Poniżej znajduje się przykład struktury niestandardowego pliku słownika.

```
<Dictionary>
   <Words>
      <Unrecognized>
         <Word>cb</Word>
      </Unrecognized>
      <Recognized>
         <Word>stylesheet</Word>
         <Word>GotDotNet</Word>
      </Recognized>
      <Deprecated>
         <Term PreferredAlternate="EnterpriseServices">ComPlus</Term>
      </Deprecated>
   </Words>
   <Acronyms>
      <CasingExceptions>
         <Acronym>CJK</Acronym>
         <Acronym>Pi</Acronym>
      </CasingExceptions>
   </Acronyms>
</Dictionary>
```

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomiń ostrzeżenie z tej reguły tylko wtedy, gdy słowo jest celowo błędne, a słowo dotyczy ograniczonego zestawu biblioteki. Prawidłowo napisane wyrazy zmniejszają krzywą uczenia, która jest wymagana w przypadku nowych bibliotek oprogramowania.

## <a name="related-rules"></a>Powiązane reguły
 [CA2204: Literały powinny być zapisane poprawnie](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

 [CA1703: Ciągi zasobu powinny być zapisane poprawnie](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

 [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Identyfikatory powinny różnić się nie tylko wielkością liter](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: Identyfikatory nie powinny zawierać podkreśleń](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1726: Używaj preferowanych terminów](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>Zobacz też
 [Instrukcje: Dostosowywanie słownika analizy kodu](../code-quality/how-to-customize-the-code-analysis-dictionary.md)
