---
title: 'CA2122: Nie ujawniaj pośrednio metod żądaniami LinkDemand'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 340d8f0a45506f15cdd9281f7ecda463583c3144
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920827"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122: Nie ujawniaj pośrednio metod żądaniami LinkDemand

|||
|-|-|
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|
|CheckId|CA2122|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
Publiczny lub chroniony element członkowski ma [wymagania dotyczące linków](/dotnet/framework/misc/link-demands) i jest wywoływany przez element członkowski, który nie wykonuje żadnych kontroli zabezpieczeń.

## <a name="rule-description"></a>Opis reguły
Zapotrzebowanie na łącza sprawdza uprawnienia tylko bezpośredniego wywołującego. Jeśli członek `X` nie ma żadnych wymagań w zakresie zabezpieczeń dla jego obiektów wywołujących i wywołuje kod chroniony przez żądanie linku, obiekt wywołujący bez wymaganych uprawnień `X` może użyć w celu uzyskania dostępu do chronionego elementu członkowskiego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Dodaj dane zabezpieczeń [oraz modelowanie](/dotnet/framework/data/index) lub żądanie do elementu członkowskiego, aby nie zapewnia on już niezabezpieczonego dostępu do elementu członkowskiego chronionego na żądanie linku.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Aby bezpiecznie pominąć ostrzeżenie z tej reguły, należy się upewnić, że kod nie przyznaje obiektom wywołującym dostęp do operacji lub zasobów, które mogą być używane w sposób niszczący.

## <a name="example-1"></a>Przykład 1
W poniższych przykładach przedstawiono bibliotekę, która narusza regułę, oraz aplikację, która demonstruje słabość biblioteki. Biblioteka Przykładowa zawiera dwie metody, które wspólnie naruszają daną regułę. `EnvironmentSetting` Metoda jest zabezpieczona przez żądanie linku dla nieograniczonego dostępu do zmiennych środowiskowych. Metoda nie wykonuje żadnych żądań związanych z zabezpieczeniami przed `EnvironmentSetting`wywołaniem. `DomainInformation`

[!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_1.cs)]

## <a name="example-2"></a>Przykład 2
Następująca aplikacja wywołuje niezabezpieczoną składową biblioteki.

[!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_2.cs)]

Ten przykład generuje następujące wyniki:

```txt
*Value from unsecured member: seattle.corp.contoso.com
```

## <a name="see-also"></a>Zobacz także

- [Wytyczne dotyczące bezpiecznego programowania](/dotnet/standard/security/secure-coding-guidelines)
- [Wymagania dotyczące linków](/dotnet/framework/misc/link-demands)
- [Dane i modelowanie](/dotnet/framework/data/index)