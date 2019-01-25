---
title: 'CA2133: Delegatów należy powiązać z metodami ze spójną jawnością | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2133
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e9fb3a7aab243465ac4412e9d3adea9152d909ee
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54786493"
---
# <a name="ca2133-delegates-must-bind-to-methods-with-consistent-transparency"></a>CA2133: Delegaci muszą być powiązani z metodami ze spójną przezroczystością
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DelegatesMustBindWithConsistentTransparency|
|CheckId|CA2133|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

> [!NOTE]
>  To ostrzeżenie jest stosowane tylko do kodu, który jest uruchomiony w środowisku CoreCLR (wersja środowiska CLR, które są specyficzne dla aplikacji sieci Web w technologii Silverlight).

## <a name="cause"></a>Przyczyna
 To ostrzeżenie uruchamiane jest na metodzie wiążącej obiekt delegowany, która jest oznaczona za pomocą <xref:System.Security.SecurityCriticalAttribute> do metody, która jest przezroczysta lub oznaczona za pomocą <xref:System.Security.SecuritySafeCriticalAttribute>. Ostrzeżenie jest także uruchamiane na metodzie wiążącej obiekt delegowany, który jest przezroczysty lub bezpieczny-krytyczny dla metody krytycznej.

## <a name="rule-description"></a>Opis reguły
 Typy delegatów i metod, które mogą powiązać musi mieć spójną przezroczystość. Delegaty przejrzyste i bezpieczny krytyczny może powiązać tylko z innych metod przezroczysty lub bezpieczny krytyczny. Podobnie krytyczne delegatów mogą powiązać tylko z metody krytyczne. Te reguły powiązania upewnij się, że tylko kod, który może wywołać metodę za pośrednictwem delegata można również wywoływane ma tę samą metodę bezpośrednio. Na przykład zasad powiązania uniemożliwia podczas wywoływania kodu krytycznego bezpośrednio przez obiekt delegowany przezroczysty kod przezroczysty.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie to ostrzeżenie, zmień przezroczystość, delegata lub metody, która wiąże ją tak, aby przezroczystość dwa są równoważne.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2133.delegatesmustbindwithconsistenttransparency/cs/ca2133 - delegatesmustbindwithconsistenttransparency.cs#1)]
