---
title: Tworzenie adaptera danych diagnostycznych na potrzeby testowania
description: Dowiedz się, jak napisać kod do wykonywania zadań w określonych punktach w przebiegu testowym przy użyciu interfejsów API udostępnionych w Visual Studio Enterprise.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Diagnostic Data Adapter [Visual Studio ALM]
- Diagnostic Data Adapter
ms.assetid: b0b53fae-7007-4ad9-a604-21685937622f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: fe1adfc62e0b8b9045ec87c1a78cdd56412ff320
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964475"
---
# <a name="create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine"></a>Tworzenie adaptera danych diagnostycznych w celu zbierania danych niestandardowych lub wpływania na maszynę testową

Można chcieć tworzyć własne adaptery danych diagnostycznych do zbierania danych, gdy zostanie uruchomiony test lub potrzeba wpłynąć na maszynę testową, jako część testu. Na przykład należy zebrać pliki dziennika, które są tworzone przez testowaną aplikację i dołączyć je do wyników testu lub należy uruchomić testy przy ograniczonym miejscu na dysku na komputerze. Korzystając z interfejsów API udostępnianych w Visual Studio Enterprise, można napisać kod do wykonywania zadań w określonych punktach w przebiegu testu. Na przykład można wykonywać zadania po rozpoczęciu przebiegu testowego, przed i po poszczególnych testach oraz po zakończeniu przebiegu testowego.

::: moniker range="vs-2017"
Można dostarczyć domyślne dane wejściowe do niestandardowego adaptera danych diagnostycznych przy użyciu pliku ustawień konfiguracji. Na przykład może dostarczyć informacji na temat lokalizacji pliku do zebrania i dołączenia do wyników testu lub ile miejsca ma pozostać w systemie. Dane te można skonfigurować dla wszystkich ustawień testu, które są tworzone. Można go wyświetlać i edytować przy użyciu domyślnego edytora dostępnego w Microsoft Test Manager lub można utworzyć własną kontrolkę użytkownika, która będzie używana jako edytor. Wszelkie zmiany wprowadzone do konfiguracji adaptera w edytorze są przechowywane z ustawieniami testu.
::: moniker-end

::: moniker range=">=vs-2019"
Można dostarczyć domyślne dane wejściowe do niestandardowego adaptera danych diagnostycznych przy użyciu pliku ustawień konfiguracji. Na przykład może dostarczyć informacji na temat lokalizacji pliku do zebrania i dołączenia do wyników testu lub ile miejsca ma pozostać w systemie. Dane te można skonfigurować dla wszystkich ustawień testu, które są tworzone. Można utworzyć własną kontrolkę użytkownika, która będzie używana jako edytor. Wszelkie zmiany wprowadzone do konfiguracji adaptera w edytorze są przechowywane z ustawieniami testu.
::: moniker-end

Jeśli uruchamiasz testy z programu Visual Studio, musisz ustawić te ustawienia testu jako aktywne. Aby uzyskać więcej informacji na temat ustawień testowych, zobacz [zbieranie informacji diagnostycznych przy użyciu ustawień testu](../test/collect-diagnostic-information-using-test-settings.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="tasks"></a>Zadania

Użyj następujących tematów pomocnych przy tworzeniu Adapterów danych diagnostycznych:

|Zadania|Skojarzone tematy|
|-|-----------------------|
|**Tworzenie adaptera danych diagnostycznych:** Utworzenie adaptera danych diagnostycznych przez utworzenie biblioteki klas, a następnie użycie interfejsów API adaptera danych diagnostycznych do zbierania żądanych informacji lub wpływu na system testowy używany do uruchamiania testów.|-   [Instrukcje: Tworzenie adaptera danych diagnostycznych](../test/how-to-create-a-diagnostic-data-adapter.md)|
|**Wybieranie niestandardowego adaptera danych diagnostycznych do użycia podczas uruchamiania testów:** Możesz wybrać, które karty danych diagnostycznych mają być używane dla ustawień testu, aby karta była używana podczas uruchamiania testów.|-   [Zbieraj dane diagnostyczne podczas testowania (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts&preserve-view=true)<br />-   [Zbieranie danych diagnostycznych w testach ręcznych (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts&preserve-view=true)|

## <a name="see-also"></a>Zobacz też

- [Zbieranie informacji diagnostycznych za pomocą ustawień testu](../test/collect-diagnostic-information-using-test-settings.md)