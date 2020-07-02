---
title: 'CA1710: Identyfikatory powinny mieć poprawny sufiks | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1710
- IdentifiersShouldHaveCorrectSuffix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectSuffix
- CA1710
ms.assetid: 2b8e6dce-b4e8-4a66-ba9a-6b79be5bfe8c
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ee7ce7c4e9edad9d941b4a70b2a199a37130e43
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543991"
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710: Identyfikatory powinny mieć poprawny sufiks
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|IdentifiersShouldHaveCorrectSuffix|
|CheckId|CA1710|
|Kategoria|Microsoft. nazewnictwo|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Identyfikator nie ma poprawnego sufiksu.

## <a name="rule-description"></a>Opis reguły
 Według Konwencji nazwy typów, które poszerzają pewne typy podstawowe lub implementują określone interfejsy lub typy pochodzące z tych typów, mają sufiks skojarzony z typem podstawowym lub interfejsem.

 Konwencje nazewnictwa zapewniają typowy wygląd bibliotek przeznaczonych dla środowiska uruchomieniowego języka wspólnego. Zmniejsza to krzywą uczenia, która jest wymagana w przypadku nowych bibliotek oprogramowania i zwiększa zaufanie klienta, że biblioteka została opracowana przez kogoś, kto ma doświadczenie w tworzeniu kodu zarządzanego.

 Poniższa tabela zawiera listę typów podstawowych i interfejsów, które mają skojarzone sufiksy.

|Typ podstawowy/interfejs|Przedrostk|
|--------------------------|------------|
|<xref:System.Attribute?displayProperty=fullName>|Atrybut|
|<xref:System.EventArgs?displayProperty=fullName>|EventArgs|
|<xref:System.Exception?displayProperty=fullName>|Wyjątek|
|<xref:System.Collections.ICollection?displayProperty=fullName>|Kolekcja|
|<xref:System.Collections.IDictionary?displayProperty=fullName>|Słownik|
|<xref:System.Collections.IEnumerable?displayProperty=fullName>|Kolekcja|
|<xref:System.Collections.Queue?displayProperty=fullName>|Kolekcja lub Kolejka|
|<xref:System.Collections.Stack?displayProperty=fullName>|Kolekcja lub stos|
|<xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>|Kolekcja|
|<xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|Słownik|
|<xref:System.Data.DataSet?displayProperty=fullName>|DataSet|
|<xref:System.Data.DataTable?displayProperty=fullName>|Kolekcja lub tabela DataTable|
|<xref:System.IO.Stream?displayProperty=fullName>|Strumień|
|<xref:System.Security.IPermission?displayProperty=fullName>|Uprawnienie|
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|Warunek|
|Delegat programu obsługi zdarzeń.|EventHandler|

 Typy implementujące <xref:System.Collections.ICollection> i stanowią uogólniony typ struktury danych, takie jak słownik, stos lub kolejka, są dozwolonymi nazwami, które dostarczają znaczących informacji o zamierzonym użyciu typu.

 Typy, które implementują <xref:System.Collections.ICollection> i są kolekcją określonych elementów, mają nazwy kończące się słowem "Collection". Na przykład kolekcja <xref:System.Collections.Queue> obiektów będzie miała nazwę "QueueCollection". Sufiks "Kolekcja" oznacza, że elementy członkowskie kolekcji można wyliczyć przy użyciu `foreach` `For Each` instrukcji (in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ).

 Typy, które implementują <xref:System.Collections.IDictionary> , mają nazwy kończące się słowem "dictionary", nawet jeśli typ implementuje również <xref:System.Collections.IEnumerable> lub <xref:System.Collections.ICollection> . Konwencje nazewnictwa "Kolekcja" i "dictionary" umożliwiają użytkownikom rozróżnianie następujących dwóch wzorców wyliczenia.

 Typy z sufiksem "Collection" są zgodne z tym wzorcem wyliczenia.

```
foreach(SomeType x in SomeCollection) { }
```

 Typy z sufiksem "dictionary" są zgodne z tym wzorcem wyliczenia.

```
foreach(SomeType x in SomeDictionary.Values) { }
```

 <xref:System.Data.DataSet>Obiekt składa się z kolekcji <xref:System.Data.DataTable> obiektów, które składają się z kolekcji <xref:System.Data.DataColumn?displayProperty=fullName> i <xref:System.Data.DataRow?displayProperty=fullName> obiektów, między innymi. Kolekcje te implementują <xref:System.Collections.ICollection> się za pomocą <xref:System.Data.InternalDataCollectionBase?displayProperty=fullName> klasy bazowej.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Zmień nazwę typu tak, aby był on sufiksem prawidłowym terminem.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Można bezpiecznie pominąć ostrzeżenie, aby użyć sufiksu "Kolekcja", jeśli typ jest uogólnioną strukturą danych, która może zostać rozszerzona lub który będzie przechowywać dowolny zestaw różnorodnych elementów. W takim przypadku nazwa, która zapewnia istotne informacje dotyczące implementacji, wydajności lub innych cech struktury danych, może mieć sens (na przykład BinaryTree). W przypadkach, gdy typ reprezentuje kolekcję określonego typu (na przykład StringCollection), nie pomijaj ostrzeżenia z tej reguły, ponieważ sufiks wskazuje, że typ można wyliczyć przy użyciu `foreach` instrukcji.

 W przypadku innych sufiksów nie należy pomijać ostrzeżenia z tej reguły. Sufiks umożliwia wykrycie zamierzonego użycia z nazwy typu.

## <a name="related-rules"></a>Powiązane reguły
 [CA1711: Identyfikatory nie powinny mieć nieprawidłowych sufiksów](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

## <a name="see-also"></a>Zobacz też
 [Atrybuty](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b) [NIB: zdarzenia i Delegaty](https://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)
