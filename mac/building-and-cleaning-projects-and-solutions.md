---
title: Kompilowanie oraz oczyszczanie projektów i rozwiązań
description: W tym artykule opisano sposób tworzenia projektu w programie Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/19/2019
ms.assetid: E4B6CB42-9FE2-43B9-93B7-BD4BD50518B1
ms.openlocfilehash: 924bdb08154ecb3caad04cabf7e860bed9204e98
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "71128455"
---
# <a name="building-and-cleaning-projects-and-solutions"></a>Projekty i rozwiązania budowlane i czyszczące

Wykonaj kroki opisane w tym artykule, aby dowiedzieć się, jak tworzyć, odbudowywać lub czyścić wszystkie lub niektóre projekty w rozwiązaniu.

> [!NOTE]
> W tym temacie stosuje się do programu Visual Studio dla komputerów Mac. W programie Visual Studio w systemie Windows zobacz [Tworzenie i czyszczenie projektów i rozwiązań w programie Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio).

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Aby zbudować, odbudować lub wyczyścić całe rozwiązanie

1. Wybierz węzeł Rozwiązanie w **konsoli rozrachycznej:**

    ![Wybieranie węzła rozwiązania](media/compiling-and-building-image1.png)

2. Wybierz menu **Kompilacja** na pasku menu i wybierz jedną z następujących opcji:

    ![wybieranie pozycji menu kompilacji](media/compiling-and-building-image2.png)

    * Wybierz **pozycję Zbuduj wszystko,** aby skompilować pliki i składniki w projekcie, które uległy zmianie od czasu ostatniej kompilacji.

    * Wybierz **pozycję Odbuduj wszystko,** aby "wyczyścić" rozwiązanie, a następnie skompiluje wszystkie pliki i składniki projektu.

    * Wybierz **pozycję Wyczyść wszystko,** aby usunąć wszystkie pliki pośrednie i wyjściowe. Po lewej stronie pozostało tylko pliki projektu i składnika, można następnie zbudować nowe wystąpienia plików pośrednich i wyjściowych.

## <a name="to-build-or-rebuild-a-single-project"></a>Aby zbudować lub odbudować pojedynczy projekt

1. Wybierz projekt w **panelu rozwiązania**.

2. Wybierz menu **Kompilacja** z paska menu.

3. Wybierz opcję Build[ProjectName], Rebuild[ProjectName] lub Clean[ProjectName].

## <a name="to-stop-a-build"></a>Aby zatrzymać kompilację

Aby zatrzymać kompilację, użyj jednej z następujących opcji:

* Naciśnij czerwony kwadrat w obszarze stanu:

    ![Naciśnij czerwony kwadrat, aby zatrzymać kompilację](media/compiling-and-building-image3.png)

* Użyj elementu **Zatrzymaj** w menu **Kompilacja.**

* Naciśnij **klawisze Cmd+Shift+Return**.

## <a name="see-also"></a>Zobacz też

- [Tworzenie i czyszczenie projektów i rozwiązań (Visual Studio w systemie Windows)](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)