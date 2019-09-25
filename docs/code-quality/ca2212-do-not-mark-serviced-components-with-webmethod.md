---
title: 'CA2212: Nie oznaczaj składników usługi atrybutem WebMethod'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7b2ace5f6e51fc7a8d29faab14cc2332fd808f93
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231656"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: Nie oznaczaj składników usługi atrybutem WebMethod

|||
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Kategoria|Microsoft.Usage|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna

Metoda w typie, który dziedziczy z <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> , jest oznaczona za pomocą. <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>

## <a name="rule-description"></a>Opis reguły

<xref:System.Web.Services.WebMethodAttribute>dotyczy metod w usłudze sieci Web XML, które zostały utworzone przy użyciu ASP.NET; sprawia, że metoda jest wywoływana z zdalnych klientów sieci Web. Metoda i Klasa muszą być publiczne i wykonywane w aplikacji sieci Web ASP.NET. <xref:System.EnterpriseServices.ServicedComponent>typy są obsługiwane przez aplikacje COM+ i mogą korzystać z usług COM+. <xref:System.Web.Services.WebMethodAttribute>nie ma zastosowania do <xref:System.EnterpriseServices.ServicedComponent> typów, ponieważ nie są one przeznaczone do tych samych scenariuszy. W celu dodania atrybutu do <xref:System.EnterpriseServices.ServicedComponent> metody nie można wywołać metody z zdalnych klientów sieci Web. Ponieważ <xref:System.Web.Services.WebMethodAttribute> Metoda ma sprzeczne zachowania i wymagania dotyczące przepływu kontekstu i transakcji, zachowanie metody będzie nieprawidłowe w niektórych scenariuszach. <xref:System.EnterpriseServices.ServicedComponent>

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, Usuń atrybut z <xref:System.EnterpriseServices.ServicedComponent> metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły. Nie ma żadnych scenariuszy, w których łączenie tych elementów jest poprawne.

## <a name="see-also"></a>Zobacz także

- <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName>
- <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>