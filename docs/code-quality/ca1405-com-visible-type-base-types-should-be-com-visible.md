---
title: 'CA1405: Typy podstawowe typu widocznego modelu COM powinny być widoczne dla modelu COM'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c0221231956c565eb2ce3792d0c88864b0e13e65
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53839326"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405: Typy podstawowe typu widocznego modelu COM powinny być widoczne dla modelu COM

|||
|-|-|
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|
|CheckId|CA1405|
|Kategoria|Microsoft.Interoperability|
|Zmiana kluczowa|DependsOnFix|

## <a name="cause"></a>Przyczyna
 Typ widoczny Component Object Model (COM) pochodzi z typu, który nie jest widoczne dla modelu COM.

## <a name="rule-description"></a>Opis reguły
 Gdy typem widoczne dla modelu COM, elementy członkowskie są dodawane w nowej wersji, należy przestrzegać ścisłe wytyczne w celu uniknięcia przerwanie klientów COM powiązanych do bieżącej wersji. Typ, który jest niewidoczna dla modelu COM przyjęto założenie, że nie trzeba należy wykonać następujące czynności COM wersji powoduje dodanie nowych elementów członkowskich. Jeśli jednak widoczne dla modelu COM typ pochodzi od typu niewidoczne COM i udostępnia interfejs klasy <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> lub <xref:System.Runtime.InteropServices.ClassInterfaceType> (ustawienie domyślne), wszystkie publiczne elementy członkowskie tego typu podstawowego (o ile są wyraźnie oznaczone jako COM niewidoczne, który zbyteczna) są widoczne dla modelu COM. Jeśli typ podstawowy dodaje nowych elementów członkowskich w kolejnej wersji, mogą przestać działać żadnych klientów COM, który należy powiązać interfejsu klasy typu pochodnego. Typy widoczne dla modelu COM powinny pochodzić tylko w typach widocznych dla modelu COM, aby zmniejszyć prawdopodobieństwo przerwanie klientów modelu COM.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, ukrywanie typów podstawowych widoczne dla modelu COM lub typu pochodnego COM.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza regułę.

 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>
- [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)