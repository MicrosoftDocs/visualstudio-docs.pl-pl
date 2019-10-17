---
title: 'CA1404: Wywołaj metodę GetLastError natychmiast po wywołaniu P-Invoke'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
helpviewer_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a6876d9e9326d67d781f49e69a65d41284f54da8
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444270"
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404: Należy wywołać GetLastError natychmiast po P/Invoke

|||
|-|-|
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|
|CheckId|CA1404|
|Kategoria|Microsoft. współdziałanie|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Wykonano wywołanie metody <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> lub równoważnej funkcji Win32 `GetLastError`, a wywołanie, które jest bezpośrednio przed nie jest metodą wywołania platformy.

## <a name="rule-description"></a>Opis reguły
Metoda wywołania platformy uzyskuje dostęp do kodu niezarządzanego i jest definiowana przy użyciu słowa kluczowego `Declare` w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] lub atrybutu <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. Ogólnie rzecz biorąc, w przypadku awarii funkcje niezarządzane wywołują funkcję Win32 `SetLastError`, aby ustawić kod błędu, który jest skojarzony z błędem. Obiekt wywołujący nieudanej funkcji wywołuje funkcję Win32 `GetLastError`, aby pobrać kod błędu i określić przyczynę niepowodzenia. Kod błędu jest obsługiwany dla każdego wątku i jest zastępowany przez następne wywołanie `SetLastError`. Po wywołaniu metody wywołania niepowodzenia platformy kod zarządzany może pobrać kod błędu, wywołując metodę <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>. Ponieważ kod błędu może zostać zastąpiony przez wywołania wewnętrzne z innych metod biblioteki zarządzanej klasy, Metoda `GetLastError` lub <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> powinna być wywoływana natychmiast po wywołaniu metody wywoływana przez platformę.

Reguła ignoruje wywołania następujących elementów zarządzanych, gdy występują między wywołaniem metody wywołania platformy i wywołaniem do <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>. Te elementy członkowskie nie zmieniają kodu błędu i są przydatne do określania sukcesu niektórych wywołań metody wywołania.

- <xref:System.IntPtr.Zero?displayProperty=fullName>

- <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

- <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, Przenieś wywołanie do <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>, aby natychmiast po wywołaniu metody wywołania platformy.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Można bezpiecznie pominąć ostrzeżenie z tej reguły, jeśli kod między wywołaniem metody wywoływanej przez platformę i wywołanie metody <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> nie może jawnie lub niejawnie spowodować zmiany kodu błędu.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje metodę, która narusza regułę i metodę, która spełnia kryteria.

[!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/VisualBasic/ca1404-call-getlasterror-immediately-after-p-invoke_1.vb)]
[!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/CSharp/ca1404-call-getlasterror-immediately-after-p-invoke_1.cs)]

## <a name="related-rules"></a>Powiązane reguły
[CA1060: Przenieś wywołania P/Invoke do klasy NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

[CA1400: Powinny istnieć punkty wejścia P/Invoke](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

[CA1401: Metody P/Invoke nie powinny być widoczne](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

[CA2101: Określ marshaling dla argumentów ciągu wywołania P/Invoke](../code-quality/ca2101.md)

[CA2205: Użyj zarządzanych odpowiedników interfejsu API Win32](../code-quality/ca2205.md)
