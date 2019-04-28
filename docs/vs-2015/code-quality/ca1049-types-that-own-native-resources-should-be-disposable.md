---
title: 'CA1049: Typy, które posiadają natywne zasoby powinny być usuwalne | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 628a50a66c973020ff62d8041672901b2a578d31
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62536083"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049: Typy, do których należą natywne zasoby, powinny być możliwe do likwidacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Odwołuje się do typu <xref:System.IntPtr?displayProperty=fullName> pola <xref:System.UIntPtr?displayProperty=fullName> pola lub <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> pola, ale nie implementuje <xref:System.IDisposable?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły
 Reguła ta zakłada, że <xref:System.IntPtr>, <xref:System.UIntPtr>, i <xref:System.Runtime.InteropServices.HandleRef> pola Zapisz wskaźniki do niezarządzanych zasobów. Typy, które alokują niezarządzane zasoby, powinny implementować <xref:System.IDisposable> aby umożliwić wywołującym zwolnienie tych zasobów na żądanie i skrócenie czasu istnienia obiektów, które zawierają te zasoby.

 Zalecany wzorzec projektowania do wyczyścić niezarządzane zasoby ma na celu dostarczenie ukrytego i oznacza, że jawne zwolnienie tych zasobów za pomocą <xref:System.Object.Finalize%2A?displayProperty=fullName> metody i <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> metody, odpowiednio. Moduł odśmiecania pamięci wywołuje <xref:System.Object.Finalize%2A> metodę obiektu w nieokreślonym czasie po obiekt jest określany jako nie jest już dostępny. Po <xref:System.Object.Finalize%2A> jest wywoływana, dodatkowy wyrzucania elementów bezużytecznych jest wymagany w celu zwolnienia obiektu. <xref:System.IDisposable.Dispose%2A> Metoda umożliwia obiektowi wywołującemu jawnie zwalniać zasoby na żądanie, starsze niż zasoby zostaną zwolnione, jeśli pole pozostanie na wyrzucanie elementów bezużytecznych. Po go czyści niezarządzane zasoby <xref:System.IDisposable.Dispose%2A> powinny wywoływać <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> metodę, aby umożliwić poinformować, że moduł odśmiecania pamięci <xref:System.Object.Finalize%2A> nie ma już wywołane; to eliminuje potrzebę stosowania dodatkowych wyrzucania elementów bezużytecznych i skraca okres istnienia obiektu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zaimplementować <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli typ nie odwołuje się do niezarządzanego zasobu. W przeciwnym razie nie Pomijaj ostrzeżeń dla tej reguły, ponieważ nie można zaimplementować <xref:System.IDisposable> może spowodować, że zasoby niezarządzane stać się niedostępne lub rozłączania.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia typ, który implementuje <xref:System.IDisposable> wyczyścić niezarządzany zasób.

 [!code-csharp[FxCop.Design.UnmanagedResources#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/cs/FxCop.Design.UnmanagedResources.cs#1)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UnmanagedResources/vb/FxCop.Design.UnmanagedResources.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2115: Wywołaj GC. KeepAlive podczas korzystania z zasobów natywnych](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816: Wywołaj GC. SuppressFinalize poprawnie](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA2216: Typy możliwe do rozporządzania powinny deklarować finalizator](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA1001: Typy, które posiadają pola usuwalne powinny być usuwalne](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>Zobacz też
  [Wzorzec Dispose](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
