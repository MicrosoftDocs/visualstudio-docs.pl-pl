---
title: 'CA1414: Oznacz logiczne argumenty P-Invoke za pomocą atrybutu MarshalAs | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8df0404657b6740c27544292dc101a6030a6563f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65691916"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: Oznacz argumenty typu boolean elementu P/Invoke argumentem MarshalAs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Kategoria|Microsoft.Interoperability|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda wywołania platformy deklaracja zawiera <xref:System.Boolean?displayProperty=fullName> parametrze lub wartości zwracanej, ale <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> atrybut nie jest stosowany do parametrów lub wartości zwracanej.

## <a name="rule-description"></a>Opis reguły
 Platforma wywołania metody uzyskuje dostęp do niezarządzanego kodu i jest definiowana za pomocą `Declare` — słowo kluczowe w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] lub <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Określa zachowanie marshalingu, która jest używana do konwersji typów danych między kodem zarządzanym i niezarządzanym. Wiele proste typy danych, na przykład <xref:System.Byte?displayProperty=fullName> i <xref:System.Int32?displayProperty=fullName>, mieć pojedynczy reprezentacji w niezarządzanym kodzie i nie wymagają specyfikacji ich zachowanie marshalingu; środowisko uruchomieniowe języka wspólnego automatycznie dostarcza poprawnego zachowania.

 <xref:System.Boolean> — Typ danych ma wiele reprezentacji w kodzie niezarządzanym. Gdy <xref:System.Runtime.InteropServices.MarshalAsAttribute> nie zostanie określony, domyślne zachowanie marshalingu <xref:System.Boolean> typ danych jest <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. To jest 32-bitową liczbę całkowitą, która nie jest odpowiednie w każdych okolicznościach. Logiczna reprezentacja, wymaganego przez niezarządzane metody powinny być określane i dopasowywane do odpowiednich <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. UnmanagedType.Bool jest typu Win32 BOOL, który jest zawsze 4 bajty. UnmanagedType.U1 powinna być używana dla języka C++ `bool` lub inne typy 1-bajtowe. Aby uzyskać więcej informacji, zobacz [domyślny Marshaling dla typów logicznych](https://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9).

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zastosować <xref:System.Runtime.InteropServices.MarshalAsAttribute> do <xref:System.Boolean> parametrze lub wartości zwracanej. Ustaw wartość atrybutu do odpowiedniego <xref:System.Runtime.InteropServices.UnmanagedType>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Nawet w przypadku domyślne zachowanie marshalingu jest właściwa, kod łatwiej jest zachowywana, gdy zachowanie jest jawnie określona.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono dwie platformy wywołania metody, które są oznaczone odpowiednią <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutów.

 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cpp/FxCop.Interoperability.BoolMarshalAs.cpp#1)]
 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cs/FxCop.Interoperability.BoolMarshalAs.cs#1)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/vb/FxCop.Interoperability.BoolMarshalAs.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1901: Deklaracje P/Invoke powinny być przenośne](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101: Należy określić marshaling dla argumentów ciągu P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Zobacz też
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> [Organizowanie domyślne dotyczące typów logicznych](https://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9) [współdziałanie z niezarządzanego kodu](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
