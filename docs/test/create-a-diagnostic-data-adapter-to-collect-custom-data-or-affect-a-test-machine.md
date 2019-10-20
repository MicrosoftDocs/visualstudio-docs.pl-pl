---
title: Tworzenie adaptera danych diagnostycznych na potrzeby testowania
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter [Visual Studio ALM]
- Diagnostic Data Adapter
ms.assetid: b0b53fae-7007-4ad9-a604-21685937622f
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1d518f911f076481e710176924036c6e3f37625e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665128"
---
# <a name="create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine"></a>Tworzenie adaptera danych diagnostycznych w celu zbierania danych niestandardowych lub wpływania na maszynę testową

Można chcieć tworzyć własne adaptery danych diagnostycznych do zbierania danych, gdy zostanie uruchomiony test lub potrzeba wpłynąć na maszynę testową, jako część testu. Na przykład należy zebrać pliki dziennika, które są tworzone przez testowaną aplikację i dołączyć je do wyników testu lub należy uruchomić testy przy ograniczonym miejscu na dysku na komputerze. Korzystając z interfejsów API udostępnianych w Visual Studio Enterprise, można napisać kod do wykonywania zadań w określonych punktach w przebiegu testu. Na przykład można wykonywać zadania po rozpoczęciu przebiegu testowego, przed i po poszczególnych testach oraz po zakończeniu przebiegu testowego.

Można dostarczyć domyślne dane wejściowe do niestandardowego adaptera danych diagnostycznych przy użyciu pliku ustawień konfiguracji. Na przykład może dostarczyć informacji na temat lokalizacji pliku do zebrania i dołączenia do wyników testu lub ile miejsca ma pozostać w systemie. Dane te można skonfigurować dla wszystkich ustawień testu, które są tworzone. Można go wyświetlać i edytować przy użyciu domyślnego edytora dostępnego w Microsoft Test Manager lub można utworzyć własną kontrolkę użytkownika, która będzie używana jako edytor. Wszelkie zmiany wprowadzone do konfiguracji adaptera w edytorze są przechowywane z ustawieniami testu.

Jeśli uruchamiasz testy z programu Visual Studio, musisz ustawić te ustawienia testu jako aktywne. Aby uzyskać więcej informacji na temat ustawień testowych, zobacz [zbieranie informacji diagnostycznych przy użyciu ustawień testu](../test/collect-diagnostic-information-using-test-settings.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="tasks"></a>Zadania

Użyj następujących tematów pomocnych przy tworzeniu Adapterów danych diagnostycznych:

|Zadania|Skojarzone tematy|
|-|-----------------------|
|**Tworzenie adaptera danych diagnostycznych:** Utworzenie adaptera danych diagnostycznych przez utworzenie biblioteki klas, a następnie użycie interfejsów API adaptera danych diagnostycznych do zbierania żądanych informacji lub wpływu na system testowy używany do uruchamiania testów.|-   [: Tworzenie adaptera danych diagnostycznych](../test/how-to-create-a-diagnostic-data-adapter.md)|
|**Wybieranie niestandardowego adaptera danych diagnostycznych do użycia podczas uruchamiania testów:** Możesz wybrać, które karty danych diagnostycznych mają być używane dla ustawień testu, aby karta była używana podczas uruchamiania testów.|-   [Zbieraj dane diagnostyczne podczas testowania (Azure test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts)<br />-   [zbierać dane diagnostyczne w testach ręcznych (Azure test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)|

## <a name="see-also"></a>Zobacz także

- [Zbieranie informacji diagnostycznych za pomocą ustawień testu](../test/collect-diagnostic-information-using-test-settings.md)