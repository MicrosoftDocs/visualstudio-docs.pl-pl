---
title: 'CA2205: Użyj zarządzanych odpowiedników Win32 API | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 931b1e5099bf221fefc7a8f4a19524d2531a4418
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609485"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: Użyj zarządzanych odpowiedników interfejsu API Win32
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Metoda wywołania platformy jest zdefiniowana, a metoda o równoważnej funkcjonalności istnieje w bibliotece klas [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

## <a name="rule-description"></a>Opis reguły
 Metoda wywołania platformy służy do wywoływania niezarządzanej funkcji DLL i jest definiowana przy użyciu atrybutu <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> lub słowa kluczowego `Declare` w Visual Basic. Nieprawidłowo zdefiniowana Metoda wywołania platformy może prowadzić do wyjątków w czasie wykonywania z powodu problemów, takich jak nieprawidłowa funkcja nazwana, wadliwe mapowanie parametrów i typów danych wartości zwracanej oraz niepoprawne specyfikacje pola, takie jak Konwencja wywoływania i znak zbiór. Jeśli jest dostępna, jest to ogólnie prostsze i mniej podatne na wywoływanie równoważnej metody zarządzanej niż w celu bezpośredniej definicji i wywołania metody niezarządzanej. Wywołanie metody Invoke platformy może również prowadzić do dodatkowych problemów z zabezpieczeniami, które muszą zostać rozwiązane.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Zastąp wywołanie funkcji niezarządzanej wywołaniem swojego równoważnego elementu zarządzanego.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomiń ostrzeżenie z tej reguły, jeśli sugerowana metoda zastępująca nie zapewnia wymaganych funkcji.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia definicję metody wywołania platformy, która narusza regułę. Ponadto są wyświetlane wywołania metody Invoke platformy i równoważnej metody zarządzanej.

 [!code-csharp[FxCop.Usage.ManagedEquivalents#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/cs/FxCop.Usage.ManagedEquivalents.cs#1)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/vb/FxCop.Usage.ManagedEquivalents.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1404: Wywołaj metodę GetLastError natychmiast po wywołaniu P/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)

 [CA1060: Przenieś wywołania P/Invoke do klasy NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: Powinny istnieć punkty wejścia P/Invoke](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: Metody P/Invoke nie powinny być widoczne](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: Określ marshaling dla argumentów ciągu wywołania P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)
