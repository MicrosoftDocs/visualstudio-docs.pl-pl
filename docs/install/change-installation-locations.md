---
title: Wybieranie lokalizacji instalacji
description: Dowiedz się, jak zmniejszyć zasięg instalacji programu Visual Studio na dysku systemowym, zmieniając lokalizację pamięci podręcznej pobierania, współużytkowane składniki, zestawy SDK i narzędzia na różne dyski. Na przykład Przenieś niektóre pliki z dysku C na dysk D.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: how-to
helpviewer_keywords:
- change installation locations for Visual Studio
- select an installation location for Visual Studio files
- move installation files to different drives
- use the D drive
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 5751ddeca2ba690ec29ff905ec7e8330a7199eab
ms.sourcegitcommit: 9e15138a34532b222e80f6b42b1a9de7b2fe0175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2020
ms.locfileid: "85419123"
---
# <a name="select-the-installation-locations-in-visual-studio"></a>Wybierz lokalizacje instalacji w programie Visual Studio

::: moniker range="vs-2019"

Możesz zmniejszyć zasięg instalacji programu Visual Studio na dysku systemowym, zmieniając lokalizację niektórych plików. W odniesieniu do plików pamięci podręcznej pobierania, składników udostępnionych, zestawów SDK i narzędzi można użyć innej lokalizacji.

::: moniker-end

::: moniker range="vs-2017"

**Nowość w wersji 15,7**: można zmniejszyć zasięg instalacji programu Visual Studio na dysku systemowym, zmieniając lokalizację niektórych plików. W odniesieniu do plików pamięci podręcznej pobierania, składników udostępnionych, zestawów SDK i narzędzi można użyć innej lokalizacji.

::: moniker-end

   > [!NOTE]
   > Istnieją pewne narzędzia i zestawy SDK, które mają różne reguły, w których można je zainstalować. Takie narzędzia i zestawy SDK są instalowane na dysku systemowym nawet w przypadku wybrania innej lokalizacji.

Chcesz zacząć? Oto jak to zrobić.

::: moniker range="vs-2017"

1. Po zainstalowaniu programu Visual Studio wybierz kartę **lokalizacje instalacji** .

   ![Visual Studio 2017 — wybierz lokalizację instalacji](media/vs-installation-locations.png "Wybierz lokalizację instalacji.")

1. W sekcji **IDE programu Visual Studio** Zaakceptuj wartość domyślną. Program Visual Studio instaluje produkt podstawowy i zawiera pliki, które są specyficzne dla tej wersji programu Visual Studio.

   ![Sekcja środowiska IDE programu Visual Studio na karcie lokalizacje instalacji](media/vs-installation-locations-ide.png "Zaakceptuj wartość domyślną w sekcji środowisko IDE programu Visual Studio na karcie Lokalizacja instalacji.")

   > [!TIP]
   > Jeśli dysk systemowy jest dyskiem SSD, zalecamy zaakceptowanie domyślnej lokalizacji na dysku systemowym. Powód? Podczas opracowywania w programie Visual Studio można czytać i zapisywać wiele plików, co zwiększa aktywność operacji we/wy dysku. Najlepiej wybrać najszybszy dysk do obsługi obciążenia.

1. W sekcji **pobieranie pamięci podręcznej pobierania** Zdecyduj, czy chcesz zachować pamięć podręczną pobierania, a następnie zdecyduj, gdzie mają być przechowywane pliki.

     ![Sekcja pamięci podręcznej pobierania na karcie lokalizacje instalacji](media/vs-installation-locations-cache.png "Wybierz, czy chcesz zachować pamięć podręczną pobierania po zakończeniu instalacji, a następnie określ dysk, na którym mają być przechowywane pliki.")

    1. Zaznacz lub usuń zaznaczenie pola **Zachowaj pamięć podręczną pobierania po zakończeniu instalacji**.

       Jeśli użytkownik zdecyduje się nie utrzymywać pamięci podręcznej pobierania, lokalizacja jest używana tylko tymczasowo. Ta akcja nie wpływa ani nie usunie plików z poprzednich instalacji.

    1. Określ dysk, na którym mają być przechowywane pliki instalacyjne i manifesty z pamięci podręcznej pobierania.

        Na przykład w przypadku wybrania obciążenia "Programowanie aplikacji klasycznych w języku C++" czas wymagany tymczasowo wynosi 1,58 GB na dysku systemowym, który zostanie zwolniony zaraz po zakończeniu instalacji.

       > [!IMPORTANT]
       > Ta lokalizacja jest ustawiana przy pierwszej instalacji i nie można jej później zmienić za pomocą interfejsu użytkownika Instalatora. Zamiast tego należy [użyć parametrów wiersza polecenia](use-command-line-parameters-to-install-visual-studio.md) , aby przenieść pamięć podręczną pobierania.

1. W sekcji **udostępnione składniki, narzędzia i zestawy SDK** Określ dysk, na którym mają być przechowywane pliki współużytkowane przez instalacje programu Visual Studio obok siebie. Zestawy SDK i narzędzia są również przechowywane w tym katalogu.

   ![Sekcja składniki udostępnione, narzędzia i zestawy SDK na karcie lokalizacje instalacji](media/vs-installation-locations-shared.png "Określ lokalizację, w której mają być przechowywane udostępnione składniki, narzędzia i zestawy SDK.")

::: moniker-end

::: moniker range="vs-2019"

1. Po zainstalowaniu programu Visual Studio wybierz kartę **lokalizacje instalacji** .

   ![Visual Studio 2019 — wybierz lokalizację instalacji](media/vs-2019/vs-installer-installation-locations.png "Wybierz lokalizację instalacji.")

1. W sekcji **IDE programu Visual Studio** Zaakceptuj wartość domyślną. Program Visual Studio instaluje produkt podstawowy i zawiera pliki, które są specyficzne dla tej wersji programu Visual Studio.

   > [!TIP]
   > Jeśli dysk systemowy jest dyskiem SSD, zalecamy zaakceptowanie domyślnej lokalizacji na dysku systemowym. Powód? Podczas opracowywania w programie Visual Studio można czytać i zapisywać wiele plików, co zwiększa aktywność operacji we/wy dysku. Najlepiej wybrać najszybszy dysk do obsługi obciążenia.

1. W sekcji **pobieranie pamięci podręcznej pobierania** Zdecyduj, czy chcesz zachować pamięć podręczną pobierania, a następnie zdecyduj, gdzie mają być przechowywane pliki.

    * Zaznacz lub usuń zaznaczenie pola **Zachowaj pamięć podręczną pobierania po zakończeniu instalacji**.

       Jeśli użytkownik zdecyduje się nie utrzymywać pamięci podręcznej pobierania, lokalizacja jest używana tylko tymczasowo. Ta akcja nie wpływa ani nie usunie plików z poprzednich instalacji.

    * Określ dysk, na którym mają być przechowywane pliki instalacyjne i manifesty z pamięci podręcznej pobierania.

        Na przykład w przypadku wybrania obciążenia "Programowanie aplikacji klasycznych w języku C++" czas wymagany tymczasowo wynosi 1,58 GB na dysku systemowym, który zostanie zwolniony zaraz po zakończeniu instalacji.

       > [!IMPORTANT]
       > Ta lokalizacja jest ustawiana przy pierwszej instalacji i nie można jej później zmienić za pomocą interfejsu użytkownika Instalatora. Zamiast tego należy [użyć parametrów wiersza polecenia](use-command-line-parameters-to-install-visual-studio.md) , aby przenieść pamięć podręczną pobierania.

1. W sekcji **współużytkowane składniki, narzędzia i zestawy SDK** należy pamiętać, że program używa tego samego dysku, który został wybrany w sekcji "pamięć podręczna pobierania". Katalog \Microsoft\VisualStudio\Shared to miejsce, w którym program Visual Studio przechowuje pliki, które są współużytkowane przez instalacje programu Visual Studio obok siebie. Zestawy SDK i narzędzia są również przechowywane w tym katalogu.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalowanie programu Visual Studio](install-visual-studio.md)
* [Aktualizowanie programu Visual Studio](update-visual-studio.md)
* [Modyfikowanie programu Visual Studio](update-visual-studio.md)
* [Odinstalowywanie programu Visual Studio](uninstall-visual-studio.md)
