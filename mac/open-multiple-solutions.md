---
title: 'Instrukcje: otwieranie wielu rozwiązań'
description: Dowiedz się, jak otworzyć więcej niż jedno rozwiązanie w Visual Studio dla komputerów Mac i jak otworzyć więcej niż jedno wystąpienie aplikacji.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 11/09/2020
ms.assetid: 592BA4E3-8DEF-4FCD-8BA0-519A4CEEE03E
ms.custom: video
ms.topic: how-to
ms.openlocfilehash: e54f002141379d93a40df69ea070d5a64eba2f7d
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493442"
---
# <a name="open-multiple-solutions-or-instances-of-visual-studio-for-mac"></a>Otwórz wiele rozwiązań lub wystąpień Visual Studio dla komputerów Mac

Domyślnie wszystkie aplikacje na komputerze Mac, w tym Visual Studio dla komputerów Mac, są aplikacjami z _jednym wystąpieniem_ . Oznacza to, że jeśli aplikacja, która ma być używana, jest już otwarta (zilustrowana kropką pod ikoną w Docku), wybranie ikony ponownie spowoduje otwarcie uruchomionego wystąpienia, a nie nowego. Jeśli potrzebujesz dodatkowych wystąpień aplikacji, możesz monitować system o jego otwarcie, zgodnie z opisem w [następnej sekcji](#open-a-second-instance-of-visual-studio-for-mac).

Ponadto podczas otwierania rozwiązania domyślne zachowanie polega na otwarciu rozwiązania w nowym obszarze roboczym i zamknięciu bieżącego obszaru roboczego (w razie potrzeby). To zachowanie domyślne można zastąpić, pozostawiając otwarty bieżący obszar roboczy, zgodnie z opisem w sekcji [Otwórz drugie rozwiązanie](#open-a-second-solution-inside-a-single-instance) .

## <a name="open-a-second-instance-of-visual-studio-for-mac"></a>Otwórz drugie wystąpienie Visual Studio dla komputerów Mac

Aby otworzyć drugie wystąpienie zintegrowanego środowiska programistycznego (IDE), kliknij prawym przyciskiem myszy ikonę programu Visual Studio w folderze Dock lub **Applications** , a następnie wybierz pozycję **nowe wystąpienie**.

![Zrzut ekranu przedstawiający opcję menu nowe wystąpienie na kliknięciu prawym przyciskiem myszy ikony programu Visual Studio](media/open-new-instance.png)

## <a name="open-a-second-solution-inside-a-single-instance"></a>Otwórz drugie rozwiązanie w ramach jednego wystąpienia

Aby otworzyć drugie rozwiązanie obok pierwszego rozwiązania, wykonaj następujące czynności:

1. Gdy pierwsze rozwiązanie jest już otwarte, wybierz pozycję **plik**  >  **Otwórz**.
2. Przejrzyj system plików, aby znaleźć istniejące rozwiązanie.
3. Wybierz plik **. sln** , a następnie wybierz **Opcje** :

    ![Zrzut ekranu przedstawiający Visual Studio dla komputerów Mac, z wyróżnionym plikiem. sln i opcjami](media/open-multiple-solutions-image3.png)

4. Wyczyść pole **Zamknij bieżący obszar roboczy** :

    ![Zrzut ekranu przedstawiający okno dialogowe Opcje z wyczyszczonym polem Zamknij bieżący obszar roboczy](media/open-multiple-solutions-image1.png)

5. Wybierz pozycję **Otwórz** , aby otworzyć drugie rozwiązanie w oknie rozwiązanie.

Alternatywnie, jeśli ostatnio otwarto rozwiązanie, można wykonać następujące czynności:

1. Przejdź do **pliku**  >  **najnowsze rozwiązania**.

    ![Zrzut ekranu przedstawiający menu ostatnich rozwiązań](media/open-multiple-solutions-image2.png)

1. Naciśnij i przytrzymaj klawisz **Ctrl** i wybierz rozwiązanie. Ta kombinacja otwiera drugie rozwiązanie w oknie rozwiązania.

## <a name="related-video"></a>Pokrewne wideo

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Work-With-Multiple-Solutions/player]
