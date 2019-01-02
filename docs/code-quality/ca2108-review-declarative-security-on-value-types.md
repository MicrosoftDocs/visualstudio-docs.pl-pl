---
title: 'CA2108: Przejrzyj zabezpieczenia deklaratywne dla typów wartości'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
helpviewer_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c62704a99e5952c313c4ba11a71fd234070d6df8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53882237"
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108: Przejrzyj zabezpieczenia deklaratywne dla typów wartości

|||
|-|-|
|TypeName|ReviewDeclarativeSecurityOnValueTypes|
|CheckId|CA2108|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Publiczny lub chroniony typ wartości jest zabezpieczony przez [dane i modelowanie](/dotnet/framework/data/index) lub [zapotrzebowania na łącza](/dotnet/framework/misc/link-demands).

## <a name="rule-description"></a>Opis reguły

Typy wartości są przydzielane i zainicjowany przez ich konstruktory domyślne przed innymi konstruktorów. Jeśli typ wartości jest zabezpieczony przez zapotrzebowania lub LinkDemand, a obiekt wywołujący nie ma uprawnienia, które spełniają innych niż kontrola zabezpieczeń, dowolny Konstruktor domyślny zakończy się niepowodzeniem i zostanie zgłoszony wyjątek zabezpieczeń. Typ wartości nie cofnięto przydziału; Pozostało się w stanie ustawione przez jej konstruktora domyślnego. Nie należy zakładać, że obiekt wywołujący, która przekazuje wystąpienie typu wartości ma uprawnienia do tworzenia lub dostęp do wystąpienia.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Nie można naprawić naruszenie tej zasady, o ile nie usuniesz sprawdzanie zabezpieczeń z typu i sprawdza, czy zabezpieczenia na poziomie metody użycia w tym miejscu. Naprawianie naruszenia w ten sposób nie uniemożliwia wywołującym z niewystarczającymi uprawnieniami uzyskanie wystąpienia typu wartości. Upewnij się, że wystąpienie typu wartości w stanie domyślnym nie spowodować ujawnienie poufnych informacji i nie można używać w szkodliwy sposób.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Ostrzeżenie od tej reguły można pominąć, jeśli dowolny obiekt wywołujący może uzyskać jedno wystąpienie typu wartości w stanie domyślnym bez stanowiące zagrożenie dla bezpieczeństwa.

## <a name="example-1"></a>Przykład 1

Poniższy przykład zawiera bibliotekę zawierającą typ wartości, która narusza tę regułę. `StructureManager` Typu przyjęto założenie, że obiekt wywołujący, która przekazuje wystąpienie typu wartości ma uprawnienia do tworzenia lub dostęp do wystąpienia.

[!code-csharp[FxCop.Security.DemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_1.cs)]

## <a name="example-2"></a>Przykład 2

Następująca aplikacja pokazuje słabość biblioteki.

[!code-csharp[FxCop.Security.TestDemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_2.cs)]

Ten przykład generuje następujące wyniki:

```txt
Structure custom constructor: Request failed.
New values SecuredTypeStructure 100 100
New values SecuredTypeStructure 200 200
```

## <a name="see-also"></a>Zobacz także

- [Zapotrzebowanie na łącza](/dotnet/framework/misc/link-demands)
- [Dane i modelowanie](/dotnet/framework/data/index)
