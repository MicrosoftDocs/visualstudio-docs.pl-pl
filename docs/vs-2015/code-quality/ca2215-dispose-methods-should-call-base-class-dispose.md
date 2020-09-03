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
ms.openlocfilehash: 4197c2faaf4aa23db930a9019538592326a84116
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534384"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: Metody Dispose powinny wywoływać metodę Dispose klasy bazowej
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Typ, który implementuje <xref:System.IDisposable?displayProperty=fullName> dziedziczy z typu, który również implementuje <xref:System.IDisposable> . <xref:System.IDisposable.Dispose%2A>Metoda typu dziedziczenia nie wywołuje <xref:System.IDisposable.Dispose%2A> metody typu nadrzędnego.

## <a name="rule-description"></a>Opis reguły
 Jeśli typ dziedziczy z typu jednorazowego, musi wywołać <xref:System.IDisposable.Dispose%2A> metodę typu podstawowego z poziomu własnej <xref:System.IDisposable.Dispose%2A> metody. Wywołanie metody Dispose typu podstawowego gwarantuje, że wszystkie zasoby utworzone przez typ podstawowy są wydane.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, wywołaj metodę `base` .<xref:System.IDisposable.Dispose%2A> w <xref:System.IDisposable.Dispose%2A> metodzie.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 W przypadku wywołania do programu można bezpiecznie pominąć ostrzeżenie z tej reguły `base` .<xref:System.IDisposable.Dispose%2A> występuje na bardziej szczegółowym poziomie wywoływania niż sprawdzanie reguł.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia typ `TypeA` , który implementuje <xref:System.IDisposable> .

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern/cs/FxCop.Usage.IDisposablePattern.cs#1)]

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ `TypeB` , który dziedziczy po typie `TypeA` i prawidłowo wywołuje jego <xref:System.IDisposable.Dispose%2A> metodę.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>Zobacz też
 <xref:System.IDisposable?displayProperty=fullName>Usuń [wzorzec](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
