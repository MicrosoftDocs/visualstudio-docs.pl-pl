---
title: 'CA1414: Oznacz argumenty typu boolean elementu P-Invoke argumentem MarshalAs'
ms.date: 11/04/2016
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
ms.openlocfilehash: 8e8d47b73009e0bd742c989ddc0311644453e5d9
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921869"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: Oznacz argumenty typu boolean elementu P/Invoke argumentem MarshalAs

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Kategoria|Microsoft. współdziałanie|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
Deklaracja metody wywołania platformy zawiera <xref:System.Boolean?displayProperty=fullName> parametr lub wartość zwracaną, <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> ale atrybut nie jest stosowany do parametru lub wartości zwracanej.

## <a name="rule-description"></a>Opis reguły
Metoda Invoke platformy uzyskuje dostęp do kodu niezarządzanego i jest definiowana `Declare` za pomocą [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] słowa kluczowego w lub <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. <xref:System.Runtime.InteropServices.MarshalAsAttribute>Określa zachowanie organizowania, które służy do konwertowania typów danych między zarządzanym i niezarządzanym kodem. Wiele prostych typów danych, takich jak <xref:System.Byte?displayProperty=fullName> i <xref:System.Int32?displayProperty=fullName>, mają pojedynczą reprezentację w kodzie niezarządzanym i nie wymaga specyfikacji ich zachowania Marshaling. środowisko uruchomieniowe języka wspólnego automatycznie dostarcza poprawne zachowanie.

Typ <xref:System.Boolean> danych ma wiele reprezentacji w kodzie niezarządzanym. Gdy nie <xref:System.Boolean> <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>jest określony, domyślnym zachowaniem organizowania dla tego typu danych jest. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Jest to 32-bitowa liczba całkowita, która nie jest odpowiednia w żadnym przypadku. Reprezentacja logiczna wymagana przez metodę niezarządzaną powinna być określona i zgodna z odpowiednią <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. UnmanagedType. bool jest typem BOOL Win32, który ma zawsze 4 bajty. Typ UnmanagedType. U1 powinien być używany C++ `bool` dla lub innych typów 1-bajtowych.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, Zastosuj <xref:System.Runtime.InteropServices.MarshalAsAttribute> <xref:System.Boolean> do parametru lub wartości zwracanej. Ustaw wartość atrybutu na odpowiednią <xref:System.Runtime.InteropServices.UnmanagedType>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły. Nawet jeśli domyślne zachowanie kierowania jest odpowiednie, kod jest łatwiejszy do utrzymania, gdy zachowanie jest jawnie określone.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje metody wywołania platformy, które są oznaczone odpowiednimi <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutami.

[!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
[!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
[!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]

## <a name="related-rules"></a>Powiązane reguły
[CA1901: Deklaracje P/Invoke powinny być przenośne](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

[CA2101 Określ kierowanie dla argumentów ciągu P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>
- [Współdziałanie z kodem niezarządzanym](/dotnet/framework/interop/index)