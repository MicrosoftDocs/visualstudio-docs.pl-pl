---
title: 'CA2220: Finalizatory powinny wywoływać finalizator klasy bazowej'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e5af6b7872f0fa05183334e6acd2bc4922f84990
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231157"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: Finalizatory powinny wywoływać finalizator klasy bazowej

|||
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|Kategoria|Microsoft.Usage|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Typ, który zastąpień <xref:System.Object.Finalize%2A?displayProperty=fullName> nie <xref:System.Object.Finalize%2A> wywołuje metody w swojej klasie bazowej.

## <a name="rule-description"></a>Opis reguły

Finalizacja musi być powielana w hierarchii dziedziczenia. Aby to zapewnić, typy muszą wywoływać metodę klasy <xref:System.Object.Finalize%2A> bazowej z poziomu własnej <xref:System.Object.Finalize%2A> metody. C# Kompilator automatycznie dodaje wywołanie do klasy bazowej finalizatora.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, wywołaj <xref:System.Object.Finalize%2A> metodę typu podstawowego <xref:System.Object.Finalize%2A> z metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły. Niektóre kompilatory, które są przeznaczone dla środowiska uruchomieniowego języka wspólnego, umożliwiają wstawienie wywołania do finalizatora typu podstawowego do języka pośredniego firmy Microsoft (MSIL). Jeśli zostanie zgłoszone ostrzeżenie z tej reguły, kompilator nie wstawia wywołania i należy dodać go do kodu.

## <a name="example"></a>Przykład

Poniższy Visual Basic przykład pokazuje typ `TypeB` , który poprawnie <xref:System.Object.Finalize%2A> wywołuje metodę w swojej klasie bazowej.

[!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]

## <a name="see-also"></a>Zobacz także

- [Wzorzec Dispose](/dotnet/standard/design-guidelines/dispose-pattern)