---
title: 'CA1415: Zadeklaruj poprawne wywołanie P- Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1415
- DeclarePInvokesCorrectly
helpviewer_keywords:
- CA1415
- DeclarePInvokesCorrectly
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b9931d29c818d95785146558637c32237e2c5276
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547852"
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415: Należy poprawnie zadeklarować P/Invokes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|DeclarePInvokesCorrectly|
|CheckId|CA1415|
|Kategoria|Microsoft. współdziałanie|
|Zmiana kluczowa|Bez przerywania — jeśli P/Invoke, które deklaruje parametr, nie mogą być widoczne poza zestawem. Przerywanie — jeśli P/Invoke, które deklaruje parametr, można zobaczyć poza zestawem.|

## <a name="cause"></a>Przyczyna
 Metoda wywołania platformy jest nieprawidłowo zadeklarowana.

## <a name="rule-description"></a>Opis reguły
 Metoda Invoke platformy uzyskuje dostęp do kodu niezarządzanego i jest definiowana za pomocą `Declare` słowa kluczowego w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] lub <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> . Obecnie ta reguła szuka deklaracji metody wywołania platformy, które są ukierunkowane na funkcje Win32, które mają wskaźnik na NAKŁADAjący się parametr struktury, a odpowiadający mu parametr zarządzany nie jest wskaźnikiem do <xref:System.Threading.NativeOverlapped?displayProperty=fullName> struktury.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy prawidłowo zadeklarować metodę wywołania platformy.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje metody wywołania platformy, które naruszają regułę i spełniają regułę.

 [!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DeclarePInvokes/cs/FxCop.Interoperability.DeclarePInvokes.cs#1)]

## <a name="see-also"></a>Zobacz też
 [Współdziałanie z kodem niezarządzanym](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
