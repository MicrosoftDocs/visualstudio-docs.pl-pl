---
title: 'CA2137: Metody przezroczyste muszą zawierać tylko możliwy do zweryfikowania kod IL | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2137
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6219acde1f62c946e08325f4764dc49dde461d2f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546578"
---
# <a name="ca2137-transparent-methods-must-contain-only-verifiable-il"></a>CA2137: Metody przezroczyste muszą zawierać tylko weryfikowalny język pośredni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|TransparentMethodsMustBeVerifiable|
|CheckId|CA2137|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda zawiera nieweryfikowalny kod lub zwraca typ przez odwołanie.

## <a name="rule-description"></a>Opis reguły
 Ta reguła jest uruchamiana podczas próby wykonywania przez kod przezroczysty pod względem zabezpieczeń nieweryfikowalnego MSIL (Microsoft Intermediate Language). Jednak reguła nie zawiera pełnej weryfikacji IL i używa heurystyki do wykrywania większości naruszeń weryfikacji MSIL.

 Aby upewnić się, że kod zawiera tylko zweryfikowane MSIL, uruchom [Peverify.exe (narzędzie PEVerify)](https://msdn.microsoft.com/library/f4f46f9e-8d08-4e66-a94b-0c69c9b0bbfa) w zestawie. Uruchom PEVerify z opcją **/transparent** , która ogranicza dane wyjściowe wyłącznie do niemożliwych do zweryfikowania metod, które spowodują wystąpienie błędu. Jeśli opcja/transparent nie jest używana, PEVerify sprawdza także metody krytyczne, które mogą zawierać kod niemożliwy do zweryfikowania.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy oznaczyć metodę <xref:System.Security.SecurityCriticalAttribute> <xref:System.Security.SecuritySafeCriticalAttribute> atrybutem or lub usunąć kod niemożliwy do zweryfikowania.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Metoda w tym przykładzie używa niemożliwego do zweryfikowania kodu i powinna być oznaczona <xref:System.Security.SecurityCriticalAttribute> <xref:System.Security.SecuritySafeCriticalAttribute> atrybutem or.

 [!code-csharp[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2137.transparentmethodsmustbeverifiable/cs/ca2137 - transparentmethodsmustbeverifiable.cs#1)]
