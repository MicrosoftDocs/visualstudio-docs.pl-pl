---
title: 'Jak: Otwórz wiele rozwiązań'
description: Dowiedz się, jak otworzyć więcej niż jedno rozwiązanie w programie Visual Studio dla komputerów Mac i jak otworzyć więcej niż jedno wystąpienie aplikacji.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 07/19/2018
ms.assetid: 592BA4E3-8DEF-4FCD-8BA0-519A4CEEE03E
ms.custom: video
ms.openlocfilehash: 3568ab8dd68deb83d668c6e46f556516e29a81ae
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "74985001"
---
# <a name="open-multiple-solutions-or-instances-of-visual-studio-for-mac"></a>Otwieranie wielu rozwiązań lub wystąpień programu Visual Studio dla komputerów Mac

Domyślnie wszystkie aplikacje na komputerze Mac, w tym Visual Studio dla komputerów Mac, są aplikacjami _z pojedynczym wystąpieniem._ Oznacza to, że jeśli aplikacja, której chcesz użyć, jest już otwarta (zilustrowana kropką pod ikoną w stacji dokującej), wybranie ikony ponownie otwiera uruchomione wystąpienie, a nie nowe. Jeśli potrzebujesz dodatkowych wystąpień aplikacji, możesz poprosić system o otwarcie jej, zgodnie z opisem w [następnej sekcji](#open-a-second-instance-of-visual-studio-for-mac).

Ponadto po otwarciu rozwiązania domyślnym zachowaniem jest otwarcie rozwiązania w nowym obszarze roboczym i zamknięcie bieżącego obszaru roboczego (jeśli to konieczne). To domyślne zachowanie można zastąpić, utrzymując bieżący obszar roboczy otwarty, zgodnie z opisem w sekcji [Otwórz drugie rozwiązanie.](#open-a-second-solution-inside-a-single-instance)

## <a name="open-a-second-instance-of-visual-studio-for-mac"></a>Otwieranie drugiego wystąpienia programu Visual Studio dla komputerów Mac

Aby otworzyć drugie wystąpienie zintegrowanego środowiska programistycznego (IDE), otwórz aplikację **Terminal** i wprowadź następujący wiersz:

```bash
open -n "/Applications/Visual Studio.app"
```

## <a name="open-a-second-solution-inside-a-single-instance"></a>Otwieranie drugiego rozwiązania wewnątrz pojedynczego wystąpienia

Aby otworzyć drugie rozwiązanie wraz z pierwszym rozwiązaniem, należy wykonać następujące czynności:

1. Gdy pierwsze rozwiązanie jest już otwarte, wybierz **pozycję Otwórz plik** > **Open**.
2. Przejrzyj system plików, aby znaleźć istniejące rozwiązanie.
3. Wybierz plik **.sln** i wybierz opcję **Opcje:**

    ![Zrzut ekranu przedstawiający program Visual Studio dla komputerów Mac z wyróżnionym plikiem .sln i opcjami](media/open-multiple-solutions-image3.png)

4. Wyczyść pole **Zamknij bieżący obszar roboczy:**

    ![Zrzut ekranu przedstawiający okno dialogowe Opcje z wyczyszczonym polem Zamknij bieżący obszar roboczy](media/open-multiple-solutions-image1.png)

5. Wybierz **otwórz,** aby otworzyć drugie rozwiązanie w panelu rozrachowy.

Alternatywnie, jeśli niedawno otwarto rozwiązanie, można wykonać następujące kroki:

1. Przejdź do **pliku** > **najnowszych rozwiązań**.

    ![Zrzut ekranu przedstawiający menu Ostatnie rozwiązania](media/open-multiple-solutions-image2.png)

1. Przytrzymaj klawisz **Ctrl** i wybierz rozwiązanie. Ta kombinacja otwiera drugie rozwiązanie w panelu rozrachowy.

## <a name="related-video"></a>Podobne wideo

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Work-With-Multiple-Solutions/player]
