---
title: 'CA2205: Użyj zarządzanych odpowiedników funkcji API Win32'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ad26dcbbbef5a34796ca0aa134653c3c9df5d763
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253255"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: Użyj zarządzanych odpowiedników funkcji API Win32

|||
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|Kategoria|Microsoft.Usage|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Metoda wywołania platformy jest zdefiniowana, a metoda o równoważnej funkcjonalności istnieje w programie .NET.

## <a name="rule-description"></a>Opis reguły

Metoda wywołania platformy służy do wywoływania niezarządzanej funkcji DLL i jest definiowana przy użyciu <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atrybutu `Declare` lub słowa kluczowego w Visual Basic. Nieprawidłowo zdefiniowana Metoda wywołania platformy może prowadzić do wyjątków w czasie wykonywania z powodu problemów, takich jak nieprawidłowa funkcja nazwana, wadliwe mapowanie parametrów i typów danych wartości zwracanej oraz niepoprawne specyfikacje pola, takie jak Konwencja wywoływania i znak zbiór. Jeśli jest dostępna, jest prostsze i mniej podatne na wywoływanie równoważnej metody zarządzanej niż w celu bezpośredniej definicji i wywołania metody niezarządzanej. Wywołanie metody Invoke platformy może również prowadzić do dodatkowych problemów z zabezpieczeniami, które muszą zostać rozwiązane.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, Zastąp wywołanie funkcji niezarządzanej wywołaniem swojego równoważnego elementu zarządzanego.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Pomiń ostrzeżenie z tej reguły, jeśli sugerowana metoda zastępująca nie zapewnia wymaganych funkcji.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia definicję metody wywołania platformy, która narusza regułę. Ponadto są wyświetlane wywołania metody Invoke platformy i równoważnej metody zarządzanej.

[!code-csharp[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/CSharp/ca2205-use-managed-equivalents-of-win32-api_1.cs)]
[!code-vb[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/VisualBasic/ca2205-use-managed-equivalents-of-win32-api_1.vb)]

## <a name="related-rules"></a>Powiązane reguły

- [CA1404: Wywołanie metody GetLastError bezpośrednio po elemencie P/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)
- [CA1060: Przenieś P/Invoke do klasy NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)
- [CA1400: Punkty wejścia P/Invoke powinny istnieć](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)
- [CA1401: P/Invoke nie powinny być widoczne](../code-quality/ca1401-p-invokes-should-not-be-visible.md)
- [CA2101 Określ kierowanie dla argumentów ciągu P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)