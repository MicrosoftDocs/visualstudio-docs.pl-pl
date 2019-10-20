---
title: 'CA2215: metody Dispose powinny wywoływać metodę Dispose klasy bazowej | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 89f3705169fb9d28a1ec773671d460f00b98d892
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662851"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: Metody Dispose powinny wywoływać operację usuwania klasy bazowej
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Typ, który implementuje <xref:System.IDisposable?displayProperty=fullName> dziedziczy z typu, który również implementuje <xref:System.IDisposable>. Metoda <xref:System.IDisposable.Dispose%2A> typu dziedziczenia nie wywołuje metody <xref:System.IDisposable.Dispose%2A> typu nadrzędnego.

## <a name="rule-description"></a>Opis reguły
 Jeśli typ dziedziczy z typu jednorazowego, musi wywołać metodę <xref:System.IDisposable.Dispose%2A> typu podstawowego z poziomu własnej metody <xref:System.IDisposable.Dispose%2A>. Wywołanie metody Dispose typu podstawowego gwarantuje, że wszystkie zasoby utworzone przez typ podstawowy są wydane.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, wywołaj `base`. <xref:System.IDisposable.Dispose%2A> w metodzie <xref:System.IDisposable.Dispose%2A>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli wywołanie do `base` było bezpieczne, można pominąć ostrzeżenie z tej reguły. <xref:System.IDisposable.Dispose%2A> występuje na bardziej szczegółowym poziomie wywoływania niż sprawdzanie reguł.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono typ `TypeA` implementujący <xref:System.IDisposable>.

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono typ `TypeB`, który dziedziczy po typie `TypeA` i prawidłowo wywołuje metodę <xref:System.IDisposable.Dispose%2A>.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>Zobacz też
 <xref:System.IDisposable?displayProperty=fullName> — [wzorzec usuwania](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
