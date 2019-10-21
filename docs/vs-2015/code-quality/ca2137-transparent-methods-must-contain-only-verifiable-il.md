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
ms.openlocfilehash: be3732fbf1fc01deb18d2af6a183d47e618db337
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602988"
---
# <a name="ca2137-transparent-methods-must-contain-only-verifiable-il"></a>CA2137: Jawne metody muszą zawierać tylko weryfikowalne IL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

 Aby upewnić się, że kod zawiera tylko zweryfikowane MSIL, uruchom [PEVerify. exe (narzędzie PEVerify)](https://msdn.microsoft.com/library/f4f46f9e-8d08-4e66-a94b-0c69c9b0bbfa) w zestawie. Uruchom PEVerify z opcją **/transparent** , która ogranicza dane wyjściowe wyłącznie do niemożliwych do zweryfikowania metod, które spowodują wystąpienie błędu. Jeśli opcja/transparent nie jest używana, PEVerify sprawdza także metody krytyczne, które mogą zawierać kod niemożliwy do zweryfikowania.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy oznaczyć metodę atrybutem <xref:System.Security.SecurityCriticalAttribute> lub <xref:System.Security.SecuritySafeCriticalAttribute> lub usunąć kod niemożliwy do zweryfikowania.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Metoda w tym przykładzie używa niemożliwego do zweryfikowania kodu i powinna być oznaczona przy użyciu atrybutu <xref:System.Security.SecurityCriticalAttribute> lub <xref:System.Security.SecuritySafeCriticalAttribute>.

 [!code-csharp[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2137.transparentmethodsmustbeverifiable/cs/ca2137 - transparentmethodsmustbeverifiable.cs#1)]
