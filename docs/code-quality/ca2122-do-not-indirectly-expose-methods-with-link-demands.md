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
ms.openlocfilehash: 8239b27cd92f66ae8f74ddb1accd95535bf56f93
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62542340"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122: Nie ujawniaj pośrednio metod żądaniami LinkDemand

|||
|-|-|
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|
|CheckId|CA2122|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Element członkowski publiczny lub chroniony ma [zapotrzebowania na łącza](/dotnet/framework/misc/link-demands) i jest wywoływany przez element członkowski, który nie sprawdza zabezpieczeń.

## <a name="rule-description"></a>Opis reguły
 Zapotrzebowanie na łącza sprawdza uprawnienia tylko bezpośredniego wywołującego. Jeśli członek `X` sprawia, że nie żądania kontroli zabezpieczeń jego wywołań i wywołuje kod chroniony przez żądanie łącza, obiekt wywołujący bez niezbędnych uprawnień, można użyć `X` uzyskać dostępu do chronionego członka.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Dodawanie zabezpieczeń [dane i modelowanie](/dotnet/framework/data/index) lub połączyć żądanie do elementu członkowskiego, tak aby nie jest już zapewnia niezabezpieczony dostęp do składowej chronionej przez żądanie łącza.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Aby bezpiecznie pominąć ostrzeżenie od tej reguły, należy upewnić się, że Twój kod nie przyznaje wywołujące dostęp do operacji lub zasobów, które mogą być używane w szkodliwy sposób.

## <a name="example-1"></a>Przykład 1
 W poniższych przykładach pokazano bibliotekę, która narusza regułę i aplikacji, która pokazuje słabość biblioteki. Biblioteka przykładowe udostępnia dwie metody, naruszających zasady. `EnvironmentSetting` Metody jest zabezpieczony przez zapotrzebowania na łącza, aby uzyskać nieograniczony dostęp do zmiennych środowiskowych. `DomainInformation` Metoda przeprowadza nie wymogów bezpieczeństwa z wywołujące przed wywołaniem `EnvironmentSetting`.

 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_1.cs)]

## <a name="example-2"></a>Przykład 2
 Następująca aplikacja wywołuje składowej niezabezpieczonej biblioteki.

 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_2.cs)]

Ten przykład generuje następujące wyniki:

```txt
*Value from unsecured member: seattle.corp.contoso.com
```

## <a name="see-also"></a>Zobacz także

- [Wytyczne dotyczące bezpiecznego programowania](/dotnet/standard/security/secure-coding-guidelines)
- [Zapotrzebowanie na łącza](/dotnet/framework/misc/link-demands)
- [Dane i modelowanie](/dotnet/framework/data/index)