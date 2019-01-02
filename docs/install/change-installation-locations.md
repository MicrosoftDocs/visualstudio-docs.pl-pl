---
title: Wybieranie lokalizacji instalacji
description: Dowiedz się, jak w celu zmniejszenia miejsca zajmowanego przez instalację programu Visual Studio na dysku systemowym, zmieniając lokalizację pamięci podręcznej pobierania, składników udostępnionych, zestawy SDK i narzędzi na różnych dyskach.
ms.date: 11/07/2018
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- change installation locations for Visual Studio
- select an installation location for Visual Studio files
- move installation files to different drives
- use the D drive
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ce04592b6de6be16047baf3736e020c2ba71536a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53837618"
---
# <a name="select-the-installation-locations-in-visual-studio-2017"></a>Wybierz lokalizację instalacji programu Visual Studio 2017

**Nowość w wersji 15.7**: Można zmniejszyć miejsca zajmowanego przez instalację programu Visual Studio na dysku systemowym, zmieniając lokalizację dla niektórych plików. W szczególności można użyć innej lokalizacji pamięci podręcznej pobierania, składników udostępnionych, zestawy SDK i pliki narzędzia.

   > [!NOTE]
   > Istnieją pewne narzędzia i zestawy SDK, które mają różne reguły, w którym można zainstalować. Takie narzędzia i zestawy SDK są instalowane na dysku systemowym, nawet jeśli wybierz inną lokalizację.

Chcesz zacząć? Poniżej przedstawiono sposób.

1. Po zainstalowaniu programu Visual Studio, wybierz **lokalizacje instalacji** kartę.

   ![Program Visual Studio 2017 — wybierz miejsce instalacji](media/vs-installation-locations.png "wybierz lokalizację instalacji.")

1. W **środowiska IDE programu Visual Studio** sekcji, zaakceptuj wartość domyślną. Visual Studio instaluje produkt core i zawiera pliki, które są specyficzne dla tej wersji programu Visual Studio.

   ![Visual Studio IDE części na karcie lokalizacje instalacji](media/vs-installation-locations-ide.png "Zaakceptuj domyślne ustawienie w sekcji środowiska IDE programu Visual Studio na karcie lokalizacji instalacji.")

   > [!TIP]
   > Jeśli dysk systemowy jest dysków półprzewodnikowych (SSD), firma Microsoft zaleca, zaakceptuj lokalizację domyślną na dysku systemowym. Przyczyna? Podczas pracy z programem Visual Studio, możesz z do odczytu i zapisu wiele plików, co zwiększa dysku, operacje wejścia / wyjścia. Najlepiej wybrać dysk najszybszy do obsługi obciążenia.

1. W **pamięć podręczna pobierania** sekcji, zdecyduj, czy chcesz zachować pamięci podręcznej pobierania i zdecydować, której chcesz przechowywać swoje pliki.

     ![Pobieranie pamięci podręcznej części na karcie lokalizacje instalacji](media/vs-installation-locations-cache.png "wybierz, czy zachowywać pamięci podręcznej pobierania po zakończeniu instalacji, a następnie określ dysk, na którym chcesz przechowywać pliki.")

    1. Zaznacz lub usuń zaznaczenie pola wyboru **pamięci podręcznej pobierania Kontynuuj po zakończeniu instalacji**.

       Jeśli nie chcesz przechowywać w pamięci podręcznej pobierania, ta lokalizacja będzie używana tylko tymczasowo. Ta akcja nie będzie mieć wpływ na lub usuwania plików z poprzedniej instalacji.

    1. Określ dysk, na którym chcesz przechowywać pliki instalacyjne i manifesty z pamięci podręcznej pobierania.

        Na przykład jeśli wybierzesz obciążenie "Programowanie aplikacji klasycznych w języku C++", tymczasowo wymagany rozmiar jest 1.58 GB na dysku systemowym, który następnie zostanie zwolniony, zaraz po zakończeniu instalacji.

       > [!IMPORTANT]
       > Ta lokalizacja została ustawiona za pomocą przez pierwszą instalację i nie można zmienić później z poziomu interfejsu użytkownika Instalatora. Zamiast tego należy [użyć parametrów wiersza polecenia](use-command-line-parameters-to-install-visual-studio.md) przenieść pamięci podręcznej pobierania.

1. W **udostępnione składniki, narzędzia i zestawy SDK** sekcji, określ dysk, na którym chcesz przechowywać pliki, które są współużytkowane przez instalacje programu Visual Studio side-by-side. Zestawy SDK i narzędzia są także przechowywane w tym katalogu.

   ![Udostępnione składniki, narzędzia i zestawy SDK części na karcie lokalizacje instalacji](media/vs-installation-locations-shared.png "Określ lokalizację, w którym chcesz przechowywać współużytkowanych składników, narzędzi i zestawów SDK.")

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Instalowanie programu Visual Studio 2017](install-visual-studio.md)
* [Update Visual Studio 2017](update-visual-studio.md)
* [Modyfikowanie programu Visual Studio 2017](update-visual-studio.md)
* [Odinstaluj program Visual Studio 2017](uninstall-visual-studio.md)
