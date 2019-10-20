---
title: 'CA2108: Sprawdź Zabezpieczenia deklaratywne typów wartości | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a05b7098d75d368f893b2504f7663675611bc0ce
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658721"
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108: Należy przejrzeć zabezpieczenia deklaratywne typów wartościowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewDeclarativeSecurityOnValueTypes|
|CheckId|CA2108|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Typ wartości publicznej lub chronionej jest zabezpieczony przez żądania [danych i modelowania](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) lub [łączenia](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d).

## <a name="rule-description"></a>Opis reguły
 Typy wartości są przydzielone i inicjowane przez ich domyślne konstruktory przed wykonaniem innych konstruktorów. Jeśli typ wartości jest zabezpieczony przez żądanie lub LinkDemand, a obiekt wywołujący nie ma uprawnień, które spełniają sprawdzanie zabezpieczeń, żaden Konstruktor inny niż domyślny zakończy się niepowodzeniem i zostanie zgłoszony wyjątek zabezpieczeń. Nie cofnięto przydziału typu wartości; pozostało w stanie ustawionym przez jego domyślnego konstruktora. Nie należy zakładać, że obiekt wywołujący, który przekazuje wystąpienie typu wartości, ma uprawnienia do tworzenia wystąpienia lub uzyskiwania do niego dostępu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Nie można naprawić naruszenia tej reguły, chyba że usuniesz kontrolę zabezpieczeń z typu i użyjemy kontroli zabezpieczeń na poziomie metody w miejscu. Należy zauważyć, że naprawianie naruszenia w ten sposób nie uniemożliwi wywołującym niewystarczających uprawnień do uzyskiwania wystąpień typu wartości. Należy upewnić się, że wystąpienie typu wartości w stanie domyślnym nie ujawnia informacji poufnych i nie może być używane w sposób szkodliwy.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Można pominąć ostrzeżenie z tej reguły, jeśli każdy obiekt wywołujący może uzyskać wystąpienia typu wartości w stanie domyślnym bez zaproponowania zagrożenia bezpieczeństwa.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono bibliotekę zawierającą typ wartości, który narusza tę regułę. Należy pamiętać, że typ `StructureManager` zakłada, że obiekt wywołujący, który przekazuje wystąpienie typu wartości, ma uprawnienia do tworzenia wystąpienia lub uzyskiwania do niego dostępu.

 [!code-csharp[FxCop.Security.DemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.DemandOnValueType/cs/FxCop.Security.DemandOnValueType.cs#1)]

## <a name="example"></a>Przykład
 Poniższa aplikacja pokazuje słabość biblioteki.

 [!code-csharp[FxCop.Security.TestDemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestDemandOnValueType/cs/FxCop.Security.TestDemandOnValueType.cs#1)]

 Ten przykład generuje następujące dane wyjściowe.

 **Konstruktor niestandardowy struktury: żądanie nie powiodło się.** 
**nowe wartości SecuredTypeStructure 100 100** 
**nowe wartości SecuredTypeStructure 200 200**
## <a name="see-also"></a>Zobacz też
 [Link wymaga](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [danych i modelowania](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
