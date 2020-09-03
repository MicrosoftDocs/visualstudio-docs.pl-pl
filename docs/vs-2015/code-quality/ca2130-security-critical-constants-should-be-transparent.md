---
title: 'CA2130: stałe krytyczne dla zabezpieczeń powinny być przezroczyste | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2130
ms.assetid: 344c7f7b-9130-4675-ae7f-9fa260cc9789
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4439e7b520232b71c16d3f3c6b4afb3a4ba35f21
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534605"
---
# <a name="ca2130-security-critical-constants-should-be-transparent"></a>CA2130: Stałe krytyczne pod względem zabezpieczeń powinny być przezroczyste
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|ConstantsShouldBeTransparent|
|CheckId|CA2130|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Pole stałej lub element członkowski wyliczenia jest oznaczony przy użyciu <xref:System.Security.SecurityCriticalAttribute> .

## <a name="rule-description"></a>Opis reguły
 Wymuszanie przezroczystości nie jest wymuszane dla wartości stałych, ponieważ kompilatory wbudowują stałe wartości, tak aby nie było wymagane żadne wyszukiwanie w czasie wykonywania. Stałe pola powinny być przezroczyste dla zabezpieczeń, tak aby recenzenci kodu nie zakładali, że przezroczysty kod nie może uzyskać dostępu do stałej.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Usuń atrybut SecurityCritical z pola lub wartości.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W poniższych przykładach wartość enum `EnumWithCriticalValues.CriticalEnumValue` i stała `CriticalConstant` powodują wystąpienie tego ostrzeżenia. Aby rozwiązać te problemy, Usuń atrybut [ `SecurityCritical` ], aby zapewnić, że zabezpieczenia są przezroczyste.

 [!code-csharp[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2130.constantsshouldbetransparent/cs/ca2130 - constantsshouldbetransparent.cs#1)]
