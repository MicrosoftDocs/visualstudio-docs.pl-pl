---
title: 'CA1044: właściwości nie powinny być tylko do zapisu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PropertiesShouldNotBeWriteOnly
- CA1044
helpviewer_keywords:
- CA1044
- PropertiesShouldNotBeWriteOnly
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2ca0fb61c0973553ee6d410bc8b2718d19aeb28c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546864"
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044: Właściwości nie powinny być tylko do zapisu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|PropertiesShouldNotBeWriteOnly|
|CheckId|CA1044|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Właściwość publiczna lub chroniona ma metodę dostępu set, ale nie ma metody dostępu get.

## <a name="rule-description"></a>Opis reguły
 Metody uzyskiwania dostępu zapewniają dostęp do odczytu do właściwości i zestaw metod dostępu zapewnia dostęp do zapisu. Chociaż posiadanie właściwości tylko do odczytu jest dopuszczalne i często konieczne, wytyczne projektowania zabraniają używania właściwości tylko do zapisu. Jest to spowodowane tym, że umożliwienie użytkownikowi ustawienia wartości, a następnie uniemożliwić użytkownikowi wyświetlanie wartości nie zapewnia żadnych zabezpieczeń. Poza tym bez dostępu do odczytu nie można przeglądać stanu obiektów udostępnionych, co ogranicza ich przydatność.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Dodaj metodę dostępu get do właściwości. Alternatywnie, jeśli konieczne jest zachowanie właściwości tylko do zapisu, należy rozważyć konwersję tej właściwości na metodę.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Zdecydowanie zaleca się, aby nie pomijać ostrzeżenia z tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie `BadClassWithWriteOnlyProperty` jest typem z właściwością tylko do zapisu. `GoodClassWithReadWriteProperty`zawiera poprawiony kod.

 [!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.PropertiesNotWriteOnly/cs/FxCop.Design.PropertiesNotWriteOnly.cs#1)]
 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.PropertiesNotWriteOnly/vb/PropertiesNotWriteOnly.vb#1)]
