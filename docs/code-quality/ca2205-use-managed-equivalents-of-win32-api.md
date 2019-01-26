---
title: 'CA2205: Użyj zarządzanych odpowiedników funkcji API Win32'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 2918750c2128b9f0eab53397b4aaf4c0cc9b6702
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55019765"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: Użyj zarządzanych odpowiedników funkcji API Win32

|||
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Wywołania platformy metoda jest zdefiniowana i metody z równoważną funkcjonalność istnieje w bibliotece klas programu .NET Framework.

## <a name="rule-description"></a>Opis reguły

Metoda wywołania platformy służy do wywoływania niezarządzanych funkcji DLL i jest definiowana za pomocą <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atrybut, lub `Declare` — słowo kluczowe w języku Visual Basic. Platforma nieprawidłowo zdefiniowana invoke, metoda może prowadzić do wyjątki środowiska uruchomieniowego ze względu na problemy, takie jak funkcja misnamed wadliwe mapowania typów danych wartości parametrów i zwrotu i specyfikacji nieprawidłowe pola, takie jak Konwencja wywoływania i znak zestaw. Jeśli to możliwe, jest prostsza i mniej podatne do wywoływania metody zarządzanych równoważne niż do definiowania i bezpośrednio wywoływać metody niezarządzanego. Wywołanie platformy Wywołaj metodę również może prowadzić do problemów zabezpieczeń, które powinny być usuwane.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, Zastąp wywołanie do funkcji niezarządzanych przy użyciu wywołania na odpowiadającą jej zarządzanych.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Pomijaj ostrzeżeń dla tej reguły, jeśli metody sugerowane zastępowania nie udostępnia wymaganych funkcji.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, a platforma wywołać definicję metody, która narusza regułę. Dodatkowo wywołania platformy wywołania metody i są wyświetlane równoważne zarządzaną metodą.

[!code-csharp[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/CSharp/ca2205-use-managed-equivalents-of-win32-api_1.cs)]
[!code-vb[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/VisualBasic/ca2205-use-managed-equivalents-of-win32-api_1.vb)]

## <a name="related-rules"></a>Powiązane reguły

- [CA1404: Wywołaj metodę GetLastError natychmiast po P/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)
- [CA1060: Przenieś P/Invokes do klasy NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)
- [CA1400: Powinny istnieć punkty wejścia P/Invoke](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)
- [CA1401: P/Invokes nie powinny być widoczne](../code-quality/ca1401-p-invokes-should-not-be-visible.md)
- [CA2101: Należy określić marshaling dla argumentów ciągu P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)