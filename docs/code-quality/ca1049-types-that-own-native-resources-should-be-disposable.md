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
ms.openlocfilehash: 415b8c95dda3fca084fcb103dfa5e4f39e1a73da
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922528"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: Typy, do których należą natywne zasoby, powinny być możliwe do likwidacji

|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Typ odwołuje się <xref:System.IntPtr?displayProperty=fullName> do pola <xref:System.UIntPtr?displayProperty=fullName> , pola lub <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> pola, ale nie implementuje <xref:System.IDisposable?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły

Ta reguła zakłada, <xref:System.IntPtr>że <xref:System.UIntPtr>pola, <xref:System.Runtime.InteropServices.HandleRef> i przechowują wskaźniki do niezarządzanych zasobów. Typy, które przydzielą zasoby <xref:System.IDisposable> niezarządzane, powinny być implementowane w celu umożliwienia wywołującym wydawania tych zasobów na żądanie i skrócenia okresu istnienia obiektów, które zawierają zasoby.

Zalecany Wzorzec projektowy w celu oczyszczenia zasobów niezarządzanych polega na dostarczeniu zarówno niejawnego, jak i jawnego środka do <xref:System.Object.Finalize%2A?displayProperty=fullName> zwolnienia tych zasobów <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> przy użyciu metody i metody. Moduł zbierający elementy bezużyteczne wywołuje <xref:System.Object.Finalize%2A> metodę obiektu w pewnym nieokreślonym czasie po ustaleniu obiektu, aby nie był już osiągalny. Po <xref:System.Object.Finalize%2A> wywołaniu jest wymagane dodatkowe wyrzucanie elementów bezużytecznych w celu zwolnienia obiektu. <xref:System.IDisposable.Dispose%2A> Metoda umożliwia obiektowi wywołującemu jawne zwolnienie zasobów na żądanie, w przypadku gdy pozostawiono do modułu wyrzucania elementów bezużytecznych. Po oczyszczeniu zasobów niezarządzanych należy <xref:System.IDisposable.Dispose%2A> <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> wywołać metodę, aby pozwolić modułowi wyrzucania elementów bezużytecznych, który <xref:System.Object.Finalize%2A> nie musi być już wywoływany; eliminuje to konieczność dodatkowego wyrzucania elementów bezużytecznych i skraca okres istnienia obiektu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, zaimplementuj <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Jeśli typ nie odwołuje się do niezarządzanego zasobu, można bezpiecznie pominąć ostrzeżenie z tej reguły. W przeciwnym razie nie pomijaj ostrzeżenia z tej reguły, ponieważ niepowodzenie <xref:System.IDisposable> implementacji może spowodować, że niezarządzane zasoby staną się niedostępne lub nieużywane.

## <a name="example"></a>Przykład
W poniższym przykładzie przedstawiono typ, który implementuje <xref:System.IDisposable> czyszczenie niezarządzanego zasobu.

[!code-csharp[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
[!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]

## <a name="related-rules"></a>Powiązane reguły
[CA2115: Wywołaj metodę GC. Utrzymywanie aktywności w przypadku korzystania z zasobów natywnych](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

[CA1816: Wywołaj metodę GC. SuppressFinalize prawidłowo](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

[CA2216 Typy jednorazowe powinny deklarować finalizator](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

[CA1001 Typy, które są własnością pól, powinny być jednorazowe](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>Zobacz także

- [Oczyszczanie zasobów niezarządzanych](/dotnet/standard/garbage-collection/unmanaged)
- [Wzorzec Dispose](/dotnet/standard/design-guidelines/dispose-pattern)