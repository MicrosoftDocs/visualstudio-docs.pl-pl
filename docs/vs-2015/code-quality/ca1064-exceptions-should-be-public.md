---
title: 'CA1064: wyjątki powinny być publiczne | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fc78c4eaacc3ef0a480b913d20537aeebe5bfc01
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539272"
---
# <a name="ca1064-exceptions-should-be-public"></a>CA1064: Wyjątki powinny być publiczne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|ExceptionsShouldBePublic|
|CheckId|CA1064|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Wyjątek niepubliczny pochodzi bezpośrednio z <xref:System.Exception> , <xref:System.SystemException> lub <xref:System.ApplicationException> .

## <a name="rule-description"></a>Opis reguły
 Wyjątek wewnętrzny jest widoczny tylko w jego własnym zakresie wewnętrznym. W przypadku wystąpienia wyjątku poza zakresem wewnętrznym tylko wyjątek podstawowy może zostać użyty do jego przechwycenia. Jeśli wewnętrzny wyjątek jest Dziedziczony z <xref:System.Exception> , <xref:System.SystemException> , lub <xref:System.ApplicationException> , kod zewnętrzny nie będzie zawierał wystarczających informacji, aby dowiedzieć się, co należy zrobić z wyjątkiem.

 Ale jeśli kod ma wyjątek publiczny, który jest później używany jako podstawa wewnętrznego wyjątku, rozsądne jest założenie, że kod jest bardziej inteligentny, z wyjątkiem podstawowym. Wyjątek publiczny będzie zawierać więcej informacji niż to, co jest zapewniane przez T:System.Exception, T:System.SystemException lub T:System.ApplicationException.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Wykonaj wyjątek publiczny lub wykorzystaj wyjątek wewnętrzny z niepublicznego wyjątku, który nie jest <xref:System.Exception> , <xref:System.SystemException> lub <xref:System.ApplicationException> .

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomiń komunikat z tej reguły, jeśli masz pewność, że wszystkie przypadki, w których wystąpił wyjątek prywatny, zostaną przechwycone w ramach własnego zakresu wewnętrznego.

## <a name="example"></a>Przykład
 Ta zasada jest uruchamiana na pierwszej przykładowej metodzie, FirstCustomException, ponieważ Klasa wyjątku dziedziczy bezpośrednio z wyjątku i jest wewnętrzna. Reguła nie jest uruchamiana na klasie SecondCustomException, ponieważ chociaż Klasa dziedziczy również bezpośrednio z wyjątku, Klasa jest zadeklarowana jako publiczna. Trzecia Klasa również nie wyzwala reguły, ponieważ nie pochodzi bezpośrednio z <xref:System.Exception?displayProperty=fullName> , <xref:System.SystemException?displayProperty=fullName> lub <xref:System.ApplicationException?displayProperty=fullName> .

 [!code-csharp[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.design.exceptionsshouldbepublic.ca1064/cs/ca1064 - exceptionsshouldbepublic.cs#1)]
