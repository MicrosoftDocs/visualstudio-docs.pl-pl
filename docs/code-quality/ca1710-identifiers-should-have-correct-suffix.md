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
ms.openlocfilehash: 154d7d36c949ac361f938aa7d8608251c2a9adee
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841910"
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710: Identyfikatory powinny mieć poprawny sufiks

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectSuffix|
|CheckId|CA1710|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Identyfikator nie ma poprawny sufiks.

Domyślnie ta reguła przegląda tylko identyfikatory widocznego na zewnątrz, ale jest to [konfigurowalne](#configurability).

## <a name="rule-description"></a>Opis reguły

Według Konwencji nazwy typów, które rozszerzają pewne typy podstawowe lub implementują określone interfejsy lub typy pochodzące z tych typów, mają sufiks, który jest skojarzony z typem bazowym lub interfejsem.

Konwencje nazewnictwa Obejmij wygląd wspólnych bibliotek obiektu docelowego środowiska uruchomieniowego języka wspólnego. Zmniejsza to nauki, jest wymagany dla nowe biblioteki oprogramowania, która zwiększa poziom zaufania klientów, że biblioteka został opracowany przez osobę, która ma doświadczenie w tworzenie kodu zarządzanego.

W poniższej tabeli wymieniono typy podstawowe i interfejsy, które mają skojarzone sufiksy.

|Interfejs podstawowy|Suffix|
|--------------------------|------------|
|<xref:System.Attribute?displayProperty=fullName>|Atrybut|
|<xref:System.EventArgs?displayProperty=fullName>|EventArgs|
|<xref:System.Exception?displayProperty=fullName>|Wyjątek|
|<xref:System.Collections.ICollection?displayProperty=fullName>|Kolekcja|
|<xref:System.Collections.IDictionary?displayProperty=fullName>|Słownik|
|<xref:System.Collections.IEnumerable?displayProperty=fullName>|Kolekcja|
|<xref:System.Collections.Queue?displayProperty=fullName>|Kolekcja lub kolejki|
|<xref:System.Collections.Stack?displayProperty=fullName>|Kolekcja lub stos|
|<xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>|Kolekcja|
|<xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|Słownik|
|<xref:System.Data.DataSet?displayProperty=fullName>|DataSet|
|<xref:System.Data.DataTable?displayProperty=fullName>|Kolekcji lub elementu DataTable|
|<xref:System.IO.Stream?displayProperty=fullName>|Strumień|
|<xref:System.Security.IPermission?displayProperty=fullName>|Uprawnienie|
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|Warunek|
|Delegat programu obsługi zdarzeń.|EventHandler|

Typami, które implementują <xref:System.Collections.ICollection> i są uogólnionych typów struktury danych, takich jak słownik, stosu lub kolejki są dozwolone nazwy, które zawierają istotne informacje o zamierzone użycie tego typu.

Typami, które implementują <xref:System.Collections.ICollection> i Kolekcja elementów określonego ma nazwy kończące się wyrazem "Collection". Na przykład zbiór <xref:System.Collections.Queue> obiekty będzie mieć nazwę "QueueCollection". Sufiks "Collection" oznacza, że elementy członkowskie kolekcji mogą być wyliczane przy użyciu `foreach` (`For Each` w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) instrukcji.

Typami, które implementują <xref:System.Collections.IDictionary> ma nazwy kończące się wyrazem "Słownik", nawet jeśli typ implementuje również <xref:System.Collections.IEnumerable> lub <xref:System.Collections.ICollection>. Konwencje nazewnictwa sufiksem "Collection" i "Słownik" pozwalają użytkownikom na rozróżnienie między następujące wzorce dwóch wyliczenia.

Typy z sufiksem "Collection" korzystać z tego wzoru wyliczenia.

```
foreach(SomeType x in SomeCollection) { }
```

Typy z sufiksem "Słownik" korzystać z tego wzoru wyliczenia.

```
foreach(SomeType x in SomeDictionary.Values) { }
```

A <xref:System.Data.DataSet> obiekt składa się z kolekcją <xref:System.Data.DataTable> obiektów, które składają się z kolekcji <xref:System.Data.DataColumn?displayProperty=fullName> i <xref:System.Data.DataRow?displayProperty=fullName> obiektów, między innymi. Te kolekcje implementują <xref:System.Collections.ICollection> za pośrednictwem base <xref:System.Data.InternalDataCollectionBase?displayProperty=fullName> klasy.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Tak, aby jako sufiks terminem poprawne, należy zmienić nazwę typu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jest bezpieczne ostrzeżenia używać sufiksem "Collection", jeśli typ jest strukturą danych uogólniony, może zostać rozszerzony lub który będzie przechowywać dowolny zestaw różnych elementów. W tym przypadku nazwę, która zawiera istotne informacje dotyczące implementacji, wydajności i inne cechy charakterystyczne struktury danych może mieć sens (na przykład BinaryTree). W przypadkach, gdzie typ reprezentuje kolekcję określonego typu (na przykład właściwości StringCollection), nie Pomijaj ostrzeżeń dla tej reguły, ponieważ sufiks wskazuje, że typ mogą być wyliczane przy użyciu `foreach` instrukcji.

Dla innych sufiksów nazw głównych nie Pomijaj ostrzeżeń dla tej reguły. Sufiks umożliwia zamierzonego użycia, aby być widoczne na podstawie nazwy typu.

## <a name="configurability"></a>Konfigurowalne

Po uruchomieniu tej reguły z [analizatory FxCop analizujące kod](install-fxcop-analyzers.md) (a nie przy użyciu statycznej analizy kodu) części, które można skonfigurować Twojej bazy kodu do uruchomienia tej reguły na, oparte na ich dostępność. Na przykład aby określić, że zasady powinny być uruchamiane wyłącznie w odniesieniu do powierzchni interfejsu API niepublicznych, Dodaj następujące pary klucz wartość w pliku .editorconfig w projekcie:

```ini
dotnet_code_quality.ca1710.api_surface = private, internal
```

Można skonfigurować tę opcję tylko reguły dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (nazewnictwa). Aby uzyskać więcej informacji, zobacz [analizatory FxCop analizujące kod z skonfigurować](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Powiązane reguły

[CA1711: Identyfikatory nie powinny mieć niepoprawnego sufiksu](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

## <a name="see-also"></a>Zobacz także

- [Atrybuty](/dotnet/standard/design-guidelines/attributes)
- [Obsługa i wywoływanie zdarzeń](/dotnet/standard/events/index)