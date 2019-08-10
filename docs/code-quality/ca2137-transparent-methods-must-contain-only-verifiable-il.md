---
title: 'CA2137: Metody przezroczyste muszą zawierać tylko weryfikowalny język pośredni'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2137
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 98b75a9f67a24fd8bea1ecc3a8782b6bd9e6b34b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920610"
---
# <a name="ca2137-transparent-methods-must-contain-only-verifiable-il"></a>CA2137: Metody przezroczyste muszą zawierać tylko weryfikowalny język pośredni

|||
|-|-|
|TypeName|TransparentMethodsMustBeVerifiable|
|CheckId|CA2137|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
Metoda zawiera nieweryfikowalny kod lub zwraca typ przez odwołanie.

## <a name="rule-description"></a>Opis reguły
Ta reguła jest uruchamiana podczas próby wykonywania przez kod przezroczysty pod względem zabezpieczeń nieweryfikowalnego MSIL (Microsoft Intermediate Language). Jednak reguła nie zawiera pełnej weryfikacji IL i używa heurystyki do wykrywania większości naruszeń weryfikacji MSIL.

Aby upewnić się, że kod zawiera tylko zweryfikowane MSIL, uruchom [PEVerify. exe (narzędzie PEVerify)](/dotnet/framework/tools/peverify-exe-peverify-tool) w zestawie. Uruchom PEVerify z opcją **/transparent** , która ogranicza dane wyjściowe wyłącznie do niemożliwych do zweryfikowania metod, które spowodują wystąpienie błędu. Jeśli opcja/transparent nie jest używana, PEVerify sprawdza także metody krytyczne, które mogą zawierać kod niemożliwy do zweryfikowania.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej zasady, należy oznaczyć metodę <xref:System.Security.SecurityCriticalAttribute> atrybutem or <xref:System.Security.SecuritySafeCriticalAttribute> lub usunąć kod niemożliwy do zweryfikowania.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
Metoda w tym przykładzie używa niemożliwego do zweryfikowania kodu i powinna być oznaczona <xref:System.Security.SecurityCriticalAttribute> atrybutem or <xref:System.Security.SecuritySafeCriticalAttribute> .

[!code-csharp[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../code-quality/codesnippet/CSharp/ca2137-transparent-methods-must-contain-only-verifiable-il_1.cs)]