---
title: Scenariusze testów obciążenia
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, user activities
- load tests, modeling scenarios
ms.assetid: fec04f2e-bf38-4d44-b2ec-fa50f58fd0d9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 647548a59c965b6feacb994efa041ecd5b6c6b91
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55908814"
---
# <a name="edit-load-test-scenarios"></a>Edytowanie scenariuszy testu obciążenia

Test obciążeniowy *scenariusza* określa wzorca obciążenia, test mieszany, mieszaną przeglądarkę i mieszany profil sieciowy. Scenariusze są ważne, ponieważ umożliwiają one Konfigurowanie testów, aby zasymulować złożonych, realistycznych obciążeń.

Na przykład użytkownik może testować witrynę e-commerce, która ma internetowy fronton używany przez setki współbieżnych użytkowników korzystających z mieszczących się za pośrednictwem wielu szybkość połączeń i różnych przeglądarek. Tym samym witryna może mieć również funkcję administracji używaną przez pracowników wewnętrznych do aktualizacji produktów oraz do wyświetlania statystyk. Ci użytkownicy wewnętrzni zazwyczaj uzyskują dostęp lokacji przy użyciu tej samej przeglądarki i szybkiego połączenia sieci LAN. Chcesz Zastosuj hermetyzację właściwości tych dwóch różnych grup użytkowników w różnych scenariuszach. Każdy scenariusz może zawierać typ użytkownika wirtualnego. W takim scenariuszu testu obciążenia można wysyłać do reprezentowania klientów wirtualnych i inny scenariusz może również reprezentować wirtualnych użytkowników wewnętrznej witryny sieci Web.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="scenario-components"></a>Składniki scenariusza

Wszelkie opcje konfiguracji początkowej i ustawienia określić po utworzeniu testu obciążenia, można zmodyfikować później w **edytora testu obciążenia**. Można również dodać obsługę nowych scenariuszy, parametrów uruchomieniowych i zbiory liczników do testu obciążeniowego.

![Scenariusze testów obciążenia](../test/media/loadtesteditinscenarios.png)

Scenariusze zawierają następujące składniki:

|Termin|Definicja|
|-|-|
|Rozkład przeglądarek|Symuluje wirtualnych użytkownicy mieli dostęp do witryny sieci Web za pomocą różnych przeglądarek sieci web.|
|Wzorzec obciążenia|Określa liczbę użytkowników wirtualnych, które są aktywne podczas testu obciążenia i szybkość uruchamiania nowych użytkowników. Na przykład: krok, stałe i ukierunkowane na cel.|
|Model testu mieszanego|Określa prawdopodobieństwo, że użytkownik wirtualny uruchomi dany test w scenariuszu testu obciążenia. Na przykład: uruchomienie testu a oraz 80% szansę na uruchomienie testu b. szansę 20%. Model testu mieszanego powinien odzwierciedlać cele testu dla danego scenariusza.|
|Test mieszany|Test mieszany jest wybór web wydajności i testy jednostkowe wchodzących w skład tego scenariusza i dystrybucji tych testów.|
|Mieszany profil sieciowy|Symuluje wirtualnych użytkownicy mieli dostęp do witryny sieci Web za pomocą różnych połączeń sieciowych. Mieszany profil sieciowy oferuje opcje, które obejmują sieć LAN, modem kablowy i inne opcje.|

Scenariusz ma kilka właściwości, które można edytować za pomocą **edytora testu obciążenia**. Aby uzyskać więcej informacji, zobacz [właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md).

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-|-----------------------|
|**Dodaj sztuczne z reakcji człowieka przerw w tym scenariuszu:** Czasy reakcji służą do symulowania zachowań ludzkich, który powoduje, że osoby do interakcji z witryny sieci Web. Czasy reakcji występują między żądaniami w teście wydajności sieci web i między poszczególnymi iteracjami testu w scenariuszu testu obciążenia. Użycie czasów reakcji w teście obciążeniowym może być przydatne przy tworzeniu bardziej dokładnych symulacji obciążenia.|-   [Edytowanie czasów reakcji w celu symulowania witryny sieci Web symulujący opóźnienia wynikające z](../test/edit-think-times-in-load-test-scenarios.md)|
|**Określ liczbę użytkowników wirtualnych dla danego scenariusza:** Można skonfigurować właściwości wzorca obciążenia, aby określić, jak symulowane obciążenie użytkownika jest korygowane w trakcie testu obciążenia. Możesz uzyskać trzy wbudowane wzorce ładowania: stałe, etapu i ukierunkowane na cel. Możesz wybrać wzorzec obciążenia i dostosować właściwości do odpowiednich poziomów dla swoich celów testu obciążenia.|-   [Edytowanie wzorców obciążenia w celu modelu aktywności wirtualnych użytkowników](../test/edit-load-patterns-to-model-virtual-user-activities.md)|
|**Konfiguruj prawdopodobieństwo, że użytkownik wirtualny uruchomi testu w scenariuszu:** Możesz użyć testu mieszanego, który określa prawdopodobieństwo, że użytkownik wirtualny uruchomi dany test w scenariuszu testu obciążenia. Dzięki temu można bardziej realistycznie symulowanie obciążenia. Zamiast tylko jedego przepływu pracy za pośrednictwem aplikacji, może mieć wiele przepływów pracy, który jest większym zbliżeniem tego jak użytkownicy końcowi są wzajemne powiązani ze swoimi aplikacjami.|-   [Edytowanie modeli testów mieszanych](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)|
|**Dodaj lub usuń test wydajności lub jednostki sieci Web w scenariuszu testu obciążenia:** Można dodać lub usunąć test wydajności lub jednostki w sieci web z testu obciążeniowego w scenariuszu. Test obciążenia zawiera jeden lub więcej scenariuszy, z których każdy zawiera jeden lub więcej testów sieci web wydajności lub jednostki.|-   [Edytuj test mieszany](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)|
|**Konfiguruj żądany mieszany profil sieciowy dla danego scenariusza:** Mieszany profil sieciowy można symulować obciążenia sieci bardziej realistycznie w scenariuszu testu obciążenia. Obciążenie jest generowane przy użyciu typów siecie zamiast jednego typu sieci. Możesz utworzyć zbliżenie tego jak użytkownicy końcowi są wzajemne powiązani ze swoimi aplikacjami. Model mieszany sieci powinien odzwierciedlać cele tego scenariusza.|-   [Określanie typów sieci wirtualnych](../test/specify-virtual-network-types-in-a-load-test-scenario.md)|
|**Wybierz odpowiednią mieszaną przeglądarkę sieci Web dla danego scenariusza:** Mieszany profil przeglądarki można symulować obciążenia sieci web bardziej realistycznie w scenariuszu testu obciążenia. Obciążenie jest generowane przy użyciu różnorodnych przeglądarek zamiast jednej przeglądarki. Możesz utworzyć zbliżenie przeglądarek, które będą używane z aplikacjami.|-   [Określanie typów przeglądarek sieci web](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)|
|**Konfiguruj ustawienia iteracji testu dla danego scenariusza:** Możesz edytować Scenariusz testów obciążenia do konfigurowania ustawień iteracji testowej przy użyciu edytora Test obciążenia i oknie dialogowym właściwości. Domyślnie scenariusz jest konfigurowany za pomocą bez maksymalnych iteracji testowych. Opcjonalnie można skonfigurować maksymalną liczbę iteracji, w tym scenariuszu i długość przerwy między nimi.|-   [Konfigurowanie iteracji testowych dla scenariuszy](../test/configure-test-iterations-in-a-load-test-scenario.md)|
|**Konfiguruj ustawienia opóźnienia dla danego scenariusza:** Za pomocą **edytora testu obciążenia** i **właściwości** oknie można określić opóźnienie przed rozpoczęciem scenariusza w teście obciążeniowym. Kiedy warto używać przykład **opóźnienie uruchamiania** właściwość jest, jeśli potrzebujesz jeden scenariusz rozpoczął produkcję elementów, które korzysta inny scenariusz. Można opóźnić scenariusz zużycia w celu umożliwienia scenariuszowi wytwarzania pewnych danych.|-   [Opóźnień uruchamiania scenariuszy Configureng](../test/configure-scenario-start-delays.md)|
|**Określ komputery zdalne do użycia w scenariuszu testu obciążenia:** Po utworzeniu testu obciążenia, można edytować właściwości scenariusza testu obciążenia, aby wskazać, którzy agenci testowi mają zostać uwzględnione. Aby uzyskać więcej informacji, zobacz [kontrolerów testów i agentów testowych](configure-test-agents-and-controllers-for-load-tests.md).|-   [Jak: Określanie agentów testowych do użycia](../test/how-to-specify-test-agents-to-use-in-load-test-scenarios.md)|

## <a name="see-also"></a>Zobacz także

- [Edytowanie testów obciążenia](../test/edit-load-tests.md)
- [Właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md)