---
title: Konfigurowanie ustawień testu obciążenia
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, configuring run settings
ms.assetid: 0c86918b-cd63-4468-8f49-6d547a1276dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ffc9d6c2e563fcd16a61e91eaa94889de8607efc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595985"
---
# <a name="configure-load-test-run-settings"></a>Konfigurowanie ustawień przebiegu testu obciążenia

*Uruchom ustawienia* to zestaw właściwości, które wpływają na sposób wykonywania testu obciążenia. Ustawienia uruchamiania są uporządkowane według kategorii w oknie **Właściwości.**

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

W teście obciążenia może być więcej niż jedno ustawienie uruchamiania, jednak tylko jedno z ustawień uruchamiania może być aktywne na przebieg. Pozostałe parametry uruchomieniowe oferują szybki sposób wyboru alternatywnego ustawienia do kolejnych przebiegów testowych.

Ustawienie początkowego uruchomienia jest tworzone podczas tworzenia testu obciążenia za pomocą **Kreatora nowego testu obciążenia**.

![Parametry uruchomieniowe testu obciążenia](../test/media/loadtestrunsettings.png)

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-|-|
|**Dodaj więcej ustawień uruchamiania do testu obciążenia:** Oprócz ustawienia uruchamiania, które jest tworzone po uruchomieniu **Kreatora nowego testu obciążenia,** można dodać więcej ustawień uruchamiania do testu obciążenia, dzięki czemu można uruchomić test w różnych warunkach.|-   [Jak: Dodawanie dodatkowych ustawień uruchamiania do testu obciążenia](../test/how-to-add-additional-run-settings-to-a-load-test.md)|
|**Określ ustawienie aktywnego uruchamiania używane z testem obciążenia:** Można wybrać ustawienie uruchamiania, które ma być używane z testem obciążenia za pomocą Edytora testów obciążenia. Aktywny parametr jest identyfikowany za pomocą przyrostka „[Aktywny]”.|-   [Jak: Wybierz ustawienie aktywnego uruchamiania dla testu obciążenia](../test/how-to-select-the-active-run-setting-for-a-load-test.md)|
|**Edytuj właściwości ustawienia przebiegu:** Można edytować właściwości ustawienia uruchamiania dla takich rzeczy, jak opcje rejestrowania (zobacz więcej poniżej), określanie długości testu, czas trwania rozgrzewania, maksymalna liczba zgłoszonych szczegółów błędu, częstotliwość próbkowania, model połączenia (tylko testy wydajności sieci web), typ magazynu wyników, poziom sprawdzania poprawności i śledzenie SQL. Parametry uruchomieniowe powinny odzwierciedlać cele testu obciążeniowego.|-   [Właściwości ustawień przebiegu testu obciążenia](../test/load-test-run-settings-properties.md)<br />-   [Zmienianie właściwości ustawień przebiegu](../test/load-test-run-settings-properties.md#change-run-setting-properties)|
|**Określ liczbę iteracji testu w ustawieniach przebiegu testu obciążenia:** Można określić, ile razy, aby uruchomić wszystkie testy wydajności sieci web i jednostki we wszystkich scenariuszach testów obciążenia, konfigurując **test iteracji** właściwości.|-   [Jak: Określ liczbę iteracji testowych w ustawieniu uruchamiania](../test/how-to-specify-the-number-of-test-iterations-in-a-load-test.md)|
|**Określ częstotliwość próbkowania dla ustawienia przebiegu testu obciążenia:** Można określić, jak często mają mieć test obciążenia zbierać dane licznika wydajności, konfigurując **Sample Rate** właściwości.|-   [Jak: Określ częstotliwość próbkowania](../test/how-to-specify-the-sample-rate-for-a-load-test.md)|
|**Określ opcję przechowywania szczegółów chronometrażu:** Można określić, jak chcesz zapisać szczegóły testu obciążenia, konfigurując właściwość **Magazyn szczegółów chronometrażu.**|-   [Jak: Określ właściwość magazynu szczegółów chronometrażu](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md)|
|**Określ okres przechowywania zasobów testowych:** Przyspiesz test > naprawić > cyklu ponownego testowania, zachowując zasoby testowe przez określony czas, ustawiając właściwość **Czas przechowywania zasobów.**|-   [Zachowaj zasoby, aby przyspieszyć testowanie obciążenia](/azure/devops/test/load-test/getting-started-with-performance-testing?view=vsts)|
|**Użyj parametrów kontekstowych:** Za pomocą parametrów kontekstu można parametryzować ciąg. Na przykład jeśli test obciążenia zawiera test wydajności sieci web, który używa sparametryzowanego serwera sieci web, można dodać parametr kontekstu do ustawień uruchamiania, który jest mapowany na inny serwer.|-   [Jak: Dodawanie parametrów kontekstu do ustawienia uruchamiania](../test/how-to-add-context-parameters-to-a-load-test-run-setting.md)|
|**Konfigurowanie właściwości rejestrowania testu:** Można skonfigurować, jak często dane są zapisywane w dzienniku, który jest skojarzony z ustawieniami przebiegu testu obciążenia. Może to być ważne, gdy uruchamiasz duży lub złożony test obciążeniowy, ponieważ dziennik może mieć wielkość kilku gigabajtów.<br /><br /> Można także skonfigurować plik dziennika, aby automatycznie zapisywał informacje o testach obciążeniowych, które zakończyły się niepowodzeniem, aby pomóc w debugowaniu i analizowaniu aplikacji.|-   [Modyfikowanie ustawień rejestrowania testu obciążenia](../test/modify-load-test-logging-settings.md)|
