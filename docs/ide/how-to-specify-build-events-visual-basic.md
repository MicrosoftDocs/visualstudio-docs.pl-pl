---
title: 'Jak: Określanie zdarzeń kompilacji (Visual Basic)'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: 40dc83bf-a7c5-4a14-816a-fa0980b6e4c3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33cf9cadc8fbf091fb213926fb25b232d14dc0d7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115106"
---
# <a name="how-to-specify-build-events-visual-basic"></a>Jak: Określanie zdarzeń kompilacji (Visual Basic)

Zdarzenia kompilacji w języku Visual Basic mogą być używane do uruchamiania skryptów, makr lub innych akcji w ramach procesu kompilacji. Zdarzenia przed kompilacją występują przed kompilacją; zdarzenia po kompilacji występują po kompilacji.

Zdarzenia kompilacji są określone w oknie dialogowym **Tworzenie zdarzeń,** dostępnym na stronie **Kompilacja** **projektanta projektu**.

> [!NOTE]
> Visual Basic Express nie obsługuje wprowadzania zdarzeń kompilacji. Jest to obsługiwane tylko w pełnym produkcie programu Visual Studio.

## <a name="how-to-specify-pre-build-and-post-build-events"></a>Jak określić zdarzenia pre-build i post-build

### <a name="to-specify-a-build-event"></a>Aby określić zdarzenie kompilacji

1. Po wybraniu projektu w **Eksploratorze rozwiązań**w menu **Projekt** kliknij polecenie **Właściwości**.

2. Kliknij kartę **Kompilowanie.**

3. Kliknij przycisk **Twórz zdarzenia,** aby otworzyć okno dialogowe **Tworzenie zdarzeń.**

4. Wprowadź argumenty wiersza polecenia dla akcji pre-build lub post-build, a następnie kliknij przycisk **OK**.

    > [!NOTE]
    > Dodaj `call` instrukcję przed wszystkimi poleceniami po kompilacji, które uruchamiają pliki *.bat.* Na przykład: `call C:\MyFile.bat` lub `call C:\MyFile.bat call C:\MyFile2.bat`.

    > [!NOTE]
    > Jeśli zdarzenie przed kompilacją lub po kompilacji nie zakończy się pomyślnie, można zakończyć kompilację, mając zakończenie akcji zdarzenia z kodem innym niż zero (0), który wskazuje pomyślną akcję.

## <a name="example-how-to-change-manifest-information-using-a-post-build-event"></a>Przykład: Jak zmienić informacje manifestu przy użyciu zdarzenia po kompilacji

Poniższa procedura pokazuje, jak ustawić minimalną wersję systemu operacyjnego w manifeście aplikacji przy użyciu polecenia *.exe* wywoływanego ze zdarzenia po kompilacji (pliku *.exe.manifest* w katalogu projektu). Minimalna wersja systemu operacyjnego to czteroczęściowy numer, taki jak 4.10.0.0. Aby to zrobić, polecenie `<dependentOS>` zmieni sekcję manifestu:

```xml
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

### <a name="to-create-an-exe-command-to-change-the-application-manifest"></a>Aby utworzyć polecenie exe, aby zmienić manifest aplikacji

1. Utwórz aplikację konsoli dla polecenia. W menu **Plik** kliknij polecenie **Nowy**, a następnie kliknij polecenie **Projekt**.

2. W oknie dialogowym **Nowy projekt** w węźle **Visual Basic** wybierz pozycję **Windows,** a następnie szablon **aplikacji konsoli.** Nazwij `ChangeOSVersionVB`projekt .

3. W *module1.vb*dodaj następujący wiersz `Imports` do innych instrukcji w górnej części pliku:

   ```vb
   Imports System.Xml
   ```

4. Dodaj następujący kod `Sub Main`w :

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

   Polecenie przyjmuje dwa argumenty. Pierwszy argument jest ścieżką do manifestu aplikacji (czyli folderu, w którym proces kompilacji tworzy manifest, zazwyczaj * \<ProjectName>.publish*). Drugim argumentem jest nowa wersja systemu operacyjnego.

5. W menu **Kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.

6. Skopiuj plik *exe* do katalogu takiego jak *C:\TEMP\ChangeOSVersionVB.exe*.

   Następnie wywołać to polecenie w zdarzeniu po kompilacji, aby zmienić manifest aplikacji.

### <a name="to-invoke-a-post-build-event-to-change-the-application-manifest"></a>Aby wywołać zdarzenie po kompilacji, aby zmienić manifest aplikacji

1. Utwórz aplikację systemu Windows dla projektu, który ma zostać opublikowany. W menu **Plik** kliknij polecenie **Nowy**, a następnie kliknij polecenie **Projekt**.

2. W oknie dialogowym **Nowy projekt** w węźle **Visual Basic** wybierz pozycję Pulpit systemu **Windows,** a następnie szablon **aplikacji Formularze systemu Windows.** Nazwij `VBWinApp`projekt .
3. Po wybraniu projektu w **Eksploratorze rozwiązań**w menu **Projekt** kliknij polecenie **Właściwości**.

4. W **Projektancie projektu**przejdź do strony **Publikowania** i ustaw **lokalizację publikowania** na *C:\TEMP*.

5. Opublikuj projekt, klikając pozycję **Publikuj teraz**.

     Plik manifestu zostanie zbudowany i umieszczony w *pliku C:\TEMP\VBWinApp_1_0_0_0\VBWinApp.exe.manifest*. Aby wyświetlić manifest, kliknij plik prawym przyciskiem myszy i kliknij polecenie Otwórz za **pomocą**, a następnie kliknij pozycję **Wybierz program z listy**, a następnie kliknij polecenie **Notatnik**.

     Wyszukaj w `<osVersionInfo>` pliku element. Na przykład wersja może być:

    ```xml
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
    ```

6. W **projektancie projektu**przejdź do karty **Kompilacja** i kliknij przycisk **Buduj zdarzenia,** aby otworzyć okno dialogowe **Tworzenie zdarzeń.**

7. W polu **Wiersz polecenia zdarzenia po utworzeniu** wprowadź następujące polecenie:

     `C:\TEMP\ChangeOSVersionVB.exe "$(TargetPath).manifest" 5.1.2600.0`

     Podczas tworzenia projektu to polecenie spowoduje zmianę minimalnej wersji systemu operacyjnego w manifeście aplikacji na 5.1.2600.0.

     Makro `$(TargetPath)` wyraża pełną ścieżkę dla tworzonego pliku wykonywalnego. W związku z tym *$(TargetPath).manifest* określi manifest aplikacji utworzony w katalogu *bin.* Publikowanie skopiuje ten manifest do lokalizacji publikowania, którą wcześniej ustawisz.

8. Ponownie opublikuj projekt. Przejdź do strony **Publikowania** i kliknij pozycję **Publikuj teraz**.

     Ponownie wyświetl manifest. Aby wyświetlić manifest, przejdź do katalogu publikowania, kliknij plik prawym przyciskiem myszy i kliknij polecenie **Otwórz za pomocą,** a następnie **wybierz program z listy**, a następnie kliknij **notatnik**.

     Wersja powinna teraz brzmieć:

    ```xml
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
    ```

## <a name="see-also"></a>Zobacz też

- [Strona kompilacji, Projektant projektu (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)
- [Strona publikowania, Projektant projektu](../ide/reference/publish-page-project-designer.md)
- [Okno dialogowe wiersza polecenia Zdarzenia przed kompilacją/po utworzeniu](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Jak: Określanie zdarzeń kompilacji (C#)](../ide/how-to-specify-build-events-csharp.md)
