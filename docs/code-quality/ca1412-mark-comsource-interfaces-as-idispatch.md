---
title: 'CA1412: Oznacz interfejsy ComSource jako IDispatch'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 227cc5c47a2001cd6c3b71718ae2a29032bed71c
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444199"
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412: Oznacz interfejsy ComSource jako IDispatch

|||
|-|-|
|TypeName|MarkComSourceInterfacesAsIDispatch|
|CheckId|CA1412|
|Kategoria|Microsoft. współdziałanie|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna

Typ jest oznaczony atrybutem <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>, a co najmniej jeden określony interfejs nie jest oznaczony atrybutem <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> ustawionym na wartość `InterfaceIsDispatch`.

## <a name="rule-description"></a>Opis reguły

<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> służy do identyfikowania interfejsów zdarzeń, które Klasa uwidacznia dla klientów Component Object Model (COM). Te interfejsy muszą być uwidocznione jako `InterfaceIsIDispatch`, aby umożliwić klientom Visual Basic 6, otrzymywanie powiadomień o zdarzeniach. Domyślnie, jeśli interfejs nie jest oznaczony atrybutem <xref:System.Runtime.InteropServices.InterfaceTypeAttribute>, zostanie uwidoczniony jako podwójny interfejs.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy dodać lub zmodyfikować atrybut <xref:System.Runtime.InteropServices.InterfaceTypeAttribute>, aby jego wartość była równa InterfaceIsIDispatch dla wszystkich interfejsów, które są określone przy użyciu atrybutu <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano klasę, w której jeden z interfejsów narusza regułę.

[!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/CSharp/ca1412-mark-comsource-interfaces-as-idispatch_1.cs)]
[!code-vb[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/VisualBasic/ca1412-mark-comsource-interfaces-as-idispatch_1.vb)]

## <a name="related-rules"></a>Powiązane reguły

[CA1408: Nie używaj wartości ClassInterfaceType dla elementu AutoDual](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Zobacz także

- [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)
