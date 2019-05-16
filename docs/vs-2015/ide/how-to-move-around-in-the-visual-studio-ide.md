---
title: 'Instrukcje: Poruszanie się w środowisku IDE | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 93200995c3afa59b0a4a27aaa9c674fa17b5ee3f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685599"
---
# <a name="how-to-move-around-in-the-visual-studio-ide"></a>Instrukcje: Poruszanie się w środowisku IDE programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zintegrowanego środowiska programistycznego (IDE) został zaprojektowany umożliwia przenoszenie okna okna i plikami na kilka różnych sposobów, w zależności od wymagań preferencji lub projektu. Można przełączać się między otwartych plików w edytorze lub przechodzić przez wszystkie aktywne okna narzędzi w IDE. Możesz również przełączyć bezpośrednio do dowolnego otwartego pliku w edytorze, niezależnie od kolejności, w którym ostatniego dostępu. Te funkcje może pomóc zwiększyć produktywność podczas pracy w środowisku IDE.

> [!NOTE]
> Dostępne opcje w oknach dialogowych i nazwy i lokalizacje poleceń menu, który zostanie wyświetlony, mogą różnić się od opisanych w pomocy, w zależności od ustawień aktywnych lub wersji. Ta strona pomocy został napisany z **ogólnych ustawieniach projektowych** na uwadze. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="keyboard-shortcuts"></a>Skróty klawiaturowe
 Prawie wszystkie polecenia menu w programie Visual Studio ma skrót klawiaturowy. Można również utworzyć własne skróty niestandardowe. Aby uzyskać więcej informacji, zobacz [określenie i dostosowywanie skrótów klawiaturowych](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

## <a name="navigating-among-files-in-the-editor"></a>Nawigacja pomiędzy pliki w edytorze
 Aby przeglądać pliki otwarte w edytorze, można użyć kilku metod. Możesz poruszać się między pliki w kolejności, w której możesz uzyskiwać do nich dostęp, użyj nawigatora środowiska IDE, aby szybko znaleźć żadnych plików, które są aktualnie otwarte lub numeru pin ulubionych plików do karty, również tak, że są one zawsze widoczne.

 Przejdź wstecz i przejdź do przodu przełączać się między otwartych plików w edytorze, na podstawie kolejności uzyskano, podobnie do przodu wobec Twojej historii przeglądania w programie Internet Explorer i kopii.

#### <a name="to-move-through-open-files-in-order-of-use"></a>Aby przeglądać otwarte pliki w kolejności użycia

- Aby aktywować otwarte dokumenty w kolejności, w której ostatnio były przez nich wspomnieliśmy, naciśnij klawisze CTRL + ZNAK MINUS.

- Aby aktywować otwartymi dokumentami w odwrotnej kolejności niż kolejność, naciśnij klawisze CTRL + SHIFT + ZNAK MINUS.

  > [!NOTE]
  > **Przejdź wstecz** i **Nawiguj do przodu** również znajduje się na **widoku** menu.

  Możesz również przełączyć się do określonego pliku, Otwórz w edytorze, niezależnie od tego, kiedy ostatniego dostępu do pliku, przy użyciu **Nawigator IDE**, **aktywnych plików** listy w edytorze lub **Windows** okno dialogowe.

  **Nawigator IDE** działa podobnie do przełącznika aplikacji Windows. Nie jest dostępne z menu i jest możliwy tylko za pomocą klawiszy skrótów. Jedno z dwóch poleceń uzyskiwać dostęp do **Nawigator IDE** (pokazana poniżej), aby przechodzić między plików, w zależności od kolejności, w której chcesz przechodzić między.

  ![Nawigator IDE programu Visual Studio](../ide/media/vs2015-ide-navigator.png "VS2015_IDE_Navigator")

  `Window.PreviousDocumentWindowNav` Umożliwia przeniesienie do pliku, który został ostatnio używane i `Window.NextDocumentWindowNav` umożliwia przeniesienie w odwrotnej kolejności. Przypisuje ogólnych ustawieniach projektowych, CTRL + SHIFT + TAB, aby `Window.PreviousDocumentWindowNav` i CTRL + TAB, aby `Window.NextDocumentWindowNav`.

> [!NOTE]
> Kombinację ustawień, którego używasz nie ma jeszcze kombinacji klawiszy skrótów, przypisany do tego polecenia, można przypisać własne niestandardowe polecenie wartości za pomocą **klawiatury** strony **opcje** okna dialogowego pole. Aby uzyskać więcej informacji, zobacz [określenie i dostosowywanie skrótów klawiaturowych](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

#### <a name="to-switch-to-specific-files-in-the-editor"></a>Aby przełączyć się do określonych plików w edytorze

- Naciśnij klawisze CTRL + TAB, aby wyświetlić **Nawigator IDE**. Naciśnij i przytrzymaj klawisz CTRL i naciskaj klawisz TAB dopiero po wybraniu pliku, który chcesz przełączyć się do.

    > [!TIP]
    > Aby odwrócić kolejność, w którym można przejść przez **aktywnych plików** listy, naciśnij i przytrzymaj klawisze CTRL + SHIFT i naciśnij klawisz TAB.

     \- lub —

- W prawym górnym rogu edytora wybierz **aktywnych plików** przycisk, a następnie wybierz plik z listy, aby przełączyć się do.

     \- lub —

- Na pasku menu wybierz **okna**, **Windows**.

- Na liście, wybierz plik, który chcesz wyświetlić, a następnie wybierz **Aktywuj**.

## <a name="navigating-among-tool-windows-in-the-ide"></a>Nawigacja pomiędzy narzędzie Windows w środowisku IDE
 **Nawigator IDE** również otworzyć pozwala przechodzić do okna narzędzi, masz w środowisku IDE. Jedno z dwóch poleceń uzyskiwać dostęp do **Nawigator IDE** umożliwia przechodzenie między okien narzędzi w zależności od kolejności, w której chcesz przechodzić między. `Window.PreviousToolWindowNav` Umożliwia przeniesienie do pliku, który został ostatnio używane i `Window.NextToolWindowNav` umożliwia przeniesienie w odwrotnej kolejności. Przypisuje ogólnych ustawieniach projektowych, SHIFT + ALT + F7, aby `Window.PreviousDocumentWindowNav` i ALT + F7, aby `Window.NextDocumentWindowNav`.

> [!NOTE]
> Kombinację ustawień, którego używasz nie ma jeszcze kombinacji klawiszy skrótów, przypisany do tego polecenia, można przypisać własne niestandardowe polecenie wartości za pomocą **klawiatury** strony **opcje** okna dialogowego pole. Aby uzyskać więcej informacji, zobacz [określenie i dostosowywanie skrótów klawiaturowych](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

#### <a name="to-switch-to-a-specific-tool-window-in-the-ide"></a>Aby przełączyć się do okna narzędzi określonych w środowisku IDE

- Naciśnij klawisze ALT + F7, aby wyświetlić **Nawigator IDE**. Naciśnij i przytrzymaj klawisz ALT i naciskaj klawisz F7, dopóki nie wybierzesz okna, które zamierzasz przejdź do.

    > [!TIP]
    > Aby odwrócić kolejność, w którym można przejść przez **Active narzędzie Windows** listy, naciśnij i przytrzymaj klawisze ALT + SHIFT i naciśnij klawisz F7.

## <a name="see-also"></a>Zobacz też
 [Dostosowywanie układów okien](../ide/customizing-window-layouts-in-visual-studio.md) [domyślne skróty klawiaturowe](../ide/default-keyboard-shortcuts-in-visual-studio.md)
