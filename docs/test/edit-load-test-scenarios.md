---
title: Scenariusze testu obciążenia
ms.date: 10/03/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, user activities
- load tests, modeling scenarios
ms.assetid: fec04f2e-bf38-4d44-b2ec-fa50f58fd0d9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8fa323d275628fe580763709884552754acfba81
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593242"
---
# <a name="edit-load-test-scenarios"></a>Edytowanie scenariuszy testów obciążenia

*Scenariusz* testu obciążenia określa wzorzec obciążenia, mix testu, mix przeglądarki i mix sieci. Scenariusze są ważne, ponieważ umożliwiają konfigurowanie testów do symulowania złożonych, realistycznych obciążeń.

Na przykład możesz testować witrynę handlu elektronicznego, która ma fronton internetowy używany przez setki równoczesnych klientów korzystających z wielu szybkości połączeń i korzystających z różnych przeglądarek. Ta sama lokacja może również mieć funkcję administracyjną, która jest używana przez wewnętrznych pracowników do aktualizowania produktów i wyświetlania statystyk. Ci użytkownicy wewnętrzni zazwyczaj uzyskują dostęp do witryny przy użyciu tej samej przeglądarki i szybkiego połączenia LAN. Należy hermetyzować właściwości tych dwóch różnych grup użytkowników w różnych scenariuszach. Każdy scenariusz może zawierać typ użytkownika wirtualnego. W takim przypadku scenariusz testu obciążenia można dokonać do reprezentowania klientów wirtualnych i inny scenariusz może być wykonane do reprezentowania wirtualnych użytkowników wewnętrznych witryny sieci Web.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="scenario-components"></a>Składniki scenariusza

Wszystkie początkowe opcje konfiguracji i ustawienia określone podczas tworzenia testu obciążenia można zmodyfikować później w **Edytorze testów obciążenia**. Można również dodać nowe scenariusze, uruchomić ustawienia i zestawy liczników do testu obciążenia.

![Scenariusze testu obciążenia](../test/media/loadtesteditinscenarios.png)

Scenariusze zawierają następujące składniki:

|Termin|Definicja|
|-|-|
|Kombinacja przeglądarki|Symuluje, że użytkownicy wirtualni uzyskują dostęp do witryny za pośrednictwem różnych przeglądarek internetowych.|
|Wzorzec obciążenia|Określa liczbę użytkowników wirtualnych, którzy są aktywni podczas testu obciążenia, oraz szybkość, z jaką nowi użytkownicy są uruchamiane. Na przykład: krok, stała i oparte na celach.|
|Testowy model miksu|Określa prawdopodobieństwo uruchomienia danego testu przez użytkownika wirtualnego w scenariuszu testu obciążenia. Na przykład: 20% szans na uruchomienie TestA i 80% szans na uruchomienie TestB. Model testu mix powinien odzwierciedlać cele testu dla określonego scenariusza.|
|Mieszanka testowa|Mix test jest wybór wydajności sieci web i testy jednostkowe, które tworzą scenariusz i dystrybucji tych testów.|
|Połączenie sieciowe|Symuluje, że użytkownicy wirtualni uzyskują dostęp do witryny sieci Web za pośrednictwem różnych połączeń sieciowych. Sieć Mix oferuje opcje, które obejmują sieć LAN, modem kablowy i inne opcje.|

Scenariusz ma kilka innych właściwości, które można edytować za pomocą **Edytora testu obciążenia**. Aby uzyskać więcej informacji, zobacz [Ładowanie właściwości scenariusza testu](../test/load-test-scenario-properties.md).

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-|-----------------------|
|**Dodaj sztuczne przerwy interakcji międzyludzkich w scenariuszu:** Czasy myśleń są używane do symulowania ludzkich zachowań, które powodują, że ludzie czekają między interakcjami z witryną sieci Web. Czasy myślenia występują między żądaniami w teście wydajności sieci web i między iteracjami testów w scenariuszu testu obciążenia. Korzystanie z czasów myślenia w teście obciążenia może być przydatne w tworzeniu dokładniejszych symulacji obciążenia.|-   [Edytuj czasy zajmów się, aby symulować opóźnienia interakcji z człowiekiem w witrynie](../test/edit-think-times-in-load-test-scenarios.md)|
|**Określ liczbę użytkowników wirtualnych dla twojego scenariusza:** Można skonfigurować właściwości wzorca obciążenia, aby określić sposób dostosowywania symulowanego obciążenia użytkownika podczas testu obciążenia. Otrzymujesz trzy wbudowane wzorce obciążenia: stały, krok i cel. Wybierz wzorzec obciążenia i dostosować właściwości do odpowiednich poziomów dla celów testu obciążenia.|-   [Edytowanie wzorców obciążenia w celu modelowania działań użytkownika wirtualnego](../test/edit-load-patterns-to-model-virtual-user-activities.md)|
|**Skonfiguruj prawdopodobieństwo uruchomienia testu przez użytkownika wirtualnego w scenariuszu:** Można użyć zestawu testowego, który określa prawdopodobieństwo, że użytkownik wirtualny uruchomi dany test w scenariuszu testu obciążenia. Dzięki temu można symulować obciążenia bardziej realistycznie. Zamiast mieć tylko jeden przepływ pracy za pośrednictwem aplikacji, można mieć kilka przepływów pracy, co jest bliższe przybliżenie sposobu interakcji użytkowników końcowych z aplikacjami.|-   [Edytowanie modeli mieszania tekstu](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)|
|**Dodawanie lub usuwanie testu wydajności sieci Web lub jednostki ze scenariusza testu obciążenia:** Można dodać lub usunąć wydajność sieci web lub test jednostkowy z testu obciążenia w scenariuszu. Test obciążenia zawiera jeden lub więcej scenariuszy, z których każdy zawiera co najmniej jeden test wydajności sieci web lub jednostki.|-   [Edycja miksu testowego](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)|
|**Skonfiguruj żądaną kombinację sieciową dla swojego scenariusza:** Za pomocą sieci mix, można symulować obciążenia sieci bardziej realistycznie w scenariuszu testu obciążenia. Obciążenie jest generowane przy użyciu niejednorodnej kombinacji typów sieci zamiast jednego typu sieci. Tworzenie bliższe przybliżenie sposobu interakcji użytkowników końcowych z aplikacjami. Model sieci powinien odzwierciedlać cele tego scenariusza.|-   [Określanie typów sieci wirtualnych](../test/specify-virtual-network-types-in-a-load-test-scenario.md)|
|**Wybierz odpowiednią kombinację przeglądarki sieci Web dla danego scenariusza:** Za pomocą kombinacji przeglądarki, można symulować obciążenia sieci web bardziej realistycznie w scenariuszu testu obciążenia. Obciążenie jest generowane przy użyciu niejednorodnej kombinacji przeglądarek zamiast jednej przeglądarki. Tworzenie bliższe przybliżenie przeglądarek, które będą używane z aplikacjami.|-   [Określanie typów przeglądarek internetowych](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)|
|**Skonfiguruj ustawienia iteracji testowej dla twojego scenariusza:** Można edytować scenariusz testu obciążenia, aby skonfigurować ustawienia iteracji testowej za pomocą Edytora testów obciążenia i okna Właściwości. Domyślnie scenariusz jest skonfigurowany bez maksymalnej iteracji testowych. Opcjonalnie można skonfigurować maksymalną liczbę iteracji w scenariuszu i jak długo, aby wstrzymać między nimi.|-   [Konfigurowanie iteracji testowych dla scenariuszy](../test/configure-test-iterations-in-a-load-test-scenario.md)|
|**Konfigurowanie ustawień opóźnienia dla scenariusza:** Za pomocą **Edytora testów obciążenia** i **właściwości** okna, można określić opóźnienie przed rozpoczęciem scenariusza w teście obciążenia. Przykładem, kiedy można użyć **delay start time** właściwość jest, jeśli potrzebujesz jednego scenariusza, aby rozpocząć produkcję elementów, które zużywa inny scenariusz. Można opóźnić scenariusz zużywania, aby włączyć scenariusz produkcji do wypełniania niektórych danych.|-   [Konfigurowanie scenariusza opóźnienia rozpoczęcia](../test/configure-scenario-start-delays.md)|
|**Określ zdalne maszyny do użycia w scenariuszu testu obciążenia:** Po utworzeniu testu obciążenia, można edytować właściwości scenariusza testu obciążenia, aby wskazać, które agentów testowych, które chcesz uwzględnić. Aby uzyskać więcej informacji, zobacz [Kontrolery testów i agenci testowi](configure-test-agents-and-controllers-for-load-tests.md).|-   [Jak: Określ agentów testowych do użycia](../test/how-to-specify-test-agents-to-use-in-load-test-scenarios.md)|

## <a name="see-also"></a>Zobacz też

- [Edytowanie testów obciążenia](../test/edit-load-tests.md)
- [Właściwości scenariusza testu obciążenia](../test/load-test-scenario-properties.md)
