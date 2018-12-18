---
title: 'Porady: otwieranie wielu rozwiązań w programie Visual Studio dla komputerów Mac'
description: Dowiedz się, jak otworzyć więcej niż jednego rozwiązania w programie Visual Studio dla komputerów Mac i jak otworzyć więcej niż jedno wystąpienie aplikacji.
author: conceptdev
ms.author: crdun
ms.date: 07/19/2018
ms.assetid: 592BA4E3-8DEF-4FCD-8BA0-519A4CEEE03E
ms.openlocfilehash: 76a536f621a3c715a62b9e132dc661a2bcf8eb07
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51294932"
---
# <a name="open-multiple-solutions-or-instances-of-visual-studio-for-mac"></a>Otwórz wielu rozwiązań lub wystąpienia programu Visual Studio dla komputerów Mac

Domyślnie wszystkie aplikacje na komputerze Mac, w tym Visual Studio dla komputerów Mac, są _jednego wystąpienia_ aplikacji. Oznacza to, że jeśli aplikacji, którą chcesz używać jest już otwarty (zilustrowane kropka pod ikoną w obszarze dock), wybierając ikonę ponownie zostanie otwarty uruchomionego wystąpienia, a nie nowy. Jeśli potrzebujesz dodatkowych wystąpień aplikacji, możesz też monitować systemu, aby go otworzyć, zgodnie z opisem w [następnej sekcji](#open-a-second-instance-of-visual-studio-for-mac).

Ponadto po otwarciu rozwiązania, zachowanie domyślne jest Otwórz rozwiązanie w nowy obszar roboczy i Zamknij bieżący obszar roboczy (jeśli jest to konieczne). To zachowanie domyślne można przesłonić, przechowując bieżącego obszaru roboczego otwarte, zgodnie z opisem w [Otwórz drugie rozwiązanie](#open-a-second-solution-inside-a-single-instance) sekcji.

## <a name="open-a-second-instance-of-visual-studio-for-mac"></a>Otwórz drugie wystąpienie programu Visual Studio dla komputerów Mac

Aby otworzyć drugie wystąpienie zintegrowanego środowiska programistycznego (IDE), otwórz **terminalu** aplikacji i wprowadź następujący wiersz:

```bash
open -n "/Applications/Visual Studio.app"
```

## <a name="open-a-second-solution-inside-a-single-instance"></a>Otwórz drugie rozwiązanie wewnątrz pojedynczego wystąpienia

Aby otworzyć drugiego rozwiązań razem swoje pierwsze rozwiązanie, użyj następujących kroków:

1. Swoje pierwsze rozwiązanie już jest otwarty, wybierz **pliku** > **Otwórz**.
2. Przeglądaj system plików można znaleźć istniejącego rozwiązania.
3. Wybierz **.sln** pliku, a następnie wybierz **opcje**:

    ![Zrzut ekranu programu Visual Studio dla komputerów Mac z plikiem .sln i opcji wyróżnionych](media/open-multiple-solutions-image3.png)

4. Wyczyść **Zamknij bieżący obszar roboczy** pola:

    ![Zrzut ekranu opcji okno dialogowe, za pomocą Zamknij bieżący obszar roboczy wyczyszczone pole wyboru](media/open-multiple-solutions-image1.png)

5. Wybierz **Otwórz** otworzyć drugim rozwiązaniem w konsoli rozwiązania.

Alternatywnie zostało ostatnio otwarte rozwiązanie, można użyć następujących czynności:

1. Przejdź do **pliku** > **najnowsze rozwiązania**.

    ![Zrzut ekranu przedstawiający menu ostatnio używane rozwiązania](media/open-multiple-solutions-image2.png)

1. Naciśnij i przytrzymaj **Ctrl** klucza, a następnie wybierz rozwiązanie. Ta kombinacja otwiera drugie rozwiązanie, w konsoli rozwiązania.
