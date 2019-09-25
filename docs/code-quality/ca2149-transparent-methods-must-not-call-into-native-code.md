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
ms.openlocfilehash: 8e75b12b820b3ff3ac5a26f83148a49ca87c12ad
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231954"
---
# <a name="ca2149-transparent-methods-must-not-call-into-native-code"></a>CA2149: Metody przezroczyste nie mogą wywoływać kodu natywnego

|||
|-|-|
|TypeName|TransparentMethodsMustNotCallNativeCode|
|CheckId|CA2149|
|Kategoria|Microsoft.Security|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna
Metoda wywołuje funkcję natywną za pomocą klasy zastępczej metody, takiej jak P/Invoke.

## <a name="rule-description"></a>Opis reguły
Ta zasada jest uruchamiana dla dowolnej przezroczystej metody, która wywołuje bezpośrednio do kodu natywnego, na przykład za pomocą P/Invoke. Naruszenia tej reguły prowadzą do <xref:System.MethodAccessException> modelu przezroczystości poziomu 2 oraz pełnych wymagań dotyczących <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> modelu przezroczystości poziomu 1.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, oznacz metodę, która wywołuje kod natywny z <xref:System.Security.SecurityCriticalAttribute> atrybutem or. <xref:System.Security.SecuritySafeCriticalAttribute>

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
[!code-csharp[FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../code-quality/codesnippet/CSharp/ca2149-transparent-methods-must-not-call-into-native-code_1.cs)]