---
title: Analiza kodu dla zarządzanego kodu — Ostrzeżenia
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- vc.project.vcfxcoptool.enablefxcop
helpviewer_keywords:
- managed code analyis, warnings
- warnings, managed code analysis
- managed code analysis warnings
- code analysis,managed code
ms.assetid: 3c2741ff-0d3a-42e6-acd5-d42310bd03c4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 3840fc6ee7a5ef0075463462062f78c1a3d2a0c4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53876143"
---
# <a name="code-analysis-for-managed-code-warnings"></a>Analiza kodu dla zarządzanego kodu — Ostrzeżenia
Narzędzie do analizy kodu zarządzanego zawiera ostrzeżenia, które wskazują naruszeń reguł w bibliotekach kodu zarządzanego. Ostrzeżenia są zorganizowane w obszarach reguł, takich jak projektu, lokalizacji, wydajność i bezpieczeństwo. Każde ostrzeżenie oznacza naruszenie reguły analizy kodu zarządzanego. Ta sekcja zawiera szczegółowe omówienie i przykłady dla każdego ostrzeżenia analizy kodu zarządzanego.

 W poniższej tabeli przedstawiono typ danych, który jest udostępniany dla każde ostrzeżenie.

|Element|Opis|
|----------|-----------------|
|Typ|Element TypeName dla tej reguły.|
|CheckId|Unikatowy identyfikator dla tej reguły. CheckId i kategoria są używane do pomijania-source ostrzeżenia.|
|Kategoria|Kategoria ostrzeżenia.|
|Zmiana kluczowa|Czy poprawkę dotyczącą naruszenie reguły jest zmianą przerywającą. Istotne zmiany oznacza, że zestaw, który ma zależność w miejscu docelowym, który spowodował naruszenia nie zostanie ponownie skompilowana przy użyciu nowego stałej wersji i może się nie powieść w czasie wykonywania ze względu na zmianę. Jeśli dostępnych jest wiele poprawek i co najmniej jedną poprawkę jest zmianą przerywającą, co poprawki nie jest określony "Złamanie" i "Istotne niż".|
|Przyczyna|Określonego kodu zarządzanego, który powoduje, że reguła ostrzeżenie będzie generowane.|
|Opis|W tym artykule omówiono problemy, które znajdują się za ostrzeżenia.|
|Jak naprawić naruszenia|Wyjaśnia, jak zmiany kodu źródłowego, które spełniają reguły i uniemożliwić zostanie wygenerowane ostrzeżenie.|
|Kiedy pominąć ostrzeżenia|Opisuje, kiedy jest bezpieczne ostrzeżenia z reguły.|
|Przykładowy kod|Przykłady, które naruszają reguły i poprawić przykładów, które spełniają reguły.|
|Powiązane ostrzeżenia|Powiązane ostrzeżenia.|

## <a name="in-this-section"></a>W tej sekcji

|||
|-|-|
|[Ostrzeżenia według identyfikatora CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)|Wyświetla wszystkie ostrzeżenia dzięki CheckId|
|[Ostrzeżenia dotyczące kryptografii](../code-quality/cryptography-warnings.md)|Ostrzeżenia, które obsługują bezpieczniejsze biblioteki i aplikacje przy użyciu poprawnego użycia kryptografii.|
|[Ostrzeżenia dotyczące projektu](../code-quality/design-warnings.md)|Ostrzeżenia, które obsługują odpowiedniej biblioteki projekt zgodnie z wytycznymi projektowania programu .NET Framework.|
|[Ostrzeżenia dotyczące globalizacji](../code-quality/globalization-warnings.md)|Ostrzeżenia, które obsługują gotowych do biblioteki i aplikacje.|
|[Ostrzeżenia dotyczące współdziałania](../code-quality/interoperability-warnings.md)|Ostrzeżenia, które obsługują interakcji z klientami COM.|
|[Ostrzeżenia dotyczące konserwacji](../code-quality/maintainability-warnings.md)|Ostrzeżenia, które obsługują konserwacji biblioteki i aplikacji.|
|[Ostrzeżenia dotyczące mobilności](../code-quality/mobility-warnings.md)|Ostrzeżenia, które obsługują efektywne zużycie energii.|
|[Ostrzeżenia dotyczące nazewnictwa](../code-quality/naming-warnings.md)|Ostrzeżenia, które obsługują gotowość do konwencji nazewnictwa wytycznych projektowych programu .NET Framework.|
|[Ostrzeżenia dotyczące wydajności](../code-quality/performance-warnings.md)|Ostrzeżenia, które obsługują bibliotek o wysokiej wydajności i aplikacji.|
|[Ostrzeżenia dotyczące przenośności](../code-quality/portability-warnings.md)|Ostrzeżenia, które obsługują przenoszenia na różnych platformach.|
|[Ostrzeżenia dotyczące niezawodności](../code-quality/reliability-warnings.md)|Ostrzeżenia, które obsługują niezawodność biblioteki i aplikacji, takich jak poprawne użycie pamięci i wątku.|
|[Ostrzeżenia dotyczące zabezpieczeń](../code-quality/security-warnings.md)|Ostrzeżenia, które obsługują bezpieczniejsze biblioteki i aplikacje.|
|[Ostrzeżenia dotyczące użycia](../code-quality/usage-warnings.md)|Ostrzeżenia, które obsługują odpowiedniego użycia programu .NET Framework.|
|[Błędy zasad analizy kodu](../code-quality/code-analysis-policy-errors.md)|Błędy, które występują, jeśli zasady analizy kodu nie zostanie spełnione, podczas ewidencjonowania.|