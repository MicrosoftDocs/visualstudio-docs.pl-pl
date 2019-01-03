---
title: Jak poruszać się w środowisku IDE
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- environments [Visual Studio], navigation
- documents [Visual Studio], navigating
- IDE, navigation
- navigation [Visual Studio]
- files [Visual Studio], navigating between
- windows [Visual Studio], navigating
- Window.NextDocumentWindowNav
- IDE navigator
ms.assetid: 6c36b6eb-c93f-496b-af08-4199f7afd8bd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bf2c00350b6b366e0e1d5ea02a8e260c8927b348
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53988887"
---
# <a name="how-to-move-around-in-the-visual-studio-ide"></a>Instrukcje: Poruszanie się w środowisku IDE programu Visual Studio

Zintegrowanego środowiska programistycznego (IDE) został zaprojektowany umożliwia przenoszenie okna okna i plikami na kilka różnych sposobów, w zależności od wymagań preferencji lub projektu. Można przełączać się między otwartych plików w edytorze lub przechodzić przez wszystkie aktywne okna narzędzi w IDE. Możesz również przełączyć bezpośrednio do dowolnego otwartego pliku w edytorze, niezależnie od kolejności, w którym ostatniego dostępu. Te funkcje może pomóc zwiększyć produktywność podczas pracy w środowisku IDE.

> [!NOTE]
> Dostępne opcje w oknach dialogowych i nazwy i lokalizacje poleceń menu, który zostanie wyświetlony, mogą różnić się z tym, co opisano w tym artykule, w zależności od ustawień aktywnych lub wersji. W tym artykule został napisany z **ogólne** ustawień na uwadze. Aby zmienić swoje ustawienia, na przykład aby **ogólne** lub **Visual C++** ustawienia, wybierz **narzędzia** > **Import i eksport ustawień**, a następnie wybierz **Resetuj wszystkie ustawienia**.

## <a name="keyboard-shortcuts"></a>Skróty klawiaturowe

Prawie wszystkie polecenia menu w programie Visual Studio ma skrót klawiaturowy. Można również utworzyć własne skróty niestandardowe. Aby uzyskać więcej informacji, zobacz [identyfikowanie i dostosowywanie skrótów klawiaturowych](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

## <a name="navigate-among-files-in-the-editor"></a>Nawigowanie między pliki w edytorze

Aby przeglądać pliki otwarte w edytorze, można użyć kilku metod. Możesz poruszać się między pliki w kolejności, w której możesz uzyskiwać do nich dostęp, użyj nawigatora środowiska IDE, aby szybko znaleźć żadnych plików, które są aktualnie otwarte lub numeru pin ulubionych plików do karty, również tak, że są one zawsze widoczne.

Przejdź wstecz i nawigować do przodu cyklu otwarte pliki w edytorze, na podstawie kolejności, w jakiej były używane, wiele kopii, takich jak i do przodu wobec Twojej historii przeglądania w programie Internet Explorer.

### <a name="to-move-through-open-files-in-order-of-use"></a>Aby przeglądać otwarte pliki w kolejności użycia

-   Aby uaktywnić otwarte dokumenty w kolejności ich zostały ostatnio korzystał z usług, naciśnij **Ctrl**+**-**.

-   Aby uaktywnić otwartymi dokumentami w odwrotnej kolejności niż kolejność, naciśnij **Ctrl**+**Shift**+**-**.

    > [!NOTE]
    > **Przejdź wstecz** i **Nawiguj do przodu** również znajduje się na **widoku** menu.

Możesz również przełączyć się do określonego pliku, Otwórz w edytorze, niezależnie od tego, kiedy ostatniego dostępu do pliku, przy użyciu **Nawigator IDE**, **aktywnych plików** listy w edytorze lub **Windows** okno dialogowe.

**Nawigator IDE** działa podobnie do przełącznika aplikacji Windows. Nie jest dostępne z menu i jest możliwy tylko za pomocą klawiszy skrótów. Jedno z dwóch poleceń uzyskiwać dostęp do **Nawigator IDE** (pokazana poniżej), aby przechodzić między plików, w zależności od kolejności, w której chcesz przechodzić między.

![Nawigator IDE programu Visual Studio](../ide/media/vs2015_ide_navigator.png)

`Window.PreviousDocumentWindowNav` Umożliwia przeniesienie do pliku, który został ostatnio używane i `Window.NextDocumentWindowNav` umożliwia przeniesienie w odwrotnej kolejności. **Ogólnych ustawieniach projektowych** przypisuje **Shift**+**Alt**+**F7** do `Window.PreviousDocumentWindowNav` i **Alt**  + **F7** do `Window.NextDocumentWindowNav`.

> [!NOTE]
> Kombinację ustawień, którego używasz nie ma jeszcze kombinacji klawiszy skrótów, przypisany do tego polecenia, można przypisać własne niestandardowe polecenie wartości za pomocą **klawiatury** strony **opcje** okna dialogowego pole. Aby uzyskać więcej informacji, zobacz [identyfikowanie i dostosowywanie skrótów klawiaturowych](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

### <a name="to-switch-to-specific-files-in-the-editor"></a>Aby przełączyć się do określonych plików w edytorze

-   Naciśnij klawisz **Ctrl**+**kartę** do wyświetlenia **Nawigator IDE**. Naciśnij i przytrzymaj **Ctrl** klucz, a następnie naciśnij klawisz **kartę** aż do momentu, gdy wybierz plik, który chcesz przełączyć się do.

    > [!TIP]
    > Aby odwrócić kolejność, w którym można przejść przez **aktywnych plików** listy, naciśnij i przytrzymaj **Ctrl**+**Shift** kluczy, a następnie naciśnij klawisz **kartę**.

    \- lub —

-   W prawym górnym rogu edytora wybierz **aktywnych plików** przycisk, a następnie wybierz plik z listy, aby przełączyć się do.

    \- lub —

-   Na pasku menu wybierz **okna** > **Windows**.

-   Na liście, wybierz plik, który chcesz wyświetlić, a następnie wybierz **Aktywuj**.

## <a name="navigate-among-tool-windows-in-the-ide"></a>Przechodzenie między oknami narzędzi w IDE

**Nawigator IDE** również otworzyć pozwala przechodzić do okna narzędzi, masz w środowisku IDE. Jedno z dwóch poleceń uzyskiwać dostęp do **Nawigator IDE** umożliwia przechodzenie między okien narzędzi w zależności od kolejności, w której chcesz przechodzić między. `Window.PreviousToolWindowNav` Umożliwia przeniesienie do pliku, który został ostatnio używane i `Window.NextToolWindowNav` umożliwia przeniesienie w odwrotnej kolejności. **Ogólnych ustawieniach projektowych** przypisuje **Shift**+**Alt**+**F7** do `Window.PreviousDocumentWindowNav` i **Alt**  + **F7** do `Window.NextDocumentWindowNav`.

> [!NOTE]
> Kombinację ustawień, którego używasz nie ma jeszcze kombinacji klawiszy skrótów, przypisany do tego polecenia, można przypisać własne niestandardowe polecenie wartości za pomocą **klawiatury** strony **opcje** okna dialogowego pole. Aby uzyskać więcej informacji, zobacz [identyfikowanie i dostosowywanie skrótów klawiaturowych](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

### <a name="to-switch-to-a-specific-tool-window-in-the-ide"></a>Aby przełączyć się do okna narzędzi określonych w środowisku IDE

-   Naciśnij klawisz **Alt**+**F7** do wyświetlenia **Nawigator IDE**. Naciśnij i przytrzymaj **Alt** klucz, a następnie naciśnij klawisz **F7** aż do momentu, gdy wybierz okno, o których chcesz przełączyć się do.

    > [!TIP]
    > Aby odwrócić kolejność, w którym można przejść przez **Active narzędzie Windows** listy, naciśnij i przytrzymaj **Shift**+**Alt** kluczy, a następnie naciśnij klawisz **F7**.

## <a name="see-also"></a>Zobacz także

- [Dostosowywanie układów okien](../ide/customizing-window-layouts-in-visual-studio.md)
- [Domyślne skróty klawiaturowe](../ide/default-keyboard-shortcuts-in-visual-studio.md)