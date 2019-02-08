---
title: 'CA1408: Nie używaj wartości AutoDual elementu ClassInterfaceType'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotUseAutoDualClassInterfaceType
- CA1408
helpviewer_keywords:
- CA1408
- DoNotUseAutoDualClassInterfaceType
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c811c7e2b6ba06c716179469c8b038fd26b3b38a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55908017"
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408: Nie używaj wartości AutoDual elementu ClassInterfaceType

|||
|-|-|
|TypeName|DoNotUseAutoDualClassInterfaceType|
|CheckId|CA1408|
|Kategoria|Microsoft.Interoperability|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ widoczny Component Object Model (COM) jest oznaczony za pomocą <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> ustawioną wartość atrybutu `AutoDual` wartość <xref:System.Runtime.InteropServices.ClassInterfaceType>.

## <a name="rule-description"></a>Opis reguły
 Typy, które korzystają z podwójnych interfejsów, umożliwiają klientom powiązanie z określonym interfejsem. Wszelkie zmiany w przyszłej wersji układu typu lub wszelkich typów podstawowych spowodują przerwanie klientów COM powiązanych z interfejsem. Domyślnie jeśli <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybut nie zostanie określony, używany jest interfejs tylko do wysyłki.

 O ile nie jest oznaczony jako inaczej, wszystkie typy nierodzajowymi publiczne są widoczne dla modelu COM; wszystkie typy niepublicznych i ogólny są niewidoczne dla modelu COM.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zmienić wartość <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybutu `None` wartość <xref:System.Runtime.InteropServices.ClassInterfaceType> i jawnie definiują interfejs.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły, jeśli nie jest pewne, czy układu typu i jego typów podstawowych nie spowoduje zmiany w przyszłych wersjach.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia klasę, która narusza regułę i ponownej deklaracji klasy, aby używać interfejsu jawnego.

 [!code-csharp[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/CSharp/ca1408-do-not-use-autodual-classinterfacetype_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/VisualBasic/ca1408-do-not-use-autodual-classinterfacetype_1.vb)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1403: Typy automatycznego układu nie powinny być widoczne dla modelu COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)

 [CA1412: Oznacz interfejsy ComSource jako IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)

## <a name="see-also"></a>Zobacz także

- [Kwalifikowanie typów .NET do międzyoperacyjności](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)