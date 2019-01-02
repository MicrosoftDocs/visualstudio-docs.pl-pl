---
title: 'CA2136: Elementy członkowskie nie powinny mieć skonfliktowanych adnotacji przezroczystości | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2127
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2136
helpviewer_keywords:
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2127
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 315725a1cc14373ecf955be38dde07a7df608496
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53939079"
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136: Elementy członkowskie nie powinny mieć skonfliktowanych adnotacji przezroczystości
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparencyAnnotationsShouldNotConflict|
|CheckId|CA2136|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Ta reguła jest uruchamiana, gdy element członkowski typu jest oznaczona za pomocą <xref:System.Security> atrybutu zabezpieczeń, który ma inną przezroczystości niż atrybutu zabezpieczeń kontenera elementu członkowskiego.

## <a name="rule-description"></a>Opis reguły
 Atrybuty przezroczystości są stosowane od elementów kodu o większym zakresie do elementów o mniejszym zakresie. Atrybuty przezroczystości elementów kodu z większym zakresem mają pierwszeństwo przed atrybutami przejrzystości elementów kodu, które są zawarte w pierwszym elemencie. Na przykład klasa, która jest oznaczona za pomocą <xref:System.Security.SecurityCriticalAttribute> atrybutu nie może zawierać metody oznaczonej za pomocą <xref:System.Security.SecuritySafeCriticalAttribute> atrybutu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać problem to naruszenie, usuń atrybut zabezpieczeń z elementu kodu, który ma niższy zakres, lub zmień jego atrybutu, aby być taka sama jak element zawierający kod.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń od tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie metoda jest oznaczona atrybutem <xref:System.Security.SecuritySafeCriticalAttribute> atrybutu i jest elementem członkowskim klasy, która jest oznaczona za pomocą <xref:System.Security.SecurityCriticalAttribute> atrybutu. Atrybut bezpieczne zabezpieczeń powinny zostać usunięte.

 [!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2136.transparencyannotationsshouldnotconflict/cs/ca2136 - transparencyannotationsshouldnotconflict.cs#1)]
