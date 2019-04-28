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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8444fa5910658ab92643b2110483efc059560674
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62990653"
---
# <a name="specify-virtual-network-types-in-a-load-test-scenario"></a>Określanie typów sieci wirtualnych w scenariuszu testu obciążenia

*Mieszany profil sieciowy* umożliwia realistycznie symulować obciążenia więcej w scenariuszu testu obciążenia. Obciążenie jest generowane przy użyciu typów siecie zamiast jednego typu sieci. Możesz utworzyć zbliżenie tego jak użytkownicy końcowi są wzajemne powiązani ze swoimi aplikacjami.

Mieszany profil sieciowy określa prawdopodobieństwo, że użytkownik wirtualny uruchomi dany *sieci profilu*. Profil sieciowy jest symulacja przepustowości sieci w warstwie aplikacji. Go nie symulowania opóźnienia.

Po utworzeniu testu obciążenia, możesz chcieć symulację obciążenia jest generowany przez więcej niż jeden typ połączenia sieciowego. Mieszany profil sieciowy oferuje kilka typów sieci. Symulowani są różnych sieci. Po wybraniu opcji przykład `Cable-DSL 1.5Mbps`, czasy oczekiwania są wstrzykiwane do testu, aby zasymulować przepustowości wybranego.

Mieszany profil sieciowy działa jak inne opcje mieszanego. Typ sieci jest zaznaczone losowo skojarzone z użytkownika wirtualnego w oparciu mieszany profil sieciowy. Ten użytkownik testy są uruchamiane, przy użyciu określonego typu sieci, na podstawie prawdopodobieństwa, które określiłeś w zestawie.

Po określeniu mieszanego profilu sieciowego można dodać i usunąć typy sieci. Można również zmienić dystrybucji mieszany profil sieciowy przy użyciu formantu mieszanego.

Kontrolka mieszanego pozwala łatwo dopasować rozkład sieci w scenariuszu.

Aby uzyskać więcej informacji, zobacz [informacje o formancie mieszanego](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="true-network-emulation"></a>Emulacja sieci true

Visual Studio używa emulacja sieciowej true bazującej na oprogramowanie dla wszystkich typów testu, w tym testy obciążenia. Emulacja sieci true symuluje warunki w sieci przez bezpośrednią manipulację pakietami sieciowymi. Emulator sieci może emulować zachowanie zarówno sieci przewodowych i bezprzewodowych, za pomocą niezawodnego łącza fizycznego, takiego jak Ethernet. Następujące atrybuty sieci są włączone w prawdziwą emulację sieci:

- Czas błądzenia za pośrednictwem sieci (opóźnienie)

- Dostępna przepustowość

- Zachowanie usługi kolejkowania wiadomości

- Utrata pakietów

- Zmiana kolejności pakietów

- Propagacje błędów.

Emulacja sieci true również zapewnia elastyczność filtrowania pakietów sieciowych na podstawie adresów IP lub protokołów, takich jak TCP, UDP i ICMP.

Emulacja sieci TRUE może służyć przez deweloperów aplikacji opartej na sieci i testerów do emulowania pożądanego środowiska testowego, oceny wydajności, przewidywania wpływu zmian lub podejmowania decyzji dotyczących optymalizacji technologii. W porównaniu z testami sprzętu, emulacji sieci true jest rozwiązaniem znacznie tańszym i bardziej elastycznym.

## <a name="to-add-new-networks-to-a-scenario"></a>Umożliwia dodawanie nowych sieci do scenariusza

1. Podczas określania mieszany profil sieciowy dla scenariusza, wybierz **Dodaj**.

     Nowy wpis sieci zostanie dodany do siatki.

    > [!NOTE]
    > Aby wyświetlić **Edytuj mieszany profil sieciowy** okna dialogowego pole, kliknij prawym przyciskiem myszy istniejący scenariusz, a następnie wybierz **Edytuj mieszany profil sieciowy**.

2. W **typu sieci** kolumnę, wybierz strzałkę znajdującą się nowy wpis. Wybierz typ wybraną sieć.

3. (Opcjonalnie) Dostosuj kontroli mieszany, aby określić rozkład testu. Aby uzyskać więcej informacji, zobacz [informacje o formancie mieszanego](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

4. Po zakończeniu dodawania sieci wybierz **OK**.

## <a name="to-remove-networks-from-a-scenario"></a>Aby usunąć sieci ze scenariusza

1. Otwórz test obciążenia.

2. Kliknij prawym przyciskiem myszy scenariusza, z którego chcesz usunąć sieć, a następnie wybierz **Edytuj mieszany profil sieciowy**. **Edytuj mieszany profil sieciowy** zostanie wyświetlone okno dialogowe.

3. Wybierz sieć w siatce, a następnie wybierz **Usuń**.

4. (Opcjonalnie) Dostosuj kontroli mieszany, aby określić rozkład testu. Aby uzyskać więcej informacji, zobacz [informacje o formancie mieszanego](../test/specify-virtual-network-types-in-a-load-test-scenario.md).

5. Po zakończeniu usuwania sieci wybierz **OK**.

## <a name="about-the-mix-control"></a>Informacje o formancie mieszany

 Kontrolka mieszanego pozwala dostosować procent obciążenia, który jest rozproszona w ramach testów, typy przeglądarek i typy sieci w scenariuszu testu obciążenia. Aby dostosować wartości procentowych, przesuń suwaki. Dostosowywanie różnych typów sieci określa prawdopodobieństwo, że użytkownik wirtualny uruchomi profilu określonej sieci w scenariuszu testu obciążenia.

 Podczas przesuwania suwaka, zmień wartości procentowe wszystkich dostępnych elementów. Jeśli masz więcej niż dwa elementy, kwota, dodawanie lub usuwanie jest rozłożona równomiernie innych elementów. Istnieje możliwość zastąpienia tego zachowania. Jeśli zaznaczysz pole wyboru w kolumnie blokady dla określonego elementu, można zablokować określoną wartość procentową wartość dla tego elementu. Następnie podczas przesuwania suwaka, kwota, dodawanie lub usuwanie są stosowane tylko do wszystkie pozostałe elementy odblokowane.

 **Dystrybucji** przycisk służy do przydzielania wartości procentowe równomiernie wszystkie elementy. Na przykład, jeśli masz trzy elementy, wybierając **dystrybucji** ustawia wartości procentowe 34, 33 i 33.

> [!WARNING]
> **Dystrybucji** przycisk zastępuje wszystkie elementy, które są zablokowane.

 Istnieje również możliwość na typ wartości procentowe bezpośrednio do **%** kolumny, a nie za pomocą suwaków. Jeśli bezpośrednio wprowadzasz wartość procentową, inne elementy nie skoryguje automatycznie.

> [!NOTE]
> Suwaki są wyłączone, gdy łączny nie powoduje dodania do 100% lub wartości procentowe są wprowadzane do **%** kolumny są liczbę miejsc dziesiętnych.

Po wprowadzeniu wartości procentowe ręcznie, należy pamiętać, że sumę wszystkich elementów wynosi 100%. Po zapisaniu mieszany, jeśli suma nie jest w 100%, możesz zostanie wyświetlony monit o zaakceptowanie wartości procentowe są one, lub przejdź wstecz i zmieniaj je tak. Jeśli zdecydujesz się je zaakceptować, ponieważ są one, będzie naliczana proporcjonalnie do 100%.  Na przykład jeśli masz dwa elementy, a następnie ręcznie ustawić je do 80% i 40%, pierwszy element zostanie ustawione na % 66,67 (80 podzielona przez 120), a drugi element zostanie ustawione na % 33,33 (40 podzielona przez 120).