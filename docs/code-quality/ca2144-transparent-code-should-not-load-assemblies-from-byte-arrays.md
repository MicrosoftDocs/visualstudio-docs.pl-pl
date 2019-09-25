---
title: 'CA2144: Kod przezroczysty nie powinien ładować zestawów z tablic bajtowych'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2144
ms.assetid: 777b1310-6e16-4413-b4ee-5f3136304f82
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33edff9b22559799cef4ad7e03058a5eb212182b
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232012"
---
# <a name="ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays"></a>CA2144: Kod przezroczysty nie powinien ładować zestawów z tablic bajtowych

|||
|-|-|
|TypeName|TransparentMethodsShouldNotLoadAssembliesFromByteArrays|
|CheckId|CA2144|
|Kategoria|Microsoft.Security|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna
Metoda przezroczysta ładuje zestaw z tablicy bajtowej przy użyciu jednej z następujących metod:

- <xref:System.Reflection.Assembly.Load%2A>

- <xref:System.Reflection.Assembly.Load%2A>

- <xref:System.Reflection.Assembly.Load%2A>

## <a name="rule-description"></a>Opis reguły
Przegląd zabezpieczeń dla kodu przezroczystego nie jest tak dokładny jak kodu krytycznego pod względem bezpieczeństwa, ponieważ przezroczysty kod nie może wykonywać czynności wrażliwych pod względem bezpieczeństwa. Zestawy, ładowane z tablicy bajtowej, mogą nie być niezauważone w przezroczystym kodzie, a ta tablica bajtów może zawierać krytyczny albo, co ważniejsze, krytyczny dla bezpieczeństwa kod, który powinien być poddany inspekcji. W związku z tym przezroczysty kod nie powinien ładować zestawów z tablicy bajtowej.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, oznacz metodę, która ładuje zestaw z <xref:System.Security.SecurityCriticalAttribute> <xref:System.Security.SecuritySafeCriticalAttribute> lub atrybut.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
Reguła jest uruchamiana na poniższym kodzie, ponieważ metoda przezroczysta ładuje zestaw z tablicy bajtowej.

[!code-csharp[FxCop.Security.CA2144.TransparentMethodsShouldNotLoadAssembliesFromByteArrays#1](../code-quality/codesnippet/CSharp/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays_1.cs)]