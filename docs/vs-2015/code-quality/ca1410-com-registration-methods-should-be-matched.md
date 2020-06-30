---
title: 'CA1410: metody rejestracji modelu COM powinny być dopasowane | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
helpviewer_keywords:
- CA1410
- ComRegistrationMethodsShouldBeMatched
ms.assetid: f3b2e62d-fd66-4093-9f0c-dba01ad995fd
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 43767ce04b32440a5c6753f5bfcabb91487c1232
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546708"
---
# <a name="ca1410-com-registration-methods-should-be-matched"></a>CA1410: Metody rejestracji modelu COM powinny mieć swoje odpowiedniki
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|ComRegistrationMethodsShouldBeMatched|
|CheckId|CA1410|
|Kategoria|Microsoft. współdziałanie|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Typ deklaruje metodę, która jest oznaczona <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> atrybutem, ale nie deklaruje metody, która jest oznaczona <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> atrybutem lub na odwrót.

## <a name="rule-description"></a>Opis reguły
 W przypadku klientów z Component Object Model (COM) do tworzenia [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] typu należy najpierw zarejestrować typ. Jeśli jest dostępna, metoda oznaczona <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> atrybutem jest wywoływana podczas procesu rejestracji w celu uruchomienia kodu określonego przez użytkownika. Odpowiadająca metoda oznaczona <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> atrybutem jest wywoływana podczas procesu wyrejestrowywania, aby wycofać operacje metody rejestracji.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Dodaj odpowiednią metodę rejestracji lub wyrejestrowywania.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza regułę. Kod z komentarzem pokazuje poprawkę dla naruszenia.

 [!code-csharp[FxCop.Interoperability.ComRegistration#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration/cs/FxCop.Interoperability.ComRegistration.cs#1)]
 [!code-vb[FxCop.Interoperability.ComRegistration#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComRegistration/vb/FxCop.Interoperability.ComRegistration.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1411: Metody rejestracji modelu COM nie powinny być widoczne](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)

## <a name="see-also"></a>Zobacz też
 <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>[Rejestrowanie zestawów przy użyciuRegasm.exe com](https://msdn.microsoft.com/library/87925795-a3ae-4833-b138-125413478551) [(Narzędzie rejestracji zestawów)](https://msdn.microsoft.com/library/e190e342-36ef-4651-a0b4-0e8c2c0281cb)
