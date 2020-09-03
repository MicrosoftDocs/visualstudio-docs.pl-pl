---
title: 'CA1058: typy nie powinny poszerzać niektórych typów podstawowych | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d8e267b1e6203759efc91936a3b13059368a3862
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545395"
---
# <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: Typy nie powinny rozszerzać niektórych typów podstawowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|TypesShouldNotExtendCertainBaseTypes|
|CheckId|CA1058|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ widoczny na zewnątrz rozszerza niektóre typy podstawowe. Obecnie ta reguła raportuje typy, które pochodzą od następujących typów:

- <xref:System.ApplicationException?displayProperty=fullName>

- <xref:System.Xml.XmlDocument?displayProperty=fullName>

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.Queue?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

- <xref:System.Collections.SortedList?displayProperty=fullName>

- <xref:System.Collections.Stack?displayProperty=fullName>

## <a name="rule-description"></a>Opis reguły
 W przypadku [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] wersji 1 zaleca się uzyskanie nowych wyjątków z programu <xref:System.ApplicationException> . Zalecenie zostało zmienione i nowe wyjątki powinny pochodzić z <xref:System.Exception?displayProperty=fullName> lub jednej z jej podklas w <xref:System> przestrzeni nazw.

 Nie należy tworzyć podklasy, <xref:System.Xml.XmlDocument> Jeśli chcesz utworzyć widok XML źródłowego modelu obiektów lub źródła danych.

### <a name="non-generic-collections"></a>Kolekcje inne niż ogólne
 Używaj i/lub rozszerzając kolekcje ogólne wszędzie tam, gdzie to możliwe. Nie należy poszerzać kolekcji innych niż ogólne w kodzie, chyba że wcześniej zostały dostarczone.

 **Przykłady nieprawidłowego użycia**

```csharp
public class MyCollection : CollectionBase
{
}

public class MyReadOnlyCollection : ReadOnlyCollectionBase
{
}
```

 **Przykłady poprawnego użycia**

```csharp
public class MyCollection : Collection<T>
{
}

public class MyReadOnlyCollection : ReadOnlyCollection<T>
{
}
```

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, należy utworzyć typ z innego typu podstawowego lub kolekcji ogólnej.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżenia z tej reguły dla naruszeń <xref:System.ApplicationException> . Można bezpiecznie pominąć ostrzeżenie z tej reguły dla naruszeń <xref:System.Xml.XmlDocument> . Można bezpiecznie pominąć ostrzeżenie o nieogólnej kolekcji, jeśli kod został wcześniej opublikowany.
