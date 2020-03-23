---
title: Rozszerzanie przewodnika programu Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.technology: vs-ide-sdk
ms.assetid: 7D00512B-9688-4D8D-87A7-F04F207E3D02
ms.openlocfilehash: c5b3b759b32acfc86b4b584b3f3d52298c138a2c
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "74983290"
---
# <a name="extending-visual-studio-for-mac-walkthrough"></a>Rozszerzanie przewodnika programu Visual Studio dla komputerów Mac

W tym temacie można przejść do tworzenia [prostego pakietu rozszerzeń](https://github.com/mjh4/AddIns/tree/master/DateInserter). Pakiet rozszerzeń utworzy nowe polecenie w programie Visual Studio dla menu Edycja komputera Mac, które umożliwia użytkownikowi wstawienie bieżącej daty i godziny do otwartego dokumentu tekstowego.

W tym przykładzie użyto programu Add-in Maker. Dodatek Maker tworzy nowy szablon projektu i wypełnia go wymaganymi plikami dla naszego niestandardowego pakietu rozszerzeń.

1. Rozpocznij od uruchomienia programu Visual Studio dla komputerów Mac, jeśli nie jest jeszcze otwarty:

   ![Zrzut ekranu przedstawiający program Visual Studio dla komputerów Mac](media/extending-visual-studio-mac-addin3.png)

2. Zainstaluj _pakiet rozszerzeń dodatku Maker_ przy użyciu Menedżera rozszerzeń. Z menu Visual Studio wybierz polecenie **Rozszerzenia...**:

   ![Karta Menedżera dodatku](media/extending-visual-studio-mac-addin4.png)

3. Przejdź do karty Galeria `Addin Maker` i wpisz na pasku wyszukiwania w prawym górnym rogu. Wybierz pozycję Addin Maker z kategorii Programistyczne dodatki i kliknij pozycję <kbd>Zainstaluj</kbd>. Jeśli nic się nie pojawi, naciśnij ponownie przycisk Odśwież i wyszukaj:

   ![Menedżer dodatków](media/extending-visual-studio-mac-addin5.png)

4. Teraz, gdy addin maker jest zainstalowany, można rozpocząć tworzenie pakietu rozszerzenia. Zacznij od utworzenia nowego rozwiązania.

5. W **oknie dialogowym Nowe rozwiązanie**wybierz polecenie **Inne > Różne > Ogólne > szablonie Xamarin Studio Addin > C#,** a `DateInserter`na poniższej nazwie ekranu nowe rozwiązanie:

   ![Tworzenie nowego rozwiązania](media/extending-visual-studio-mac-addin7New.png)

6. Visual Studio dla komputerów Mac wypełni nowe rozwiązanie:

   ![Rozwiązanie wypełnione](media/extending-visual-studio-mac-addin8.png)

7. Usuń kod szablonu `Manifest.addin.xml` i zastąp go następującymi:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
      <ExtensionModel>
          <Extension path = "/MonoDevelop/Ide/Commands/Edit">
              <Command id = "DateInserter.DateInserterCommands.InsertDate"
                  _label = "Insert Date"
                  defaultHandler = "DateInserter.InsertDateHandler" />
          </Extension>

          <Extension path = "/MonoDevelop/Ide/MainMenu/Edit">
              <CommandItem id="DateInserter.DateInserterCommands.InsertDate" />
          </Extension>
      </ExtensionModel>
   ```

8. Teraz musisz skonfigurować pliki, które ostatecznie obejmą wstawianie daty i godziny do edytora tekstu. Kliknij prawym przyciskiem myszy węzeł projektu i dodaj nowy plik. Wybierz **opcję Ogólne > pustej klasy** i nazwij nowy plik *InsertDateHandler:*

   ![Wstawianie programu obsługi daty](media/extending-visual-studio-mac-addin9.png)

9. Usuńmy kod szablonu `InsertDateHandler.cs` i zastąp go następującym kodem:

   ```cs
   using MonoDevelop.Components.Commands;
   using MonoDevelop.Ide;
   using MonoDevelop.Ide.Gui;
   using System;

   namespace DateInserter
   {
      class InsertDateHandler : CommandHandler
      {
          protected override void Run()
          {

          }

          protected override void Update(CommandInfo info)
          {

          }
      }
   }
   ```

   Rozwiń te dwie metody zastępcze później.

10. Kliknij prawym przyciskiem myszy projekt **DateInserter** i wybierz polecenie **Dodaj > nowy plik**. Wybierz **opcję Ogólne > Puste wyliczenie**, a następnie nazwij nowy plik *DataInserterCommands:*

    ![DataInserterCommands](media/extending-visual-studio-mac-addin10.png)

11. Dodaj `InsertDate` polecenie jako nowe wyliczenie `DateInserterCommands.cs` w pliku:

    ``` cs
    using System;

    namespace DateInserter
    {
      public enum DateInserterCommands
      {
          InsertDate,
      }
    }
    ```

12. W tym momencie powinieneś mieć działający pakiet rozszerzeń. Można go przetestować, zapisując pracę i uruchamiając aplikację. IDE uruchomi nowe wystąpienie programu Visual Studio dla komputerów Mac z zainstalowanym nowym pakietem rozszerzenia. Jeśli przejdziesz do **menu Edycja,** zobaczysz, że program Visual Studio dla komputerów Mac ma nową opcję o nazwie **Wstaw datę**, jak pokazano na poniższym zrzucie ekranu:

    ![Polecenie Wstaw datę](media/extending-visual-studio-mac-addin11.png)

    Należy zauważyć, że wybranie opcji Wstaw datę z menu nie ma wpływu, ponieważ bieżąca implementacja ma tylko metody zastępcze.

13. Struktura jest w miejscu dla pakietu rozszerzenia i nadszedł czas, aby napisać kod, który uprawnienia wstawiania daty. Najpierw upewnij się, że **polecenie Wstaw datę** jest włączone tylko wtedy, `Update` gdy `InsertDateHandler.cs` użytkownik ma otwarty plik tekstowy, zastępując metodę następującym kodem:

    ```cs
    protected override void Update(CommandInfo info)
    {
      info.Enabled = IdeApp.Workbench.ActiveDocument?.Editor != null;
    }
    ```

14. Zaktualizuj `Run` metodę polecenia, aby wstawić datę i godzinę za pomocą następującego kodu:

    ``` cs
    protected override void Run () {
      var editor = IdeApp.Workbench.ActiveDocument.Editor;
      var date = DateTime.Now.ToString ();
      editor.InsertAtCaret (date);

    }
    ```

15. Na koniec uruchommy nasz pakiet rozszerzeń, aby go przetestować. W nowym wystąpieniu programu Visual Studio dla komputerów Mac wybierz pozycję **Edytuj > Wstaw datę**. Aktualna data i godzina są wstawiane w naszej daszcie, jak pokazano na poniższym zrzucie ekranu:

    ![Wstaw datę zrzutu ekranu](media/extending-visual-studio-mac-addin12.png)

## <a name="see-also"></a>Zobacz też

- [Tworzenie pierwszego rozszerzenia (Visual Studio w systemie Windows)](/visualstudio/extensibility/extensibility-hello-world)