---
title: 'CA1710: Identyfikatory powinny mieć poprawny sufiks'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1710
- IdentifiersShouldHaveCorrectSuffix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectSuffix
- CA1710
ms.assetid: 2b8e6dce-b4e8-4a66-ba9a-6b79be5bfe8c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50c67c614c4ece8f1925f4133f749a1c5747fe31
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234171"
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710: Identyfikatory powinny mieć poprawny sufiks

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectSuffix|
|CheckId|CA1710|
|Kategoria|Microsoft.Naming|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna

Identyfikator nie ma poprawnego sufiksu.

Domyślnie ta reguła sprawdza tylko widoczne na zewnątrz identyfikatory, ale [można to skonfigurować](#configurability).

## <a name="rule-description"></a>Opis reguły

Według Konwencji nazwy typów, które poszerzają pewne typy podstawowe lub implementują określone interfejsy lub typy pochodzące z tych typów, mają sufiks skojarzony z typem podstawowym lub interfejsem.

Konwencje nazewnictwa zapewniają typowy wygląd bibliotek przeznaczonych dla środowiska uruchomieniowego języka wspólnego. Zmniejsza to krzywą uczenia, która jest wymagana w przypadku nowych bibliotek oprogramowania i zwiększa zaufanie klienta, że biblioteka została opracowana przez kogoś, kto ma doświadczenie w tworzeniu kodu zarządzanego.

Poniższa tabela zawiera listę typów podstawowych i interfejsów, które mają skojarzone sufiksy.

|Typ podstawowy/interfejs|Suffix|
|--------------------------|------------|
|<xref:System.Attribute?displayProperty=fullName>|Atrybut|
|<xref:System.EventArgs?displayProperty=fullName>|EventArgs|
|<xref:System.Exception?displayProperty=fullName>|Wyjątek|
|<xref:System.Collections.ICollection?displayProperty=fullName>|Kolekcja|
|<xref:System.Collections.IDictionary?displayProperty=fullName>|Dictionary|
|<xref:System.Collections.IEnumerable?displayProperty=fullName>|Kolekcja|
|<xref:System.Collections.Queue?displayProperty=fullName>|Kolekcja lub Kolejka|
|<xref:System.Collections.Stack?displayProperty=fullName>|Kolekcja lub stos|
|<xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>|Kolekcja|
|<xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|Dictionary|
|<xref:System.Data.DataSet?displayProperty=fullName>|DataSet|
|<xref:System.Data.DataTable?displayProperty=fullName>|Kolekcja lub tabela DataTable|
|<xref:System.IO.Stream?displayProperty=fullName>|Strumień|
|<xref:System.Security.IPermission?displayProperty=fullName>|Uprawnienie|
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|Warunek|
|Delegat programu obsługi zdarzeń.|EventHandler|

Typy implementujące <xref:System.Collections.ICollection> i stanowią uogólniony typ struktury danych, takie jak słownik, stos lub kolejka, są dozwolonymi nazwami, które dostarczają znaczących informacji o zamierzonym użyciu typu.

Typy, które <xref:System.Collections.ICollection> implementują i są kolekcją określonych elementów, mają nazwy kończące się słowem "Collection". Na przykład kolekcja <xref:System.Collections.Queue> obiektów będzie miała nazwę "QueueCollection". Sufiks "Kolekcja" oznacza, że elementy członkowskie kolekcji można wyliczyć przy użyciu `foreach` instrukcji (`For Each` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

Typy, które <xref:System.Collections.IDictionary> implementują, mają nazwy kończące się słowem "dictionary", nawet jeśli <xref:System.Collections.IEnumerable> typ <xref:System.Collections.ICollection>implementuje również lub. Konwencje nazewnictwa "Kolekcja" i "dictionary" umożliwiają użytkownikom rozróżnianie następujących dwóch wzorców wyliczenia.

Typy z sufiksem "Collection" są zgodne z tym wzorcem wyliczenia.

```
foreach(SomeType x in SomeCollection) { }
```

Typy z sufiksem "dictionary" są zgodne z tym wzorcem wyliczenia.

```
foreach(SomeType x in SomeDictionary.Values) { }
```

Obiekt składa się z <xref:System.Data.DataTable> kolekcji obiektów, <xref:System.Data.DataColumn?displayProperty=fullName> które składają się z kolekcji i <xref:System.Data.DataRow?displayProperty=fullName> obiektów, między innymi. <xref:System.Data.DataSet> Kolekcje te implementują <xref:System.Collections.ICollection> się za <xref:System.Data.InternalDataCollectionBase?displayProperty=fullName> pomocą klasy bazowej.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Zmień nazwę typu tak, aby był on sufiksem prawidłowym terminem.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Można bezpiecznie pominąć ostrzeżenie, aby użyć sufiksu "Kolekcja", jeśli typ jest uogólnioną strukturą danych, która może zostać rozszerzona lub który będzie przechowywać dowolny zestaw różnorodnych elementów. W takim przypadku nazwa, która zapewnia istotne informacje dotyczące implementacji, wydajności lub innych cech struktury danych, może mieć sens (na przykład BinaryTree). W przypadkach, gdy typ reprezentuje kolekcję określonego typu (na przykład StringCollection), nie pomijaj ostrzeżenia z tej reguły, ponieważ sufiks wskazuje, że typ można wyliczyć przy użyciu `foreach` instrukcji.

W przypadku innych sufiksów nie należy pomijać ostrzeżenia z tej reguły. Sufiks umożliwia wykrycie zamierzonego użycia z nazwy typu.

## <a name="configurability"></a>Określając

Jeśli uruchamiasz tę regułę z [analizatorów FxCop](install-fxcop-analyzers.md) (a nie ze starszą analizą), możesz skonfigurować, które części bazy kodu mają uruchamiać tę regułę, na podstawie ich dostępności. Na przykład aby określić, że reguła powinna być uruchamiana tylko względem powierzchni niepublicznego interfejsu API, Dodaj następującą parę klucz-wartość do pliku editorconfig w projekcie:

```ini
dotnet_code_quality.ca1710.api_surface = private, internal
```

Tę opcję można skonfigurować tylko dla tej reguły, dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (nazywanie). Aby uzyskać więcej informacji, zobacz [Konfigurowanie analizatorów FxCop](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Powiązane reguły

[CA1711 Identyfikatory nie powinny mieć niepoprawnego sufiksu](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

## <a name="see-also"></a>Zobacz także

- [Atrybuty](/dotnet/standard/design-guidelines/attributes)
- [Obsługa i wywoływanie zdarzeń](/dotnet/standard/events/index)