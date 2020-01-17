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
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115301"
---
# <a name="specify-virtual-network-types-in-a-load-test-scenario"></a>Określanie typów sieci wirtualnych w scenariuszu testu obciążenia

*Mieszanie sieci* umożliwia symulowanie obciążenia w scenariuszu testu obciążenia. Obciążenie jest generowane przy użyciu heterogenicznej mieszanki typów sieci zamiast jednego typu sieci. Należy utworzyć bliższe przybliżenie, w jaki sposób użytkownicy końcowi współpracują z aplikacjami.

Mieszanie sieci określa prawdopodobieństwo, że użytkownik wirtualny uruchomił dany *profil sieciowy*. Profil sieci to symulacja przepustowości sieci w warstwie aplikacji. Nie symuluje opóźnienia.

Podczas tworzenia testu obciążenia warto zasymulować, że obciążenie jest generowane przez więcej niż jeden typ połączenia sieciowego. Mieszanie sieciowe oferuje kilka typów sieci. Różne sieci są symulowane. Po wybraniu opcji, takiej jak `Cable-DSL 1.5Mbps`, czasy oczekiwania są wstrzykiwane do testu, aby symulować wybraną przepustowość.

Mieszanie sieciowe działa jak inne opcje mieszane. Typ sieci jest wybierany losowo z użytkownikiem wirtualnym w oparciu o mieszanie sieciowe. Testy tego użytkownika są uruchamiane przy użyciu określonego typu sieci, na podstawie prawdopodobieństwa określonego w kombinacji.

Po określeniu kombinacji sieci można dodawać i usuwać typy sieci. Możesz również zmienić dystrybucję mieszanych sieci przy użyciu kontrolki mieszanej.

Formant mieszany umożliwia łatwe dostosowanie dystrybucji sieci w scenariuszu.

Aby uzyskać więcej informacji, zobacz [informacje o formancie mieszanego](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="true-network-emulation"></a>Emulacja prawdziwej sieci

Program Visual Studio używa emulacji sieci opartej na oprogramowaniu dla wszystkich typów testów, w tym testów obciążenia. Emulacja sieci true symuluje warunki w sieci przez bezpośrednią manipulację pakietami sieciowymi. Emulator sieci może emulować zachowanie zarówno sieci przewodowych i bezprzewodowych, za pomocą niezawodnego łącza fizycznego, takiego jak Ethernet. Następujące atrybuty sieci są włączone w prawdziwą emulację sieci:

- Czas błądzenia w sieci (opóźnienie)

- Dostępna przepustowość

- Zachowanie usługi kolejkowania wiadomości

- Utrata pakietów

- Zmiana kolejności pakietów

- Propagacje błędów.

Emulacja sieci true również zapewnia elastyczność filtrowania pakietów sieciowych na podstawie adresów IP lub protokołów, takich jak TCP, UDP i ICMP.

Emulacja sieci może być używana przez deweloperów aplikacji i testerów do emulowania pożądanego środowiska testowego, oceny wydajności, przewidywania wpływu zmian lub podejmowania decyzji dotyczących optymalizacji technologii. W porównaniu z testami sprzętu, emulacji sieci true jest rozwiązaniem znacznie tańszym i bardziej elastycznym.

## <a name="to-add-new-networks-to-a-scenario"></a>Aby dodać nowe sieci do scenariusza

1. Podczas procesu określania mieszanki sieciowej dla scenariusza wybierz pozycję **Dodaj**.

     Do siatki zostanie dodany nowy wpis sieciowy.

    > [!NOTE]
    > Aby wyświetlić okno dialogowe **Edytowanie miksu sieci** , kliknij prawym przyciskiem myszy istniejący scenariusz, a następnie wybierz polecenie **Edytuj mieszanie sieciowe**.

2. W kolumnie **Typ sieci** wybierz strzałkę dla nowego wpisu. Wybierz żądany typ sieci.

3. (Opcjonalnie) Dostosuj kontroli mieszany, aby określić rozkład testu. Aby uzyskać więcej informacji, zobacz [informacje o formancie mieszanego](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

4. Po zakończeniu dodawania sieci wybierz **przycisk OK**.

## <a name="to-remove-networks-from-a-scenario"></a>Aby usunąć sieci z scenariusza

1. Otwórz test obciążenia.

2. Kliknij prawym przyciskiem myszy scenariusz, z którego chcesz usunąć sieć, a następnie wybierz pozycję **Edytuj mieszanie sieciowe**. Zostanie wyświetlone okno dialogowe **Edytowanie sieci mieszanej** .

3. Wybierz sieć w siatce, a następnie wybierz pozycję **Usuń**.

4. (Opcjonalnie) Dostosuj kontroli mieszany, aby określić rozkład testu. Aby uzyskać więcej informacji, zobacz [informacje o formancie mieszanego](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

5. Po zakończeniu usuwania sieci wybierz **przycisk OK**.

## <a name="about-the-mix-control"></a>Informacje o formancie mieszany

Kontrolka mieszana umożliwia dostosowanie wartości procentowej obciążenia między testami, typami przeglądarek lub typami sieci w scenariuszu testu obciążenia. Aby dostosować wartości procentowe, przesuń suwaki. Dostosowanie mieszanki dla typów sieci określa prawdopodobieństwo, że użytkownik wirtualny uruchamiający konkretny profil sieci w scenariuszu testu obciążenia.

Podczas przesuwania suwaka, zmień wartości procentowe wszystkich dostępnych elementów. Jeśli masz więcej niż dwa elementy, kwota, dodawanie lub usuwanie jest rozłożona równomiernie innych elementów. Istnieje możliwość zastąpienia tego zachowania. Jeśli zaznaczysz pole wyboru w kolumnie blokady dla określonego elementu, można zablokować określoną wartość procentową wartość dla tego elementu. Następnie podczas przesuwania suwaka, kwota, dodawanie lub usuwanie są stosowane tylko do wszystkie pozostałe elementy odblokowane.

**Dystrybucji** przycisk służy do przydzielania wartości procentowe równomiernie wszystkie elementy. Na przykład, jeśli masz trzy elementy, wybierając **dystrybucji** ustawia wartości procentowe 34, 33 i 33.

> [!WARNING]
> **Dystrybucji** przycisk zastępuje wszystkie elementy, które są zablokowane.

Istnieje również możliwość na typ wartości procentowe bezpośrednio do **%** kolumny, a nie za pomocą suwaków. Jeśli bezpośrednio wprowadzasz wartość procentową, inne elementy nie skoryguje automatycznie.

> [!NOTE]
> Suwaki są wyłączone, gdy łączny nie powoduje dodania do 100% lub wartości procentowe są wprowadzane do **%** kolumny są liczbę miejsc dziesiętnych.

Po wprowadzeniu wartości procentowe ręcznie, należy pamiętać, że sumę wszystkich elementów wynosi 100%. W przypadku zapisania mieszanki, jeśli suma nie jest równa 100%, zostanie wyświetlony monit o zaakceptowanie wartości procentowych w miarę ich lub przywrócenia i dostosowania. Jeśli zdecydujesz się je zaakceptować, ponieważ są one, będzie naliczana proporcjonalnie do 100%.  Na przykład jeśli masz dwa elementy, a następnie ręcznie ustawić je do 80% i 40%, pierwszy element zostanie ustawione na % 66,67 (80 podzielona przez 120), a drugi element zostanie ustawione na % 33,33 (40 podzielona przez 120).
