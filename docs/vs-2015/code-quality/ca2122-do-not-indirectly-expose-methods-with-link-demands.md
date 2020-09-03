---
title: 'CA2122: nie ujawniaj pośrednio metod z wymaganiami dotyczącymi linków | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 846ce010cddfd505bb967ec612a5c31dd8321977
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544329"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122: Nie ujawniaj pośrednio metod żądaniami LinkDemand
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|
|CheckId|CA2122|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Publiczny lub chroniony element członkowski ma [wymagania dotyczące linków](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) i jest wywoływany przez element członkowski, który nie wykonuje żadnych kontroli zabezpieczeń.

## <a name="rule-description"></a>Opis reguły
 Zapotrzebowanie na łącza sprawdza uprawnienia tylko bezpośredniego wywołującego. Jeśli członek `X` nie ma żadnych wymagań w zakresie zabezpieczeń dla jego obiektów wywołujących i wywołuje kod chroniony przez żądanie linku, obiekt wywołujący bez wymaganych uprawnień może użyć `X` w celu uzyskania dostępu do chronionego elementu członkowskiego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Dodaj dane zabezpieczeń [oraz modelowanie](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) lub żądanie do elementu członkowskiego, aby nie zapewnia on już niezabezpieczonego dostępu do elementu członkowskiego chronionego na żądanie linku.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Aby bezpiecznie pominąć ostrzeżenie z tej reguły, należy się upewnić, że kod nie przyznaje obiektom wywołującym dostęp do operacji lub zasobów, które mogą być używane w sposób niszczący.

## <a name="example"></a>Przykład
 W poniższych przykładach przedstawiono bibliotekę, która narusza regułę, oraz aplikację, która demonstruje słabość biblioteki. Biblioteka Przykładowa zawiera dwie metody, które wspólnie naruszają daną regułę. `EnvironmentSetting`Metoda jest zabezpieczona przez żądanie linku dla nieograniczonego dostępu do zmiennych środowiskowych. `DomainInformation`Metoda nie wykonuje żadnych żądań związanych z zabezpieczeniami przed wywołaniem `EnvironmentSetting` .

 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.UnsecuredDoNotCall/cs/FxCop.Security.UnsecuredDoNotCall.cs#1)]

## <a name="example"></a>Przykład
 Następująca aplikacja wywołuje niezabezpieczoną składową biblioteki.

 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestUnsecuredDoNot1/cs/FxCop.Security.TestUnsecuredDoNot1.cs#1)]

 Ten przykład generuje następujące dane wyjściowe.

 **Wartość z niezabezpieczonego elementu członkowskiego: seattle.corp.contoso.com**
## <a name="see-also"></a>Zobacz też
 [Link](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [wytyczne dotyczące bezpiecznego kodowania](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) — [dane i modelowanie](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
