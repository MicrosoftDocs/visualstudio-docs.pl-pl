---
title: Analiza kodu dla zarządzanego kodu — Ostrzeżenia
ms.date: 08/31/2020
ms.topic: reference
f1_keywords:
- vc.project.vcfxcoptool.enablefxcop
helpviewer_keywords:
- managed code analyis, warnings
- warnings, managed code analysis
- managed code analysis warnings
- code analysis,managed code
ms.assetid: 3c2741ff-0d3a-42e6-acd5-d42310bd03c4
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 566b9827f42f646cd9350cfc015a460485212a09
ms.sourcegitcommit: a18c7e9b367c2f92f6e54c3eaef442775d457667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2020
ms.locfileid: "90094333"
---
# <a name="net-code-analysis-rules"></a>Reguły analizy kodu platformy .NET
Analiza kodu platformy .NET zawiera reguły wskazujące naruszenia jakości kodu lub sugestie dotyczące poprawy jakości kodu. Reguły są zorganizowane w obszary reguły, takie jak projektowanie, lokalizacja, wydajność i zabezpieczenia. Niektóre reguły są specyficzne dla użycia interfejsu API platformy .NET, a pozostałe reguły dotyczą jakości kodu ogólnego. Ta sekcja zawiera szczegółowe omówienie i przykłady dla każdej reguły.

 W poniższej tabeli przedstawiono typ informacji, które są dostępne dla każdej diagnostyki.

|Element|Opis|
|----------|-----------------|
|Typ|Nazwa typu dla reguły.|
|RuleId|Unikatowy identyfikator reguły. RuleId i Category są używane do pomijania w źródle ostrzeżenia.|
|Kategoria|Kategoria ostrzeżenia.|
|Zmiana podziału|Czy poprawka dla naruszenia reguły jest istotną zmianą. Istotna zmiana oznacza, że zestaw, który ma zależność od obiektu docelowego, który spowodował naruszenie, nie zostanie ponownie skompilowany przy użyciu nowej stałej wersji lub może zakończyć się niepowodzeniem w czasie wykonywania ze względu na zmianę. Jeśli jest dostępnych wiele poprawek, a co najmniej jedna poprawka jest istotną zmianą, a jedna poprawka nie jest, określono zarówno element "", jak i "bez przerywania".|
|Przyczyna|Określony kod zarządzany, który powoduje wygenerowanie ostrzeżenia przez regułę.|
|Opis|W tym artykule omówiono problemy, które znajdują się za ostrzeżeniem.|
|Jak naprawić naruszenia|Wyjaśnia, jak zmienić kod źródłowy w celu spełnienia reguły i uniemożliwić wygenerowanie ostrzeżenia.|
|Kiedy pominąć ostrzeżenia|Opisuje, kiedy można bezpiecznie pominąć ostrzeżenie z reguły.|
|Przykładowy kod|Przykłady naruszające regułę i poprawione przykłady, które spełniają regułę.|
|Powiązane ostrzeżenia|Powiązane ostrzeżenia.|

## <a name="in-this-section"></a>W tej sekcji

|Kategoria|Opis|
|-|-|
|[Reguły według identyfikatora](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)|Wyświetla wszystkie reguły według RuleID|
|[Reguły projektowania](../code-quality/design-warnings.md)|Reguły, które obsługują prawidłowy projekt biblioteki, zgodnie z zaleceniami dotyczącymi projektowania platformy .NET.|
|[Reguły dokumentacji](../code-quality/documentation-warnings.md)|Reguły, które obsługują dobrze udokumentowane Projektowanie biblioteki przez poprawne użycie komentarzy dokumentacji XML.|
|[Reguły globalizacji](../code-quality/globalization-warnings.md)|Reguły obsługujące gotowe do używania biblioteki i aplikacje.|
|[Reguły utrzymania](../code-quality/maintainability-warnings.md)|Reguły obsługujące konserwację biblioteki i aplikacji.|
|[Reguły nazewnictwa](../code-quality/naming-warnings.md)|Reguły, które obsługują przestrzeganie konwencji nazewnictwa w wytycznych dotyczących projektowania platformy .NET.|
|[Reguły wydajności](../code-quality/performance-warnings.md)|Reguły obsługujące biblioteki i aplikacje o wysokiej wydajności.|
|[Przenośność i reguły współdziałania](../code-quality/interoperability-warnings.md)|Reguły obsługujące przenośność na różnych platformach i interakcje z klientami COM.|
|[Publikowanie reguł](../code-quality/publish-warnings.md)|Reguły obsługujące odpowiednie publikowanie aplikacji platformy .NET.|
|[Reguły niezawodności](../code-quality/reliability-warnings.md)|Reguły, które obsługują niezawodność biblioteki i aplikacji, takie jak poprawne użycie pamięci i wątku.|
|[Reguły zabezpieczeń](../code-quality/security-warnings.md)|Reguły obsługujące bezpieczniejsze biblioteki i aplikacje.|
|[Reguły użycia](../code-quality/usage-warnings.md)|Reguły obsługujące odpowiednie użycie platformy .NET.|
