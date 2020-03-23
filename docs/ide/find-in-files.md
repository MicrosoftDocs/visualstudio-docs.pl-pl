---
title: Znajdź w plikach
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.findreplace.findinfiles
- vs.findinfiles
helpviewer_keywords:
- objects [Visual Studio], finding
- text searches, replacing text
- objects [Visual Studio], searching for
- Find and Replace window, Find in Files tab
- text searches, Find and Replace window
- documents, searching
- files, searching
- Find in Files tab, Find and Replace window
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e1f067df647f843819e085f283005606699f3bb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595478"
---
# <a name="find-in-files"></a>Znajdź w plikach

**Znajdź w plikach** umożliwia wyszukiwanie określonego zestawu plików. Znalezione dopasowania i podjęte akcje są wyświetlane w oknie **Znajdź wyniki** wybranym w obszarze **Opcje wyników**.

Do wyświetlenia **funkcji Znajdź w oknie Znajdź w** oknie Znajdź i **zamień** można użyć dowolnej z następujących metod.

## <a name="to-display-find-in-files"></a>Aby wyświetlić pozycję Znajdź w plikach

1. Na pasku menu wybierz pozycję **Edytuj** > **znajdź i zamień**.

1. Wybierz pozycję **Znajdź w plikach**.

Aby anulować operację Znajdź, naciśnij klawisz **Ctrl** + **Break**.

> [!NOTE]
> Narzędzie Znajdź i zamień nie `Hidden` wyszukuje katalogów z atrybutem lub `System` atrybutem.

## <a name="find-what"></a>Znajdź

Aby wyszukać nowy ciąg tekstowy lub wyrażenie, należy określić je w polu. Aby wyszukać dowolny z 20 ciągów, które ostatnio wyszukiwano, otwórz listę rozwijaną i wybierz ciąg. Wybierz sąsiedni przycisk **Konstruktora wyrażeń,** jeśli chcesz użyć jednego lub więcej wyrażeń regularnych w ciągu wyszukiwania. Aby uzyskać więcej informacji, zobacz [Używanie wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

> [!NOTE]
> Przycisk **Konstruktora wyrażeń** będzie włączony tylko wtedy, gdy w obszarze **Opcje znajdowania**wybrano opcję **Użyj wyrażeń regularnych** .

## <a name="look-in"></a>Zajrzyj do

Opcja wybrana z listy rozwijanej **Szukaj w** określa, czy **wyszukiwanie w plikach** umożliwia wyszukiwanie tylko w aktualnie aktywnych plikach, czy we wszystkich plikach przechowywanych w określonych folderach. Wybierz zakres wyszukiwania z listy lub kliknij przycisk **Przeglądaj (...)** , aby wyświetlić okno dialogowe **Wybieranie folderów wyszukiwania** i wprowadzić własny zestaw katalogów. Można również wpisać ścieżkę bezpośrednio w polu **Szukaj w.**

> [!WARNING]
> W opcjach **Całe rozwiązanie** lub **Bieżący projekt** pliki projektów i rozwiązań nie są przeszukiwane. Jeśli chcesz szukać w plikach projektu, wybierz folder wyszukiwania.

> [!NOTE]
> Jeśli wybrana opcja **Szukaj w** powoduje przeszukanie pliku, który został wyewidencjonowany z kontroli kodu źródłowego, przeszukiwana jest tylko wersja tego pliku pobrana na komputer lokalny.

## <a name="include-subfolders"></a>Uwzględnij podfoldery

Określa, że będą przeszukiwane podfoldery folderu **Szukaj w** folderze.

## <a name="find-options"></a>Znajdź opcje

Można rozwinąć lub zwinąć sekcję **Opcje znajdowania.** Można wybrać lub wyczyścić następujące opcje:

**Uwzględnij wielkość liter**

Gdy ta opcja jest zaznaczona, wyszukiwanie **wyników wyszukiwania** będzie miało rozróżnianą wielkość liter

**Dopasuj całe słowo**

Po wybraniu tej opcji okna **Znajdź wyniki** zwracają tylko dopasowania całego wyrazu.

**Używanie wyrażeń regularnych**

Jeśli to pole wyboru jest zaznaczone, można użyć specjalnych notacji do zdefiniowania wzorców tekstu, aby dopasować je w polach tekstowych **Znajdź, co** lub **Zamień na** nią. Aby uzyskać listę tych notacji, zobacz [Używanie wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

**Spójrz na te typy plików**

Ta lista wskazuje typy plików do przeszukania w katalogach **Szukaj w.** Jeśli to pole jest puste, zostaną przeszukane wszystkie pliki w katalogach **Szukaj w** katalogach.

Wybierz dowolny element na liście, aby wprowadzić wstępnie skonfigurowany ciąg wyszukiwania, który znajdzie pliki tych typów.

## <a name="result-options"></a>Opcje wyników

Można rozwinąć lub zwinąć sekcję **Opcje wyników.** Można wybrać lub wyczyścić następujące opcje:

**Znajdź wyniki 1 okno**

Po wybraniu tej opcji wyniki bieżącego wyszukiwania zastąpią zawartość okna **Znajdź wyniki 1.** To okno zostanie otwarte automatycznie, aby wyświetlić wyniki wyszukiwania. Aby ręcznie otworzyć to okno, wybierz **polecenie Inne okna** z menu **Widok** i wybierz polecenie Znajdź **wyniki 1**.

**Znajdź wyniki 2 okno**

Po wybraniu tej opcji wyniki bieżącego wyszukiwania zastąpią zawartość okna **Znajdź wyniki 2.** To okno zostanie otwarte automatycznie, aby wyświetlić wyniki wyszukiwania. Aby ręcznie otworzyć to okno, wybierz **polecenie Inne okna** z menu **Widok** i wybierz polecenie Znajdź **wyniki 2**.

**Wyświetlanie tylko nazw plików**

Wyświetla listę plików zawierających dopasowania wyszukiwania, a nie wyświetlanie samych dopasowań wyszukiwania.

**Dołączanie wyników**

Dołącza wyniki wyszukiwania do poprzednich wyników wyszukiwania.

## <a name="see-also"></a>Zobacz też

- [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md)
- [Zastąp w plikach](../ide/replace-in-files.md)
- [Polecenia programu Visual Studio](../ide/reference/visual-studio-commands.md)
