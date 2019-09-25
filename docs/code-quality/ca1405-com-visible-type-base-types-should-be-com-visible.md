---
title: 'CA1405: Typy podstawowe typów widocznych dla modelu COM powinny być widoczne dla modelu COM'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8e4e5c4ed258bcc88fedbb6d015fed576d326a0f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234954"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405: Typy podstawowe typów widocznych dla modelu COM powinny być widoczne dla modelu COM

|||
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|CheckId|CA1405|
|Kategoria|Microsoft. współdziałanie|
|Zmiana podziału|DependsOnFix|

## <a name="cause"></a>Przyczyna
Typ widoczny dla Component Object Model (COM) pochodzi z typu, który nie jest widoczny dla modelu COM.

## <a name="rule-description"></a>Opis reguły
Gdy typ widoczny dla modelu COM dodaje członków w nowej wersji, musi przestrzegać ścisłych wytycznych, aby uniknąć przerwania klientów COM, które są powiązane z bieżącą wersją. Typ, który jest niewidoczny dla modelu COM, zakłada, że nie musi on być zgodny z regułami dotyczącymi obsługi wersji modelu COM podczas dodawania nowych elementów członkowskich. Jeśli jednak typ widoczny dla modelu COM pochodzi od typu niewidocznego dla modelu COM i uwidacznia Interfejs <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> klasy <xref:System.Runtime.InteropServices.ClassInterfaceType> lub (domyślnie), wszystkie publiczne elementy członkowskie typu podstawowego (chyba że są one jawnie oznaczone jako niewidoczne dla modelu COM, co byłoby nadmiarowe) są dostępne dla modelu COM. Jeśli typ podstawowy dodaje nowych członków w kolejnej wersji, każdy klient COM, który powiąże się z interfejsem klasy typu pochodnego może zostać zerwana. Typy widoczne dla modelu COM powinny dziedziczyć tylko z typów widocznych dla modelu COM, aby zmniejszyć prawdopodobieństwo przerwania klientów COM.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, Zmień typy podstawowe modelu COM widoczne lub niewidoczny typ pochodny COM.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje typ, który narusza regułę.

[!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
[!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>
- [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)