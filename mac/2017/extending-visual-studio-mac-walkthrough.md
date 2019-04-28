---
title: Rozszerzanie programu Visual Studio dla komputerów Mac wskazówki
author: conceptdev
ms.author: crdun
ms.date: 04/14/2017
ms.technology: vs-ide-sdk
ms.assetid: 7D00512B-9688-4D8D-87A7-F04F207E3D02
ms.openlocfilehash: cbf0d99bd87b31484b6c74e9a6d67ac88dc5ba99
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62998565"
---
# <a name="extending-visual-studio-for-mac-walkthrough"></a>Rozszerzanie programu Visual Studio dla komputerów Mac wskazówki

Ten temat przeprowadzi Cię przez tworzenie [pakietu proste rozszerzenie](https://github.com/mjh4/AddIns/tree/master/DateInserter). Pakiet rozszerzenia spowoduje utworzenie nowego polecenia w programie Visual Studio dla komputerów Mac menu Edycja, który umożliwia użytkownikowi Wstawianie dokument tekstowy Otwórz bieżącej daty i godziny.

W tym przykładzie użyto twórcę dodatku. Twórca dodatku utworzenie nowego szablonu projektu i wypełnia wymaganych plików dla naszego pakietu rozszerzenia niestandardowego.

1. Rozpocznij poprzez uruchomienie programu Visual Studio dla komputerów Mac, jeśli nie jest już otwarty:

   ![Program Visual Studio for Mac zrzut ekranu](media/extending-visual-studio-mac-addin3.png)

2. Zainstaluj _dodatku twórca pakietu rozszerzenia_ korzystanie z Menedżera rozszerzeń. Wybierz z menu programu Visual Studio **rozszerzeń...** :

   ![Karta Menedżer dodatków](media/extending-visual-studio-mac-addin4.png)

3. Przejdź na kartę Galeria i wpisz `Addin Maker` na pasku wyszukiwania w prawym górnym rogu. Wybierz dodatek Maker z kategorii rozwoju w dodatku, a następnie kliknij przycisk <kbd>zainstalować</kbd>. Jeśli nic nie zostaną wyświetlone, odświeżam i wyszukać ponownie:

   ![Menedżer dodatków](media/extending-visual-studio-mac-addin5.png)

4. Teraz, gdy producent dodatek programu jest zainstalowany, możesz zacząć tworzyć pakietu rozszerzenia. Rozpocznij od utworzenia nowego rozwiązania.

5. Z **nowe rozwiązanie w oknie dialogowym**, wybierz **innych > Różne > Ogólne > Xamarin Studio dodatek > C#** szablonu i na poniższym ekranie Nazwa nowego rozwiązania `DateInserter`:

   ![Tworzenie nowego rozwiązania](media/extending-visual-studio-mac-addin7New.png)

6. Program Visual Studio for Mac zostaną wyświetlone nowe rozwiązanie:

   ![Wypełnione rozwiązania](media/extending-visual-studio-mac-addin8.png)

7. Usuń kod szablonu w `Manifest.addin.xml` i zastąp go następującym kodem:

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

8. Teraz musisz skonfigurować pliki, które będzie ostatecznie obsługiwać Wstawianie daty i godziny do edytora tekstu. Kliknij prawym przyciskiem myszy węzeł projektu i Dodaj nowy plik. Wybierz **ogólne > Pusta klasa** i nadaj nowemu plikowi *InsertDateHandler*:

   ![Wstaw datę obsługi](media/extending-visual-studio-mac-addin9.png)

9. Kod szablonu z przewodnika usuńmy `InsertDateHandler.cs` i zastąp go następującym kodem:

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

   Firma Microsoft będzie później rozszerzyć tych dwóch metod symbol zastępczy.

10. Kliknij prawym przyciskiem myszy **DateInserter** projektu i wybierz pozycję **Dodaj > Nowy plik**. Wybierz **ogólne > puste wyliczenie**, a następnie nadaj nowemu plikowi *DateInserterCommands*:

    ![DateInserterCommands](media/extending-visual-studio-mac-addin10.png)

11. Dodaj `InsertDate` polecenia jako nowe wyliczenie w `DateInserterCommands.cs` pliku:

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

12. W tym momencie powinien mieć pakiet rozszerzenia pracy. Zapisywanie pracy i działania aplikacji, można przetestować działanie. IDE spowoduje uruchomienie nowego wystąpienia programu Visual Studio dla komputerów Mac przy użyciu nowego pakietu rozszerzenia zainstalowane. Jeśli przejdziesz do **menu Edycja**, zobaczysz, że program Visual Studio for Mac ma nową opcję o nazwie **Wstaw datę**, jak pokazano na poniższym zrzucie ekranu:

    ![Wstaw datę, polecenie](media/extending-visual-studio-mac-addin11.png)

    Należy pamiętać, że wybierając Wstaw datę z menu nie ma znaczenia, ponieważ bieżąca implementacja ma tylko metod symbol zastępczy.

13. Struktura znajduje się w miejscu, aby pakiet rozszerzenia i nadszedł czas, aby napisać kod, który obsługuje wstawiania daty. Najpierw upewnij się, że **polecenia Insert data** jest włączona jedynie wtedy, gdy użytkownik ma tekstu, plik jest otwarty, zastępując `Update` method in Class metoda `InsertDateHandler.cs` następującym kodem:

    ```cs
    protected override void Update(CommandInfo info)
    {
      info.Enabled = IdeApp.Workbench.ActiveDocument?.Editor != null;
    }
    ```

14. Zaktualizuj polecenie `Run` metodę, aby wstawić datę i godzinę, z następującym kodem:

    ``` cs
    protected override void Run () {
      var editor = IdeApp.Workbench.ActiveDocument.Editor;
      var date = DateTime.Now.ToString ();
      editor.InsertAtCaret (date);

    }
    ```

15. Na koniec uruchom naszego pakietu rozszerzenia do testowania. W wystąpieniu programu Visual Studio dla komputerów Mac, wybierz **Edytuj > Wstaw datę**. Bieżącą datę i godzinę, zostanie wstawione w naszej daszka, jak pokazano na poniższym zrzucie ekranu:

    ![Wstaw datę zrzut ekranu](media/extending-visual-studio-mac-addin12.png)

## <a name="see-also"></a>Zobacz także

- [Tworzenie pierwszego rozszerzenia (Visual Studio Windows)](/visualstudio/extensibility/extensibility-hello-world)