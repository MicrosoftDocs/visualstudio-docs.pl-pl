---
title: 'CA1049: typy posiadające zasoby natywne powinny być jednorazowe | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1049
- TypesThatOwnNativeResourcesShouldBeDisposable
helpviewer_keywords:
- TypesThatOwnNativeResourcesShouldBeDisposable
- CA1049
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: aaaf95346c51e2cb5cadb01a39e482bb508bc764
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668904"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: Typy, które posiadają natywne zasoby powinny być usuwalne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Typ odwołuje się do pola <xref:System.IntPtr?displayProperty=fullName>, <xref:System.UIntPtr?displayProperty=fullName> lub pola <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>, ale nie implementuje <xref:System.IDisposable?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły
 Ta reguła zakłada, że pola <xref:System.IntPtr>, <xref:System.UIntPtr> i <xref:System.Runtime.InteropServices.HandleRef> przechowują wskaźniki do zasobów niezarządzanych. Typy, które przydzielą zasoby niezarządzane, powinny implementować <xref:System.IDisposable>, aby umożliwić wywoływanie tych zasobów na żądanie i skrócić okresy istnienia obiektów przechowujących zasoby.

 Zalecany Wzorzec projektowy w celu oczyszczenia zasobów niezarządzanych polega na dostarczeniu zarówno niejawnego, jak i jawnego środka do zwolnienia tych zasobów przy użyciu metody <xref:System.Object.Finalize%2A?displayProperty=fullName> i metody <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>. Moduł wyrzucania elementów bezużytecznych wywołuje metodę <xref:System.Object.Finalize%2A> obiektu w pewnym nieokreślonym czasie po ustaleniu obiektu, aby nie był już osiągalny. Po wywołaniu <xref:System.Object.Finalize%2A> jest wymagane dodatkowe wyrzucanie elementów bezużytecznych w celu zwolnienia obiektu. Metoda <xref:System.IDisposable.Dispose%2A> umożliwia obiektowi wywołującemu jawne zwolnienie zasobów na żądanie, w przypadku gdy pozostawiono do modułu wyrzucania elementów bezużytecznych. Po oczyszczeniu zasobów niezarządzanych <xref:System.IDisposable.Dispose%2A> powinna wywołać metodę <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>, aby pozwolić modułowi wyrzucania elementów bezużytecznych, który nie <xref:System.Object.Finalize%2A> już wywoływany; Eliminuje to konieczność dodatkowego wyrzucania elementów bezużytecznych i skraca okres istnienia obiektu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zaimplementować <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli typ nie odwołuje się do niezarządzanego zasobu, można bezpiecznie pominąć ostrzeżenie z tej reguły. W przeciwnym razie nie pomijaj ostrzeżenia z tej reguły, ponieważ błąd implementacji <xref:System.IDisposable> może spowodować, że niezarządzane zasoby staną się niedostępne lub nieużywane.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia typ, który implementuje <xref:System.IDisposable> w celu oczyszczenia niezarządzanego zasobu.

 [!code-csharp[FxCop.Design.UnmanagedResources#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/cs/FxCop.Design.UnmanagedResources.cs#1)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/vb/FxCop.Design.UnmanagedResources.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2115: Wywołaj funkcję GC.KeepAlive w przypadku korzystania z zasobów natywnych](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816: Wywołaj poprawnie metodę GC.SuppressFinalize](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA2216: Typy możliwe do likwidacji powinny deklarować finalizator](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA1001: Typy z polami możliwymi do likwidacji powinny być możliwe do likwidacji](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>Zobacz też
  [Wzorzec Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
