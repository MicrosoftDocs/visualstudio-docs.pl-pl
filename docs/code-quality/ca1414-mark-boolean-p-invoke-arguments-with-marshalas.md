---
title: 'CA1414: Oznacz argumenty typu boolean elementu P-Invoke argumentem MarshalAs'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 68b0400e366f70690acb7a04b425472e0059b726
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55021978"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: Oznacz argumenty typu boolean elementu P/Invoke argumentem MarshalAs

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Kategoria|Microsoft.Interoperability|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda wywołania platformy deklaracja zawiera <xref:System.Boolean?displayProperty=fullName> parametrze lub wartości zwracanej, ale <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> atrybut nie jest stosowany do parametrów lub wartości zwracanej.

## <a name="rule-description"></a>Opis reguły
 Platforma wywołania metody uzyskuje dostęp do niezarządzanego kodu i jest definiowana za pomocą `Declare` — słowo kluczowe w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] lub <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Określa zachowanie marshalingu, która jest używana do konwersji typów danych między kodem zarządzanym i niezarządzanym. Wiele proste typy danych, na przykład <xref:System.Byte?displayProperty=fullName> i <xref:System.Int32?displayProperty=fullName>, mieć pojedynczy reprezentacji w niezarządzanym kodzie i nie wymagają specyfikacji ich zachowanie marshalingu; środowisko uruchomieniowe języka wspólnego automatycznie dostarcza poprawnego zachowania.

 <xref:System.Boolean> — Typ danych ma wiele reprezentacji w kodzie niezarządzanym. Gdy <xref:System.Runtime.InteropServices.MarshalAsAttribute> nie zostanie określony, domyślne zachowanie marshalingu <xref:System.Boolean> typ danych jest <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. To jest 32-bitową liczbę całkowitą, która nie jest odpowiednie w każdych okolicznościach. Logiczna reprezentacja, wymaganego przez niezarządzane metody powinny być określane i dopasowywane do odpowiednich <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. UnmanagedType.Bool jest typu Win32 BOOL, który jest zawsze 4 bajty. UnmanagedType.U1 powinna być używana dla języka C++ `bool` lub inne typy 1-bajtowe.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zastosować <xref:System.Runtime.InteropServices.MarshalAsAttribute> do <xref:System.Boolean> parametrze lub wartości zwracanej. Ustaw wartość atrybutu do odpowiedniego <xref:System.Runtime.InteropServices.UnmanagedType>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Nawet w przypadku domyślne zachowanie marshalingu jest właściwa, kod łatwiej jest zachowywana, gdy zachowanie jest jawnie określona.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano wywołanie platformy metody, które są oznaczone odpowiednią <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutów.

 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1901: Deklaracje P/Invoke powinny być przenośne](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101: Należy określić marshaling dla argumentów ciągu P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>
- [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)