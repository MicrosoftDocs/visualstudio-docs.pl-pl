---
title: 'CA2220: finalizatory powinny wywoływać finalizator klasy bazowej | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1a4538c66d351956da8168d4f84c1895190ab453
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663588"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: Finalizatory powinny wywoływać finalizatory klasy bazowej
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Typ, który zastępuje <xref:System.Object.Finalize%2A?displayProperty=fullName>, nie wywołuje metody <xref:System.Object.Finalize%2A> w swojej klasie podstawowej.

## <a name="rule-description"></a>Opis reguły
 Finalizacja musi być powielana w hierarchii dziedziczenia. Aby to zapewnić, typy muszą wywoływać swoją klasę bazową <xref:System.Object.Finalize%2A> metodę z poziomu własnej metody <xref:System.Object.Finalize%2A>. C# Kompilator automatycznie dodaje wywołanie do klasy bazowej finalizatora.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, wywołaj metodę <xref:System.Object.Finalize%2A> typu podstawowego z metody <xref:System.Object.Finalize%2A>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Niektóre kompilatory, które są przeznaczone dla środowiska uruchomieniowego języka wspólnego, umożliwiają wstawienie wywołania do finalizatora typu podstawowego do języka pośredniego firmy Microsoft (MSIL). Jeśli zostanie zgłoszone ostrzeżenie z tej reguły, kompilator nie wstawia wywołania i należy dodać go do kodu.

## <a name="example"></a>Przykład
 Poniższy przykład Visual Basic ilustruje typ `TypeB`, który prawidłowo wywołuje metodę <xref:System.Object.Finalize%2A> w swojej klasie bazowej.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>Zobacz też
 [Wzorzec Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
