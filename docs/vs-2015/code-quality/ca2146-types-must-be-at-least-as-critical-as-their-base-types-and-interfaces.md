---
title: 'CA2146: typy muszą być co najmniej tak krytyczne jak ich typy podstawowe i interfejsy | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2146
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ab621ade120a257508eddbf9527f674b5fda8748
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610188"
---
# <a name="ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces"></a>CA2146: Typy muszą być co najmniej tak ważne, jak ich typy podstawowe i interfejsy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|
|CheckId|CA2146|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ przezroczysty pochodzi od typu, który jest oznaczony za pomocą <xref:System.Security.SecuritySafeCriticalAttribute> lub <xref:System.Security.SecurityCriticalAttribute> lub typ, który jest oznaczony za pomocą atrybutu <xref:System.Security.SecuritySafeCriticalAttribute> pochodzi od typu, który jest oznaczony atrybutem <xref:System.Security.SecurityCriticalAttribute>.

## <a name="rule-description"></a>Opis reguły
 Ta reguła jest uruchamiana, gdy typ pochodny ma atrybut przezroczystości pod względem zabezpieczeń, który nie jest tak krytyczny, jak jego typ podstawowy lub zaimplementowany interfejs. Tylko typy krytyczne pod względem zabezpieczeń mogą pochodzić od podstawowych typów krytycznych lub implementować interfejsy krytyczne, a tylko typy krytyczne lub krytyczne dla bezpieczeństwa mogą pochodzić od podstawowych typów krytycznych dla bezpieczeństwa lub implementować interfejsy krytyczne dla bezpieczeństwa. Naruszenia tej reguły w wyniku przejrzystości poziomu 2 dla typu pochodnego <xref:System.TypeLoadException>.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać ten problem, należy oznaczyć typ pochodny lub implementujący atrybutem przezroczystości, który jest co najmniej jako krytyczny dla typu podstawowego lub interfejsu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 [!code-csharp[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2146.typesmustbeatleastascriticalasbasetypes/cs/ca2146 - typesmustbeatleastascriticalasbasetypes.cs#1)]
