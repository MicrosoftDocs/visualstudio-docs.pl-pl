---
title: Wybieranie lokalizacji instalacji
description: Dowiedz się, jak zmniejszyć rozmiar instalacji Visual Studio dysku systemowego, zmieniając lokalizację pamięci podręcznej pobierania, współużytkowanych składników, zestawów SDK i narzędzi na różne dyski. Na przykład przenieś niektóre pliki z dysku C na dysk D.
ms.date: 03/30/2019
ms.custom: vs-acquisition
ms.topic: how-to
helpviewer_keywords:
- change installation locations for Visual Studio
- select an installation location for Visual Studio files
- move installation files to different drives
- use the D drive
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 5ad065a780a16420727d90605d95038cc5f4080a
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387570"
---
# <a name="select-the-installation-locations-in-visual-studio"></a>Wybierz lokalizacje instalacji w Visual Studio

::: moniker range=">=vs-2019"

Możesz zmniejszyć rozmiar instalacji Visual Studio dysku systemowego, zmieniając lokalizację niektórych plików. W szczególności można użyć innej lokalizacji dla pamięci podręcznej pobierania, składników udostępnionych, zestawów SDK i plików narzędzi.

::: moniker-end

::: moniker range="vs-2017"

**Nowość w wersji 15.7:** możesz zmniejszyć rozmiar instalacji Visual Studio dysku systemowego, zmieniając lokalizację niektórych plików. W szczególności można użyć innej lokalizacji dla pamięci podręcznej pobierania, składników udostępnionych, zestawów SDK i plików narzędzi.

::: moniker-end

   > [!NOTE]
   > Istnieją pewne narzędzia i zestawy SDK, które mają różne reguły dotyczące miejsca, w którym można je zainstalować. Takie narzędzia i zestawy SDK są instalowane na dysku systemowym, nawet jeśli wybierzesz inną lokalizację.

Możemy zaczynać? Oto jak to zrobić.

::: moniker range="vs-2017"

1. Po zainstalowaniu Visual Studio wybierz **kartę Lokalizacje** instalacji.

   ![Visual Studio 2017 — wybieranie lokalizacji instalacji](media/vs-installation-locations.png "Wybierz lokalizację instalacji.")

1. W sekcji **Visual Studio IDE** zaakceptuj wartość domyślną. Visual Studio produkt podstawowy i zawiera pliki specyficzne dla tej wersji programu Visual Studio.

   ![Visual Studio IDE na karcie Lokalizacje instalacji](media/vs-installation-locations-ide.png "Zaakceptuj wartość domyślną dla Visual Studio IDE na karcie Lokalizacja instalacji.")

   > [!TIP]
   > Jeśli dysk systemowy jest dyskiem półprzewodnikowym (SSD), zalecamy zaakceptowanie domyślnej lokalizacji na dysku systemowym. Powód? Podczas tworzenia aplikacji przy Visual Studio odczytu i zapisu w wielu plikach, co zwiększa aktywność we/wy dysku. Najlepiej wybrać najszybszy dysk do obsługi obciążenia.

1. W sekcji **Pobieranie pamięci podręcznej** zdecyduj, czy chcesz zachować pamięć podręczną pobierania, a następnie zdecyduj, gdzie chcesz przechowywać jej pliki.

     ![Sekcja Pobieranie pamięci podręcznej na karcie Lokalizacje instalacji](media/vs-installation-locations-cache.png "Wybierz, czy pamięć podręczna pobierania ma być zapisywana po zakończeniu instalacji, a następnie określ dysk, na którym mają być przechowywane pliki.")

    1. Zaznacz lub usuń zaznaczenie **pola wyboru Zachowaj pamięć podręczną pobierania po zakończeniu instalacji.**

       Jeśli zdecydujesz się nie przechowywać pamięci podręcznej pobierania, lokalizacja będzie używana tylko tymczasowo. Ta akcja nie wpłynie na pliki z poprzednich instalacji ani ich nie usunie.

    1. Określ dysk, na którym mają być przechowywane pliki instalacyjne i manifesty z pamięci podręcznej pobierania.

        Jeśli na przykład wybierzesz obciążenie "Tworzenie aplikacji klasycznych w języku C++", tymczasowo wymagany rozmiar to 1,58 GB na dysku systemowym, który jest następnie bezpłatny zaraz po zakończeniu instalacji.

       > [!IMPORTANT]
       > Ta lokalizacja jest ustawiana przy pierwszej instalacji i nie można jej później zmienić z interfejsu użytkownika instalatora. Zamiast tego należy użyć [parametrów wiersza polecenia, aby](use-command-line-parameters-to-install-visual-studio.md) przenieść pamięć podręczną pobierania.

1. W sekcji **Współdzielone składniki,** narzędzia i zestawy SDK określ dysk, na którym mają być przechowywane pliki współużytkowe współużytkowania przez Visual Studio instalacji. Zestawy SDK i narzędzia są również przechowywane w tym katalogu.

   ![Sekcja Współdzielone składniki, narzędzia i zestawy SDK na karcie Lokalizacje instalacji](media/vs-installation-locations-shared.png "Określ lokalizację, w której mają być przechowywane udostępnione składniki, narzędzia i zestawy SDK.")

::: moniker-end

::: moniker range=">=vs-2019"

1. Po zainstalowaniu Visual Studio wybierz **kartę Lokalizacje** instalacji.

   ![Visual Studio 2019 r. — wybierz lokalizację instalacji](media/vs-2019/vs-installer-installation-locations.png "Wybierz lokalizację instalacji.")

1. W sekcji **Visual Studio IDE** zaakceptuj wartość domyślną. Visual Studio produkt podstawowy i zawiera pliki specyficzne dla tej wersji programu Visual Studio.

   > [!TIP]
   > Jeśli dysk systemowy jest dyskiem półprzewodnikowym (SSD), zalecamy zaakceptowanie domyślnej lokalizacji na dysku systemowym. Powód? Podczas tworzenia aplikacji przy Visual Studio odczytu i zapisu w wielu plikach, co zwiększa aktywność we/wy dysku. Najlepiej wybrać najszybszy dysk do obsługi obciążenia.

1. W sekcji **Pobieranie pamięci podręcznej** zdecyduj, czy chcesz zachować pamięć podręczną pobierania, a następnie zdecyduj, gdzie chcesz przechowywać jej pliki.

    * Zaznacz lub usuń zaznaczenie **pola wyboru Zachowaj pamięć podręczną pobierania po zakończeniu instalacji.**

       Jeśli zdecydujesz się nie przechowywać pamięci podręcznej pobierania, lokalizacja będzie używana tylko tymczasowo. Ta akcja nie wpłynie na pliki z poprzednich instalacji ani ich nie usunie.

    * Określ dysk, na którym mają być przechowywane pliki instalacyjne i manifesty z pamięci podręcznej pobierania.

        Jeśli na przykład wybierzesz obciążenie "Tworzenie aplikacji klasycznych w języku C++", tymczasowo wymagany rozmiar to 1,58 GB na dysku systemowym, który jest następnie bezpłatny zaraz po zakończeniu instalacji.

       > [!IMPORTANT]
       > Ta lokalizacja jest ustawiana przy pierwszej instalacji i nie można jej później zmienić z interfejsu użytkownika instalatora. Zamiast tego należy użyć [parametrów wiersza polecenia, aby](use-command-line-parameters-to-install-visual-studio.md) przenieść pamięć podręczną pobierania.

1. W sekcji **Udostępnione składniki, narzędzia** i zestawy SDK zwróć uwagę, że używa ona tego samego dysku, który został wybrany w sekcji "Pobieranie pamięci podręcznej". Katalog \Microsoft\VisualStudio\Shared Visual Studio, w którym przechowywane są pliki współużytwone przez współużytkowanie obok siebie Visual Studio instalacji. Zestawy SDK i narzędzia są również przechowywane w tym katalogu.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalowanie programu Visual Studio](install-visual-studio.md)
* [Aktualizowanie programu Visual Studio](update-visual-studio.md)
* [Modyfikowanie programu Visual Studio](update-visual-studio.md)
* [Odinstalowywanie programu Visual Studio](uninstall-visual-studio.md)
