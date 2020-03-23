---
title: Identyfikowanie i dostosowywanie skrótów klawiaturowych
ms.date: 11/04/2016
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce87385314ec84c7c0ed9d30c806a6287bb91d9e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591336"
---
# <a name="identify-and-customize-keyboard-shortcuts-in-visual-studio"></a>Identyfikowanie i dostosowywanie skrótów klawiaturowych w programie Visual Studio

Można zidentyfikować skróty klawiaturowe dla poleceń programu Visual Studio, dostosować te skróty i eksportować je dla innych użytkowników. Wiele skrótów zawsze wywołuje te same polecenia, ale zachowanie skrótu może zależeć od następujących warunków:

- Jakie domyślne ustawienia środowiska wybrać przy pierwszym&mdash;otwarciu programu Visual Studio, na przykład ogólne rozwoju lub visual C#. (Aby uzyskać informacje na temat zmiany lub zresetowania ustawień, zobacz [Ustawienia środowiska).](environment-settings.md)

- Czy dostosowywałeś zachowanie danego skrótu.

- W którym kontekście jesteś w momencie wybierania skrótu. Na przykład skrót **F2** wywołuje `Edit.EditCell` polecenie, jeśli używasz **Projektanta ustawień** `File.Rename` i wywołuje to polecenie, jeśli używasz **Eksploratora zespołu.**

Niezależnie od ustawień, dostosowywania i kontekstu zawsze można znaleźć i zmienić skrót klawiaturowy w oknie dialogowym **Opcje.** Można również wyszukać domyślne skróty klawiaturowe dla kilkudziesięciu poleceń w [popularnych skrótów klawiaturowych](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md). Aby uzyskać pełną listę wszystkich skrótów domyślnych (na podstawie ustawień **ogólnego rozwoju),** zobacz [Wszystkie skróty klawiaturowe](../ide/default-keyboard-shortcuts-in-visual-studio.md).

Jeśli skrót jest przypisany do polecenia w kontekście *globalnym* i nie ma innych kontekstów, ten skrót zawsze będzie wywoływać to polecenie. Jednak skrót może być przypisany do jednego polecenia w kontekście globalnym i innego polecenia w określonym kontekście. Gdy korzystasz z takiego skrótu podczas pracy w określonym kontekście, skrót wywołuje polecenie odpowiadające temu kontekstowi, a nie kontekstowi globalnemu.

> [!NOTE]
> Twoje ustawienia i wersja programu Visual Studio mogą zmienić nazwy i lokalizacje poleceń menu oraz opcje, które pojawiają się w oknach dialogowych. Ta strona jest oparta na profilu ustawień **ogólnego rozwoju.**

## <a name="identify-a-keyboard-shortcut"></a>Identyfikowanie skrótu klawiaturowego

1. Na pasku menu wybierz pozycję**Opcje** **narzędzi** > .

2. Rozwiń **węzeł Środowisko**, a następnie wybierz pozycję **Klawiatura**.

   ![Wyświetlanie skrótów klawiaturowych w oknie dialogowym Opcje](../ide/media/optionskeyboard.png)

3. W polu **Pokaż polecenia zawierające** wprowadź całość lub część nazwy polecenia bez spacji.

   Na przykład można znaleźć polecenia `solutionexplorer`dla .

4. Na liście, wybierz odpowiednie polecenie.

    Na przykład można `View.SolutionExplorer`wybrać opcję .

5. Jeśli polecenie zawiera skrót klawiaturowy, pojawi się na liście **skrótów dla wybranych poleceń.**

   ![Wyświetlanie skrótu dla określonego polecenia](../ide/media/viewshortcut.png)

## <a name="customize-a-keyboard-shortcut"></a>Dostosowywanie skrótu klawiaturowego

1. Na pasku menu wybierz pozycję**Opcje** **narzędzi** > .

2. Rozwiń **węzeł Środowisko**, a następnie wybierz pozycję **Klawiatura**.

3. Opcjonalnie: Filtruj listę poleceń, wprowadzając całość lub część nazwy polecenia, bez spacji, w polu **Pokaż polecenia zawierające.**

4. Z listy wybierz polecenie, do którego chcesz przypisać skrót klawiaturowy.

   Na liście **Użyj nowego skrótu** wybierz obszar funkcji, w którym chcesz użyć skrótu.

   Na przykład można wybrać **opcję Globalny,** jeśli skrót ma działać we wszystkich kontekstach. Można użyć dowolnego skrótu, który nie jest mapowany (jako globalny) w innym edytorze. W przeciwnym razie edytor zastępuje skrót.

   > [!NOTE]
   > Nie można przypisać następujących klawiszy jako części skrótu klawiaturowego w **aplikacji Global:**
   >
   > - Enter, Tab, Caps Lock
   > - Drukuj Scrn/Sys Rq, Blokada przewijania, Pauza/Przerwa
   > - Wstaw, Strona główna, Koniec, Strona w górę, Strona w dół
   > - Klawisz logo Systemu Windows, klawisz aplikacji, dowolny z klawiszy strzałek
   > - Num Lock, Delete lub Clear na klawiaturze numerycznej
   > - Kombinacja klawiszy Ctrl+Alt+Delete

6. W polu **Klawisze skrótów** wprowadź skrót, którego chcesz użyć.

    > [!NOTE]
    > Można utworzyć skrót łączący literę z klawiszem **Alt,** klawiszem **Ctrl** lub obydwoma. Można również utworzyć skrót łączący klawisz **Shift** i literę z klawiszem **Alt,** klawiszem **Ctrl** lub obydwoma.

     Jeśli skrót jest już przypisany do innego polecenia, pojawi się w polu **Skrót aktualnie używany przez.** W takim przypadku wybierz klawisz **Backspace,** aby usunąć ten skrót przed wypróbowaniem innego skrótu.

    ![Określanie innego skrótu dla polecenia](../ide/media/reassignshortcut.png)

7. Wybierz przycisk **Przypisz.**

    > [!NOTE]
    > Jeśli określisz inny skrót dla polecenia, kliknij przycisk **Przypisz**, a następnie kliknij przycisk **Anuluj,** aby zamknąć okno dialogowe, przypisany skrót nie zostanie przywrócony.

## <a name="share-custom-keyboard-shortcuts"></a>Udostępnianie niestandardowych skrótów klawiaturowych

Możesz udostępniać własne skróty, eksportując je do pliku, a następnie przekazując plik innym osobom, aby mogły importować dane.

### <a name="to-export-only-keyboard-shortcuts"></a>Aby wyeksportować tylko skróty klawiaturowe

1. Na pasku menu wybierz pozycję Ustawienia**importu i eksportu** **narzędzi** > .

2. Wybierz **pozycję Eksportuj wybrane ustawienia środowiska**, a następnie wybierz pozycję **Dalej**.

3. W obszarze **Jakie ustawienia chcesz wyeksportować?** wyczyść pole wyboru **Wszystkie ustawienia,** rozwiń węzeł **Opcje**, a następnie rozwiń **węzeł Środowisko**.

4. Zaznacz pole wyboru **Klawiatura,** a następnie wybierz pozycję **Dalej**.

   ![Eksportowanie tylko niestandardowych skrótów klawiaturowych](../ide/media/exportshortcuts.png)

5. W polu **Co chcesz nazwać plik ustawień** i **Przechowywać plik ustawień w tym katalogu,** pozostaw wartości domyślne lub określ różne wartości, a następnie wybierz pozycję **Zakończ**.

::: moniker range="vs-2017"

Domyślnie skróty są zapisywane w pliku w folderze *%USERPROFILE%\Documents\Visual Studio 2017\Settings.* Nazwa pliku odzwierciedla datę eksportowania ustawień, a rozszerzenie to *.vssettings*.

::: moniker-end

::: moniker range=">=vs-2019"

Domyślnie skróty są zapisywane w pliku w folderze *%USERPROFILE%\Documents\Visual Studio 2019\Settings.* Nazwa pliku odzwierciedla datę eksportowania ustawień, a rozszerzenie to *.vssettings*.

::: moniker-end

### <a name="to-import-only-keyboard-shortcuts"></a>Aby zaimportować tylko skróty klawiaturowe

1. Na pasku menu wybierz pozycję Ustawienia**importu i eksportu** **narzędzi** > .

2. Wybierz przycisk opcji **Importuj wybrane ustawienia środowiska,** a następnie wybierz pozycję **Dalej**.

3. Wybierz **przycisk Nie, po prostu zaimportuj nowe ustawienia, zastąpisz** przycisk opcji bieżące ustawienia, a następnie wybierz pozycję **Dalej**.

4. W obszarze **Moje ustawienia**wybierz plik zawierający skróty, które chcesz zaimportować, lub wybierz przycisk **Przeglądaj,** aby zlokalizować poprawny plik.

5. Wybierz pozycję **Dalej**.

6. W obszarze **Które ustawienia chcesz zaimportować?** wyczyść pole wyboru **Wszystkie ustawienia,** rozwiń węzeł **Opcje**, a następnie rozwiń **węzeł Środowisko**.

7. Zaznacz pole wyboru **Klawiatura,** a następnie wybierz polecenie **Zakończ**.

   ![Importowanie tylko niestandardowych skrótów klawiaturowych](../ide/media/importshortcuts.png)

## <a name="see-also"></a>Zobacz też

- [Funkcje ułatwień dostępu programu Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)
