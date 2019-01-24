---
title: 'CA2122: Nie ujawniaj pośrednio metod żądaniami linkdemand | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 637fa666dbaba539b39fb3537df49fbd12baef3a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54757762"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122: Nie ujawniaj pośrednio metod żądaniami LinkDemand
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|
|CheckId|CA2122|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Element członkowski publiczny lub chroniony ma [zapotrzebowania na łącza](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) i jest wywoływany przez element członkowski, który nie sprawdza zabezpieczeń.

## <a name="rule-description"></a>Opis reguły
 Zapotrzebowanie na łącza sprawdza uprawnienia tylko bezpośredniego wywołującego. Jeśli członek `X` sprawia, że nie żądania kontroli zabezpieczeń jego wywołań i wywołuje kod chroniony przez żądanie łącza, obiekt wywołujący bez niezbędnych uprawnień, można użyć `X` uzyskać dostępu do chronionego członka.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Dodawanie zabezpieczeń [dane i modelowanie](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) lub połączyć żądanie do elementu członkowskiego, tak aby nie jest już zapewnia niezabezpieczony dostęp do składowej chronionej przez żądanie łącza.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Aby bezpiecznie pominąć ostrzeżenie od tej reguły, należy upewnić się, że Twój kod nie przyznaje wywołujące dostęp do operacji lub zasobów, które mogą być używane w szkodliwy sposób.

## <a name="example"></a>Przykład
 W poniższych przykładach pokazano bibliotekę, która narusza regułę i aplikacji, która pokazuje słabość biblioteki. Biblioteka przykładowe udostępnia dwie metody, naruszających zasady. `EnvironmentSetting` Metody jest zabezpieczony przez zapotrzebowania na łącza, aby uzyskać nieograniczony dostęp do zmiennych środowiskowych. `DomainInformation` Metoda przeprowadza nie wymogów bezpieczeństwa z wywołujące przed wywołaniem `EnvironmentSetting`.

 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.UnsecuredDoNotCall/cs/FxCop.Security.UnsecuredDoNotCall.cs#1)]

## <a name="example"></a>Przykład
 Następująca aplikacja wywołuje składowej niezabezpieczonej biblioteki.

 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestUnsecuredDoNot1/cs/FxCop.Security.TestUnsecuredDoNot1.cs#1)]

 Ten przykład generuje następujące dane wyjściowe.

 **Wartość od niezabezpieczonej elementu członkowskiego: seattle.corp.contoso.com**
## <a name="see-also"></a>Zobacz też
 [Wytyczne dotyczące bezpiecznego programowania](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [Link zapotrzebowanie](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [dane i modelowanie](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
