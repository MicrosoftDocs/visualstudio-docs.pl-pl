---
title: 'Instrukcje: Określanie zdarzeń kompilacji (Visual Basic)'
description: Dowiedz się, jak zdarzenia kompilacji w Visual Basic mogą służyć do uruchamiania skryptów, makr lub innych akcji w ramach procesu kompilacji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: how-to
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
ms.openlocfilehash: 00655d1f30d18da4170782384c634ff189b104ee
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136930"
---
# <a name="how-to-specify-build-events-visual-basic"></a>Instrukcje: Określanie zdarzeń kompilacji (Visual Basic)

Zdarzenia kompilacji w Visual Basic mogą służyć do uruchamiania skryptów, makr lub innych akcji w ramach procesu kompilacji. Zdarzenia przed kompilacją są wykonywane przed kompilacją; zdarzenia po kompilacji występują po kompilacji.

Zdarzenia kompilacji są określone w oknie dialogowym **zdarzenia kompilacji** dostępne na stronie **kompilacja** **projektanta projektu**.

> [!NOTE]
> Visual Basic Express nie obsługuje wprowadzania zdarzeń kompilacji. Jest to obsługiwane tylko w pełnym produkcie Visual Studio.

## <a name="how-to-specify-pre-build-and-post-build-events"></a>Jak określić zdarzenia przed kompilacją i po kompilacji

### <a name="to-specify-a-build-event"></a>Aby określić zdarzenie kompilacji

1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.

2. Kliknij kartę **kompilacja** .

3. Kliknij przycisk **Kompiluj zdarzenia** , aby otworzyć okno dialogowe **zdarzenia kompilacji** .

4. Wprowadź argumenty wiersza polecenia dla akcji przed kompilacją lub po kompilacji, a następnie kliknij przycisk **OK**.

    > [!NOTE]
    > Dodaj `call` instrukcję przed wszystkimi poleceniami po kompilacji, które uruchamiają pliki *. bat* . Na przykład: `call C:\MyFile.bat` lub `call C:\MyFile.bat call C:\MyFile2.bat`.

    > [!NOTE]
    > Jeśli wydarzenie przed kompilacją lub po kompilacji nie zakończy się pomyślnie, możesz przerwać kompilację, aby zakończyć działanie zdarzenia z kodem innym niż zero (0), co oznacza pomyślne wykonanie akcji.

## <a name="example-how-to-change-manifest-information-using-a-post-build-event"></a>Przykład: jak zmienić informacje manifestu przy użyciu zdarzenia po kompilacji

Poniższa procedura pokazuje, jak ustawić minimalną wersję systemu operacyjnego w manifeście aplikacji przy użyciu polecenia *. exe* wywoływanego z zdarzenia po kompilacji (plik *. exe. manifest* w katalogu projektu). Minimalna wersja systemu operacyjnego to czterocyfrowy numer, taki jak 4.10.0.0. W tym celu polecenie zmieni `<dependentOS>` sekcję manifestu:

```xml
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

### <a name="to-create-an-exe-command-to-change-the-application-manifest"></a>Aby utworzyć polecenie. exe w celu zmiany manifestu aplikacji

1. Utwórz aplikację konsolową dla polecenia. W menu **plik** kliknij pozycję **Nowy**, a następnie kliknij pozycję **projekt**.

2. W oknie dialogowym **Nowy projekt** w węźle **Visual Basic** wybierz pozycję **Windows** , a następnie szablon **aplikacja konsoli** . Nadaj nazwę projektowi `ChangeOSVersionVB` .

3. W *Module1. vb*Dodaj następujący wiersz do innych `Imports` instrukcji w górnej części pliku:

   ```vb
   Imports System.Xml
   ```

4. Dodaj następujący kod w `Sub Main` :

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

   Polecenie przyjmuje dwa argumenty. Pierwszy argument jest ścieżką do manifestu aplikacji (czyli folder, w którym proces kompilacji tworzy manifest, zwykle * \<ProjectName> . publish*). Drugi argument to nowa wersja systemu operacyjnego.

5. W menu **Kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.

6. Skopiuj plik *. exe* do katalogu, takiego jak *C:\TEMP\ChangeOSVersionVB.exe*.

   Następnie Wywołaj to polecenie w zdarzeniu po kompilacji, aby zmienić manifest aplikacji.

### <a name="to-invoke-a-post-build-event-to-change-the-application-manifest"></a>Aby wywołać zdarzenie po kompilacji w celu zmiany manifestu aplikacji

1. Utwórz aplikację systemu Windows dla projektu do opublikowania. W menu **plik** kliknij pozycję **Nowy**, a następnie kliknij pozycję **projekt**.

2. W oknie dialogowym **Nowy projekt** w węźle **Visual Basic** wybierz pozycję **Windows Desktop** , a następnie szablon **aplikacji Windows Forms** . Nadaj nazwę projektowi `VBWinApp` .
3. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.

4. W **projektancie projektu**przejdź do strony **Publikowanie** i ustaw **lokalizację publikowania** na *C:\Temp*.

5. Opublikuj projekt, klikając pozycję **Opublikuj teraz**.

     Plik manifestu zostanie skompilowany i umieszczony w *C:\TEMP\VBWinApp_1_0_0_0\VBWinApp.exe. manifest*. Aby wyświetlić manifest, kliknij prawym przyciskiem myszy plik, a następnie kliknij polecenie **Otwórz za pomocą**, a następnie kliknij pozycję **Wybierz program z listy**, a następnie kliknij przycisk **Notatnik**.

     Wyszukaj w pliku `<osVersionInfo>` element. Na przykład wersja może być:

    ```xml
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
    ```

6. W **projektancie projektu**przejdź do karty **kompilacja** , a następnie kliknij przycisk **Kompiluj zdarzenia** , aby otworzyć okno dialogowe **zdarzenia kompilacji** .

7. W polu **wiersz polecenia zdarzenia po kompilacji** wprowadź następujące polecenie:

     `C:\TEMP\ChangeOSVersionVB.exe "$(TargetPath).manifest" 5.1.2600.0`

     Podczas kompilowania projektu to polecenie zmieni minimalną wersję systemu operacyjnego w manifeście aplikacji na 5.1.2600.0.

     `$(TargetPath)`Makro wyraża pełną ścieżkę do tworzonego pliku wykonywalnego. W związku z tym *$ (TargetPath). manifest* określi manifest aplikacji utworzony w katalogu *bin* . Opublikowanie spowoduje skopiowanie tego manifestu do lokalizacji publikowania, która została ustawiona wcześniej.

8. Opublikuj projekt ponownie. Przejdź do strony **Publikowanie** , a następnie kliknij pozycję **Opublikuj teraz**.

     Ponownie Wyświetl manifest. Aby wyświetlić manifest, przejdź do katalogu publikowania, kliknij plik prawym przyciskiem myszy i kliknij polecenie **Otwórz za pomocą** , a następnie **Wybierz program z listy**, a następnie kliknij przycisk **Notatnik**.

     Wersja powinna teraz zostać odczytana:

    ```xml
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
    ```

## <a name="see-also"></a>Zobacz też

- [Strona kompilowania, Projektant projektu (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md)
- [Strona publikowania, Projektant projektu](../ide/reference/publish-page-project-designer.md)
- [Zdarzenie przed kompilacją/wiersz polecenia zdarzenia po kompilacji](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Instrukcje: Określanie zdarzeń kompilacji (C#)](../ide/how-to-specify-build-events-csharp.md)
