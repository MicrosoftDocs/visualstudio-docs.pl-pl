---
title: 'CA2212: Nie oznaczaj usługowych składników atrybutem WebMethod | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 46adf703c679ae6133cff428e573f93eb3aacd4c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53893012"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: Nie oznaczaj usługowych składników atrybutem WebMethod
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda w typie, który dziedziczy z <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> jest oznaczona za pomocą <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły
 <xref:System.Web.Services.WebMethodAttribute> ma zastosowanie do metody w ramach usługi XML sieci Web, które zostały utworzone za pomocą programu ASP.NET; zapewnia metody wywoływane z klientów zdalnych w sieci Web. Metody i klasy musi być publiczny i wykonywanie w aplikacji sieci Web platformy ASP.NET. <xref:System.EnterpriseServices.ServicedComponent> typy są hostowane przez aplikacji modelu COM + i mogą używać usług COM +. <xref:System.Web.Services.WebMethodAttribute> nie ma zastosowania do <xref:System.EnterpriseServices.ServicedComponent> typów, ponieważ nie są przeznaczone dla tych samych scenariuszy. W szczególności Dodawanie atrybutu do <xref:System.EnterpriseServices.ServicedComponent> metody nie oznacza, że metody wywoływane z klientów zdalnych w sieci Web. Ponieważ <xref:System.Web.Services.WebMethodAttribute> i <xref:System.EnterpriseServices.ServicedComponent> metody mają konflikt zachowania i wymagania dotyczące kontekstu i przepływu transakcji, zachowanie metod będzie niepoprawne w niektórych scenariuszach.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, usuń atrybut z <xref:System.EnterpriseServices.ServicedComponent> metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Istnieje nie scenariuszy, w którym połączenie tych elementów jest poprawna.

## <a name="see-also"></a>Zobacz też
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName><xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>
