---
title: 'CA2123: Zastąpienie konsolidacji powinny być identyczne z bazowym | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2123
- OverrideLinkDemandsShouldBeIdenticalToBase
helpviewer_keywords:
- OverrideLinkDemandsShouldBeIdenticalToBase
- CA2123
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 338d61db9c24972b7fef656498abd43f8ea0b976
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687220"
---
# <a name="ca2123-override-link-demands-should-be-identical-to-base"></a>CA2123: Przesłonięcia żądań konsolidacji powinny być identyczne z podstawowymi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideLinkDemandsShouldBeIdenticalToBase|
|CheckId|CA2123|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda publiczna lub chroniona w typie publicznym zastępuje metody lub implementuje interfejs i nie ma takie same [zapotrzebowania na łącza](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) jako interfejs lub metoda wirtualna.

## <a name="rule-description"></a>Opis reguły
 Ta reguła dopasowuje metodę do jej metody podstawowej, która jest interfejsem lub metodą wirtualną innego typu, a następnie porównuje zapotrzebowania na łącza na każdym z nich. Naruszenie zasad jest zgłaszany, jeśli metoda lub metoda podstawowa ma zapotrzebowania na łącza, a drugi nie.

 Jeśli zasada ta jest naruszona, złośliwy wywołujący może pominąć zapotrzebowanie na łącza przez wywołanie niezabezpieczonej metody.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, dotyczą tego samego zapotrzebowania na łącza zastąpić te metody lub implementacji. Jeśli nie jest to możliwe, oznacz metodę z pełnego żądania lub całkowicie Usuń atrybut.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje różne naruszenie tej zasady.

 [!code-csharp[FxCop.Security.OverridesAndSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.OverridesAndSecurity/cs/FxCop.Security.OverridesAndSecurity.cs#1)]

## <a name="see-also"></a>Zobacz też
 [Wytyczne dotyczące bezpiecznego programowania](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [Link żądania](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)
