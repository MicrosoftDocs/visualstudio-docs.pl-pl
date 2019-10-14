---
title: 'CA1049: Typy, do których należą natywne zasoby, powinny być możliwe do likwidacji'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1049
- TypesThatOwnNativeResourcesShouldBeDisposable
helpviewer_keywords:
- TypesThatOwnNativeResourcesShouldBeDisposable
- CA1049
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- cplusplus
ms.openlocfilehash: 03b8d222fc2349022ef324c9905279677fc86849
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306121"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: Typy, do których należą natywne zasoby, powinny być możliwe do likwidacji

|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|Category|Microsoft.Design|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Typ odwołuje się do pola <xref:System.IntPtr?displayProperty=fullName>, <xref:System.UIntPtr?displayProperty=fullName> lub pola <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>, ale nie implementuje <xref:System.IDisposable?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły

Ta reguła zakłada, że pola <xref:System.IntPtr>, <xref:System.UIntPtr> i <xref:System.Runtime.InteropServices.HandleRef> przechowują wskaźniki do zasobów niezarządzanych. Typy, które przydzielą zasoby niezarządzane, powinny implementować <xref:System.IDisposable>, aby umożliwić wywoływanie tych zasobów na żądanie i skrócić okresy istnienia obiektów przechowujących zasoby.

Zalecany Wzorzec projektowy w celu oczyszczenia zasobów niezarządzanych polega na przeniesieniu zarówno niejawnego, jak i jawnego środka do zwolnienia tych zasobów przy użyciu metody <xref:System.Object.Finalize%2A?displayProperty=fullName> i metody <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>. Moduł zbierający elementy bezużyteczne wywołuje metodę <xref:System.Object.Finalize%2A> obiektu w pewnym nieokreślonym czasie po ustaleniu obiektu, aby nie był już osiągalny. Po wywołaniu <xref:System.Object.Finalize%2A> do zwolnienia obiektu wymagane jest dodatkowe wyrzucanie elementów bezużytecznych. Metoda <xref:System.IDisposable.Dispose%2A> umożliwia obiektowi wywołującemu jawne zwolnienie zasobów na żądanie, w przypadku gdy pozostawiono do modułu zbierającego elementy bezużyteczne. Po oczyszczeniu zasobów niezarządzanych <xref:System.IDisposable.Dispose%2A> powinna wywołać metodę <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>, aby pozwolić modułowi wyrzucania elementów bezużytecznych wiedzieć, że <xref:System.Object.Finalize%2A> nie musi już być wywoływana; Eliminuje to konieczność dodatkowego wyrzucania elementów bezużytecznych i skraca okres istnienia obiektu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej zasady, należy zaimplementować <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Jeśli typ nie odwołuje się do niezarządzanego zasobu, można bezpiecznie pominąć ostrzeżenie z tej reguły. W przeciwnym razie nie pomijaj ostrzeżenia z tej reguły, ponieważ błąd implementacji <xref:System.IDisposable> może spowodować, że niezarządzane zasoby staną się niedostępne lub nieużywane.

## <a name="example"></a>Przykład
Poniższy przykład przedstawia typ, który implementuje <xref:System.IDisposable> w celu oczyszczenia niezarządzanego zasobu.

[!code-csharp[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
[!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]

## <a name="related-rules"></a>Powiązane reguły
[CA2115: Wywołaj metodę GC. Utrzymywanie aktywności w przypadku korzystania z zasobów natywnych @ no__t-0

[CA1816: Wywołaj metodę GC. SuppressFinalize prawidłowo @ no__t-0

[CA2216: Typy jednorazowe powinny deklarować finalizator @ no__t-0

[CA1001: Typy, które są własnością pól, powinny być jednorazowe @ no__t-0

## <a name="see-also"></a>Zobacz także

- [Oczyszczanie zasobów niezarządzanych](/dotnet/standard/garbage-collection/unmanaged)
- [Wzorzec Dispose](/dotnet/standard/design-guidelines/dispose-pattern)