---
title: Określ typy sieci wirtualnych (testowanie obciążenia)
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
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
ms.openlocfilehash: b505ae281042264d909b72ff0f7911381a2d8ad8
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809875"
---
# <a name="specify-virtual-network-types-in-a-load-test-scenario"></a>Określanie typów sieci wirtualnych w scenariuszu testu obciążenia

*Mieszanie sieci* umożliwia symulowanie obciążenia w scenariuszu testu obciążenia. Obciążenie jest generowane przy użyciu heterogenicznej mieszanki typów sieci zamiast jednego typu sieci. Należy utworzyć bliższe przybliżenie, w jaki sposób użytkownicy końcowi współpracują z aplikacjami.

Mieszanie sieci określa prawdopodobieństwo, że użytkownik wirtualny uruchomił dany *profil sieciowy*. Profil sieci to symulacja przepustowości sieci w warstwie aplikacji. Nie symuluje opóźnienia.

Podczas tworzenia testu obciążenia warto zasymulować, że obciążenie jest generowane przez więcej niż jeden typ połączenia sieciowego. Mieszanie sieciowe oferuje kilka typów sieci. Różne sieci są symulowane. Po wybraniu opcji, takiej jak `Cable-DSL 1.5Mbps` , czasy oczekiwania są wstrzykiwane do testu, aby symulować wybraną przepustowość.

Mieszanie sieciowe działa jak inne opcje mieszane. Typ sieci jest wybierany losowo z użytkownikiem wirtualnym w oparciu o mieszanie sieciowe. Testy tego użytkownika są uruchamiane przy użyciu określonego typu sieci, na podstawie prawdopodobieństwa określonego w kombinacji.

Po określeniu kombinacji sieci można dodawać i usuwać typy sieci. Możesz również zmienić dystrybucję mieszanych sieci przy użyciu kontrolki mieszanej.

Formant mieszany umożliwia łatwe dostosowanie dystrybucji sieci w scenariuszu.

Aby uzyskać więcej informacji, zobacz [Informacje o kontrolce mieszanej](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="true-network-emulation"></a>Emulacja prawdziwej sieci

Program Visual Studio używa emulacji sieci opartej na oprogramowaniu dla wszystkich typów testów, w tym testów obciążenia. Emulacja sieci prawda symuluje warunki sieci przez bezpośrednie manipulowanie pakietami sieciowymi. Prawdziwy emulator sieci może emulować zachowanie zarówno sieci przewodowych, jak i bezprzewodowych, za pomocą niezawodnego łącza fizycznego, takiego jak Ethernet. Następujące atrybuty sieci są włączone w ramach prawdziwej emulacji sieci:

- Czas błądzenia w sieci (opóźnienie)

- Ilość dostępnej przepustowości

- Zachowanie kolejkowania

- Utrata pakietów

- Zmiana kolejności pakietów

- Propagacje błędów.

Emulacja sieci zapewnia również elastyczność filtrowania pakietów sieciowych na podstawie adresów IP lub protokołów, takich jak TCP, UDP i ICMP.

Emulacja sieci może być używana przez deweloperów aplikacji i testerów do emulowania pożądanego środowiska testowego, oceny wydajności, przewidywania wpływu zmian lub podejmowania decyzji dotyczących optymalizacji technologii. W porównaniu do Beds testu sprzętu prawdziwe Emulacja sieci to znacznie tańsze i bardziej elastyczne rozwiązanie.

## <a name="to-add-new-networks-to-a-scenario"></a>Aby dodać nowe sieci do scenariusza

1. Podczas procesu określania mieszanki sieciowej dla scenariusza wybierz pozycję **Dodaj**.

     Do siatki zostanie dodany nowy wpis sieciowy.

    > [!NOTE]
    > Aby wyświetlić okno dialogowe **Edytowanie miksu sieci** , kliknij prawym przyciskiem myszy istniejący scenariusz, a następnie wybierz polecenie **Edytuj mieszanie sieciowe**.

2. W kolumnie **Typ sieci** wybierz strzałkę dla nowego wpisu. Wybierz żądany typ sieci.

3. Obowiązkowe Dostosuj kontrolkę mieszanie, aby określić dystrybucję testu. Aby uzyskać więcej informacji, zobacz [Informacje o kontrolce mieszanej](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

4. Po zakończeniu dodawania sieci wybierz **przycisk OK**.

## <a name="to-remove-networks-from-a-scenario"></a>Aby usunąć sieci z scenariusza

1. Otwórz test obciążenia.

2. Kliknij prawym przyciskiem myszy scenariusz, z którego chcesz usunąć sieć, a następnie wybierz pozycję **Edytuj mieszanie sieciowe**. Zostanie wyświetlone okno dialogowe **Edytowanie sieci mieszanej** .

3. Wybierz sieć w siatce, a następnie wybierz pozycję **Usuń**.

4. Obowiązkowe Dostosuj kontrolkę mieszanie, aby określić dystrybucję testu. Aby uzyskać więcej informacji, zobacz [Informacje o kontrolce mieszanej](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

5. Po zakończeniu usuwania sieci wybierz **przycisk OK**.

## <a name="about-the-mix-control"></a>Informacje o kontrolce mieszanej

Kontrolka mieszana umożliwia dostosowanie wartości procentowej obciążenia między testami, typami przeglądarek lub typami sieci w scenariuszu testu obciążenia. Aby dostosować wartości procentowe, przesuń suwaki. Dostosowanie mieszanki dla typów sieci określa prawdopodobieństwo, że użytkownik wirtualny uruchamiający konkretny profil sieci w scenariuszu testu obciążenia.

Przesunięcie suwaka powoduje zmianę wartości procentowej wszystkich dostępnych elementów. Jeśli masz więcej niż dwa elementy, ilość dodawana lub usunięta jest dystrybuowana równomiernie między innymi elementami. Istnieje możliwość zastąpienia tego zachowania. W przypadku zaznaczenia pola wyboru w kolumnie blokada dla określonego elementu należy zablokować określoną wartość procentową tego elementu. Następnie po przesunięciu suwaka ilość dodawana lub usuwana jest stosowana tylko do wszystkich pozostałych odblokowanych elementów.

Przycisk **Dystrybuuj** służy do przydzielania wartości procentowych równomiernie między wszystkimi elementami. Na przykład jeśli masz trzy elementy, wybranie opcji **Dystrybuuj** ustawia wartości procentowe na 34, 33 i 33.

> [!WARNING]
> Przycisk **Dystrybuuj** zastępuje wszystkie elementy, które są zablokowane.

Można również wpisać wartości procentowe bezpośrednio w **%** kolumnie zamiast używać suwaków. Jeśli wprowadzisz wartość procentową bezpośrednio, pozostałe elementy nie zostaną dostosowane automatycznie.

> [!NOTE]
> Suwaki są wyłączone, gdy suma nie dodaje do 100%, lub gdy wartości procentowe wprowadzone do **%** kolumny są miejscami dziesiętnymi.

Po ręcznym wprowadzeniu wartości procentowych należy upewnić się, że suma wszystkich elementów wynosi 100%. W przypadku zapisania mieszanki, jeśli suma nie jest równa 100%, zostanie wyświetlony monit o zaakceptowanie wartości procentowych w miarę ich lub przywrócenia i dostosowania. Jeśli zdecydujesz się na ich zaakceptowanie, zostanie nadana proporcjonalnie do 100%.  Na przykład jeśli masz dwa elementy i ręcznie ustawisz je na 80% i 40%, pierwszy element zostanie ustawiony na 66,67% (80 podzielony przez 120), a drugi element zostanie ustawiony na 33,33% (40 podzielony przez 120).
