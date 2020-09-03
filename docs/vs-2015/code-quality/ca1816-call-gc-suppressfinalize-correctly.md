---
title: 'CA1816: Wywołaj metodę GC. SuppressFinalize poprawnie | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 532478a8d6ed6b88347d196b4a74b6f19a38ef85
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546773"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: Poprawnie wywołaj metodę GC.SuppressFinalize
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|Kategoria|Microsoft. Użycie|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna

- Metoda, która jest implementacją, nie <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> wywołuje <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

- Metoda, która nie jest implementacją <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> wywołań <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

- Metoda wywołuje <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> i przekazuje coś innego niż this (mnie w Visual Basic).

## <a name="rule-description"></a>Opis reguły
 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>Metoda umożliwia użytkownikom zwalnianie zasobów w dowolnym momencie przed udostępnieniem obiektu do wyrzucania elementów bezużytecznych. Jeśli <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> Metoda jest wywoływana, zwalnia zasoby obiektu. To sprawia, że finalizacja nie jest konieczna. <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> należy wywołać, <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> Aby moduł zbierający elementy bezużyteczne nie wywoływał finalizatora obiektu.

 Aby zapobiec ponownemu wdrożeniu [System. IDisposable] w typach pochodnych z finalizatorami<!-- TODO: review code entity reference <xref:assetId:///System.IDisposable?qualifyHint=True&amp;autoUpgrade=False>  -->) i wywołanie go, niezapieczętowane typy bez finalizatorów powinny nadal być wywoływane <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły:

 Jeśli metoda jest implementacją programu <xref:System.IDisposable.Dispose%2A> , Dodaj wywołanie do <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

 Jeśli metoda nie jest implementacją programu <xref:System.IDisposable.Dispose%2A> , należy usunąć wywołanie <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> lub przenieść je do <xref:System.IDisposable.Dispose%2A> implementacji typu.

 Zmień wszystkie wywołania na <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> , aby przekazać je (Me w Visual Basic).

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomijaj ostrzeżenie tylko z tej reguły, jeśli jest używane <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> do kontrolowania okresu istnienia innych obiektów. Nie pomijaj ostrzeżenia z tej reguły, jeśli implementacja nie <xref:System.IDisposable.Dispose%2A> wywołuje <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> . W tej sytuacji niepowodzenie pomijania finalizowania oceny wydajności i nie zapewnia żadnych korzyści.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia metodę, która nieprawidłowo wywołuje <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly.vb#1)]

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia metodę, która prawidłowo wywołuje <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> .

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2215: Metody Dispose powinny wywoływać metodę Dispose klasy bazowej](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA2216: Typy możliwe do likwidacji powinny deklarować finalizator](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>Zobacz też
 [Wzorzec Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
