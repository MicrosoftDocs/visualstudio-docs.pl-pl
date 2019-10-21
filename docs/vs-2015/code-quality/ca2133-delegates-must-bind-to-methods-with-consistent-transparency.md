---
title: 'CA2133: Delegaty muszą być powiązane z metodami ze spójną przezroczystością | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2133
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 487047b7dd3096e65a6e287d79d91d3029f3dc5a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72608987"
---
# <a name="ca2133-delegates-must-bind-to-methods-with-consistent-transparency"></a>CA2133: Delegatów należy powiązać z metodami ze spójną jawnością
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DelegatesMustBindWithConsistentTransparency|
|CheckId|CA2133|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

> [!NOTE]
> To ostrzeżenie jest stosowane tylko do kodu, na którym działa CoreCLR (wersja środowiska CLR, która jest specyficzna dla aplikacji sieci Web Silverlight).

## <a name="cause"></a>Przyczyna
 To ostrzeżenie jest generowane na metodzie, która wiąże delegata, który jest oznaczony <xref:System.Security.SecurityCriticalAttribute> do metody, która jest przezroczysta lub oznaczona przy użyciu <xref:System.Security.SecuritySafeCriticalAttribute>. Ostrzeżenie jest także uruchamiane na metodzie wiążącej obiekt delegowany, który jest przezroczysty lub bezpieczny-krytyczny dla metody krytycznej.

## <a name="rule-description"></a>Opis reguły
 Typy delegatów i metody, do których są powiązane, muszą mieć spójną przejrzystość. Delegaty przezroczyste i krytyczne o krytycznym znaczeniu mogą wiązać się tylko z innymi niejawnymi lub bezpiecznymi metodami. Podobnie Delegaty krytyczne mogą wiązać się tylko z metodami krytycznymi. Te reguły powiązań zapewniają, że jedyny kod, który może wywołać metodę za pośrednictwem delegata, mógł również wywołać tę samą metodę bezpośrednio. Na przykład reguły powiązań uniemożliwiają przezroczystemu kodowi Wywoływanie kodu krytycznego bezpośrednio za pośrednictwem przezroczystego delegata.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tego ostrzeżenia, Zmień przezroczystość delegata lub metodę, która jest powiązana, tak aby przezroczystość obu tych elementów była odpowiednikiem.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2133.delegatesmustbindwithconsistenttransparency/cs/ca2133 - delegatesmustbindwithconsistenttransparency.cs#1)]
