---
title: Kompilowanie oraz oczyszczanie projektów i rozwiązań
description: W tym artykule opisano sposób tworzenia projektu w programie Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: E4B6CB42-9FE2-43B9-93B7-BD4BD50518B1
ms.openlocfilehash: 7278b599e6a9c26ec33ea2167402dd641e6005d1
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "74983321"
---
# <a name="building-and-cleaning-projects-and-solutions"></a>Projekty i rozwiązania budowlane i czyszczące

Wykonaj kroki opisane w tym artykule, aby dowiedzieć się, jak tworzyć, odbudowywać i czyścić rozwiązanie i projekt.

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Aby zbudować, odbudować lub wyczyścić całe rozwiązanie

Aby utworzyć, odbudować lub wyczyścić całe rozwiązanie:

1. Wybierz węzeł Rozwiązanie w konsoli rozrachycznej:

    ![Wybieranie węzła rozwiązania](media/compiling-and-building-image1.png)

2. Wybierz polecenie Zbuduj menu na pasku menu i wybierz jedną z następujących opcji:

    ![wybieranie pozycji menu kompilacji](media/compiling-and-building-image2.png)

    * **Zbuduj wszystko** — próbuje utworzyć wszystkie pliki w ramach projektu, które uległy zmianie w ramach projektu od ostatniej kompilacji.
    * **Odbuduj wszystko** — czyści rozwiązanie, a następnie buduje go.
    * **Clean All** - Usuwa wszystkie produkty kompilacji z rozwiązania.

## <a name="to-build-or-rebuild-a-single-project"></a>Aby zbudować lub odbudować pojedynczy projekt

1. W panelu rozwiązania wybierz projekt.

2. Na pasku menu wybierz pozycję Buduj, a następnie wybierz pozycję Build[ProjectName], Rebuild[ProjectName] lub Clean[ProjectName].

## <a name="to-stop-a-build"></a>Aby zatrzymać kompilację

Aby zatrzymać kompilację, naciśnij czerwony kwadrat w obszarze stanu:

![Naciśnij czerwony kwadrat, aby zatrzymać kompilację](media/compiling-and-building-image3.png)

## <a name="see-also"></a>Zobacz też

- [Tworzenie i czyszczenie projektów i rozwiązań (Visual Studio w systemie Windows)](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)