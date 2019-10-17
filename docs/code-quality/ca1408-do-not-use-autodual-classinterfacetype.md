---
title: 'CA1408: Nie używać AutoDual ClassInterfaceType'
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
ms.openlocfilehash: 142d011ff73fbaf03af62164f962470f8feb3246
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440400"
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408: Nie używać AutoDual ClassInterfaceType

|||
|-|-|
|TypeName|DoNotUseAutoDualClassInterfaceType|
|CheckId|CA1408|
|Kategoria|Microsoft. współdziałanie|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna
Typ widoczny dla Component Object Model (COM) jest oznaczony atrybutem <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> ustawionym na wartość `AutoDual` <xref:System.Runtime.InteropServices.ClassInterfaceType>.

## <a name="rule-description"></a>Opis reguły
Typy, które korzystają z podwójnych interfejsów, umożliwiają klientom powiązanie z określonym interfejsem. Wszelkie zmiany w przyszłej wersji układu typu lub wszelkich typów podstawowych spowodują przerwanie klientów COM powiązanych z interfejsem. Domyślnie, jeśli atrybut <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> nie jest określony, używany jest interfejs tylko do wysyłania.

O ile nie zostanie oznaczona inaczej, wszystkie publiczne typy nieogólne są widoczne dla modelu COM. wszystkie typy niepubliczne i ogólne są niewidoczne dla modelu COM.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, Zmień wartość atrybutu <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> na wartość `None` <xref:System.Runtime.InteropServices.ClassInterfaceType> i jawnie Zdefiniuj interfejs.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżenia z tej reguły, chyba że nie ma pewności, że układ typu i jego typy podstawowe nie zmienią się w przyszłej wersji.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje klasę, która narusza regułę i ponowną deklarację klasy w celu użycia jawnego interfejsu.

[!code-csharp[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/CSharp/ca1408-do-not-use-autodual-classinterfacetype_1.cs)]
[!code-vb[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/VisualBasic/ca1408-do-not-use-autodual-classinterfacetype_1.vb)]

## <a name="related-rules"></a>Powiązane reguły
[CA1403: Typy automatycznego układu nie powinny być widoczne dla modelu COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)

[CA1412: Oznacz interfejsy ComSource jako interfejsy IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)

## <a name="see-also"></a>Zobacz także

- [Kwalifikowanie typów .NET do międzyoperacyjności](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)
