---
title: Wybieranie lokalizacji instalacji
description: Dowiedz się, jak zmniejszyć rozmiar instalacji programu Visual Studio na dysku systemowym, zmieniając lokalizację pamięci podręcznej pobierania, składników udostępnionych, zestawów SDK i narzędzi na różne dyski. Na przykład przenieść niektóre pliki z dysku C do dysku D.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
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
ms.openlocfilehash: 7f80d3c30c536e58811f8ca92676694b6d010010
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76111790"
---
# <a name="select-the-installation-locations-in-visual-studio"></a>Wybieranie lokalizacji instalacji w programie Visual Studio

::: moniker range="vs-2019"

Można zmniejszyć rozmiar instalacji programu Visual Studio na dysku systemowym, zmieniając lokalizację dla niektórych jego plików. W szczególności można użyć innej lokalizacji dla pamięci podręcznej pobierania, udostępnionych składników, zestawów SDK i plików narzędzi.

::: moniker-end

::: moniker range="vs-2017"

**Nowość w wersji 15.7**: Można zmniejszyć rozmiar instalacji programu Visual Studio na dysku systemowym, zmieniając lokalizację niektórych jego plików. W szczególności można użyć innej lokalizacji dla pamięci podręcznej pobierania, udostępnionych składników, zestawów SDK i plików narzędzi.

::: moniker-end

   > [!NOTE]
   > Istnieje kilka narzędzi i zestawów SDK, które mają różne reguły dotyczące miejsca ich zainstalowania. Takie narzędzia i zestawY SDK są instalowane na dysku systemowym, nawet jeśli wybierzesz inną lokalizację.

Chcesz zacząć? Oto jak to zrobić.

::: moniker range="vs-2017"

1. Po zainstalowaniu programu Visual Studio wybierz kartę **Lokalizacje instalacji.**

   ![Visual Studio 2017 — wybieranie lokalizacji instalacji](media/vs-installation-locations.png "Wybierz lokalizację instalacji.")

1. W sekcji **IDE programu Visual Studio** zaakceptuj wartość domyślną. Visual Studio instaluje podstawowy produkt i zawiera pliki, które są specyficzne dla tej wersji programu Visual Studio.

   ![Sekcja IDE programu Visual Studio na karcie Lokalizacje instalacji](media/vs-installation-locations-ide.png "Zaakceptuj domyślną sekcję IDE programu Visual Studio na karcie Lokalizacja instalacji.")

   > [!TIP]
   > Jeśli dysk systemowy jest dyskiem SSD, zalecamy zaakceptowanie domyślnej lokalizacji na dysku systemowym. Powód? Podczas tworzenia za pomocą programu Visual Studio, odczytywanie i zapis do wielu plików, co zwiększa działanie we/wy dysku. Najlepiej wybrać najszybszy dysk, aby obsłużyć obciążenie.

1. W sekcji **Pobieranie pamięci podręcznej** zdecyduj, czy chcesz zachować pamięć podręczną pobierania, a następnie zdecyduj, gdzie chcesz przechowywać jej pliki.

     ![Sekcja Pobieranie pamięci podręcznej na karcie Lokalizacje instalacji](media/vs-installation-locations-cache.png "Wybierz, czy pamięć podręczna pobierania ma być przechowywana po instalacji, a następnie określ dysk, na którym mają być przechowywane pliki.")

    1. Zaznacz lub wyewidencjonuj pozycję **Zachowaj pamięć podręczną pobierania po instalacji**.

       Jeśli zdecydujesz się nie przechowywać pamięci podręcznej pobierania, lokalizacja jest używana tylko tymczasowo. Ta akcja nie wpływa ani nie usuwa plików z poprzednich instalacji.

    1. Określ dysk, na którym chcesz przechowywać pliki instalacyjne i manifesty z pamięci podręcznej pobierania.

        Na przykład jeśli wybierzesz "Tworzenie pulpitu z C++" obciążenia, tymczasowo wymagany rozmiar jest 1,58 GB na dysku systemowym, który jest następnie zwalniany po zakończeniu instalacji.

       > [!IMPORTANT]
       > Ta lokalizacja jest ustawiona przy pierwszej instalacji i nie można jej później zmienić z interfejsu użytkownika instalatora. Zamiast tego należy [użyć parametrów wiersza polecenia,](use-command-line-parameters-to-install-visual-studio.md) aby przenieść pamięć podręczną pobierania.

1. W udostępnione **składniki, narzędzia i zestawów SDK** określić dysk, na którym chcesz przechowywać pliki, które są współużytkowane przez instalacje programu Visual Studio obok siebie. ZestawY SDK i narzędzia są również przechowywane w tym katalogu.

   ![Udostępnione składniki, narzędzia i zestaw SDK sekcji na karcie Lokalizacje instalacji](media/vs-installation-locations-shared.png "Określ lokalizację, w której mają być przechowywane udostępnione składniki, narzędzia i zestawy SDK.")

::: moniker-end

::: moniker range="vs-2019"

1. Po zainstalowaniu programu Visual Studio wybierz kartę **Lokalizacje instalacji.**

   ![Visual Studio 2019 — wybieranie lokalizacji instalacji](media/vs-2019/vs-installer-installation-locations.png "Wybierz lokalizację instalacji.")

1. W sekcji **IDE programu Visual Studio** zaakceptuj wartość domyślną. Visual Studio instaluje podstawowy produkt i zawiera pliki, które są specyficzne dla tej wersji programu Visual Studio.

   > [!TIP]
   > Jeśli dysk systemowy jest dyskiem SSD, zalecamy zaakceptowanie domyślnej lokalizacji na dysku systemowym. Powód? Podczas tworzenia za pomocą programu Visual Studio, odczytywanie i zapis do wielu plików, co zwiększa działanie we/wy dysku. Najlepiej wybrać najszybszy dysk, aby obsłużyć obciążenie.

1. W sekcji **Pobieranie pamięci podręcznej** zdecyduj, czy chcesz zachować pamięć podręczną pobierania, a następnie zdecyduj, gdzie chcesz przechowywać jej pliki.

    * Zaznacz lub wyewidencjonuj pozycję **Zachowaj pamięć podręczną pobierania po instalacji**.

       Jeśli zdecydujesz się nie przechowywać pamięci podręcznej pobierania, lokalizacja jest używana tylko tymczasowo. Ta akcja nie wpływa ani nie usuwa plików z poprzednich instalacji.

    * Określ dysk, na którym chcesz przechowywać pliki instalacyjne i manifesty z pamięci podręcznej pobierania.

        Na przykład jeśli wybierzesz "Tworzenie pulpitu z C++" obciążenia, tymczasowo wymagany rozmiar jest 1,58 GB na dysku systemowym, który jest następnie zwalniany po zakończeniu instalacji.

       > [!IMPORTANT]
       > Ta lokalizacja jest ustawiona przy pierwszej instalacji i nie można jej później zmienić z interfejsu użytkownika instalatora. Zamiast tego należy [użyć parametrów wiersza polecenia,](use-command-line-parameters-to-install-visual-studio.md) aby przenieść pamięć podręczną pobierania.

1. W udostępnione **składniki, narzędzia i zestawów SDK** sekcji, należy pamiętać, że używa tego samego dysku, który został wybrany w sekcji "Pobierz pamięć podręczną". Katalog \Microsoft\VisualStudio\Shared to miejsce, w którym program Visual Studio przechowuje pliki współużytkowane przez instalacje programu Visual Studio obok siebie. ZestawY SDK i narzędzia są również przechowywane w tym katalogu.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalacja programu Visual Studio](install-visual-studio.md)
* [Aktualizowanie programu Visual Studio](update-visual-studio.md)
* [Modyfikowanie programu Visual Studio](update-visual-studio.md)
* [Odinstalowywanie programu Visual Studio](uninstall-visual-studio.md)
