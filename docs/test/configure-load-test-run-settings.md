---
title: Konfigurowanie ustawień testu obciążenia
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, configuring run settings
ms.assetid: 0c86918b-cd63-4468-8f49-6d547a1276dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e8002373b7ad34796df557686c1aff6a417d49ea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85288835"
---
# <a name="configure-load-test-run-settings"></a>Skonfiguruj ustawienia przebiegu testu obciążenia

*Parametry uruchomieniowe* są zestawem właściwości, które mają wpływ na sposób uruchamiania testu obciążenia. Parametry uruchomieniowe są zorganizowane według kategorii w oknie **Właściwości** .

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

W teście obciążenia można mieć więcej niż jedno ustawienie uruchomieniowe, ale tylko jedno z ustawień uruchomieniowych może być aktywne dla każdego uruchomienia. Pozostałe parametry uruchomieniowe oferują szybki sposób wyboru alternatywnego ustawienia do kolejnych przebiegów testowych.

Początkowe ustawienie uruchomieniowe jest tworzone podczas tworzenia testu obciążenia przy użyciu **nowego Kreator testu obciążeniowego**.

![Parametry uruchomieniowe testu obciążenia](../test/media/loadtestrunsettings.png)

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-|-|
|**Dodaj więcej parametrów uruchomieniowych do testu obciążenia:** Oprócz ustawienia uruchomieniowego, które jest tworzone podczas uruchamiania **nowego Kreator testu obciążeniowego**, można dodać więcej parametrów uruchomieniowych do testu obciążenia, aby można było uruchomić test w różnych warunkach.|-   [Instrukcje: Dodawanie dodatkowych parametrów uruchomieniowych do testu obciążenia](../test/how-to-add-additional-run-settings-to-a-load-test.md)|
|**Określ aktywne ustawienie uruchomieniowe do użycia z testem obciążenia:** Możesz wybrać ustawienie uruchomieniowe, które ma być używane z testem obciążenia przy użyciu Edytor testu obciążeniowego. Aktywny parametr jest identyfikowany za pomocą przyrostka „[Aktywny]”.|-   [Instrukcje: Wybieranie aktywnego ustawienia uruchomieniowego dla testu obciążenia](../test/how-to-select-the-active-run-setting-for-a-load-test.md)|
|**Edytuj właściwości ustawienia uruchomieniowego:** Można edytować właściwości ustawienia uruchomieniowego dla takich elementów jak opcje rejestrowania (Zobacz więcej poniżej), określanie długości testu, czasu trwania rozgrzewania, maksymalnej liczby raportowanych szczegółów błędu, częstotliwości próbkowania, modelu połączenia (tylko testy wydajności sieci Web), wyników typu magazynu, poziomu walidacji i śledzenia SQL. Parametry uruchomieniowe powinny odzwierciedlać cele testu obciążeniowego.|-   [Właściwości ustawień przebiegu testu obciążenia](../test/load-test-run-settings-properties.md)<br />-   [Zmiana właściwości ustawień uruchomieniowych](../test/load-test-run-settings-properties.md#change-run-setting-properties)|
|**Określ liczbę iteracji testu w ustawieniach przebiegu testu obciążenia:** Można określić, ile razy mają być uruchamiane wszystkie testy wydajności sieci Web i testów jednostkowych we wszystkich scenariuszach testów obciążenia przez skonfigurowanie właściwości **iteracje testu** .|-   [Instrukcje: Określanie liczby iteracji testowych w ustawieniu uruchamiania](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md)|
|**Określ częstotliwość próbkowania dla ustawienia przebiegu testu obciążenia:** Możesz określić częstotliwość, z jaką test obciążenia zbiera dane licznika wydajności, konfigurując Właściwość **częstotliwość próbkowania** .|-   [Instrukcje: Określanie częstotliwości próbkowania](../test/how-to-specify-the-sample-rate-for-a-load-test.md)|
|**Określ opcję przechowywania szczegółów czasu:** Można określić, jak mają być zapisywane szczegóły testu obciążenia przez skonfigurowanie właściwości **Magazyn informacji o chronometrażu** .|-   [Instrukcje: Określanie właściwości przechowywania informacji o chronometrażu](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md)|
|**Określ okres przechowywania zasobu testowego:** Aby przyspieszyć testowanie > poprawić > cykl przetestowania przez zatrzymywanie zasobów testowych przez określony czas, należy ustawić właściwość **czas przechowywania zasobów** .|-   [Zachowaj zasoby, aby przyspieszyć testowanie obciążenia](/azure/devops/test/load-test/getting-started-with-performance-testing?view=vsts)|
|**Użyj parametrów kontekstu:** Do Sparametryzuj ciągu można użyć parametrów kontekstu. Na przykład jeśli test obciążenia zawiera test wydajności sieci Web, który używa sparametryzowanego serwera sieci Web, można dodać parametr kontekstowy do ustawień uruchomieniowych, które są mapowane na inny serwer.|-   [Instrukcje: Dodawanie parametrów kontekstu do ustawienia uruchomieniowego](../test/how-to-add-context-parameters-to-a-load-test-run-setting.md)|
|**Konfigurowanie właściwości rejestrowania testów:** Można skonfigurować, jak często dane są zapisywane w dzienniku, który jest skojarzony z ustawieniami przebiegu testu obciążenia. Może to być ważne, gdy uruchamiasz duży lub złożony test obciążeniowy, ponieważ dziennik może mieć wielkość kilku gigabajtów.<br /><br /> Można także skonfigurować plik dziennika, aby automatycznie zapisywał informacje o testach obciążeniowych, które zakończyły się niepowodzeniem, aby pomóc w debugowaniu i analizowaniu aplikacji.|-   [Modyfikowanie ustawień rejestrowania testu obciążenia](../test/modify-load-test-logging-settings.md)|
