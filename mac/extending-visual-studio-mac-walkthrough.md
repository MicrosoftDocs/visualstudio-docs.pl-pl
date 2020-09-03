---
title: Rozszerzanie przewodnika Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.technology: vs-ide-sdk
ms.assetid: 7D00512B-9688-4D8D-87A7-F04F207E3D02
ms.topic: how-to
ms.openlocfilehash: 8b0f1213d500563e9fa6f3574c6b622e3214e03a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85939170"
---
# <a name="extending-visual-studio-for-mac-walkthrough"></a>Rozszerzanie przewodnika Visual Studio dla komputerów Mac

Ten temat przeprowadzi Cię przez proces tworzenia [prostego pakietu rozszerzenia](https://github.com/mjh4/AddIns/tree/master/DateInserter). Pakiet rozszerzenia utworzy nowe polecenie w menu edycji Visual Studio dla komputerów Mac, które umożliwi użytkownikowi wstawienie bieżącej daty i godziny do otwartego dokumentu tekstowego.

W tym przykładzie jest użyty program dodatki. Producent dodatku tworzy nowy szablon projektu i wypełnia go przy użyciu plików wymaganych dla naszego niestandardowego pakietu rozszerzenia.

1. Zacznij od uruchomienia Visual Studio dla komputerów Mac, jeśli nie jest jeszcze otwarty:

   ![Zrzut ekranu Visual Studio dla komputerów Mac](media/extending-visual-studio-mac-addin3.png)

2. Zainstaluj _pakiet rozszerzenia programu Add-in Maker_ przy użyciu Menedżera rozszerzeń. Z menu programu Visual Studio wybierz pozycję **rozszerzenia...**:

   ![Karta Menedżera dodatków](media/extending-visual-studio-mac-addin4.png)

3. Przejdź do karty Galeria i wpisz `Addin Maker` w prawym górnym pasku wyszukiwania. Wybierz pozycję addin Maker z kategorii Programowanie dodatków, a następnie kliknij przycisk <kbd>Instaluj</kbd>. Jeśli nic nie zostanie wyświetlone, kliknij przycisk Odśwież i Wyszukaj ponownie:

   ![Menedżer dodatków](media/extending-visual-studio-mac-addin5.png)

4. Teraz, gdy jest zainstalowany program addin Maker, możesz rozpocząć tworzenie pakietu rozszerzenia. Zacznij od utworzenia nowego rozwiązania.

5. W **oknie dialogowym Nowe rozwiązanie**wybierz kolejno pozycje **inne > różne > ogólne > Xamarin Studio addin > szablon C#** i na poniższym ekranie Nazwij nowe rozwiązanie `DateInserter` :

   ![Tworzenie nowego rozwiązania](media/extending-visual-studio-mac-addin7New.png)

6. Visual Studio dla komputerów Mac wypełni nowe rozwiązanie:

   ![Wypełnione rozwiązanie](media/extending-visual-studio-mac-addin8.png)

7. Usuń kod szablonu w `Manifest.addin.xml` i zastąp go następującym:

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

8. Teraz musisz skonfigurować pliki, które będą ostatecznie obsługiwać Wstawianie daty i godziny do edytora tekstu. Kliknij prawym przyciskiem myszy węzeł projektu i Dodaj nowy plik. Wybierz pozycję **ogólne > pustą klasę** i Nadaj nowemu plikowi nazwę *InsertDateHandler*:

   ![Wstaw procedurę obsługi daty](media/extending-visual-studio-mac-addin9.png)

9. Usuńmy kod szablonu z `InsertDateHandler.cs` i zastąp go następującym kodem:

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

   Te dwie metody zastępcze zostaną później rozwinięcia.

10. Kliknij prawym przyciskiem myszy projekt **DateInserter** i wybierz polecenie **Dodaj > nowy plik**. Wybierz pozycję **ogólne > puste Wyliczenie**, a następnie nadaj nazwę nowemu plikowi *DateInserterCommands*:

    ![DateInserterCommands](media/extending-visual-studio-mac-addin10.png)

11. Dodaj `InsertDate` polecenie jako nowe Wyliczenie w `DateInserterCommands.cs` pliku:

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

12. W tym momencie powinien istnieć pakiet rozszerzenia działającego. Możesz go przetestować, zapisując swoją służbę i uruchamiając aplikację. W środowisku IDE zostanie uruchomione nowe wystąpienie Visual Studio dla komputerów Mac z zainstalowanym nowym pakietem rozszerzeń. Jeśli przejdziesz do **menu Edycja**, zobaczysz, że Visual Studio dla komputerów Mac ma nową opcję o nazwie **Wstaw datę**, jak pokazano na poniższym zrzucie ekranu:

    ![Wstaw datę — polecenie](media/extending-visual-studio-mac-addin11.png)

    Należy zauważyć, że wybranie opcji Wstaw datę z menu nie ma żadnego efektu, ponieważ bieżąca implementacja ma tylko metody symboli zastępczych.

13. Platforma jest zainstalowana dla pakietu rozszerzenia i czas pisania kodu, który umożliwia wstawienie daty. Najpierw upewnij się, że **polecenie Wstaw datę** jest włączone tylko wtedy, gdy użytkownik ma otwarty plik tekstowy, zastępując `Update` metodę w `InsertDateHandler.cs` następującym kodzie:

    ```cs
    protected override void Update(CommandInfo info)
    {
      info.Enabled = IdeApp.Workbench.ActiveDocument?.Editor != null;
    }
    ```

14. Zaktualizuj metodę polecenia, `Run` Aby wstawić datę i godzinę do następującego kodu:

    ``` cs
    protected override void Run () {
      var editor = IdeApp.Workbench.ActiveDocument.Editor;
      var date = DateTime.Now.ToString ();
      editor.InsertAtCaret (date);

    }
    ```

15. Na koniec Uruchom pakiet rozszerzenia, aby go przetestować. W nowym wystąpieniu Visual Studio dla komputerów Mac wybierz pozycję **edytuj > Wstaw datę**. Bieżąca data i godzina są wstawiane przy użyciu karetki, jak pokazano na poniższym zrzucie ekranu:

    ![Wstaw zrzut ekranu daty](media/extending-visual-studio-mac-addin12.png)

## <a name="see-also"></a>Zobacz też

- [Tworzenie pierwszego rozszerzenia (Visual Studio w systemie Windows)](/visualstudio/extensibility/extensibility-hello-world)