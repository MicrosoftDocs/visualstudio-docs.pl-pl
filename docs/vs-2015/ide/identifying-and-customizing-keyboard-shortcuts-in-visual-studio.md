---
title: Identyfikowanie i dostosowywanie skrótów klawiaturowych
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Environment.Keyboard
helpviewer_keywords:
- keyboard shortcuts [Visual Studio], customizing
- importing shortcut keys [Visual Studio]
- shortcut key combinations [Visual Studio]
- commands [Visual Studio], shortcut keys
- custom shortcut keys [Visual Studio]
- customizing keyboard shortcuts [Visual Studio]
- exporting shortcut keys [Visual Studio]
ms.assetid: d2774be2-60a4-4d6f-95f1-79d0d9e55b56
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3dbb6c9c778ed1010c90a901fa9ee9e2e9299252
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53931180"
---
# <a name="identifying-and-customizing-keyboard-shortcuts-in-visual-studio"></a>Identyfikowanie i dostosowywanie skrótów klawiaturowych w Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można zidentyfikować skróty klawiaturowe dla poleceń programu Visual Studio, dostosować te skróty i eksportować je dla innych użytkowników. Wiele skrótów zawsze wywołuje te same polecenia, ale zachowanie skrótu może zależeć od następujących warunków:

- Które domyślne ustawienia środowiska wybrano podczas pierwszego uruchomienia programu Visual Studio (na przykład ogólne ustawienia projektowania lub Visual C#).

- Czy dostosowywałeś zachowanie danego skrótu.

- W którym kontekście jesteś w momencie wybierania skrótu. Na przykład skrót F2 wywołuje polecenie Edit.EditCell, jeśli używasz Projektanta ustawień, i polecenie File.Rename, jeśli używasz Eksploratora zespołów.

  Niezależnie od ustawień, dostosowania i kontekstu, zawsze możesz znaleźć i zmienić skrót klawiaturowy w **opcje** okno dialogowe. Możesz również wyszukać domyślne skróty klawiaturowe dla kilkudziesięciu poleceń w [domyślne skróty klawiaturowe dla często używane polecenia](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md), możesz znaleźć, aby uzyskać pełną listę wszystkich skrótów domyślnych (na podstawie ogólnego projektowania Ustawienia) w [domyślne skróty klawiaturowe](../ide/default-keyboard-shortcuts-in-visual-studio.md).

  **W tym temacie**

- [Identyfikowanie skrótu klawiaturowego](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md#bkmk_identify)

- [Dostosowywanie skrótu klawiaturowego](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md#bkmk_assign)

- [Udostępnianie niestandardowych skrótów klawiaturowych](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md#bkmk_transfer)

  Jeśli skrót jest przypisany do polecenia wyłącznie w kontekście globalnym, ten skrót zawsze będzie wywoływał dane polecenie. Jednak skrót może być przypisany do jednego polecenia w kontekście globalnym i innego polecenia w określonym kontekście. Gdy korzystasz z takiego skrótu podczas pracy w określonym kontekście, skrót wywołuje polecenie odpowiadające temu kontekstowi, a nie kontekstowi globalnemu.

> [!NOTE]
>  Twoje ustawienia i wersja programu Visual Studio mogą zmienić nazwy i lokalizacje poleceń menu oraz opcje, które pojawiają się w oknach dialogowych. Ten temat opiera się na **ogólnych ustawieniach projektowych**.

##  <a name="bkmk_identify"></a> Identyfikowanie skrótu klawiaturowego

1.  Na pasku menu wybierz **narzędzia**, **opcje**.

2.  Rozwiń **środowiska**, a następnie wybierz **klawiatury**.

     ![Wyświetlić skróty klawiaturowe w oknie dialogowym Opcje](../ide/media/optionskeyboard.png "OptionsKeyboard")

3.  W **Pokaż polecenia zawierające** wpisz całość lub część nazwy polecenia bez spacji.

     Na przykład można znaleźć polecenia dla **solutionexplorer**.

4.  Na liście, wybierz odpowiednie polecenie.

     Na przykład, można wybrać **View.SolutionExplorer**.

5.  Jeśli polecenie ma skrót klawiaturowy, pojawia się w **skróty dla wybranego polecenia** listy.

     ![Wyświetl skrót dla określonego polecenia](../ide/media/viewshortcut.png "ViewShortcut")

##  <a name="bkmk_assign"></a> Dostosowywanie skrótu klawiaturowego

1.  Na pasku menu wybierz **narzędzia**, **opcje**.

2.  Rozwiń **środowiska** folder, a następnie wybierz **klawiatury**.

     ![Wyświetlić skróty klawiaturowe w oknie dialogowym Opcje](../ide/media/optionskeyboard.png "OptionsKeyboard")

3.  W **Pokaż polecenia zawierające** wpisz całość lub część nazwy polecenia bez spacji.

     Na przykład można znaleźć polecenia dla **solutionexplorer**.

4.  Z listy wybierz polecenie, do którego chcesz przypisać skrót klawiaturowy.

5.  W **Użyj nowego skrótu** listy, wybierz obszar funkcji, w której chcesz użyć skrótu.

     Na przykład, można wybrać **Global** Jeśli chcesz, aby skrót działał we wszystkich kontekstach. Można użyć dowolnego skrótu, który nie jest mapowany (jako globalny) w innym edytorze. W przeciwnym razie edytor zastępuje skrót.

    > [!NOTE]
    >  Nie można przypisać następujących klawiszy jako części skrótów klawiaturowych w **Global**: Drukuj podręcznego/Sys Rq, Scroll Lock, Pause/Break, kartę, włączony klawisz Caps Lock, Insert, Home, End, Page Up, Page Down, klawiszy logo Windows, klucz aplikacji, za pomocą klawiszy strzałek lub Enter; Num Lock, Delete lub Clear na klawiaturze numerycznej; lub Ctrl + Alt + Delete.

6.  W **naciśnij klawisze skrótu** wprowadź skrót, którego chcesz użyć.

    > [!NOTE]
    >  Można utworzyć skrót, który łączy literę z klawiszem Alt, Ctrl lub oboma. Można też utworzyć skrót, który łączy klawisz Shift i literę z klawiszem Alt, Ctrl lub oboma.

     Jeśli skrót jest już przypisany do innego polecenia, pojawia się w **skrót aktualnie używany przez** pole. W takim przypadku należy wybrać klawisz Backspace, aby usunąć skrót, przed wpisaniem innego.

     ![Określ inny skrót dla polecenia](../ide/media/reassignshortcut.png "ReassignShortcut")

7.  Wybierz **przypisać** przycisku.

    > [!NOTE]
    >  Jeśli określisz inny skrót dla polecenia, wybierz **przypisać** przycisk, a następnie wybierz **anulować** przycisku, okno dialogowe zostanie zamknięte, ale zmiany nie zostanie wycofana.

##  <a name="bkmk_transfer"></a> Udostępnianie niestandardowych skrótów klawiaturowych
 Możesz udostępniać własne skróty, eksportując je do pliku, a następnie przekazując plik innym osobom, aby mogły importować dane.

#### <a name="to-export-only-keyboard-shortcuts"></a>Aby wyeksportować tylko skróty klawiaturowe

1.  Na pasku menu wybierz **narzędzia**, **Import i eksport ustawień**.

2.  Wybierz **Eksportuj wybrane ustawienia środowiska**, a następnie wybierz **dalej** przycisku.

3.  W obszarze **jakie ustawienia chcesz eksportować?**, wyczyść **wszystkie ustawienia** pole wyboru, rozwiń **opcje**, a następnie rozwiń węzeł **środowiska**.

4.  Wybierz **klawiatury** pole wyboru, a następnie wybierz **dalej** przycisku.

     ![Eksportowanie dostosować tylko skróty klawiaturowe](../ide/media/exportshortcuts.png "ExportShortcuts")

5.  W **co chcesz nazwać plik swoich ustawień?** i **Store plik moich ustawień w tym katalogu** pola, albo pozostaw wartości domyślne lub określ różne wartości, a następnie wybierz  **Zakończ** przycisku.

     Domyślnie skróty są zapisywane w pliku w folderze %USERPROFILE%\Documents\Visual Studio 2013\Settings. Nazwa pliku odzwierciedla datę, kiedy zostały wyeksportowane ustawienia, a rozszerzenie to .vssettings.

#### <a name="to-import-only-keyboard-shortcuts"></a>Aby zaimportować tylko skróty klawiaturowe

1.  Na pasku menu wybierz **narzędzia**, **Import i eksport ustawień**.

2.  Wybierz **Importuj ustawienia wybranego środowiska** przycisk opcji, a następnie wybierz **dalej** przycisku.

3.  Wybierz **nie, tylko zaimportuj nowe ustawienia, zastępując Moje bieżące ustawienia** przycisk opcji, a następnie wybierz **dalej** przycisku.

4.  W obszarze **Moje ustawienia**, wybierz plik zawierający skróty, które chcesz zaimportować, lub wybierz **Przeglądaj** przycisk, aby zlokalizować odpowiedni plik.

5.  Wybierz **dalej** przycisku.

6.  W obszarze **ustawienia, które chcesz zaimportować?**, wyczyść **wszystkie ustawienia** pole wyboru, rozwiń **opcje**, a następnie rozwiń węzeł **środowiska**.

7.  Wybierz **klawiatury** pole wyboru, a następnie wybierz **Zakończ** przycisku.

     ![Importuj tylko dostosować skróty klawiaturowe](../ide/media/importshortcuts.png "ImportShortcuts")

## <a name="see-also"></a>Zobacz też
 [Ułatwienia dostępu w Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)
