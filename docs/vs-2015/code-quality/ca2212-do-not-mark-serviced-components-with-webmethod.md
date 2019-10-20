---
title: 'CA2212: nie oznaczaj serwisowanych składników za pomocą metody WEBMETHOD | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2ee166f8bbc14e66968cd4f7c265331854905ac9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662951"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: Nie należy oznaczać obsługiwanych składników znacznikiem WebMethod
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda w typie, która dziedziczy po <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> jest oznaczona za pomocą <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły
 <xref:System.Web.Services.WebMethodAttribute> ma zastosowanie do metod w ramach usługi sieci Web XML, które zostały utworzone przy użyciu ASP.NET; sprawia, że metoda jest wywoływana z zdalnych klientów sieci Web. Metoda i Klasa muszą być publiczne i wykonywane w aplikacji sieci Web ASP.NET. typy <xref:System.EnterpriseServices.ServicedComponent> są obsługiwane przez aplikacje COM+ i mogą korzystać z usług COM+. <xref:System.Web.Services.WebMethodAttribute> nie jest stosowany do typów <xref:System.EnterpriseServices.ServicedComponent>, ponieważ nie są one przeznaczone do tych samych scenariuszy. W celu dodania atrybutu do metody <xref:System.EnterpriseServices.ServicedComponent> nie można wywołać metody z zdalnych klientów sieci Web. Ponieważ <xref:System.Web.Services.WebMethodAttribute> i <xref:System.EnterpriseServices.ServicedComponent> Metoda ma sprzeczne zachowania i wymagania dotyczące przepływu kontekstu i transakcji, zachowanie metody będzie nieprawidłowe w niektórych scenariuszach.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Usuń atrybut z metody <xref:System.EnterpriseServices.ServicedComponent>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Nie ma żadnych scenariuszy, w których łączenie tych elementów jest poprawne.

## <a name="see-also"></a>Zobacz też
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName><xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>
