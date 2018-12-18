---
title: Konfigurowanie ustawień testu obciążenia
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, configuring run settings
ms.assetid: 0c86918b-cd63-4468-8f49-6d547a1276dc
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 9aa2defb458fba0d7962813743fa603fe71081e2
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53053321"
---
# <a name="configure-load-test-run-settings"></a>Konfigurowanie ustawień testu obciążenia

*Parametry uruchomieniowe* są zestawem właściwości wpływającym na sposób wykonywania testu obciążeniowego. Ustawienia uruchamiania są zorganizowane według kategorii w **właściwości** okna.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Może mieć więcej niż jedno ustawienie uruchamiania w teście obciążenia, ale tylko jeden z parametrów uruchomieniowych może być aktywny na przebieg. Pozostałe parametry uruchomieniowe oferują szybki sposób wyboru alternatywnego ustawienia do kolejnych przebiegów testowych.

Początkowy parametr uruchomieniowy jest tworzony podczas tworzenia testu obciążeniowego za pomocą **Kreatora nowego testu obciążeniowego**.

![Parametry uruchomieniowe testu obciążenia](../test/media/loadtestrunsettings.png)

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-|-|
|**Dodanie kolejnych parametrów uruchomieniowych do testu obciążeniowego:** oprócz parametru uruchomieniowego tworzonego podczas uruchamiania **Kreatora nowego testu obciążeniowego**, można dodać kolejnych parametrów uruchomieniowych do testu obciążeniowego, aby uruchomić test w różnych warunki.|-   [Porady: Dodawanie dodatkowych ustawień przebiegu testu obciążenia](../test/how-to-add-additional-run-settings-to-a-load-test.md)|
|**Określenie aktywnego parametru uruchomieniowego do użycia w teście obciążeniowym:** można wybrać parametr uruchomieniowy, którą chcesz używać z testu obciążenia za pomocą edytora testu obciążenia. Aktywny parametr jest identyfikowany za pomocą przyrostka „[Aktywny]”.|-   [Porady: Wybierz aktywne ustawienia uruchamiania dla testu obciążenia](../test/how-to-select-the-active-run-setting-for-a-load-test.md)|
|**Edytuj właściwości ustawienia przebiegu:** przebieg można edytować właściwości ustawienia dla takich operacji jak opcje logowania (zobacz poniżej), określająca długość testu, czas trwania rozgrzewania, maksymalną liczbę błędów podać szczegóły, częstotliwość próbkowania połączenia Model (tylko testy wydajności sieci web), typ przechowywania wyników, poziom sprawdzania poprawności i śledzenie SQL. Parametry uruchomieniowe powinny odzwierciedlać cele testu obciążeniowego.|-   [Właściwości ustawień przebiegu testu obciążeniowego](../test/load-test-run-settings-properties.md)<br />-   [Zmiana właściwości ustawienia przebiegu](../test/load-test-run-settings-properties.md#change-run-setting-properties)|
|**Określanie liczby iteracji testowych w ustawieniach testu obciążenia:** można określić liczbę razy, aby uruchomić wszystkie sieci web wydajności i testy jednostkowe we wszystkich scenariuszach testu obciążeniowego przez skonfigurowanie **iteracje testu** Właściwość.|-   [Porady: Określanie liczby iteracji testowych w ustawieniach testu](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md)|
|**Określ częstotliwość próbkowania dla testu obciążeniowego uruchomieniowy:** można określić, jak często testy zbierać dane licznika wydajności, konfigurując obciążeniowe mają **częstotliwość próbkowania** właściwości.|-   [Porady: określanie wielkości próbki](../test/how-to-specify-the-sample-rate-for-a-load-test.md)|
|**Określ opcje przechowywania szczegółów czasu:** można określić, jak zapisywać Szczegóły testu obciążeniowego przez skonfigurowanie **przechowywanie informacji** właściwości.|-   [Porady: Określanie właściwości magazynowania szczegółów chronometrażu](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md)|
|**Określ okres przechowywania zasobów testowych:** przyspieszenia testu > Rozwiąż > przetestowanie cyklu przy zachowaniu zasobów testowych w wybranym okresie, ustawiając **czas przechowywania zasobów** właściwości.|-   [Przechowywania zasobów w celu przyspieszenia testowania obciążenia](/azure/devops/test/load-test/getting-started-with-performance-testing?view=vsts)|
|**Korzystanie z parametrów kontekstu:** można użyć parametrów kontekstu do parametryzowania ciągu tekstowego. Na przykład jeśli test obciążenia zawiera test wydajności sieci web, który korzysta z serwera sieci web sparametryzowane, można dodać parametr kontekstu do parametrów uruchomieniowych, które są mapowane na inny serwer.|-   [Porady: Dodawanie parametrów kontekstu do ustawień](../test/how-to-add-context-parameters-to-a-load-test-run-setting.md)|
|**Konfigurowanie właściwości logowania testu:** można skonfigurować, jak często dane są zapisywane w dzienniku, które jest skojarzone z parametrów uruchomieniowych testu obciążeniowego. Może to być ważne, gdy uruchamiasz duży lub złożony test obciążeniowy, ponieważ dziennik może mieć wielkość kilku gigabajtów.<br /><br /> Można także skonfigurować plik dziennika, aby automatycznie zapisywał informacje o testach obciążeniowych, które zakończyły się niepowodzeniem, aby pomóc w debugowaniu i analizowaniu aplikacji.|-   [Modyfikowanie ustawień rejestrowania testu obciążeniowego](../test/modify-load-test-logging-settings.md)|