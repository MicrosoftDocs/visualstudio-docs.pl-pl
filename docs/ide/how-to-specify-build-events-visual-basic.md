---
title: 'Instrukcje: Określanie zdarzeń kompilacji (Visual Basic)'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: 40dc83bf-a7c5-4a14-816a-fa0980b6e4c3
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 88903c1370219976bca6e8418c3254d048db51d2
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2019
ms.locfileid: "58324724"
---
# <a name="how-to-specify-build-events-visual-basic"></a>Instrukcje: Określanie zdarzeń kompilacji (Visual Basic)

Zdarzenia kompilacji, w języku Visual Basic mogą służyć do uruchamiania skryptów, makr lub innych działań jako część procesu kompilacji. Zdarzenia prekompilacyjnego występują przed kompilacji; zdarzenia postkompilacyjnego występują po kompilacji.

Tworzenie zdarzenia są określone w **zdarzenia kompilacji** dostępne okno dialogowe **skompilować** strony **projektanta projektu**.

> [!NOTE]
> Visual Basic Express nie obsługuje zapis zdarzeń kompilacji. Jest to obsługiwane tylko w przypadku pełnego produktu Visual Studio.

## <a name="how-to-specify-pre-build-and-post-build-events"></a>Jak określić zdarzenia sprzed kompilacji i po kompilacji

### <a name="to-specify-a-build-event"></a>Aby określić zdarzenia kompilacji

1.  Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.

2.  Kliknij przycisk **skompilować** kartę.

3.  Kliknij przycisk **zdarzenia kompilacji** przycisk, aby otworzyć **zdarzenia kompilacji** okno dialogowe.

4.  Wprowadź argumenty wiersza polecenia dla akcji kompilacji przed lub po kompilacji, a następnie kliknij przycisk **OK**.

    > [!NOTE]
    > Dodaj `call` instrukcji przed poleceniami wszystkich wykonywanych po kompilacji, które są uruchamiane *.bat* plików. Na przykład `call C:\MyFile.bat` lub `call C:\MyFile.bat call C:\MyFile2.bat`.

    > [!NOTE]
    > Jeśli zdarzenia sprzed kompilacji lub po kompilacji nie zostanie ukończone pomyślnie, możesz zakończyć działanie kompilacji przez akcję zdarzenia zakończyć pracę z kodem niż zero (0), co oznacza pomyślne akcji.

## <a name="example-how-to-change-manifest-information-using-a-post-build-event"></a>Przykład: Jak zmienić informacje manifestu za pomocą zdarzenia mające miejsce po kompilacji

Poniższa procedura pokazuje, jak ustawić wersję minimalną wersję systemu operacyjnego w aplikacji manifestu za pomocą *.exe* polecenia wywoływane z zdarzenia postkompilacyjnego ( *. exe.manifest* pliku w projekcie katalog). Wersja minimalna wersja systemu operacyjnego jest Czteroczęściowy numer, takich jak 4.10.0.0. Aby to zrobić, polecenia zmieni `<dependentOS>` sekcji manifestu:

```xml
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

### <a name="to-create-an-exe-command-to-change-the-application-manifest"></a>Aby utworzyć polecenie .exe, aby zmienić manifest aplikacji

1. Utwórz aplikację konsolową dla polecenia. Z **pliku** menu, kliknij przycisk **New**, a następnie kliknij przycisk **projektu**.

2. W **nowy projekt** dialogowym **języka Visual Basic** węzła, wybierz opcję **Windows** a następnie **aplikację Konsolową** szablonu. Nadaj projektowi nazwę `ChangeOSVersionVB`.

3. W *Module1.vb*, Dodaj następujący wiersz do drugiego `Imports` instrukcji w górnej części pliku:

   ```vb
   Imports System.Xml
   ```

4. Dodaj następujący kod w `Sub Main`:

   ```vb
   Sub Main()
      Dim applicationManifestPath As String
      applicationManifestPath = My.Application.CommandLineArgs(0)
      Console.WriteLine("Application Manifest Path: " & applicationManifestPath.ToString)

      'Get version name
      Dim osVersion As Version
      If My.Application.CommandLineArgs.Count >= 2 Then
         osVersion = New Version(My.Application.CommandLineArgs(1).ToString)
      Else
         Throw New ArgumentException("OS Version not specified.")
      End If
      Console.WriteLine("Desired OS Version: " & osVersion.ToString())

      Dim document As XmlDocument
      Dim namespaceManager As XmlNamespaceManager
      namespaceManager = New XmlNamespaceManager(New NameTable())
      With namespaceManager
         .AddNamespace("asmv1", "urn:schemas-microsoft-com:asm.v1")
         .AddNamespace("asmv2", "urn:schemas-microsoft-com:asm.v2")
      End With

      document = New XmlDocument()
      document.Load(applicationManifestPath)

      Dim baseXPath As String
      baseXPath = "/asmv1:assembly/asmv2:dependency/asmv2:dependentOS/asmv2:osVersionInfo/asmv2:os"

      'Change minimum required OS Version.
      Dim node As XmlNode
      node = document.SelectSingleNode(baseXPath, namespaceManager)
      node.Attributes("majorVersion").Value = osVersion.Major.ToString()
      node.Attributes("minorVersion").Value = osVersion.Minor.ToString()
      node.Attributes("buildNumber").Value = osVersion.Build.ToString()
      node.Attributes("servicePackMajor").Value = osVersion.Revision.ToString()

      document.Save(applicationManifestPath)
   End Sub
   ```

   Polecenie przyjmuje dwa argumenty. Pierwszy argument jest ścieżką do manifestu aplikacji (czyli folderu, w którym proces kompilacji tworzy manifest, zwykle  *\<nazwa_projektu > .publish*). Drugi argument jest nowa wersja systemu operacyjnego.

5. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

6. Kopiuj *.exe* plik do katalogu, takie jak *C:\TEMP\ChangeOSVersionVB.exe*.

   Następnie wywołaj to polecenie zdarzenie po kompilacji, aby zmienić manifest aplikacji.

### <a name="to-invoke-a-post-build-event-to-change-the-application-manifest"></a>Aby wywołać zdarzenie po kompilacji, aby zmienić manifest aplikacji

1.  Tworzenie aplikacji Windows dla projektu, które mają zostać opublikowane. Z **pliku** menu, kliknij przycisk **New**, a następnie kliknij przycisk **projektu**.

2.  W **nowy projekt** dialogowym **języka Visual Basic** węzła, wybierz opcję **pulpitu Windows** a następnie **aplikacja formularzy Windows** szablonu. Nadaj projektowi nazwę `VBWinApp`.
3.  Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.

4.  W **projektanta projektu**, przejdź do **Publikuj** strony, a następnie ustaw **publikowania lokalizacji** do *C:\TEMP*.

5.  Opublikuj projekt, klikając **Publikuj teraz**.

     Plik manifestu zostanie utworzone i umieścić w *C:\TEMP\VBWinApp_1_0_0_0\VBWinApp.exe.manifest*. Aby wyświetlić manifest, kliknij prawym przyciskiem myszy plik, a następnie kliknij przycisk **Otwórz za pomocą**, następnie kliknij przycisk **wybierz program, z listy**, a następnie kliknij przycisk **Notatnik**.

     Wyszukaj w pliku `<osVersionInfo>` elementu. Na przykład może być wersji:

    ```xml
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
    ```

6.  W **projektanta projektu**, przejdź do **skompilować** kartę, a następnie kliknij przycisk **zdarzenia kompilacji** przycisk, aby otworzyć **zdarzenia kompilacji** okno dialogowe.

7.  W **wiersz polecenia zdarzenia po kompilacji** wprowadź następujące polecenie:

     `C:\TEMP\ChangeOSVersionVB.exe "$(TargetPath).manifest" 5.1.2600.0`

     Podczas tworzenia projektu, to polecenie zmieni się w manifeście aplikacji wersja minimalna wersja systemu operacyjnego na 5.1.2600.0.

     `$(TargetPath)` — Makro określa pełną ścieżkę do pliku wykonywalnego tworzona. W związku z tym *.manifest $(TargetPath)* określą manifestem aplikacji utworzonym w *bin* katalogu. Publikowanie skopiuje tego manifestu do lokalizacji publikowania, które zostały ustawione wcześniej.

8.  Opublikuj projekt ponownie. Przejdź do **Publikuj** strony, a następnie kliknij przycisk **Publikuj teraz**.

     Ponownie wyświetlić manifest. Aby wyświetlić manifest, przejdź do katalogu publikowania, kliknij prawym przyciskiem myszy plik, a następnie kliknij przycisk **Otwórz za pomocą** i następnie **wybierz program, z listy**, a następnie kliknij przycisk **Notatnik**.

     Wersja powinien mieć teraz treść:

    ```xml
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
    ```

## <a name="see-also"></a>Zobacz także

- [Strona kompilowania, Projektant projektu (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)
- [Strona publikowania, Projektant projektu](../ide/reference/publish-page-project-designer.md)
- [Okno dialogowe wiersz polecenia zdarzenia/po kompilacji — zdarzenie prekompilacyjne](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Instrukcje: Określanie zdarzeń kompilacji (C#)](../ide/how-to-specify-build-events-csharp.md)