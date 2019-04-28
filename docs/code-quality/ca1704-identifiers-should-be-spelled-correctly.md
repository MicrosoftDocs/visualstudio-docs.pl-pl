---
title: 'CA1704: Pisownia identyfikatorów powinna być poprawna'
ms.date: 03/28/2018
ms.topic: reference
f1_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
helpviewer_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8dbfc8081f980b7b9e978da782f1627a88a716a3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62809411"
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704: Pisownia identyfikatorów powinna być poprawna

|||
|-|-|
|TypeName|IdentifiersShouldBeSpelledCorrectly|
|CheckId|CA1704|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Nazwa identyfikatora zawiera jeden lub więcej wyrazów, które nie są rozpoznawane przez bibliotekę sprawdzania pisowni Microsoft. Ta zasada nie Sprawdź konstruktorów lub członków o nazwie specjalne, takie jak pobieranie i ustaw metod dostępu do właściwości.

## <a name="rule-description"></a>Opis reguły

Ta reguła analizuje identyfikator na tokeny oraz sprawdzając pisownię każdego tokenu. Algorytm analizy wykonuje następujące przekształcenia:

- Wielkie litery uruchomić nowy token. Na przykład MyNameIsJoe tokenizes "Mój", "Name", "Is", "Jan".

- Wiele wielkich liter ostatni wielką literą rozpoczyna się nowy token. Na przykład GUIEditor tokenizes do "Graficznym interfejsem użytkownika", "Editor".

- Początkowe i końcowe apostrofy są usuwane. Na przykład "nadawca" tokenizes do "sender".

- Podkreślenia oznaczającego koniec token i są usuwane. Na przykład Hello_world tokenizes do "Hello", "world".

- Takie osadzone znaki zostaną usunięte. Na przykład w przypadku & mat tokenizes do "format".

## <a name="language"></a>Język

Moduł sprawdzania pisowni sprawdza obecnie wyłącznie w odniesieniu do słowników kulturę opartą na język angielski. Możesz zmienić kulturę projektu w pliku projektu, dodając **CodeAnalysisCulture** elementu.

Na przykład:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Jeśli ustawisz kultury na coś innego niż kulturę opartą na język angielski, ten reguł analizy kodu dyskretnie jest wyłączone.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, Popraw pisownię wyrazu, lub Dodaj ten wyraz do słownika niestandardowego.

### <a name="to-add-words-to-a-custom-dictionary"></a>Aby dodać wyrazy do słownika niestandardowego

Nazwa pliku niestandardowego słownika XML *CustomDictionary.xml*. Umieść słowniku, w katalogu instalacji narzędzia do katalogu projektu lub katalogu, który jest skojarzony z narzędzia w ramach profilu użytkownika (*%USERPROFILE%\Application danych\\...* ). Aby dowiedzieć się, jak dodać słownika niestandardowego do projektu programu Visual Studio, zobacz [jak: Dostosowywanie słownika analizy kodu](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

- Dodaj wyrazy, które nie powinny powodować naruszenie w ścieżce słów/słownik/Recognized.

- Dodawanie wyrazów, która powinna powodować naruszenie w ścieżce słów/słownik/nierozpoznane.

- Dodaj wyrazy, które powinny zostać oznaczone jako przestarzałe w ścieżce słów/słownik/przestarzały. Zobacz temat powiązane reguły [CA1726: Używaj preferowanych terminów](../code-quality/ca1726-use-preferred-terms.md) Aby uzyskać więcej informacji.

- Dodać wyjątki do reguł stosowania wielkości liter akronim ścieżkę akronimów/słownik/CasingExceptions.

Oto przykład struktury pliku słownika niestandardowego:

```xml
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

Pomijaj ostrzeżeń dla tej reguły, tylko wtedy, gdy dane słowo jest celowo błędnie napisane słowa mają zastosowanie do ograniczonego zestawu biblioteki. Poprawnie właściwej słów skrócić czas nauki, które jest wymagane nowe biblioteki oprogramowania.

## <a name="related-rules"></a>Powiązane reguły

- [CA2204: Literały powinny być zapisane poprawnie](../code-quality/ca2204-literals-should-be-spelled-correctly.md)
- [CA1703: Ciągi zasobów, które powinny być zapisane poprawnie](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Identyfikatory powinny różnić się przez więcej niż wielkością liter](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
- [CA1707: Identyfikatory nie powinny zawierać podkreśleń](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)
- [CA1726: Używaj preferowanych terminów](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Dostosowywanie słownika analizy kodu](../code-quality/how-to-customize-the-code-analysis-dictionary.md)
