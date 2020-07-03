---
title: Kompilowanie oraz oczyszczanie projektów i rozwiązań
description: W tym artykule opisano sposób tworzenia projektu w Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/19/2019
ms.assetid: E4B6CB42-9FE2-43B9-93B7-BD4BD50518B1
ms.topic: how-to
ms.openlocfilehash: a33b590290880a7e20e7c0ec44c0b12942b1240e
ms.sourcegitcommit: 2ce59c2ffeba5ba7f628c2e6c75cba4731deef8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2020
ms.locfileid: "85939104"
---
# <a name="building-and-cleaning-projects-and-solutions"></a>Kompilowanie i czyszczenie projektów i rozwiązań

Wykonaj kroki opisane w tym artykule, aby dowiedzieć się, jak tworzyć, odbudować lub czyścić wszystkie lub niektóre projekty w rozwiązaniu.

> [!NOTE]
> Ten temat ma zastosowanie do Visual Studio dla komputerów Mac. W przypadku programu Visual Studio w systemie Windows Zobacz [Tworzenie i czyszczenie projektów oraz rozwiązań w programie Visual Studio](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio).

## <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Aby skompilować, skompilować lub wyczyścić całe rozwiązanie

1. Wybierz węzeł rozwiązania w **okienko rozwiązania**:

    ![Wybieranie węzła rozwiązania](media/compiling-and-building-image1.png)

2. Wybierz menu **kompilacja** na pasku menu, a następnie wybierz jedną z następujących opcji:

    ![Wybieranie elementu menu Kompiluj wszystko](media/compiling-and-building-image2.png)

    * Wybierz opcję **Kompiluj wszystko** , aby skompilować pliki i składniki w ramach projektu, które uległy zmianie od czasu ostatniej kompilacji.

    * Wybierz opcję **Kompiluj ponownie wszystkie** do "Wyczyść" rozwiązania, a następnie kompiluje wszystkie pliki projektu i składniki.

    * Wybierz pozycję **Wyczyść wszystko** , aby usunąć wszystkie pliki pośrednie i wyjściowe. Tylko w przypadku pozostałych plików projektu i składników można skompilować nowe wystąpienia plików pośrednich i wyjściowych.

## <a name="to-build-or-rebuild-a-single-project"></a>Aby skompilować lub skompilować pojedynczy projekt

1. Wybierz projekt w **okienko rozwiązania**.

2. Wybierz menu **kompilacja** z paska menu.

3. Wybierz pozycję kompilacja [ProjectName], Skompiluj ponownie [ProjectName] lub wyczyść [ProjectName].

## <a name="to-stop-a-build"></a>Aby zatrzymać kompilację

Aby zatrzymać kompilację, użyj jednej z następujących opcji:

* Naciśnij czerwony kwadrat w obszarze Stan:

    ![Naciśnij czerwony kwadrat, aby zatrzymać kompilację](media/compiling-and-building-image3.png)

* Użyj elementu **stop** w menu **kompilacja** .

* Naciśnij klawisze **cmd + Shift + Return**.

## <a name="see-also"></a>Zobacz też

- [Twórz i czyść projekty i rozwiązania (Visual Studio w systemie Windows)](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)