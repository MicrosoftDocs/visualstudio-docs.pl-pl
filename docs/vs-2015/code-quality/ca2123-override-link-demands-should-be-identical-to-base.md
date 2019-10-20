---
title: 'CA2123: Przesłoń wymagania dotyczące linków powinny być identyczne z podstawowymi | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: bec8f129c094f94ba3eb4021092c402e8263812b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660255"
---
# <a name="ca2123-override-link-demands-should-be-identical-to-base"></a>CA2123: Przesłonięcia żądań konsolidacji powinny być identyczne z bazowym
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideLinkDemandsShouldBeIdenticalToBase|
|CheckId|CA2123|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda publiczna lub chroniona w typie publicznym przesłania metodę lub implementuje interfejs i nie ma tego samego [łącza](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) , jak interfejs lub metoda wirtualna.

## <a name="rule-description"></a>Opis reguły
 Ta reguła dopasowuje metodę do jej metody podstawowej, która jest interfejsem lub metodą wirtualną innego typu, a następnie porównuje zapotrzebowania na łącza na każdym z nich. Zgłaszane jest naruszenie, jeśli metoda lub metoda podstawowa ma żądanie linku, a druga nie.

 W przypadku naruszenia tej reguły złośliwy obiekt wywołujący może ominąć żądanie linku tylko przez wywołanie niezabezpieczonej metody.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Zastosuj to samo żądanie linku do metody overide lub implementacji. Jeśli nie jest to możliwe, oznacz metodę pełnym zapotrzebowaniem lub usuń atrybut całkowicie.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono różne naruszenia tej reguły.

 [!code-csharp[FxCop.Security.OverridesAndSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.OverridesAndSecurity/cs/FxCop.Security.OverridesAndSecurity.cs#1)]

## <a name="see-also"></a>Zobacz też
 [Wymagania dotyczące linków](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [bezpiecznego kodowania](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)
