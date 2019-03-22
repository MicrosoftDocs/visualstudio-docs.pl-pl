---
title: 'Instrukcje: Określanie zdarzeń kompilacji (C#)'
ms.date: 03/21/2019
ms.topic: conceptual
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: b4ce1ad9-5215-4b6f-b6a2-798b249aa335
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 28718a213e42f3db8c4beee5d45666044148601d
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2019
ms.locfileid: "58355360"
---
# <a name="how-to-specify-build-events-c"></a>Porady: Określanie zdarzeń kompilacji (C#)

Korzystanie ze zdarzeń kompilacji określić polecenia, które są uruchamiane przed rozpoczęciem kompilacji lub po zakończeniu kompilacji. Zdarzenia kompilacji wykonać tylko wtedy, gdy kompilacja pomyślnie osiągnie tych punktów w procesie kompilacji.

Podczas kompilowania projektu zdarzenia sprzed kompilacji są dodawane do pliku o nazwie *PreBuildEvent.bat* i zdarzenia mające miejsce po kompilacji są dodawane do pliku o nazwie *PostBuildEvent.bat*. Jeśli chcesz upewnić się, sprawdzanie błędów, należy dodać własne polecenia sprawdzania błędów do kroków kompilacji.

## <a name="specify-a-build-event"></a>Określanie zdarzeń kompilacji

1. W **Eksploratora rozwiązań**, wybierz projekt, dla którego chcesz określić zdarzeń kompilacji.

2. Na **projektu** menu, kliknij przycisk **właściwości**.

3. Wybierz **zdarzenia kompilacji** kartę.

4. W **wiersz polecenia zdarzenia sprzed kompilacji** Określ składnia zdarzenia kompilacji.

    > [!NOTE]
    > Jeśli projekt jest aktualny, a nie kompilacja zostaje wyzwolona, nie należy uruchamiać zdarzenia prekompilacyjnego.

5. W **wiersz polecenia zdarzenia po kompilacji** Określ składnia zdarzenia kompilacji.

    > [!NOTE]
    > Dodaj `call` instrukcji przed poleceniami wszystkich wykonywanych po kompilacji, które są uruchamiane *.bat* plików. Na przykład `call C:\MyFile.bat` lub `call C:\MyFile.bat call C:\MyFile2.bat`.

6. W **Uruchom zdarzenie po kompilacji** należy określić, na jakich warunkach, aby uruchomić zdarzenie mające miejsce po kompilacji.

    > [!NOTE]
    > Aby dodać długiej składni lub wybrać dowolne makra z kompilacji [zdarzeń/po kompilacji — zdarzenia prekompilacyjnego wiersza polecenia, okno dialogowe](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md), kliknij przycisk oznaczony wielokropkiem (**...** ) do wyświetlenia w polu edycji.

     Składnia zdarzenia kompilacji może zawierać dowolne polecenie, które jest prawidłowa, w wierszu polecenia lub w *.bat* pliku. Nazwa pliku wsadowego powinien być poprzedzony `call` aby upewnić się, że wszystkie kolejne polecenia są wykonywane.

    > [!NOTE]
    > Jeśli zdarzenia sprzed kompilacji lub po kompilacji nie zostanie ukończone pomyślnie, możesz zakończyć działanie kompilacji przez akcję zdarzenia zakończyć pracę z kodem niż zero (0), co oznacza pomyślne akcji.

## <a name="example"></a>Przykład

Poniższa procedura pokazuje, jak ustawić wersję minimalną wersję systemu operacyjnego w manifeście aplikacji przy użyciu *.exe* polecenia, która jest wywoływana z zdarzenia postkompilacyjnego ( *. exe.manifest* w pliku katalog projektu). Wersja minimalna wersja systemu operacyjnego jest Czteroczęściowy numer, takich jak 4.10.0.0. Aby to zrobić, polecenia zmieni `<dependentOS>` sekcji manifestu:

```xml
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

### <a name="create-an-exe-command-to-change-the-application-manifest"></a>Utwórz polecenie .exe w taki sposób, aby zmienić manifest aplikacji

1. Utwórz nową **aplikacja Konsolowa** projektu dla polecenia. Nadaj projektowi nazwę **ChangeOSVersionCS**.

2. W *Program.cs*, Dodaj następujący wiersz do drugiego `using` instrukcji w górnej części pliku:

   ```csharp
   using System.Xml;
   ```

3. W `ChangeOSVersionCS` przestrzeni nazw, Zastąp `Program` Implementacja klasy z następującym kodem:

   ```csharp
   class Program
   {
      /// <summary>
      /// This function will set the minimum operating system version for a ClickOnce application.
      /// </summary>
      /// <param name="args">
      /// Command Line Arguments:
      /// 0 - Path to application manifest (.exe.manifest).
      /// 1 - Version of OS
      ///</param>
      static void Main(string[] args)
      {
         string applicationManifestPath = args[0];
         Console.WriteLine("Application Manifest Path: " + applicationManifestPath);

         // Get version name.
         Version osVersion = null;
         if (args.Length >=2 ){
            osVersion = new Version(args[1]);
         }else{
            throw new ArgumentException("OS Version not specified.");
         }
         Console.WriteLine("Desired OS Version: " + osVersion.ToString());

         XmlDocument document;
         XmlNamespaceManager namespaceManager;
         namespaceManager = new XmlNamespaceManager(new NameTable());
         namespaceManager.AddNamespace("asmv1", "urn:schemas-microsoft-com:asm.v1");
         namespaceManager.AddNamespace("asmv2", "urn:schemas-microsoft-com:asm.v2");

         document = new XmlDocument();
         document.Load(applicationManifestPath);

         string baseXPath;
         baseXPath = "/asmv1:assembly/asmv2:dependency/asmv2:dependentOS/asmv2:osVersionInfo/asmv2:os";

         // Change minimum required operating system version.
         XmlNode node;
         node = document.SelectSingleNode(baseXPath, namespaceManager);
         node.Attributes["majorVersion"].Value = osVersion.Major.ToString();
         node.Attributes["minorVersion"].Value = osVersion.Minor.ToString();
         node.Attributes["buildNumber"].Value = osVersion.Build.ToString();
         node.Attributes["servicePackMajor"].Value = osVersion.Revision.ToString();

         document.Save(applicationManifestPath);
      }
   }
   ```

   Polecenie przyjmuje dwa argumenty: ścieżkę manifestu aplikacji (czyli folderu, w którym proces kompilacji tworzy manifest, zwykle *Projectname.publish*), a nową wersję systemu operacyjnego.

4. Skompiluj projekt.

5. Kopiuj *.exe* plik do katalogu, takie jak *C:\TEMP\ChangeOSVersionVB.exe*.

   Następnie wywołaj to polecenie zdarzenie po kompilacji, aby zmodyfikować manifest aplikacji.

### <a name="invoke-a-post-build-event-to-modify-the-application-manifest"></a>Wywołaj zdarzenie po kompilacji, aby zmodyfikować manifest aplikacji

1. Utwórz nową **Windows Forms App** projektu i nadaj mu nazwę **CSWinApp**.

2. Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, wybierz **właściwości**.

3. W **projektanta projektu**, zlokalizuj **Publikuj** strony, a następnie ustaw **publikowania lokalizacji** do *C:\TEMP*.

4. Opublikuj projekt, klikając **Publikuj teraz**.

     Plik manifestu jest utworzone i zapisane w *C:\TEMP\CSWinApp_1_0_0_0\CSWinApp.exe.manifest*. Aby wyświetlić manifest, kliknij prawym przyciskiem myszy plik, kliknij przycisk **Otwórz za pomocą**, wybierz opcję **wybierz program, z listy**, a następnie kliknij przycisk **Notatnik**.

     Wyszukaj w pliku `<osVersionInfo>` elementu. Na przykład może być wersji:

    ```xml
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
    ```

5. Ponownie **projektanta projektu**, kliknij przycisk **zdarzenia kompilacji** kartę, a następnie kliknij przycisk **edytować po kompilacji**.

6. W **wiersz polecenia zdarzenia po kompilacji** wpisz następujące polecenie:

     `C:\TEMP\ChangeOSVersionCS.exe "$(TargetPath).manifest" 5.1.2600.0`

     Podczas tworzenia projektu, to polecenie zmienia 5.1.2600.0 minimalnej wersji systemu operacyjnego w manifeście aplikacji.

     Ponieważ `$(TargetPath)` — makro określa pełną ścieżkę do pliku wykonywalnego, trwa tworzenie `$(TargetPath)` *.manifest* określą manifestem aplikacji utworzonym w *bin* katalogu. Publikowanie kopiuje ten manifest do lokalizacji publikowania, które zostały ustawione wcześniej.

7. Opublikuj projekt ponownie.

     Wersja manifestu powinien mieć teraz treść:

    ```xml
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
    ```

## <a name="see-also"></a>Zobacz także

- [Strona zdarzenia, Projektant projektu kompilacji (C#)](../ide/reference/build-events-page-project-designer-csharp.md)
- [Okno dialogowe wiersz polecenia zdarzenia/po kompilacji — zdarzenie prekompilacyjne](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Instrukcje: Określanie zdarzeń kompilacji (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md)
- [Kompilowanie i tworzenie kompilacji](../ide/compiling-and-building-in-visual-studio.md)