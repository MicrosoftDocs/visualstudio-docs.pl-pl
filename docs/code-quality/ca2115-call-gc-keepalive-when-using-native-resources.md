---
title: 'CA2115: Wywołaj funkcję GC.KeepAlive w przypadku korzystania z zasobów natywnych'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CallGCKeepAliveWhenUsingNativeResources
- CA2115
helpviewer_keywords:
- CA2115
- CallGCKeepAliveWhenUsingNativeResources
ms.assetid: f00a59a7-2c6a-4bbe-a1b3-7bf77d366f34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: eb6d28e15870907034479e698ba8e7464f4f5159
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232721"
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115: Wywołaj funkcję GC.KeepAlive w przypadku korzystania z zasobów natywnych

|||
|-|-|
|TypeName|CallGCKeepAliveWhenUsingNativeResources|
|CheckId|CA2115|
|Kategoria|Microsoft.Security|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Metoda zadeklarowana w typie z finalizatorem odwołuje się <xref:System.IntPtr?displayProperty=fullName> do pola lub <xref:System.UIntPtr?displayProperty=fullName> , ale nie wywołuje <xref:System.GC.KeepAlive%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły

Wyrzucanie elementów bezużytecznych kończy obiekt, jeśli nie ma więcej odwołań do niego w kodzie zarządzanym. Niezarządzane odwołania do obiektów nie uniemożliwiają wyrzucania elementów bezużytecznych. Ta reguła wykrywa błędy, które mogą wystąpić, ponieważ kończy się działanie niezarządzanego zasobu, a wciąż jest on używany w kodzie niezarządzanym.

Ta reguła zakłada, <xref:System.IntPtr> że <xref:System.UIntPtr> i pola są przechowywane ze wskaźnikami do niezarządzanych zasobów. Ponieważ celem finalizatora jest zwolnienie niezarządzanych zasobów, reguła zakłada, że finalizator spowoduje zwolnienie niezarządzanego zasobu wskazywanego przez pola wskaźnika. Ta reguła zakłada również, że metoda odwołuje się do pola wskaźnika, aby przekazać niezarządzany zasób do kodu niezarządzanego.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, Dodaj <xref:System.GC.KeepAlive%2A> wywołanie do metody, przekazując bieżące wystąpienie (`this` w C# i C++) jako argument. Umieść wywołanie po ostatnim wierszu kodu, w którym obiekt musi być chroniony przed wyrzucaniem elementów bezużytecznych. Natychmiast po wywołaniu <xref:System.GC.KeepAlive%2A>, obiekt jest ponownie uznawany za gotowy do wyrzucania elementów bezużytecznych przy założeniu, że nie istnieją żadne zarządzane odwołania.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Ta reguła wykonuje pewne założenia, które mogą prowadzić do fałszywych wartości dodatnich. Możesz bezpiecznie pominąć ostrzeżenie z tej reguły, jeśli:

- Finalizator nie zwalnia zawartości ani <xref:System.IntPtr> <xref:System.UIntPtr> pola, do którego odwołuje się metoda.

- Metoda nie przekazuje <xref:System.IntPtr> pola lub <xref:System.UIntPtr> do niezarządzanego kodu.

Uważnie Przejrzyj inne komunikaty przed wyłączeniem ich. Ta zasada wykrywa błędy, które są trudne do odtworzenia i debugowania.

## <a name="example"></a>Przykład

W poniższym przykładzie `BadMethod` nie zawiera wywołania do `GC.KeepAlive` i w związku z tym narusza zasady. `GoodMethod`zawiera poprawiony kod.

> [!NOTE]
> Ten przykład to pseudo-kod. Chociaż kod kompiluje i uruchamia, ostrzeżenie nie zostanie wyzwolone, ponieważ niezarządzany zasób nie został utworzony ani zwolniony.

[!code-csharp[FxCop.Security.IntptrAndFinalize#1](../code-quality/codesnippet/CSharp/ca2115-call-gc-keepalive-when-using-native-resources_1.cs)]

## <a name="see-also"></a>Zobacz także

- <xref:System.GC.KeepAlive%2A?displayProperty=fullName>
- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.Object.Finalize%2A?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>
- [Wzorzec Dispose](/dotnet/standard/design-guidelines/dispose-pattern)