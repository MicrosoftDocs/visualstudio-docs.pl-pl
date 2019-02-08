---
title: 'CA2134: Metody muszą zachowywać spójną przezroczystość podczas nadpisywania metod bazowych'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2134
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 67114c20a7fcf5e8ff01773d8777b23d3caf3d91
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55954663"
---
# <a name="ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods"></a>CA2134: Metody muszą zachowywać spójną przezroczystość podczas nadpisywania metod bazowych

|||
|-|-|
|TypeName|MethodsMustOverrideWithConsistentTransparency|
|CheckId|CA2134|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Ta reguła jest uruchamiana, gdy metoda oznaczona za pomocą <xref:System.Security.SecurityCriticalAttribute> zastępuje metodę, która jest przezroczysta lub oznaczona za pomocą <xref:System.Security.SecuritySafeCriticalAttribute>. Reguła jest również uruchamiana, gdy metoda, która jest przezroczysta lub oznaczona za pomocą <xref:System.Security.SecuritySafeCriticalAttribute> zastępuje metodę, która jest oznaczona za pomocą <xref:System.Security.SecurityCriticalAttribute>.

 Reguła jest stosowana podczas zastępowania metody wirtualnej lub implementującej interfejs.

## <a name="rule-description"></a>Opis reguły
 Ta reguła jest uruchamiana na próby zmiany ułatwień dostępu zabezpieczeń metodę dalsze górę łańcucha dziedziczenia. Na przykład jeśli metoda wirtualna w klasie bazowej jest przezroczysty lub bezpieczny krytyczny, następnie klasy pochodnej musi zastąpić ją metoda przezroczysty lub bezpieczny krytyczny. Z drugiej strony Jeśli wirtualnej jest krytyczny dla bezpieczeństwa, klasy pochodnej musi zastąpić ją zabezpieczeń metody krytycznej. Ta sama zasada dotyczy implementacji metody interfejsu.

 Zasady przezroczystości są wymuszane, gdy kod jest skompilowana zamiast w czasie wykonywania w trybie JIT, tak, aby obliczenia przejrzystości nie ma informacji o typie dynamicznych. W związku z tym wynik obliczenia przejrzystości musi mieć możliwość można określić wyłącznie z typów statycznych jest kompilowany dokładnie na czas, niezależnie od typu dynamicznego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, zmień przezroczystość metodę, która jest zastępowania metody wirtualnej lub implementującej interfejs do dopasowania przezroczystości, wirtualnej lub metody interfejsu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń od tej reguły. Naruszenie tej zasady spowoduje w środowisku uruchomieniowym <xref:System.TypeLoadException> dla zestawów, które używać przezroczystości poziomu 2.

## <a name="examples"></a>Przykłady

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods_1.cs)]

## <a name="see-also"></a>Zobacz także
 [Kod o przezroczystym poziomie bezpieczeństwa, poziom 2](/dotnet/framework/misc/security-transparent-code-level-2)