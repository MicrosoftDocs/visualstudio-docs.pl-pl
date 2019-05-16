---
title: 'CA2108: Przejrzyj zabezpieczenia deklaratywne dla typów wartości | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
helpviewer_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f6a17bf57f00923cfd31bd477f211ba66169672a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687367"
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108: Przejrzyj zabezpieczenia deklaratywne dla typów wartości
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewDeclarativeSecurityOnValueTypes|
|CheckId|CA2108|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Publiczny lub chroniony typ wartości jest zabezpieczony przez [dane i modelowanie](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) lub [zapotrzebowania na łącza](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d).

## <a name="rule-description"></a>Opis reguły
 Typy wartości są przydzielane i zainicjowany przez ich konstruktory domyślne przed innymi konstruktorów. Jeśli typ wartości jest zabezpieczony przez zapotrzebowania lub LinkDemand, a obiekt wywołujący nie ma uprawnienia, które spełniają innych niż kontrola zabezpieczeń, dowolny Konstruktor domyślny zakończy się niepowodzeniem i zostanie zgłoszony wyjątek zabezpieczeń. Typ wartości nie cofnięto przydziału; Pozostało się w stanie ustawione przez jej konstruktora domyślnego. Nie należy zakładać, że obiekt wywołujący, która przekazuje wystąpienie typu wartości ma uprawnienia do tworzenia lub dostęp do wystąpienia.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Nie można naprawić naruszenie tej zasady, o ile nie usuniesz sprawdzanie zabezpieczeń z typu i sprawdza, czy zabezpieczenia na poziomie metody użycia w tym miejscu. Należy pamiętać, że naprawianie naruszenia w ten sposób nie zapobiega wywołań z niewystarczającymi uprawnieniami uzyskanie wystąpienia typu wartości. Upewnij się, że wystąpienie typu wartości w stanie domyślnym nie spowodować ujawnienie poufnych informacji i nie można używać w szkodliwy sposób.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Ostrzeżenie od tej reguły można pominąć, jeśli dowolny obiekt wywołujący może uzyskać jedno wystąpienie typu wartości w stanie domyślnym bez stanowiące zagrożenie dla bezpieczeństwa.

## <a name="example"></a>Przykład
 Poniższy przykład zawiera bibliotekę zawierającą typ wartości, która narusza tę regułę. Należy pamiętać, że `StructureManager` typu przyjęto założenie, że obiekt wywołujący, która przekazuje wystąpienie typu wartości ma uprawnienia do tworzenia lub dostęp do wystąpienia.

 [!code-csharp[FxCop.Security.DemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.DemandOnValueType/cs/FxCop.Security.DemandOnValueType.cs#1)]

## <a name="example"></a>Przykład
 Następująca aplikacja pokazuje słabość biblioteki.

 [!code-csharp[FxCop.Security.TestDemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestDemandOnValueType/cs/FxCop.Security.TestDemandOnValueType.cs#1)]

 Ten przykład generuje następujące dane wyjściowe.

 **Struktura konstruktora niestandardowego: Żądanie nie powiodło się. ** 
 **Nowe wartości SecuredTypeStructure 100 100**
**nowe wartości SecuredTypeStructure 200 200**
## <a name="see-also"></a>Zobacz też
 [Link zapotrzebowanie](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [dane i modelowanie](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
