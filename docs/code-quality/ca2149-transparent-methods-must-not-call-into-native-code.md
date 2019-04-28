---
title: 'CA2149: Metody przezroczyste nie mogą wywoływać kodu natywnego'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2149
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 462ddeebba217e3a129736d1532aeec6b106d0cb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62542147"
---
# <a name="ca2149-transparent-methods-must-not-call-into-native-code"></a>CA2149: Metody przezroczyste nie mogą wywoływać kodu natywnego

|||
|-|-|
|TypeName|TransparentMethodsMustNotCallNativeCode|
|CheckId|CA2149|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda wywołania funkcji macierzystej za pośrednictwem szkieletu metody, takie jak metody P/Invoke.

## <a name="rule-description"></a>Opis reguły
 Ta reguła jest uruchamiana na każdej przezroczystej metody metodę, która wywołuje bezpośrednio kod natywny, na przykład za pośrednictwem metody P/Invoke. Naruszenie tej zasady prowadzi do <xref:System.MethodAccessException> w poziomie 2 modelu przezroczystości i pełnego żądania dla <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> w modelu przezroczystości poziomu 1.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy oznaczyć metody, która wywołuje kodu natywnego za pomocą <xref:System.Security.SecurityCriticalAttribute> lub <xref:System.Security.SecuritySafeCriticalAttribute> atrybutu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 [!code-csharp[FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../code-quality/codesnippet/CSharp/ca2149-transparent-methods-must-not-call-into-native-code_1.cs)]