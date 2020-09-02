---
title: Identyfikowanie i dostosowywanie skrótów klawiaturowych
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e63395838d7d91170d54edbb07c0b38db548ccdf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670487"
---
# <a name="identifying-and-customizing-keyboard-shortcuts-in-visual-studio"></a>Identyfikowanie i dostosowywanie skrótów klawiaturowych w Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można zidentyfikować skróty klawiaturowe dla poleceń programu Visual Studio, dostosować te skróty i eksportować je dla innych użytkowników. Wiele skrótów zawsze wywołuje te same polecenia, ale zachowanie skrótu może zależeć od następujących warunków:

- Które domyślne ustawienia środowiska wybrano podczas pierwszego uruchomienia programu Visual Studio (na przykład ogólne ustawienia projektowania lub Visual C#).

- Czy dostosowywałeś zachowanie danego skrótu.

- W którym kontekście jesteś w momencie wybierania skrótu. Na przykład skrót F2 wywołuje polecenie Edit.EditCell, jeśli używasz Projektanta ustawień, i polecenie File.Rename, jeśli używasz Eksploratora zespołów.

  Niezależnie od ustawień, dostosowania i kontekstu, można zawsze znaleźć i zmienić skrót klawiaturowy w oknie dialogowym **Opcje** . Możesz również wyszukać domyślne skróty klawiaturowe kilku poleceń w [domyślnych skrótach klawiaturowych dla często używanych poleceń](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md)i można znaleźć pełną listę wszystkich skrótów domyślnych (na podstawie ogólnych ustawień deweloperskich) w [domyślnych skrótach klawiaturowych](../ide/default-keyboard-shortcuts-in-visual-studio.md).

  **W tym temacie**

- [Identyfikowanie skrótu klawiaturowego](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md#bkmk_identify)

- [Dostosowywanie skrótu klawiaturowego](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md#bkmk_assign)

- [Udostępnianie niestandardowych skrótów klawiaturowych](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md#bkmk_transfer)

  Jeśli skrót jest przypisany do polecenia wyłącznie w kontekście globalnym, ten skrót zawsze będzie wywoływał dane polecenie. Jednak skrót może być przypisany do jednego polecenia w kontekście globalnym i innego polecenia w określonym kontekście. Gdy korzystasz z takiego skrótu podczas pracy w określonym kontekście, skrót wywołuje polecenie odpowiadające temu kontekstowi, a nie kontekstowi globalnemu.

> [!NOTE]
> Twoje ustawienia i wersja programu Visual Studio mogą zmienić nazwy i lokalizacje poleceń menu oraz opcje, które pojawiają się w oknach dialogowych. Ten temat jest oparty na **ogólnych ustawieniach deweloperskich**.

## <a name="identifying-a-keyboard-shortcut"></a><a name="bkmk_identify"></a> Identyfikowanie skrótu klawiaturowego

1. Na pasku menu wybierz **Narzędzia**, **Opcje**.

2. Rozwiń węzeł **środowisko**, a następnie wybierz pozycję **Klawiatura**.

     ![Wyświetl skróty klawiaturowe w oknie dialogowym Opcje](../ide/media/optionskeyboard.png "OptionsKeyboard")

3. W polu **Pokaż polecenia zawierające** wpisz wszystko lub część nazwy polecenia bez spacji.

     Można na przykład znaleźć polecenia dla **SolutionExplorer**.

4. Na liście, wybierz odpowiednie polecenie.

     Na przykład możesz wybrać **View. SolutionExplorer**.

5. Jeśli polecenie ma skrót klawiaturowy, pojawia się w **skrótach dla wybranej listy poleceń** .

     ![Wyświetl skrót do określonego polecenia](../ide/media/viewshortcut.png "ViewShortcut")

## <a name="customizing-a-keyboard-shortcut"></a><a name="bkmk_assign"></a> Dostosowywanie skrótu klawiaturowego

1. Na pasku menu wybierz **Narzędzia**, **Opcje**.

2. Rozwiń folder **środowisko** , a następnie wybierz pozycję **Klawiatura**.

     ![Wyświetl skróty klawiaturowe w oknie dialogowym Opcje](../ide/media/optionskeyboard.png "OptionsKeyboard")

3. W polu **Pokaż polecenia zawierające** wpisz wszystko lub część nazwy polecenia bez spacji.

     Można na przykład znaleźć polecenia dla **SolutionExplorer**.

4. Z listy wybierz polecenie, do którego chcesz przypisać skrót klawiaturowy.

5. Na liście **Użyj nowego skrótu w** wybierz obszar funkcji, w którym chcesz użyć skrótu.

     Na przykład, możesz wybrać **globalne** , jeśli chcesz, aby skrót działał we wszystkich kontekstach. Można użyć dowolnego skrótu, który nie jest mapowany (jako globalny) w innym edytorze. W przeciwnym razie edytor zastępuje skrót.

    > [!NOTE]
    > Nie można przypisać następujących kluczy jako części skrótu klawiaturowego w języku **globalnym**: Print Scrn/sys RQ, Scroll Lock, Pause/Break, TAB, Caps Lock, INSERT, Home, end, Page Up, Page Down, logo Windows, Key aplikacji, dowolne klawisze strzałek lub ENTER; Num Lock, DELETE lub Clear na klawiaturze numerycznej; lub Ctrl + Alt + Delete.

6. W polu **naciśnij klawisz skrótu** Wprowadź skrót, którego chcesz użyć.

    > [!NOTE]
    > Można utworzyć skrót, który łączy literę z klawiszem Alt, Ctrl lub oboma. Można też utworzyć skrót, który łączy klawisz Shift i literę z klawiszem Alt, Ctrl lub oboma.

     Jeśli skrót jest już przypisany do innego polecenia, pojawia się w polu **skrót aktualnie używany przez** . W takim przypadku należy wybrać klawisz Backspace, aby usunąć skrót, przed wpisaniem innego.

     ![Określ inny skrót dla polecenia](../ide/media/reassignshortcut.png "ReassignShortcut")

7. Wybierz przycisk **Przypisz** .

    > [!NOTE]
    > Jeśli określisz inny skrót dla polecenia, wybierz przycisk **Przypisz** , a następnie wybierz przycisk **Anuluj** , okno dialogowe zostanie zamknięte, ale zmiana nie zostanie wycofana.

## <a name="sharing-custom-keyboard-shortcuts"></a><a name="bkmk_transfer"></a> Udostępnianie niestandardowych skrótów klawiaturowych
 Możesz udostępniać własne skróty, eksportując je do pliku, a następnie przekazując plik innym osobom, aby mogły importować dane.

#### <a name="to-export-only-keyboard-shortcuts"></a>Aby wyeksportować tylko skróty klawiaturowe

1. Na pasku menu wybierz kolejno opcje **Narzędzia**, **Importuj i Eksportuj ustawienia**.

2. Wybierz opcję **Eksportuj wybrane ustawienia środowiska**, a następnie wybierz przycisk **dalej** .

3. W obszarze **jakie ustawienia chcesz eksportować?** wyczyść pole wyboru **wszystkie ustawienia** , rozwiń **Opcje**, a następnie rozwiń **środowisko**.

4. Zaznacz pole wyboru **Klawiatura** , a następnie wybierz przycisk **dalej** .

     ![Eksportuj tylko dostosowane skróty klawiaturowe](../ide/media/exportshortcuts.png "ExportShortcuts")

5. W polu jak **chcesz nazwać plik ustawień?** i **Zapisz plik My Settings w tym katalogu** , pozostaw wartości domyślne lub określ różne wartości, a następnie wybierz przycisk **Zakończ** .

     Domyślnie skróty są zapisywane w pliku w folderze %USERPROFILE%\Documents\Visual Studio 2013\Settings. Nazwa pliku odzwierciedla datę, kiedy zostały wyeksportowane ustawienia, a rozszerzenie to .vssettings.

#### <a name="to-import-only-keyboard-shortcuts"></a>Aby zaimportować tylko skróty klawiaturowe

1. Na pasku menu wybierz kolejno opcje **Narzędzia**, **Importuj i Eksportuj ustawienia**.

2. Wybierz przycisk opcji **Importuj wybrane ustawienia środowiska** , a następnie wybierz przycisk **dalej** .

3. Wybierz przycisk opcji **nie, tylko zaimportuj nowe ustawienia, zastępując Moje bieżące ustawienia** , a następnie wybierz przycisk **dalej** .

4. W obszarze **Moje ustawienia**wybierz plik zawierający skróty, które chcesz zaimportować, lub kliknij przycisk **Przeglądaj** , aby zlokalizować właściwy plik.

5. Wybierz przycisk **dalej** .

6. W obszarze **jakie ustawienia chcesz zaimportować?** wyczyść pole wyboru **wszystkie ustawienia** , rozwiń **Opcje**, a następnie rozwiń **środowisko**.

7. Zaznacz pole wyboru **Klawiatura** , a następnie wybierz przycisk **Zakończ** .

     ![Importuj tylko dostosowane skróty klawiaturowe](../ide/media/importshortcuts.png "ImportShortcuts")

## <a name="see-also"></a>Zobacz też
 [Ułatwienia dostępu w Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)
