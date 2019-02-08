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
ms.openlocfilehash: 034f80c9198ab098070e6642f4a4d96cff1744c5
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55927649"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: Finalizatory powinny wywoływać finalizator klasy bazowej

|||
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Typ, który zastępuje <xref:System.Object.Finalize%2A?displayProperty=fullName> nie mogą wywoływać <xref:System.Object.Finalize%2A> metody w klasie bazowej.

## <a name="rule-description"></a>Opis reguły

Finalizacja musi być powielana w hierarchii dziedziczenia. Aby to zapewnić, typy muszą wywołać klasy bazowej <xref:System.Object.Finalize%2A> metodę z własnych <xref:System.Object.Finalize%2A> metody. Kompilator języka C#, które automatycznie dodaje wywołanie finalizatory klasy bazowej.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy wywołać typ podstawowy <xref:System.Object.Finalize%2A> metody z Twojej <xref:System.Object.Finalize%2A> metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły. Niektóre kompilatory, których platformą docelową środowiska uruchomieniowego języka wspólnego Wstawianie wywołania finalizator typu podstawowego języka Microsoft intermediate language (MSIL). Jeśli ostrzeżenie od tej reguły jest zgłaszany, kompilator nie wstawić wywołanie i należy go dodać do kodu.

## <a name="example"></a>Przykład

W poniższym przykładzie w języku Visual Basic przedstawiono typu `TypeB` poprawnie wywołująca <xref:System.Object.Finalize%2A> metody w klasie bazowej.

[!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]

## <a name="see-also"></a>Zobacz także

- [Wzorzec Dispose](/dotnet/standard/design-guidelines/dispose-pattern)