---
title: Tworzenie karty danych diagnostycznych do testowania
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter [Visual Studio ALM]
- Diagnostic Data Adapter
ms.assetid: b0b53fae-7007-4ad9-a604-21685937622f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2eadce12890e483f1b1c7aafccb61d9a6ee28e3a
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880302"
---
# <a name="create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine"></a>Tworzenie karty danych diagnostycznych w celu zbierania danych niestandardowych lub wpładowynia na maszynę testową

Można chcieć tworzyć własne adaptery danych diagnostycznych do zbierania danych, gdy zostanie uruchomiony test lub potrzeba wpłynąć na maszynę testową, jako część testu. Na przykład należy zebrać pliki dziennika, które są tworzone przez testowaną aplikację i dołączyć je do wyników testu lub należy uruchomić testy przy ograniczonym miejscu na dysku na komputerze. Za pomocą interfejsów API dostarczonych w programie Visual Studio Enterprise, można napisać kod do wykonywania zadań w określonych punktach w przebiegu testu. Na przykład można wykonywać zadania po rozpoczęciu przebiegu testowego, przed i po poszczególnych testach oraz po zakończeniu przebiegu testowego.

::: moniker range="vs-2017"
Można dostarczyć domyślne dane wejściowe do niestandardowego adaptera danych diagnostycznych przy użyciu pliku ustawień konfiguracji. Na przykład może dostarczyć informacji na temat lokalizacji pliku do zebrania i dołączenia do wyników testu lub ile miejsca ma pozostać w systemie. Dane te można skonfigurować dla wszystkich ustawień testu, które są tworzone. Może być wyświetlany i edytowany za pomocą domyślnego edytora dostarczonego z Microsoft Test Manager lub można utworzyć własną kontrolę użytkownika do użycia jako edytor. Wszelkie zmiany wprowadzone do konfiguracji adaptera w edytorze są przechowywane z ustawieniami testu.
::: moniker-end

::: moniker range=">=vs-2019"
Można dostarczyć domyślne dane wejściowe do niestandardowego adaptera danych diagnostycznych przy użyciu pliku ustawień konfiguracji. Na przykład może dostarczyć informacji na temat lokalizacji pliku do zebrania i dołączenia do wyników testu lub ile miejsca ma pozostać w systemie. Dane te można skonfigurować dla wszystkich ustawień testu, które są tworzone. Można utworzyć własną kontrolę użytkownika do użycia jako edytor. Wszelkie zmiany wprowadzone do konfiguracji adaptera w edytorze są przechowywane z ustawieniami testu.
::: moniker-end

Jeśli korzystasz z testów z programu Visual Studio, należy ustawić te ustawienia testu, aby były aktywne. Aby uzyskać więcej informacji o ustawieniach testu, zobacz [Zbieranie informacji diagnostycznych przy użyciu ustawień testu](../test/collect-diagnostic-information-using-test-settings.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="tasks"></a>Zadania

Użyj następujących tematów pomocnych przy tworzeniu Adapterów danych diagnostycznych:

|Zadania|Skojarzone tematy|
|-|-----------------------|
|**Tworzenie karty danych diagnostycznych:** Należy utworzyć kartę danych diagnostycznych, tworząc bibliotekę klas, a następnie użyj interfejsów API karty danych diagnostycznych do zbierania informacji, które chcesz lub wpływ na system testowy, który jest używany do uruchamiania testów.|-   [Jak: Tworzenie karty danych diagnostycznych](../test/how-to-create-a-diagnostic-data-adapter.md)|
|**Wybranie niestandardowej karty danych diagnostycznych do użycia podczas uruchamiania testów:** Można wybrać kartę danych diagnostycznych do użycia w ustawieniach testu, tak aby karta była używana podczas uruchamiania testów.|-   [Zbieranie danych diagnostycznych podczas testowania (plany testów platformy Azure)](/azure/devops/test/collect-diagnostic-data?view=vsts)<br />-   [Zbieranie danych diagnostycznych w testach ręcznych (plany testów platformy Azure)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)|

## <a name="see-also"></a>Zobacz też

- [Zbieranie informacji diagnostycznych przy użyciu ustawień testu](../test/collect-diagnostic-information-using-test-settings.md)
