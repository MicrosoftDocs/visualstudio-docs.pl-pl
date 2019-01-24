---
title: 'CA2215: Metody Dispose powinny wywoływać metodę dispose klasy bazowej | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2215
- DisposeMethodsShouldCallBaseClassDispose
- Dispose methods should call base class dispose
helpviewer_keywords:
- DisposeMethodsShouldCallBaseClassDispose
- CA2215
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fb0fb1e1270e2e881b885873cf202cdf38106a05
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54778241"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: Metody Dispose powinny wywoływać metodę Dispose klasy bazowej
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ, który implementuje <xref:System.IDisposable?displayProperty=fullName> dziedziczy z typu, który także implementuje <xref:System.IDisposable>. <xref:System.IDisposable.Dispose%2A> Metoda dziedziczącej typu nie mogą wywoływać <xref:System.IDisposable.Dispose%2A> metodę typu nadrzędnego.

## <a name="rule-description"></a>Opis reguły
 Jeśli typ dziedziczy z typu usuwalnego, musi on wywołać <xref:System.IDisposable.Dispose%2A> metody typu podstawowego z w obrębie własnej <xref:System.IDisposable.Dispose%2A> metody. Wywołanie metody typu podstawowego usuwania gwarantuje, czy wszystkie zasoby utworzone przez typ bazowy są wydawane.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy wywołać `base`.<xref:System.IDisposable.Dispose%2A> w swojej <xref:System.IDisposable.Dispose%2A> metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest to bezpieczne pominąć ostrzeżenie od tej reguły, jeśli wywołanie `base`.<xref:System.IDisposable.Dispose%2A> występuje, dokładniejsze wywoływania niż sprawdzanie reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano typu `TypeA` implementującej <xref:System.IDisposable>.

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano typu `TypeB` który dziedziczy z typu `TypeA` i prawidłowo wywołuje jego <xref:System.IDisposable.Dispose%2A> metody.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>Zobacz też
 <xref:System.IDisposable?displayProperty=fullName> [Wzorzec Dispose](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
