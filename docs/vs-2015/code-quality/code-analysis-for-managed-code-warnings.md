---
title: Analiza kodu dla ostrzeżeń związanych z kodem zarządzanym | Microsoft Docs
ms.date: 08/31/2020
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vc.project.vcfxcoptool.enablefxcop
helpviewer_keywords:
- managed code analyis, warnings
- warnings, managed code analysis
- managed code analysis warnings
- code analysis,managed code
ms.assetid: 3c2741ff-0d3a-42e6-acd5-d42310bd03c4
caps.latest.revision: 22
author: mikadumont
ms.author: midumont
manager: wpickett
ms.openlocfilehash: e689d137e071096d096e117ef3b79df405a060ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2020
ms.locfileid: "89285752"
---
# <a name="net-code-analysis-rules"></a>Reguły analizy kodu platformy .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Narzędzie do analizy kodu zarządzanego zawiera ostrzeżenia wskazujące naruszenia reguł w zarządzanych bibliotekach kodu. Ostrzeżenia są zorganizowane w obszary reguły, takie jak projektowanie, lokalizacja, wydajność i zabezpieczenia. Każde ostrzeżenie oznacza naruszenie reguły analizy kodu zarządzanego. Ta sekcja zawiera szczegółowe omówienie i przykłady dla każdego ostrzeżenia analizy kodu zarządzanego.

 W poniższej tabeli przedstawiono typ informacji, które są dostępne dla każdego ostrzeżenia.

|Element|Opis|
|----------|-----------------|
|Typ|Nazwa typu dla reguły.|
|CheckId|Unikatowy identyfikator reguły. CheckId i Category są używane do pomijania w źródle ostrzeżenia.|
|Kategoria|Kategoria ostrzeżenia.|
|Zmiana kluczowa|Czy poprawka dla naruszenia reguły jest istotną zmianą. Istotna zmiana oznacza, że zestaw, który ma zależność od obiektu docelowego, który spowodował naruszenie, nie zostanie ponownie skompilowany przy użyciu nowej stałej wersji lub może zakończyć się niepowodzeniem w czasie wykonywania ze względu na zmianę. Jeśli jest dostępnych wiele poprawek, a co najmniej jedna poprawka jest istotną zmianą, a jedna poprawka nie jest, określono zarówno "", jak i "bez przerywania".|
|Przyczyna|Określony kod zarządzany, który powoduje wygenerowanie ostrzeżenia przez regułę.|
|Opis|W tym artykule omówiono problemy, które znajdują się za ostrzeżeniem.|
|Jak naprawić naruszenia|Wyjaśnia, jak zmienić kod źródłowy w celu spełnienia reguły i uniemożliwić wygenerowanie ostrzeżenia.|
|Kiedy pominąć ostrzeżenia|Opisuje, kiedy można bezpiecznie pominąć ostrzeżenie z reguły.|
|Przykładowy kod|Przykłady naruszające regułę i poprawione przykłady, które spełniają regułę.|
|Powiązane ostrzeżenia|Powiązane ostrzeżenia.|

## <a name="in-this-section"></a>W tej sekcji

|Element|Wartość|
|-|-|
|[Ostrzeżenia według CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)|Wyświetla wszystkie ostrzeżenia według CheckId|
|[Ostrzeżenia kryptografii](../code-quality/cryptography-warnings.md)|Ostrzeżenia, które obsługują bezpieczniejsze biblioteki i aplikacje poprzez poprawne użycie kryptografii.|
|[Ostrzeżenia projektu](../code-quality/design-warnings.md)|Ostrzeżenia, które obsługują właściwy projekt biblioteki, zgodnie z [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] wytycznymi dotyczącymi projektowania.|
|[Ostrzeżenia globalizacji](../code-quality/globalization-warnings.md)|Ostrzeżenia, które obsługują biblioteki i aplikacje gotowe do używania na całym świecie.|
|[Ostrzeżenia dotyczące współdziałania](../code-quality/interoperability-warnings.md)|Ostrzeżenia, które obsługują interakcję z klientami COM.|
|[Ostrzeżenia dotyczące utrzymania](../code-quality/maintainability-warnings.md)|Ostrzeżenia, które obsługują konserwację biblioteki i aplikacji.|
|[Ostrzeżenia dotyczące mobilności](../code-quality/mobility-warnings.md)|Ostrzeżenia, które obsługują wydajne zużycie mocy.|
|[Ostrzeżenia dotyczące nazewnictwa](../code-quality/naming-warnings.md)|Ostrzeżenia, które wspierają przestrzeganie konwencji nazewnictwa [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] wytycznych dotyczących projektowania.|
|[Ostrzeżenia dotyczące wydajności](../code-quality/performance-warnings.md)|Ostrzeżenia, które obsługują biblioteki i aplikacje o wysokiej wydajności.|
|[Ostrzeżenia dotyczące przenośności](../code-quality/portability-warnings.md)|Ostrzeżenia, które obsługują przenośność na różnych platformach.|
|[Ostrzeżenia o niezawodności](../code-quality/reliability-warnings.md)|Ostrzeżenia, które obsługują niezawodność biblioteki i aplikacji, takie jak poprawne użycie pamięci i wątku.|
|[Ostrzeżenia dotyczące zabezpieczeń](../code-quality/security-warnings.md)|Ostrzeżenia, które obsługują bezpieczniejsze biblioteki i aplikacje.|
|[Ostrzeżenia dotyczące użycia](../code-quality/usage-warnings.md)|Ostrzeżenia, które obsługują odpowiednie użycie [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .|
|[Błędy zasad analizy kodu](../code-quality/code-analysis-policy-errors.md)|Błędy, które występują, jeśli zasady analizy kodu nie są spełnione podczas ewidencjonowania.|
