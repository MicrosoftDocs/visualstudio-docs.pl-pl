---
title: 'CA1064: Wyjątki powinny być publiczne'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1064
- ExceptionsShouldBePublic
helpviewer_keywords:
- ExceptionsShouldBePublic
- CA1064
ms.assetid: 83eb224c-2456-4368-acf4-3b3378e67759
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d858b5b266b80d84bcbd6eb409a4183105960ee1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018686"
---
# <a name="ca1064-exceptions-should-be-public"></a>CA1064: Wyjątki powinny być publiczne

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

 Ale, jeśli kod ma publiczny wyjątek, który później jest używany jako podstawa dla wewnętrznego wyjątku, można zasadnie przyjęto założenie, że kod dalsze się będzie mógł czymś inteligentne z wyjątkiem podstawowej. Wyjątek publicznego mają więcej informacji, niż dostarczanych przez <xref:System.Exception>, <xref:System.SystemException>, lub <xref:System.ApplicationException>.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Upublicznić wyjątku lub pochodzi z wewnętrznego wyjątku z publicznych wyjątek, który nie jest <xref:System.Exception>, <xref:System.SystemException>, lub <xref:System.ApplicationException>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Wiadomości od tej reguły należy pominąć, jeśli masz pewność, we wszystkich przypadkach, w ramach własnego zakresu wewnętrznego zostanie przechwycony wyjątek prywatnych.

## <a name="example"></a>Przykład
 Ta reguła jest uruchamiana na pierwszej metody przykład FirstCustomException, ponieważ pochodzi bezpośrednio z wyjątkiem klasy wyjątku, a wewnętrznej. Reguła nie zostanie wywołane w klasie SecondCustomException, ponieważ mimo, że klasa również pochodzi bezpośrednio z wyjątków, klasa jest zadeklarowany jako publiczny. Klasa innych również nie jest wyzwalana, reguły, ponieważ nie pochodzi bezpośrednio z <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName>, lub <xref:System.ApplicationException?displayProperty=fullName>.

 [!code-csharp[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../code-quality/codesnippet/CSharp/ca1064-exceptions-should-be-public_1.cs)]
