---
title: Tworzenie adaptera danych diagnostycznych do testowania
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter [Visual Studio ALM]
- Diagnostic Data Adapter
ms.assetid: b0b53fae-7007-4ad9-a604-21685937622f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 800e866e2bfa915590060b09a98539533460bed3
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55928481"
---
# <a name="create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine"></a>Tworzenie adaptera danych diagnostycznych do zbierania danych niestandardowych lub wpływać na komputer testowy

Można chcieć tworzyć własne adaptery danych diagnostycznych do zbierania danych, gdy zostanie uruchomiony test lub potrzeba wpłynąć na maszynę testową, jako część testu. Na przykład należy zebrać pliki dziennika, które są tworzone przez testowaną aplikację i dołączyć je do wyników testu lub należy uruchomić testy przy ograniczonym miejscu na dysku na komputerze. Za pomocą interfejsów API dostarczonych w ramach programu Visual Studio Enterprise, można napisać kod do wykonywania zadań w określonych punktach w przebiegu testowym. Na przykład można wykonywać zadania po rozpoczęciu przebiegu testowego, przed i po poszczególnych testach oraz po zakończeniu przebiegu testowego.

Można dostarczyć domyślne dane wejściowe do niestandardowego adaptera danych diagnostycznych przy użyciu pliku ustawień konfiguracji. Na przykład może dostarczyć informacji na temat lokalizacji pliku do zebrania i dołączenia do wyników testu lub ile miejsca ma pozostać w systemie. Dane te można skonfigurować dla wszystkich ustawień testu, które są tworzone. Mogą być wyświetlane i edytowane przy użyciu domyślnego edytora dostarczane z Microsoft Test Manager lub utworzyć własną kontrolkę użytkownika do używania jako edytora. Wszelkie zmiany wprowadzone do konfiguracji adaptera w edytorze są przechowywane z ustawieniami testu.

Jeśli używasz testów z programu Visual Studio, musisz ustawić te ustawienia testów, aby być aktywne. Aby uzyskać więcej informacji na temat ustawień testowych, zobacz [zbieranie informacji diagnostycznych przy użyciu ustawień testu](../test/collect-diagnostic-information-using-test-settings.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="tasks"></a>Zadania

Użyj następujących tematów pomocnych przy tworzeniu Adapterów danych diagnostycznych:

|Zadania|Skojarzone tematy|
|-|-----------------------|
|**Tworzenie adaptera danych diagnostycznych:** Tworzenie adaptera danych diagnostycznych, tworząc bibliotekę klas, a następnie zebrać informacje lub mieć wpływ na system testowy, który jest używany do uruchamiania testów za pomocą interfejsu API adaptera danych diagnostycznych.|-   [Jak: Tworzenie adaptera danych diagnostycznych](../test/how-to-create-a-diagnostic-data-adapter.md)|
|**Wybranie niestandardowego adaptera danych diagnostycznych do użycia gdy testy są uruchamiane:** Tak, że karta jest używana podczas uruchamiania testów, można wybrać kartę danych diagnostycznych, w której do użycia w ustawieniach testu.|-   [Zbieranie danych diagnostycznych podczas testowania (planów testowych platformy Azure)](/azure/devops/test/collect-diagnostic-data?view=vsts)<br />-   [Zbieranie danych diagnostycznych podczas wykonywania testów ręcznych (planów testowych platformy Azure)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)|

## <a name="see-also"></a>Zobacz także

- [Zbieranie informacji diagnostycznych za pomocą ustawień testów](../test/collect-diagnostic-information-using-test-settings.md)