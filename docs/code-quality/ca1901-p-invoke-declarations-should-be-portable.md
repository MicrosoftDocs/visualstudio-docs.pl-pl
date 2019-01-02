---
title: 'CA1901: Deklaracje P-Invoke powinny być przenośne'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
helpviewer_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cbc1bbb0bc298973a9cfc3714049fb6dd7dd9302
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53825636"
---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901: Deklaracje P/Invoke powinny być przenośne

|||
|-|-|
|TypeName|PInvokeDeclarationsShouldBePortable|
|CheckId|CA1901|
|Kategoria|Microsoft.Portability|
|Zmiana kluczowa|Istotne - P/Invoke jest widoczna spoza zestawu. Bez podziału — Jeśli P/Invoke nie jest widoczna spoza zestawu.|

## <a name="cause"></a>Przyczyna
 Ta reguła oblicza rozmiar każdego parametru oraz wartość zwracaną metody P/Invoke i sprawdza, czy ich rozmiar przekazywania do kodu niezarządzanego na platformach 32-bitowych i 64-bitowych jest poprawny. Najbardziej typowe naruszenie tej zasady jest do przekazania liczby całkowitej stałych rozmiarach, w których wymagane jest zależny od platformy, wskaźnika wielkości zmiennej.

## <a name="rule-description"></a>Opis reguły
 Jedną z następujących scenariuszy narusza tę regułę występuje:

- Wartość zwracana lub parametr jest wpisane jako liczba całkowita stałym rozmiarze, gdy powinna być typizowana jako `IntPtr`.

- Wartość zwracana lub parametr jest wpisana jako `IntPtr` kiedy powinna być typizowana jako liczbą całkowitą o stałym rozmiarze.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 To naruszenie można rozwiązać za pomocą `IntPtr` lub `UIntPtr` do reprezentowania dojścia, zamiast `Int32` lub `UInt32`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie należy pominąć to ostrzeżenie.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano naruszenie tej zasady.

```csharp
internal class NativeMethods
{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, IntPtr nIconIndex);
}
```

 W tym przykładzie `nIconIndex` parametru jest zadeklarowany jako `IntPtr`, który wynosi 4 bajty szerokiego to platforma 32-bitowych i 8 bajtów szerokości na platformie 64-bitowej. W deklaracji niezarządzanych poniżej, możesz zobaczyć, że `nIconIndex` jest 4-bajtowa liczba całkowita bez znaku na wszystkich platformach.

```csharp
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,
    UINT nIconIndex);
```

## <a name="example"></a>Przykład
 Aby naprawić naruszenie, zmień deklarację do następujących:

```csharp
internal class NativeMethods{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)] 
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, uint nIconIndex);
}
```

## <a name="see-also"></a>Zobacz także
 [Ostrzeżenia dotyczące przenośności](../code-quality/portability-warnings.md)