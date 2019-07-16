---
title: 'CA1058: Typy nie powinny rozszerzać niektórych typów podstawowych | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TypesShouldNotExtendCertainBaseTypes
- CA1058
helpviewer_keywords:
- CA1058
- TypesShouldNotExtendCertainBaseTypes
ms.assetid: 8446ee40-beb1-49fa-8733-4d8e813471c0
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1ce67a70b6cbe955ef13bf6475a672bcbb687d95
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200448"
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: Typy nie powinny rozszerzać niektórych typów podstawowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesShouldNotExtendCertainBaseTypes|
|CheckId|CA1058|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ widoczny na zewnątrz rozszerza niektóre typy podstawowe. Obecnie ta zasada zgłasza typów wyprowadzonych z następujących typów:

- <xref:System.ApplicationException?displayProperty=fullName>

- <xref:System.Xml.XmlDocument?displayProperty=fullName>

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.Queue?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

- <xref:System.Collections.SortedList?displayProperty=fullName>

- <xref:System.Collections.Stack?displayProperty=fullName>

## <a name="rule-description"></a>Opis reguły
 Aby uzyskać [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] wersji 1 zalecano do wyprowadzenia nowego wyjątki od <xref:System.ApplicationException>. Zalecenie został zmieniony i nowych wyjątków powinien pochodzić od <xref:System.Exception?displayProperty=fullName> lub jedna z jej podklasach w <xref:System> przestrzeni nazw.

 Nie należy tworzyć podklasą <xref:System.Xml.XmlDocument> Jeśli chcesz utworzyć widok XML z bazowego źródła danych lub modelu obiektu.

### <a name="non-generic-collections"></a>Kolekcje ogólne
 Użyj i/lub rozszerzyć kolekcje ogólne, jeśli to możliwe. Kolekcje ogólne w kodzie, nie zostanie rozszerzony, chyba że wcześniej wysłane.

 **Przykłady nieprawidłowe użycie**

```csharp
public class MyCollection : CollectionBase
{
}

public class MyReadOnlyCollection : ReadOnlyCollectionBase
{
}
```

 **Przykłady poprawne użycie**

```csharp
public class MyCollection : Collection<T>
{
}

public class MyReadOnlyCollection : ReadOnlyCollection<T>
{
}
```

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, pobierają typ z innym typem bazowym lub kolekcję ogólną.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły za naruszenia o <xref:System.ApplicationException>. Bezpiecznie Pomijaj ostrzeżeń dla tej reguły za naruszenia o <xref:System.Xml.XmlDocument>. Jest bezpieczne pominąć ostrzeżenie dotyczące nieogólna kolekcja, jeśli kod został wydany wcześniej.
