---
title: 'CA1414: Oznacz argumenty logiczne P-Invoke za pomocą elementu MarshalAs | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 588e16a6b21b320ad7012bd20d79a62d027679e3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652690"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: Oznacz logiczne argumenty P/Invoke za pomocą MarshalAs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Kategoria|Microsoft. współdziałanie|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Deklaracja metody wywołania platformy zawiera parametr <xref:System.Boolean?displayProperty=fullName> lub wartość zwracaną, ale atrybut <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> nie jest stosowany do parametru lub wartości zwracanej.

## <a name="rule-description"></a>Opis reguły
 Metoda Invoke platformy uzyskuje dostęp do kodu niezarządzanego i jest definiowana za pomocą słowa kluczowego `Declare` w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] lub <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. <xref:System.Runtime.InteropServices.MarshalAsAttribute> określa zachowanie organizowania, które służy do konwertowania typów danych między zarządzanym i niezarządzanym kodem. Wiele prostych typów danych, takich jak <xref:System.Byte?displayProperty=fullName> i <xref:System.Int32?displayProperty=fullName>, mają jedną reprezentację w kodzie niezarządzanym i nie wymaga specyfikacji ich zachowania Marshaling; środowisko uruchomieniowe języka wspólnego automatycznie dostarcza poprawne zachowanie.

 Typ danych <xref:System.Boolean> ma wiele reprezentacji w kodzie niezarządzanym. Gdy nie określono <xref:System.Runtime.InteropServices.MarshalAsAttribute>, domyślne zachowanie kierowania dla typu danych <xref:System.Boolean> jest <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. Jest to 32-bitowa liczba całkowita, która nie jest odpowiednia w żadnym przypadku. Reprezentacja logiczna wymagana przez metodę niezarządzaną powinna zostać określona i dopasowana do odpowiedniej <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. UnmanagedType. bool jest typem BOOL Win32, który ma zawsze 4 bajty. Nie można używać elementu UnmanagedType. U1 C++ dla `bool` lub innych typów 1-bajtowych. Aby uzyskać więcej informacji, zobacz [domyślne kierowanie dla typów logicznych](https://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9).

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zastosować <xref:System.Runtime.InteropServices.MarshalAsAttribute> do parametru <xref:System.Boolean> lub wartości zwracanej. Ustaw wartość atrybutu na odpowiednią <xref:System.Runtime.InteropServices.UnmanagedType>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Nawet jeśli domyślne zachowanie kierowania jest odpowiednie, kod jest łatwiejszy do utrzymania, gdy zachowanie jest jawnie określone.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje dwie metody wywołania platformy, które są oznaczone odpowiednimi atrybutami <xref:System.Runtime.InteropServices.MarshalAsAttribute>.

 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cpp/FxCop.Interoperability.BoolMarshalAs.cpp#1)]
 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cs/FxCop.Interoperability.BoolMarshalAs.cs#1)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/vb/FxCop.Interoperability.BoolMarshalAs.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1901: Deklaracje P/Invoke powinny być przenośne](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101: Określ marshaling dla argumentów ciągu wywołania P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Zobacz też
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> [kierowanie domyślne dla typów logicznych](https://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9) [współpracujących z niezarządzanym kodem](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
