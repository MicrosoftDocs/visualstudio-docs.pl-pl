---
title: 'CA1901: Deklaracje metody P-Invoke powinny być przenośne'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d878572c4391805773a9a711ee88e7b58f507c65
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233296"
---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901: Deklaracje metody P/Invoke powinny być przenośne

|||
|-|-|
|TypeName|PInvokeDeclarationsShouldBePortable|
|CheckId|CA1901|
|Kategoria|Microsoft. przenośność|
|Zmiana podziału|Przerywanie — jeśli P/Invoke jest widoczny poza zestawem. Bez przerywania — jeśli P/Invoke nie jest widoczny poza zestawem.|

## <a name="cause"></a>Przyczyna
Ta reguła służy do obliczania rozmiaru każdego parametru oraz wartości zwracanej P/Invoke i sprawdza, czy ich rozmiar w przypadku przekierowania do kodu niezarządzanego na 32-bitowych i 64-bitowych platformach jest poprawny. Najbardziej typowym naruszeniem tej reguły jest przekazanie liczby całkowitej o stałym rozmiarze, gdy wymagana jest zmienna o rozmiarze wskaźnika zależnym od platformy.

## <a name="rule-description"></a>Opis reguły
Jeden z następujących scenariuszy narusza tę regułę:

- Wartość zwracana lub parametr są wpisywane jako liczba całkowita o stałym rozmiarze, gdy powinna być wpisana jako `IntPtr`.

- Wartość zwracana lub parametr są wpisywane jako `IntPtr` typ, który powinien być typem w postaci liczby całkowitej o stałym rozmiarze.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Możesz naprawić to naruszenie, `IntPtr` używając lub `UIntPtr` `Int32` do reprezentowania dojść zamiast lub `UInt32`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie należy pomijać tego ostrzeżenia.

## <a name="example"></a>Przykład
Poniższy przykład demonstruje naruszenie tej reguły.

```csharp
internal class NativeMethods
{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, IntPtr nIconIndex);
}
```

W tym przykładzie `nIconIndex` parametr jest zadeklarowany `IntPtr`jako, który ma 4 bajty na platformie 32-bitowej i 8 bajtów na platformie 64-bitowej. W następującej deklaracji niezarządzanej można zobaczyć, że `nIconIndex` jest to 4-bajtowa liczba całkowita bez znaku na wszystkich platformach.

```csharp
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,
    UINT nIconIndex);
```

## <a name="example"></a>Przykład
Aby naprawić naruszenie, zmień deklarację na następujący:

```csharp
internal class NativeMethods{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, uint nIconIndex);
}
```

## <a name="see-also"></a>Zobacz także
[Ostrzeżenia dotyczące przenośności](../code-quality/portability-warnings.md)