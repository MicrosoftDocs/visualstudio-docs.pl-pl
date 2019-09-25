---
title: 'CA1412: Oznacz interfejsy ComSource atrybutem IDispatch'
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
ms.openlocfilehash: caaae787d5e4801f3fc3b8d881b386595fb2eca4
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234688"
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412: Oznacz interfejsy ComSource atrybutem IDispatch

|||
|-|-|
|TypeName|MarkComSourceInterfacesAsIDispatch|
|CheckId|CA1412|
|Kategoria|Microsoft. współdziałanie|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna

Typ jest oznaczony <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> atrybutem, a co najmniej jeden określony interfejs nie jest oznaczony <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> atrybutem ustawionym na `InterfaceIsDispatch` wartość.

## <a name="rule-description"></a>Opis reguły

<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>służy do identyfikowania interfejsów zdarzeń, które Klasa uwidacznia dla klientów Component Object Model (COM). Te interfejsy muszą być uwidocznione `InterfaceIsIDispatch` jako, aby umożliwić klientom Visual Basic 6 com otrzymywanie powiadomień o zdarzeniach. Domyślnie, jeśli interfejs nie jest oznaczony <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> atrybutem, zostanie uwidoczniony jako podwójny interfejs.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy dodać lub zmodyfikować <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> atrybut, tak aby jego wartość była równa InterfaceIsIDispatch dla wszystkich interfejsów, które są określone <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> przy użyciu atrybutu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano klasę, w której jeden z interfejsów narusza regułę.

[!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/CSharp/ca1412-mark-comsource-interfaces-as-idispatch_1.cs)]
[!code-vb[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/VisualBasic/ca1412-mark-comsource-interfaces-as-idispatch_1.vb)]

## <a name="related-rules"></a>Powiązane reguły

[CA1408: Nie używaj AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Zobacz także

- [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)