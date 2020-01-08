---
title: Scenariusze testów obciążenia
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593242"
---
# <a name="edit-load-test-scenarios"></a>Edytowanie scenariuszy testu obciążenia

W *scenariuszu* testu obciążenia określono wzorzec obciążenia, test mieszany, mieszany z przeglądarką i mieszany profil sieciowy. Scenariusze są ważne, ponieważ umożliwiają konfigurowanie testów w celu symulowania skomplikowanych, realistycznych obciążeń.

Na przykład może być testowana witryna handlu elektronicznego z frontonem internetowym, który jest używany przez setki równoczesnych klientów, którzy korzystają z wielu szybkości połączenia i używają różnych przeglądarek. Ta sama lokacja może również mieć funkcję administracyjną, która jest używana przez pracowników wewnętrznych do aktualizowania produktów i wyświetlania statystyk. Ci użytkownicy wewnętrzni zwykle uzyskują dostęp do witryny za pomocą tej samej przeglądarki i połączenia sieci LAN o dużej szybkości. Warto hermetyzować właściwości tych dwóch różnych grup użytkowników w różnych scenariuszach. Każdy scenariusz może zawierać typ użytkownika wirtualnego. W takim przypadku można wykonać scenariusz testu obciążenia reprezentujący klientów wirtualnych i inny scenariusz do reprezentowania wirtualnych użytkowników wewnętrznych witryny sieci Web.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="scenario-components"></a>Składniki scenariusza

Wszystkie opcje konfiguracji początkowej i ustawienia, które można określić podczas tworzenia testu obciążenia, można modyfikować w dalszej części **Edytor testu obciążeniowego**. Możesz również dodawać nowe scenariusze, uruchamiać ustawienia i zestawy liczników do testu obciążenia.

![Scenariusze testów obciążenia](../test/media/loadtesteditinscenarios.png)

Scenariusze zawierają następujące składniki:

|Termin|Definicja|
|-|-|
|Mieszanie przeglądarki|Symuluje, że użytkownicy wirtualną uzyskują dostęp do witryny internetowej za pomocą różnych przeglądarek sieci Web.|
|Wzorzec obciążenia|Określa liczbę wirtualnych użytkowników, którzy są aktywni podczas testu obciążenia, oraz częstotliwość uruchamiania nowych użytkowników. Na przykład: krok, stała i oparty na celach.|
|Model testu mieszanego|Określa prawdopodobieństwo, że użytkownik wirtualny uruchamia dany test w scenariuszu testu obciążenia. Na przykład: 20% szansy do uruchomienia a i 80% szansy do uruchomienia TestB. Model testu mieszanego powinien odzwierciedlać cele testu w konkretnym scenariuszu.|
|Test mieszany|Test mieszany to wybór testów wydajności sieci Web i jednostek, które stanowią scenariusz, oraz rozkładu tych testów.|
|Mieszanie sieci|Symuluje, że użytkownicy wirtualną uzyskują dostęp do witryny sieci Web za pomocą różnych połączeń sieciowych. Mieszanie sieciowe oferuje opcje, które obejmują sieć LAN, modem kablowy i inne opcje.|

Scenariusz ma kilka innych właściwości, które można edytować za pomocą **Edytor testu obciążeniowego**. Aby uzyskać więcej informacji, zobacz [właściwości scenariusza testu obciążenia](../test/load-test-scenario-properties.md).

## <a name="tasks"></a>Zadania

|Zadania|Skojarzone tematy|
|-|-----------------------|
|**W scenariuszu należy dodać sztuczną interakcję człowieka:** Czasy reakcji służą do symulowania zachowań ludzi, które powodują, że osoby czekają na interakcję z witryną sieci Web. Czasy reakcji występują między żądaniami w teście wydajności sieci Web i między iteracjami testu w scenariuszu testu obciążenia. Użycie czasów reakcji w teście obciążenia może być przydatne podczas tworzenia bardziej precyzyjnych symulacji obciążenia.|-   [Edytowanie czasów reakcji w celu symulowania opóźnień interakcji z witryną sieci Web](../test/edit-think-times-in-load-test-scenarios.md)|
|**Określ liczbę wirtualnych użytkowników w danym scenariuszu:** Można skonfigurować właściwości wzorca obciążenia, aby określić sposób, w jaki symulowane obciążenie użytkownika jest dostosowywane podczas testu obciążenia. Uzyskasz trzy wbudowane wzorce obciążeń: stałe, krok i oparty na celach. Wybór wzorca obciążenia i dostosowanie właściwości do odpowiednich poziomów dla celów testów obciążenia.|-   [Edytuj wzorce obciążenia, aby modelować aktywność użytkownika wirtualnego](../test/edit-load-patterns-to-model-virtual-user-activities.md)|
|**Skonfiguruj prawdopodobieństwo uruchomienia przez użytkownika wirtualnego testu w scenariuszu:** Możesz użyć testu mieszanego, który określa prawdopodobieństwo, że użytkownik wirtualny uruchamia dany test w scenariuszu testu obciążenia. Dzięki temu można bardziej realistycznie symulowanie obciążenia. Zamiast tylko jedego przepływu pracy za pośrednictwem aplikacji, może mieć wiele przepływów pracy, który jest większym zbliżeniem tego jak użytkownicy końcowi są wzajemne powiązani ze swoimi aplikacjami.|-   [edytować modele mieszane](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)|
|**Dodaj lub Usuń test wydajności sieci Web lub testów jednostkowych ze scenariusza testu obciążenia:** Możesz dodać lub usunąć test wydajności sieci Web lub testów jednostkowych z testu obciążenia w scenariuszu. Test obciążenia zawiera jeden lub więcej scenariuszy, z których każdy zawiera co najmniej jeden test wydajności sieci Web lub testy jednostkowe.|-   [edytować test mieszany](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)|
|**Skonfiguruj żądany miks sieci dla danego scenariusza:** W przypadku korzystania z sieci mieszanej można bardziej realistycznie symulować obciążenie sieci w scenariuszu testu obciążenia. Obciążenie jest generowane przy użyciu heterogenicznej mieszanki typów sieci zamiast jednego typu sieci. Należy utworzyć bliższe przybliżenie, w jaki sposób użytkownicy końcowi współpracują z aplikacjami. Model mieszany sieci powinien odzwierciedlać cele tego scenariusza.|-   [Określ typy sieci wirtualnych](../test/specify-virtual-network-types-in-a-load-test-scenario.md)|
|**Wybierz odpowiedni miks przeglądarki internetowej dla danego scenariusza:** Korzystając z przeglądarki mieszanej, można bardziej realistycznie symulować obciążenia sieci Web w scenariuszu testu obciążenia. Obciążenie jest generowane przy użyciu heterogenicznej kombinacji przeglądarek zamiast jednej przeglądarki. Tworzysz bliższe przybliżenie przeglądarek, które będą używane z aplikacjami.|-   [określić typów przeglądarek sieci Web](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md)|
|**Skonfiguruj ustawienia iteracji testu dla Twojego scenariusza:** Można edytować scenariusz testu obciążenia, aby skonfigurować ustawienia iteracji testu przy użyciu Edytor testu obciążeniowego i okno Właściwości. Domyślnie scenariusz jest ustawiany bez maksymalnej iteracji testu. Opcjonalnie można skonfigurować maksymalną liczbę iteracji w scenariuszu i czas ich wstrzymywania między nimi.|-   [skonfigurować iteracje testu dla scenariuszy](../test/configure-test-iterations-in-a-load-test-scenario.md)|
|**Skonfiguruj ustawienia opóźnień dla scenariusza:** Przy użyciu **Edytor testu obciążeniowego** i okna **Właściwości** można określić opóźnienie przed rozpoczęciem scenariusza w teście obciążenia. Przykładem sytuacji, w której możesz chcieć użyć właściwości **czas rozpoczęcia opóźnienia** , jeśli potrzebujesz jednego scenariusza, aby rozpocząć tworzenie elementów, które są używane w innym scenariuszu. Można opóźnić scenariusz zużywający, aby umożliwić tworzenie w scenariuszu tworzenia danych.|-   [opóźnienia uruchamiania scenariusza Configureng](../test/configure-scenario-start-delays.md)|
|**Określ maszyny zdalne do użycia w scenariuszu testu obciążenia:** Po utworzeniu testu obciążenia można edytować właściwości scenariusza testu obciążenia, aby wskazać, którzy agenci testowi mają dołączać. Aby uzyskać więcej informacji, zobacz [kontrolerów testów i agentów testowych](configure-test-agents-and-controllers-for-load-tests.md).|-   [: Określanie agentów testowych do użycia](../test/how-to-specify-test-agents-to-use-in-load-test-scenarios.md)|

## <a name="see-also"></a>Zobacz także

- [Edytuj testy obciążenia](../test/edit-load-tests.md)
- [Właściwości scenariusza testów obciążenia](../test/load-test-scenario-properties.md)
