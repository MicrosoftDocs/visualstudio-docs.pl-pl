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
ms.openlocfilehash: b26d92ca63a94cac7e293a688b1c7b3331586877
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234792"
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408: Nie używaj wartości AutoDual elementu ClassInterfaceType

|||
|-|-|
|TypeName|DoNotUseAutoDualClassInterfaceType|
|CheckId|CA1408|
|Kategoria|Microsoft. współdziałanie|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna
Typ widoczny dla Component Object Model (com) jest oznaczony <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybutem ustawionym `AutoDual` na wartość <xref:System.Runtime.InteropServices.ClassInterfaceType>.

## <a name="rule-description"></a>Opis reguły
Typy, które korzystają z podwójnych interfejsów, umożliwiają klientom powiązanie z określonym interfejsem. Wszelkie zmiany w przyszłej wersji układu typu lub wszelkich typów podstawowych spowodują przerwanie klientów COM powiązanych z interfejsem. Domyślnie, jeśli <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybut nie jest określony, używany jest interfejs tylko do wysyłania.

O ile nie zostanie oznaczona inaczej, wszystkie publiczne typy nieogólne są widoczne dla modelu COM. wszystkie typy niepubliczne i ogólne są niewidoczne dla modelu COM.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, Zmień wartość <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> atrybutu `None` na wartość <xref:System.Runtime.InteropServices.ClassInterfaceType> i jawnie Zdefiniuj interfejs.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżenia z tej reguły, chyba że nie ma pewności, że układ typu i jego typy podstawowe nie zmienią się w przyszłej wersji.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje klasę, która narusza regułę i ponowną deklarację klasy w celu użycia jawnego interfejsu.

[!code-csharp[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/CSharp/ca1408-do-not-use-autodual-classinterfacetype_1.cs)]
[!code-vb[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/VisualBasic/ca1408-do-not-use-autodual-classinterfacetype_1.vb)]

## <a name="related-rules"></a>Powiązane reguły
[CA1403: Typy Autoukładu nie powinny być widoczne dla modelu COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)

[CA1412: Oznacz interfejsy ComSource jako IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)

## <a name="see-also"></a>Zobacz także

- [Kwalifikowanie typów .NET do międzyoperacyjności](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)