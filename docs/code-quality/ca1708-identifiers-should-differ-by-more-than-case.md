---
title: 'CA1708: Identyfikatory powinny różnić się nie tylko wielkością liter'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 204e19e6abb40b8b50af4bd8b206c643f44e08ba
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55920083"
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708: Identyfikatory powinny różnić się nie tylko wielkością liter

|||
|-|-|
|TypeName|IdentifiersShouldDifferByMoreThanCase|
|CheckId|CA1708|
|Kategoria|Microsoft.Naming|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Nazwy dwa typy, członków lub przestrzeni nazw FQDN parametrów są identyczne, gdy są one konwertowane na małe litery.

## <a name="rule-description"></a>Opis reguły
 Identyfikatory przestrzeni nazw, typów, elementów członkowskich i parametry nie mogą się różnić jedynie wielkością liter, ponieważ języki dla środowiska uruchomieniowego języka wspólnego nie muszą rozróżniać wielkości liter. Na przykład [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] to powszechnie używany język bez uwzględniania wielkości liter.

 Ta reguła jest uruchamiana na tylko członków publicznie widoczne.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Wybierz nazwę, która jest unikatowa, gdy jest porównywana do innych identyfikatorów, bez uwzględniania wielkości liter.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Biblioteka może nie być można używać we wszystkich językach w programie .NET Framework.

## <a name="example-of-a-violation"></a>Przykładem naruszenia
 W poniższym przykładzie pokazano naruszenie tej zasady.

 [!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../code-quality/codesnippet/CSharp/ca1708-identifiers-should-differ-by-more-than-case_1.cs)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)