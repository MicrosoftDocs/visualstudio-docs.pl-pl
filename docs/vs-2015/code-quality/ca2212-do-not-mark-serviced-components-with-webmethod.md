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
ms.openlocfilehash: a3c707fef5562b932b6232300131f6e6e6efef6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534566"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: Nie oznaczaj składników usługi atrybutem WebMethod
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda w typie, który dziedziczy z, <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> jest oznaczona za pomocą <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName> .

## <a name="rule-description"></a>Opis reguły
 <xref:System.Web.Services.WebMethodAttribute> dotyczy metod w usłudze sieci Web XML, które zostały utworzone przy użyciu ASP.NET; sprawia, że metoda jest wywoływana z zdalnych klientów sieci Web. Metoda i Klasa muszą być publiczne i wykonywane w aplikacji sieci Web ASP.NET. <xref:System.EnterpriseServices.ServicedComponent> typy są obsługiwane przez aplikacje COM+ i mogą korzystać z usług COM+. <xref:System.Web.Services.WebMethodAttribute> nie ma zastosowania do <xref:System.EnterpriseServices.ServicedComponent> typów, ponieważ nie są one przeznaczone do tych samych scenariuszy. W celu dodania atrybutu do metody nie można <xref:System.EnterpriseServices.ServicedComponent> wywołać metody z zdalnych klientów sieci Web. Ponieważ <xref:System.Web.Services.WebMethodAttribute> <xref:System.EnterpriseServices.ServicedComponent> Metoda ma sprzeczne zachowania i wymagania dotyczące przepływu kontekstu i transakcji, zachowanie metody będzie nieprawidłowe w niektórych scenariuszach.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Usuń atrybut z <xref:System.EnterpriseServices.ServicedComponent> metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Nie ma żadnych scenariuszy, w których łączenie tych elementów jest poprawne.

## <a name="see-also"></a>Zobacz też
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>
