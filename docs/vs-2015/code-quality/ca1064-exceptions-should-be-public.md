---
title: 'CA1064: Wyjątki powinny być publiczne | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1064
- ExceptionsShouldBePublic
helpviewer_keywords:
- ExceptionsShouldBePublic
- CA1064
ms.assetid: 83eb224c-2456-4368-acf4-3b3378e67759
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 00d188188f722907c2bac20e84cb9291ef8bc0fe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200428"
---
# <a name="ca1064-exceptions-should-be-public"></a>CA1064: Wyjątki powinny być publiczne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ExceptionsShouldBePublic|
|CheckId|CA1064|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Wyjątek niepublicznych pochodzi bezpośrednio z <xref:System.Exception>, <xref:System.SystemException>, lub <xref:System.ApplicationException>.

## <a name="rule-description"></a>Opis reguły
 Wyjątek wewnętrzny jest widoczna tylko wewnątrz własnego zakresu wewnętrznego. W przypadku wystąpienia wyjątku poza zakresem wewnętrznym tylko wyjątek podstawowy może zostać użyty do jego przechwycenia. Jeśli wyjątek wewnętrzny jest dziedziczony z <xref:System.Exception>, <xref:System.SystemException>, lub <xref:System.ApplicationException>, kod zewnętrzny nie ma wystarczające informacje, aby wiedzieli, co należy zrobić z wyjątkiem.

 Ale, jeśli kod ma publiczny wyjątek, który później jest używany jako podstawa dla wewnętrznego wyjątku, można zasadnie przyjęto założenie, że kod dalsze się będzie mógł czymś inteligentne z wyjątkiem podstawowej. Wyjątek publicznego mają więcej informacji, niż dostarczanych przez T:System.Exception, T:System.SystemException lub T:System.ApplicationException.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Upublicznić wyjątku lub pochodzi z wewnętrznego wyjątku z publicznych wyjątek, który nie jest <xref:System.Exception>, <xref:System.SystemException>, lub <xref:System.ApplicationException>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Wiadomości od tej reguły należy pominąć, jeśli masz pewność, we wszystkich przypadkach, w ramach własnego zakresu wewnętrznego zostanie przechwycony wyjątek prywatnych.

## <a name="example"></a>Przykład
 Ta reguła jest uruchamiana na pierwszej metody przykład FirstCustomException, ponieważ pochodzi bezpośrednio z wyjątkiem klasy wyjątku, a wewnętrznej. Reguła nie zostanie wywołane w klasie SecondCustomException, ponieważ mimo, że klasa również pochodzi bezpośrednio z wyjątków, klasa jest zadeklarowany jako publiczny. Klasa innych również nie jest wyzwalana, reguły, ponieważ nie pochodzi bezpośrednio z <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName>, lub <xref:System.ApplicationException?displayProperty=fullName>.

 [!code-csharp[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.design.exceptionsshouldbepublic.ca1064/cs/ca1064 - exceptionsshouldbepublic.cs#1)]
