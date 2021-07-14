---
description: Można zidentyfikować skróty klawiaturowe dla poleceń programu Visual Studio, dostosować te skróty i eksportować je dla innych użytkowników.
title: Identyfikowanie i dostosowywanie skrótów klawiaturowych
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cc9b38b27df28d551fc33e9a23bdad8276a422a4
ms.sourcegitcommit: 15821c790d6498210f30b3268402ffad6bb70c7c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2021
ms.locfileid: "113725550"
---
# <a name="identify-and-customize-keyboard-shortcuts-in-visual-studio"></a>Identyfikowanie i dostosowywanie skrótów klawiaturowych w Visual Studio

Można zidentyfikować skróty klawiaturowe dla poleceń programu Visual Studio, dostosować te skróty i eksportować je dla innych użytkowników. Wiele skrótów zawsze wywołuje te same polecenia, ale zachowanie skrótu może zależeć od następujących warunków:

- Które domyślne ustawienia środowiska są wybierane przy pierwszym otwarciu Visual Studio, na przykład &mdash; Ogólne lub Visual C#. (Aby uzyskać informacje na temat zmieniania lub resetowania ustawień, zobacz [Ustawienia środowiska).](environment-settings.md)

- Czy dostosowywałeś zachowanie danego skrótu.

- W którym kontekście jesteś w momencie wybierania skrótu. Na przykład skrót **F2** wywołuje polecenie , jeśli używasz narzędzia Ustawienia Designer i wywołuje polecenie , jeśli używasz Team Explorer `Edit.EditCell`  `File.Rename` . 

Niezależnie od ustawień, dostosowywania i kontekstu w oknie dialogowym  Opcje zawsze można znaleźć i zmienić skrót klawiaturowy. Możesz również sprawdzić domyślne skróty klawiaturowe dla kilkudziesięciu poleceń w tece [Popularne skróty klawiaturowe](../ide/default-keyboard-shortcuts-in-visual-studio.md#popular). Aby uzyskać pełną listę wszystkich skrótów domyślnych (na podstawie ogólnych **ustawień programistyki),** zobacz Wszystkie [skróty klawiaturowe](../ide/default-keyboard-shortcuts-in-visual-studio.md).

Jeśli skrót jest przypisany do polecenia w kontekście *globalnym* i nie ma innych kontekstów, ten skrót zawsze wywoła to polecenie. Jednak skrót może być przypisany do jednego polecenia w kontekście globalnym i innego polecenia w określonym kontekście. Gdy korzystasz z takiego skrótu podczas pracy w określonym kontekście, skrót wywołuje polecenie odpowiadające temu kontekstowi, a nie kontekstowi globalnemu.

> [!NOTE]
> Twoje ustawienia i wersja programu Visual Studio mogą zmienić nazwy i lokalizacje poleceń menu oraz opcje, które pojawiają się w oknach dialogowych. Ta strona jest oparta na **profilu Ogólne ustawienia** programowe.

## <a name="identify-a-keyboard-shortcut"></a>Identyfikowanie skrótu klawiaturowego

1. Na pasku menu wybierz pozycję **Opcje**  >  **narzędzi.**

2. Rozwiń **pozycję Środowisko**, a następnie wybierz pozycję **Klawiatura.**

   ![Wyświetlanie skrótów klawiaturowych w oknie dialogowym Opcje](../ide/media/optionskeyboard.png)

3. W **pokaż polecenia zawierające** pole, wprowadź wszystkie lub część nazwy polecenia bez spacji.

   Można na przykład znaleźć polecenia dla `solutionexplorer` polecenia .

4. Na liście, wybierz odpowiednie polecenie.

    Możesz na przykład wybrać pozycję `View.SolutionExplorer` .

5. Jeśli polecenie ma skrót klawiaturowy, pojawia się na **liście Skróty dla wybranych** poleceń.

   ![Wyświetlanie skrótu dla określonego polecenia](../ide/media/viewshortcut.png)

## <a name="customize-a-keyboard-shortcut"></a>Dostosowywanie skrótu klawiaturowego

1. Na pasku menu wybierz pozycję **Opcje**  >  **narzędzi.**

2. Rozwiń **pozycję Środowisko**, a następnie wybierz pozycję **Klawiatura.**

3. Opcjonalnie: filtruj listę poleceń, wprowadzając całą lub część nazwy polecenia bez spacji w polu **Pokaż polecenia zawierające.**

4. Z listy wybierz polecenie, do którego chcesz przypisać skrót klawiaturowy.

   Na liście **Użyj nowego skrótu wybierz** obszar funkcji, w którym chcesz użyć skrótu.

   Możesz na przykład wybrać opcję **Globalne,** jeśli skrót ma działać we wszystkich kontekstach. Można użyć dowolnego skrótu, który nie jest mapowany (jako globalny) w innym edytorze. W przeciwnym razie edytor zastępuje skrót.

   > [!NOTE]
   > Nie można przypisać następujących klawiszy w ramach skrótu klawiaturowego w **globalnej**:
   >
   > - Enter, Tab, Caps Lock
   > - Scrn drukowania/Sys Rq, blokada przewijania, wstrzymywanie/przerywanie
   > - Insert, Home, End, Page Up, Page Down
   > - Klucz Windows, klucz aplikacji, dowolny z klawiszy strzałek
   > - Blokada numeryczna, usuwanie lub usuwanie na klawiaturze numerycznej
   > - Kombinacja klawiszy Ctrl+Alt+Delete

6. W **polu Naciśnij klawisze skrótu** wprowadź skrót, którego chcesz użyć.

    > [!NOTE]
    > Możesz utworzyć skrót, który łączy literę z **klawiszem Alt,** **klawiszem Ctrl** lub obu. Można również utworzyć skrót, który łączy klawisz **Shift** i literę z klawiszem **Alt,** **Ctrl** lub obu.

     Jeśli skrót jest już przypisany do innego polecenia, pojawia się on w polu **Skrót aktualnie używany przez.** W takim przypadku wybierz klawisz **Backspace,** aby usunąć ten skrót, zanim spróbujesz użyć innego.

    ![Określanie innego skrótu dla polecenia](../ide/media/reassignshortcut.png)

7. Wybierz przycisk **Przypisz.**

    > [!NOTE]
    > Jeśli określisz inny skrót dla polecenia, kliknij przycisk Przypisz **,** a następnie kliknij przycisk **Anuluj,** aby zamknąć okno dialogowe, przypisany skrót nie zostanie przywrócony.

## <a name="share-custom-keyboard-shortcuts"></a>Udostępnianie niestandardowych skrótów klawiaturowych

Możesz udostępniać własne skróty, eksportując je do pliku, a następnie przekazując plik innym osobom, aby mogły importować dane.

### <a name="to-export-only-keyboard-shortcuts"></a>Aby wyeksportować tylko skróty klawiaturowe

1. Na pasku menu wybierz pozycję **Narzędzia**  >  **Importuj i eksportuj Ustawienia.**

2. Wybierz **pozycję Eksportuj wybrane ustawienia środowiska,** a następnie wybierz pozycję **Dalej.**

3. W **obszarze Jakie ustawienia chcesz wyeksportować?** wyczyść pole wyboru Wszystkie **Ustawienia** rozwiń pozycję **Opcje,** a następnie rozwiń pozycję **Środowisko**.

4. Zaznacz pole **wyboru Klawiatura,** a następnie wybierz pozycję **Dalej.**

   ![Eksportowanie tylko dostosowanych skrótów klawiaturowych](../ide/media/exportshortcuts.png)

5. W **polach What do you want to name your settings file** (Co chcesz nazwać plik ustawień) i Store my settings file in this **directory** (Przechowuj plik ustawień w tym katalogu) pozostaw wartości domyślne lub określ różne wartości, a następnie wybierz pozycję **Finish (Zakończ).**

::: moniker range="vs-2017"

Domyślnie skróty są zapisywane w pliku w *folderze %USERPROFILE%\Documents\Visual Studio 2017\Ustawienia* folderze. Nazwa pliku odzwierciedla datę wyeksportowania ustawień, a rozszerzenie *to .vssettings*.

::: moniker-end

::: moniker range=">=vs-2019"

Domyślnie skróty są zapisywane w pliku w *folderze %USERPROFILE%\Documents\Visual Studio 2019\Ustawienia* folderze. Nazwa pliku odzwierciedla datę wyeksportowania ustawień, a rozszerzenie *to .vssettings*.

::: moniker-end

### <a name="to-import-only-keyboard-shortcuts"></a>Aby zaimportować tylko skróty klawiaturowe

1. Na pasku menu wybierz pozycję **Narzędzia**  >  **Importuj i eksportuj Ustawienia.**

2. Wybierz przycisk **Importuj wybrane ustawienia środowiska,** a następnie wybierz pozycję **Dalej.**

3. Wybierz przycisk **Nie, po prostu zaimportuj** nowe ustawienia, nadpisując przycisk opcji Moje bieżące ustawienia, a następnie wybierz pozycję **Dalej.**

4. W **obszarze Ustawienia** wybierz plik zawierający skróty, które chcesz zaimportować,  lub wybierz przycisk Przeglądaj, aby zlokalizować prawidłowy plik.

5. Wybierz pozycję **Next** (Dalej).

6. W **obszarze Które ustawienia chcesz zaimportować?** wyczyść pole wyboru Wszystkie Ustawienia rozwiń pozycję **Opcje,** **a** następnie rozwiń pozycję **Środowisko**.

7. Zaznacz pole **wyboru Klawiatura,** a następnie wybierz pozycję **Zakończ.**

   ![Importowanie tylko dostosowanych skrótów klawiaturowych](../ide/media/importshortcuts.png)

## <a name="see-also"></a>Zobacz też

- [Funkcje ułatwień dostępu Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)
