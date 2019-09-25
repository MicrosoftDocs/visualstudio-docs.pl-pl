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
ms.openlocfilehash: 8ae8f507f17a1c64cb9fdfc5872ffa22e3c0f170
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232233"
---
# <a name="ca2137-transparent-methods-must-contain-only-verifiable-il"></a>CA2137: Metody przezroczyste muszą zawierać tylko weryfikowalny język pośredni

|||
|-|-|
|TypeName|TransparentMethodsMustBeVerifiable|
|CheckId|CA2137|
|Kategoria|Microsoft.Security|
|Zmiana podziału|Kluczowa|

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