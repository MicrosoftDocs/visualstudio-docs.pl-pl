---
title: Określanie typów sieci wirtualnych w scenariuszu testu obciążenia
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, scenarios
- load tests, adding networks
- load tests, removing networks
- load tests, virtual networks
- network mix
ms.assetid: 3c4f7874-081a-4ec4-9510-4d6d7d863a11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 60fa2bd38f3d7e594e9af7ba8ec544518bdbb920
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115301"
---
# <a name="specify-virtual-network-types-in-a-load-test-scenario"></a>Określanie typów sieci wirtualnej w scenariuszu testu obciążenia

*Mix sieci* umożliwia bardziej realistyczne symulowanie obciążenia w scenariuszu testu obciążenia. Obciążenie jest generowane przy użyciu niejednorodnej kombinacji typów sieci zamiast jednego typu sieci. Tworzenie bliższe przybliżenie sposobu interakcji użytkowników końcowych z aplikacjami.

Połączenie sieciowe określa prawdopodobieństwo uruchomienia przez użytkownika wirtualnego danego *profilu sieciowego*. Profil sieciowy jest symulacją przepustowości sieci w warstwie aplikacji. Nie symuluje opóźnienia.

Podczas tworzenia testu obciążenia można symulować, że obciążenie jest generowane za pośrednictwem więcej niż jednego typu połączenia sieciowego. Sieć oferuje kilka typów sieci. Symulowane są różne sieci. Po wybraniu opcji, `Cable-DSL 1.5Mbps`takiej jak , czas oczekiwania są wstrzykiwane do testu, aby symulować wybraną przepustowość.

Mix sieci działa jak inne opcje mix. Typ sieci jest wybierany losowo skojarzony z użytkownikiem wirtualnym na podstawie kombinacji sieciowej. Testy tego użytkownika są uruchamiane przy użyciu określonego typu sieci, na podstawie prawdopodobieństwa określonego w mieszance.

Po określeniu kombinacji sieci można dodawać i usuwać typy sieci. Można również zmienić dystrybucję miksu sieciowego za pomocą formantu mieszania.

Formant miksu umożliwia łatwe dostosowanie dystrybucji sieci w scenariuszu.

Aby uzyskać więcej informacji, zobacz [Informacje o formancie mieszania](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="true-network-emulation"></a>Prawdziwa emulacja sieci

Visual Studio używa emulacji sieci true oparte na oprogramowaniu dla wszystkich typów testów, w tym testów obciążenia. Prawdziwa emulacja sieci symuluje warunki sieciowe poprzez bezpośrednią manipulację pakietami sieciowymi. Prawdziwy emulator sieci może emulować zachowanie zarówno sieci przewodowych, jak i bezprzewodowych przy użyciu niezawodnego łącza fizycznego, takiego jak Ethernet. Następujące atrybuty sieci są włączone do emulacji sieci true:

- Czas podróży w obie strony przez sieć (opóźnienie)

- Ilość dostępnej przepustowości

- Zachowanie kolejkowania

- Utrata pakietów

- Ponowne kolejność pakietów

- Propagacja błędów.

Prawdziwa emulacja sieci zapewnia również elastyczność filtrowania pakietów sieciowych na podstawie adresów IP lub protokołów, takich jak TCP, UDP i ICMP.

Prawdziwa emulacja sieci może być używana przez programistów i testerów aplikacji opartych na sieci do emulowania żądanego środowiska testowego, oceny wydajności, przewidywania wpływu zmian lub podejmowania decyzji dotyczących optymalizacji technologii. W porównaniu do łóżek testowych sprzętu, prawdziwa emulacja sieci jest znacznie tańszym i bardziej elastycznym rozwiązaniem.

## <a name="to-add-new-networks-to-a-scenario"></a>Aby dodać nowe sieci do scenariusza

1. Podczas procesu określania koszyka sieciowego dla scenariusza wybierz pozycję **Dodaj**.

     Nowy wpis sieci zostanie dodany do siatki.

    > [!NOTE]
    > Aby wyświetlić okno dialogowe **Edytowanie koszyka sieciowego,** kliknij prawym przyciskiem myszy istniejący scenariusz, a następnie wybierz polecenie **Edytuj miks sieciowy**.

2. W kolumnie **Typ sieci** wybierz strzałkę dla nowego wpisu. Wybierz żądany typ sieci.

3. (Opcjonalnie) Wyreguluj formant miksu, aby określić rozkład testowy. Aby uzyskać więcej informacji, zobacz [Informacje o formancie mieszania](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

4. Po zakończeniu dodawania sieci wybierz przycisk **OK**.

## <a name="to-remove-networks-from-a-scenario"></a>Aby usunąć sieci ze scenariusza

1. Otwórz test obciążenia.

2. Kliknij prawym przyciskiem myszy scenariusz, z którego chcesz usunąć sieć, a następnie wybierz polecenie **Edytuj miks sieciowy**. Zostanie wyświetlone okno dialogowe **Edytowanie koszyka** sieciowego.

3. Wybierz sieć w siatce, a następnie wybierz pozycję **Usuń**.

4. (Opcjonalnie) Wyreguluj formant miksu, aby określić rozkład testowy. Aby uzyskać więcej informacji, zobacz [Informacje o formancie mieszania](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

5. Po zakończeniu usuwania sieci wybierz przycisk **OK**.

## <a name="about-the-mix-control"></a>Informacje o kontroli mieszania

Formant mix umożliwia dostosowanie procent obciążenia, który jest rozdzielany między testy, typy przeglądarki lub typy sieci w scenariuszu testu obciążenia. Aby dostosować wartości procentowe, przesuń suwaki. Dostosowanie kombinacji dla typów sieci określa prawdopodobieństwo, że użytkownik wirtualny uruchomi określony profil sieciowy w scenariuszu testu obciążenia.

Podczas przenoszenia suwaka zmieniają się wartości procentowe wszystkich dostępnych elementów. Jeśli masz więcej niż dwa elementy, kwota dodana lub wyrównana jest rozłożona równomiernie między inne elementy. Istnieje możliwość zastąpienia tego zachowania. Jeśli zaznaczysz pole wyboru w kolumnie blokady dla określonego elementu, zostanie zablokowana określona wartość procentowa dla tego elementu. Następnie po przeniesieniu suwaka kwota dodania lub usunięcia jest stosowana tylko do pozostałych odblokowanych elementów.

**Przycisk Rozłóż** służy do równego przydzielania wartości procentowych między wszystkie elementy. Na przykład jeśli masz trzy elementy, wybranie opcji **Rozmieść** ustawia wartości procentowe na 34, 33 i 33.

> [!WARNING]
> Przycisk **Rozłóż** zastępuje wszystkie elementy, które są zablokowane.

Możliwe jest również wpisanie wartości procentowych **%** bezpośrednio w kolumnie zamiast za pomocą suwaków. Jeśli wprowadzisz wartość procentową bezpośrednio, pozostałe elementy nie zostaną automatycznie dostosowane.

> [!NOTE]
> Suwaki są wyłączone, gdy suma nie sumuje się do 100%, **%** lub gdy wartości procentowe wprowadzone w kolumnie są dziesiętne.

Podczas ręcznego wprowadzania wartości procentowych należy upewnić się, że suma wszystkich elementów wynosi 100%. Po zapisaniu mieszanki, jeśli suma nie jest 100%, zostanie wyświetlony monit o zaakceptowanie wartości procentowych w ich stanie lub o ich powrót i dostosowanie. Jeśli zdecydujesz się je zaakceptować w taki sposób, w jaki są, będą one proporcjonalnie do 100%.  Na przykład, jeśli masz dwa elementy i ręcznie ustawisz je na 80% i 40%, pierwszy element zostanie ustawiony na 66,67% (80 podzielonych przez 120), a drugi element zostanie ustawiony na 33,33% (40 podzielonych przez 120).
