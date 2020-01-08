---
title: Wybieranie lokalizacji instalacji
description: Dowiedz się, jak w celu zmniejszenia miejsca zajmowanego przez instalację programu Visual Studio na dysku systemowym, zmieniając lokalizację pamięci podręcznej pobierania, składników udostępnionych, zestawy SDK i narzędzi na różnych dyskach. Na przykład Przenieś niektóre pliki z dysku C na dysk D.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- change installation locations for Visual Studio
- select an installation location for Visual Studio files
- move installation files to different drives
- use the D drive
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 3ea0651ee1cfde14d5ef7b422095707d8f81cb2f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590153"
---
# <a name="select-the-installation-locations-in-visual-studio"></a>Wybierz lokalizacje instalacji w programie Visual Studio

::: moniker range="vs-2019"

Możesz zmniejszyć zasięg instalacji programu Visual Studio na dysku systemowym, zmieniając lokalizację niektórych plików. W szczególności można użyć innej lokalizacji pamięci podręcznej pobierania, składników udostępnionych, zestawy SDK i pliki narzędzia.

::: moniker-end

::: moniker range="vs-2017"

**Nowość w wersji 15,7**: można zmniejszyć zasięg instalacji programu Visual Studio na dysku systemowym, zmieniając lokalizację niektórych plików. W szczególności można użyć innej lokalizacji pamięci podręcznej pobierania, składników udostępnionych, zestawy SDK i pliki narzędzia.

::: moniker-end

   > [!NOTE]
   > Istnieją pewne narzędzia i zestawy SDK, które mają różne reguły, w którym można zainstalować. Takie narzędzia i zestawy SDK są instalowane na dysku systemowym, nawet jeśli wybierz inną lokalizację.

Chcesz rozpocząć pracę? Poniżej przedstawiono sposób.

::: moniker range="vs-2017"

1. Po zainstalowaniu programu Visual Studio, wybierz **lokalizacje instalacji** kartę.

   ![Visual Studio 2017 — wybierz lokalizację instalacji](media/vs-installation-locations.png "Wybierz lokalizację instalacji.")

1. W **środowiska IDE programu Visual Studio** sekcji, zaakceptuj wartość domyślną. Visual Studio instaluje produkt core i zawiera pliki, które są specyficzne dla tej wersji programu Visual Studio.

   ![Sekcja środowiska IDE programu Visual Studio na karcie lokalizacje instalacji](media/vs-installation-locations-ide.png "Zaakceptuj wartość domyślną w sekcji środowisko IDE programu Visual Studio na karcie Lokalizacja instalacji.")

   > [!TIP]
   > Jeśli dysk systemowy jest dysków półprzewodnikowych (SSD), firma Microsoft zaleca, zaakceptuj lokalizację domyślną na dysku systemowym. Przyczyna? Podczas pracy z programem Visual Studio, możesz z do odczytu i zapisu wiele plików, co zwiększa dysku, operacje wejścia / wyjścia. Najlepiej wybrać dysk najszybszy do obsługi obciążenia.

1. W **pamięć podręczna pobierania** sekcji, zdecyduj, czy chcesz zachować pamięci podręcznej pobierania i zdecydować, której chcesz przechowywać swoje pliki.

     ![Sekcja pamięci podręcznej pobierania na karcie lokalizacje instalacji](media/vs-installation-locations-cache.png "Wybierz, czy chcesz zachować pamięć podręczną pobierania po zakończeniu instalacji, a następnie określ dysk, na którym mają być przechowywane pliki.")

    1. Zaznacz lub usuń zaznaczenie pola wyboru **pamięci podręcznej pobierania Kontynuuj po zakończeniu instalacji**.

       Jeśli nie chcesz przechowywać w pamięci podręcznej pobierania, ta lokalizacja będzie używana tylko tymczasowo. Ta akcja nie będzie mieć wpływ na lub usuwania plików z poprzedniej instalacji.

    1. Określ dysk, na którym chcesz przechowywać pliki instalacyjne i manifesty z pamięci podręcznej pobierania.

        Na przykład jeśli wybierzesz obciążenie "Programowanie aplikacji klasycznych w języku C++", tymczasowo wymagany rozmiar jest 1.58 GB na dysku systemowym, który następnie zostanie zwolniony, zaraz po zakończeniu instalacji.

       > [!IMPORTANT]
       > Ta lokalizacja została ustawiona za pomocą przez pierwszą instalację i nie można zmienić później z poziomu interfejsu użytkownika Instalatora. Zamiast tego należy [użyć parametrów wiersza polecenia](use-command-line-parameters-to-install-visual-studio.md) przenieść pamięci podręcznej pobierania.

1. W **udostępnione składniki, narzędzia i zestawy SDK** sekcji, określ dysk, na którym chcesz przechowywać pliki, które są współużytkowane przez instalacje programu Visual Studio side-by-side. Zestawy SDK i narzędzia są także przechowywane w tym katalogu.

   ![Sekcja składniki udostępnione, narzędzia i zestawy SDK na karcie lokalizacje instalacji](media/vs-installation-locations-shared.png "Określ lokalizację, w której mają być przechowywane udostępnione składniki, narzędzia i zestawy SDK.")

::: moniker-end

::: moniker range="vs-2019"

1. Po zainstalowaniu programu Visual Studio, wybierz **lokalizacje instalacji** kartę.

   ![Visual Studio 2019 — wybierz lokalizację instalacji](media/vs-2019/vs-installer-installation-locations.png "Wybierz lokalizację instalacji.")

1. W **środowiska IDE programu Visual Studio** sekcji, zaakceptuj wartość domyślną. Visual Studio instaluje produkt core i zawiera pliki, które są specyficzne dla tej wersji programu Visual Studio.

   > [!TIP]
   > Jeśli dysk systemowy jest dysków półprzewodnikowych (SSD), firma Microsoft zaleca, zaakceptuj lokalizację domyślną na dysku systemowym. Przyczyna? Podczas pracy z programem Visual Studio, możesz z do odczytu i zapisu wiele plików, co zwiększa dysku, operacje wejścia / wyjścia. Najlepiej wybrać dysk najszybszy do obsługi obciążenia.

1. W **pamięć podręczna pobierania** sekcji, zdecyduj, czy chcesz zachować pamięci podręcznej pobierania i zdecydować, której chcesz przechowywać swoje pliki.

    * Zaznacz lub usuń zaznaczenie pola wyboru **pamięci podręcznej pobierania Kontynuuj po zakończeniu instalacji**.

       Jeśli nie chcesz przechowywać w pamięci podręcznej pobierania, ta lokalizacja będzie używana tylko tymczasowo. Ta akcja nie będzie mieć wpływ na lub usuwania plików z poprzedniej instalacji.

    * Określ dysk, na którym chcesz przechowywać pliki instalacyjne i manifesty z pamięci podręcznej pobierania.

        Na przykład jeśli wybierzesz obciążenie "Programowanie aplikacji klasycznych w języku C++", tymczasowo wymagany rozmiar jest 1.58 GB na dysku systemowym, który następnie zostanie zwolniony, zaraz po zakończeniu instalacji.

       > [!IMPORTANT]
       > Ta lokalizacja została ustawiona za pomocą przez pierwszą instalację i nie można zmienić później z poziomu interfejsu użytkownika Instalatora. Zamiast tego należy [użyć parametrów wiersza polecenia](use-command-line-parameters-to-install-visual-studio.md) przenieść pamięci podręcznej pobierania.

1. W sekcji **współużytkowane składniki, narzędzia i zestawy SDK** należy pamiętać, że program używa tego samego dysku, który został wybrany w sekcji "pamięć podręczna pobierania". Katalog \Microsoft\VisualStudio\Shared to miejsce, w którym program Visual Studio przechowuje pliki, które są współużytkowane przez instalacje programu Visual Studio obok siebie. Zestawy SDK i narzędzia są także przechowywane w tym katalogu.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Instalowanie programu Visual Studio](install-visual-studio.md)
* [Aktualizowanie programu Visual Studio](update-visual-studio.md)
* [Modyfikowanie programu Visual Studio](update-visual-studio.md)
* [Odinstalowywanie programu Visual Studio](uninstall-visual-studio.md)
