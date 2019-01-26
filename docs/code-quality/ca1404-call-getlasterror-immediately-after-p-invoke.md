---
title: 'CA1404: Wywołaj metodę GetLastError bezpośrednio po elemencie P-Invoke'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: eec2a29f3d1e967d946488043882e96eb4f081de
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54970932"
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404: Wywołaj metodę GetLastError bezpośrednio po elemencie P/Invoke

|||
|-|-|
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|
|CheckId|CA1404|
|Kategoria|Microsoft.Interoperability|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Połączenie jest nawiązywane w przypadku <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> metody lub równoważne Win32 `GetLastError` funkcji i wywołanie, które pochodzą bezpośrednio przed nie jest to platforma wywołania metody.

## <a name="rule-description"></a>Opis reguły
 Platforma wywołania metody uzyskuje dostęp do niezarządzanego kodu i jest definiowana za pomocą `Declare` — słowo kluczowe w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] lub <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atrybutu. Ogólnie rzecz biorąc, w przypadku awarii funkcji niezarządzanych wywołanie Win32 `SetLastError` funkcję, aby ustawić kod błędu, który jest skojarzony z określonym błędem. Obiekt wywołujący zakończonej niepowodzeniem funkcji wywołuje funkcję Win32 `GetLastError` funkcję, aby pobrać kod błędu i ustalić przyczynę niepowodzenia. Kod błędu jest przechowywany w zasadzie na wątek i jest zastępowany przy następnym wywołaniu `SetLastError`. Po wywołanie nie powiodło się platformy wywołania metody, kodu zarządzanego, mogą pobrać kod błędu przez wywołanie metody <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> metody. Ponieważ kod błędu mogą zostać zastąpione przez wywołania wewnętrznego z innych metod biblioteki zarządzanej klasy `GetLastError` lub <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> metoda powinna być wywoływana bezpośrednio, po wywołaniu metody wywołania platformy.

 Reguła ignoruje wywołania do następujących zarządzanych elementów członkowskich, kiedy występują one między wywołań do platformy wywołania metod i wywołanie <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>. Te elementy członkowskie nie zmieniaj błąd kodu i są przydatne do określenia sukcesu niektóre platformy wywołania wywołania metody.

- <xref:System.IntPtr.Zero?displayProperty=fullName>

- <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

- <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Przenieś wywołanie <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> tak, aby od razu następuje wywołanie platformy wywołania metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomijaj ostrzeżeń dla tej reguły, jeśli kod między platformę wywołania wywołania metody można bezpiecznie i <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> wywołanie metody nie można jawnie lub niejawnie spowodować, że kod błędu, aby zmienić.

## <a name="example"></a>Przykład
 Poniższy kod przedstawia metodę, która narusza regułę określającą, a metoda, która spełnia reguły.

 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/VisualBasic/ca1404-call-getlasterror-immediately-after-p-invoke_1.vb)]
 [!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/CSharp/ca1404-call-getlasterror-immediately-after-p-invoke_1.cs)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1060: Przenieś P/Invokes do klasy NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: Powinny istnieć punkty wejścia P/Invoke](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: P/Invokes nie powinny być widoczne](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: Należy określić marshaling dla argumentów ciągu P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

 [CA2205: Użyj zarządzanych odpowiedników funkcji Win32 API](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)