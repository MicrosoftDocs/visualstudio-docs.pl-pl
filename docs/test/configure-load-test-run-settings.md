---
title: Konfigurowanie ustawień testu obciążenia
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, configuring run settings
ms.assetid: 0c86918b-cd63-4468-8f49-6d547a1276dc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.openlocfilehash: dcb66eb8ebc4aeb09e4cd9d00467808be0b93f28
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55043587"
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
|**Dodaj więcej parametrów uruchomieniowych do testu obciążeniowego:** Oprócz parametru uruchomieniowego tworzonego podczas uruchamiania **Kreatora nowego testu obciążeniowego**, można dodać kolejnych parametrów uruchomieniowych do testu obciążeniowego, aby uruchomić test w innych warunkach.|-   [Jak: Dodawanie dodatkowych ustawień przebiegu testu obciążenia](../test/how-to-add-additional-run-settings-to-a-load-test.md)|
|**Określenie aktywnego parametru uruchomieniowego do użycia w teście obciążeniowym:** Można wybrać parametr uruchomieniowy, którą chcesz używać z testu obciążenia za pomocą edytora testu obciążenia. Aktywny parametr jest identyfikowany za pomocą przyrostka „[Aktywny]”.|-   [Jak: Wybierz aktywne ustawienia uruchamiania dla testu obciążenia](../test/how-to-select-the-active-run-setting-for-a-load-test.md)|
|**Edytuj właściwości ustawienia przebiegu:** Możesz edytować przebieg Ustawianie właściwości dla takich operacji jak opcje logowania (zobacz poniżej), określająca długość testu, czas trwania rozgrzewania, maksymalną liczbę błędów podać szczegóły, częstotliwość próbkowania, model połączenia (tylko testy wydajności sieci web), wyniki Typ magazynu, poziom sprawdzania poprawności i śledzenie SQL. Parametry uruchomieniowe powinny odzwierciedlać cele testu obciążeniowego.|-   [Właściwości ustawień przebiegu testu obciążeniowego](../test/load-test-run-settings-properties.md)<br />-   [Zmiana właściwości ustawienia przebiegu](../test/load-test-run-settings-properties.md#change-run-setting-properties)|
|**Określ licznik iteracji testu w ustawieniach testu obciążenia:** Można określić liczbę razy, aby uruchomić wszystkie sieci web wydajności i testy jednostkowe we wszystkich scenariuszach testu obciążeniowego przez skonfigurowanie **iteracji testu** właściwości.|-   [Jak: Określanie liczby iteracji testowych w ustawieniach testu](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md)|
|**Określ częstotliwość próbkowania dla testu obciążeniowego uruchomieniowy:** Można określić, jak często testy zbierać dane licznika wydajności, konfigurując obciążeniowe mają **częstotliwość próbkowania** właściwości.|-   [Jak: Określ częstotliwość próbkowania](../test/how-to-specify-the-sample-rate-for-a-load-test.md)|
|**Określ opcje przechowywania szczegółów czasu:** Można określić, jak zapisywać Szczegóły testu obciążeniowego przez skonfigurowanie **przechowywanie informacji** właściwości.|-   [Jak: Określanie właściwości magazynowania szczegółów chronometrażu](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md)|
|**Określ okres przechowywania zasobów testowych:** Przyspiesz testu > naprawić > przetestowanie cyklu przy zachowaniu zasobów testowych w wybranym okresie, ustawiając **czas przechowywania zasobów** właściwości.|-   [Przechowywania zasobów w celu przyspieszenia testowania obciążenia](/azure/devops/test/load-test/getting-started-with-performance-testing?view=vsts)|
|**Korzystanie z parametrów kontekstu:** Można użyć parametrów kontekstu do parametryzowania ciągu tekstowego. Na przykład jeśli test obciążenia zawiera test wydajności sieci web, który korzysta z serwera sieci web sparametryzowane, można dodać parametr kontekstu do parametrów uruchomieniowych, które są mapowane na inny serwer.|-   [Jak: Dodawanie parametrów kontekstu do ustawień](../test/how-to-add-context-parameters-to-a-load-test-run-setting.md)|
|**Konfigurowanie właściwości logowania testu:** Można skonfigurować, jak często dane są zapisywane w dzienniku, które jest skojarzone z parametrów uruchomieniowych testu obciążeniowego. Może to być ważne, gdy uruchamiasz duży lub złożony test obciążeniowy, ponieważ dziennik może mieć wielkość kilku gigabajtów.<br /><br /> Można także skonfigurować plik dziennika, aby automatycznie zapisywał informacje o testach obciążeniowych, które zakończyły się niepowodzeniem, aby pomóc w debugowaniu i analizowaniu aplikacji.|-   [Modyfikowanie ustawień rejestrowania testu obciążeniowego](../test/modify-load-test-logging-settings.md)|