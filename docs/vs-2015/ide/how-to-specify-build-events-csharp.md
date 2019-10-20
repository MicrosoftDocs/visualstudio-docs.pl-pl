---
title: 'Instrukcje: Określanie zdarzeń kompilacji (C#) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: b4ce1ad9-5215-4b6f-b6a2-798b249aa335
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 41d3ef0efd4c9eb8eab16bd12cc79f8df1449d65
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670687"
---
# <a name="how-to-specify-build-events-c"></a>Porady: określanie zdarzeń kompilacji (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Użyj zdarzeń kompilacji, aby określić polecenia, które są uruchamiane przed rozpoczęciem kompilacji lub po zakończeniu kompilacji. Zdarzenia kompilacji są wykonywane tylko wtedy, gdy kompilacja pomyślnie osiągnie te punkty w procesie kompilacji.

 Po skompilowaniu projektu zdarzenia przed kompilacją są dodawane do pliku o nazwie PreBuildEvent. bat, a zdarzenia po kompilacji są dodawane do pliku o nazwie PostBuildEvent. bat. Aby zapewnić sprawdzanie błędów, należy dodać własne polecenia sprawdzania błędów do kroków kompilacji.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="how-to-specify-pre-build-and-post-build-events"></a>Jak określić zdarzenia przed kompilacją i po kompilacji

#### <a name="to-specify-a-build-event"></a>Aby określić zdarzenie kompilacji

1. W **Eksplorator rozwiązań**wybierz projekt, dla którego chcesz określić zdarzenie kompilacji.

2. W menu **projekt** kliknij polecenie **Właściwości**.

3. Wybierz kartę **zdarzenia kompilacji** .

4. W polu **wiersz polecenia zdarzenia przed kompilacją** Określ składnię zdarzenia kompilacji.

    > [!NOTE]
    > Zdarzenia przed kompilacją nie są uruchamiane, jeśli projekt jest aktualny i żadna kompilacja nie zostanie wyzwolona.

5. W polu **wiersz polecenia zdarzenia po kompilacji** Określ składnię zdarzenia kompilacji.

    > [!NOTE]
    > Dodaj instrukcję `call` przed wszystkimi poleceniami po kompilacji, które uruchamiają pliki. bat. Na przykład `call C:\MyFile.bat` lub `call C:\MyFile.bat call C:\MyFile2.bat`.

6. W polu **Uruchom zdarzenie po kompilacji** Określ, w jaki sposób mają być uruchamiane zdarzenia po kompilacji.

    > [!NOTE]
    > Aby dodać dłuższą składnię lub wybrać dowolne makra kompilacji z [okna dialogowego zdarzenia sprzed kompilacji/zdarzenia po kompilacji](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md), kliknij przycisk wielokropka ( **...** ), aby wyświetlić pole edycji.

     Składnia zdarzenia kompilacji może zawierać dowolne polecenie, które jest prawidłowe w wierszu polecenia lub pliku. bat. Nazwa pliku wsadowego powinna być poprzedzona `call`, aby upewnić się, że wszystkie kolejne polecenia są wykonywane.

     **Uwaga** Jeśli wydarzenie przed kompilacją lub po kompilacji nie zakończy się pomyślnie, możesz przerwać kompilację, aby zakończyć działanie zdarzenia z kodem innym niż zero (0), co oznacza pomyślne wykonanie akcji.

## <a name="example-how-to-change-manifest-information-by-using-a-post-build-event"></a>Przykład: jak zmienić informacje manifestu przy użyciu zdarzenia po kompilacji
 Poniższa procedura pokazuje, jak ustawić minimalną wersję systemu operacyjnego w manifeście aplikacji przy użyciu polecenia. exe, które jest wywoływane z zdarzenia po kompilacji (plik. exe. manifest w katalogu projektu). Minimalna wersja systemu operacyjnego to czterocyfrowy numer, taki jak 4.10.0.0. W tym celu polecenie zmieni `<dependentOS>` sekcji manifestu:

```
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

#### <a name="to-create-an-exe-command-to-change-the-application-manifest"></a>Aby utworzyć polecenie. exe w celu zmiany manifestu aplikacji

1. Utwórz aplikację konsolową dla polecenia. W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.

2. W oknie dialogowym **Nowy projekt** rozwiń pozycję **Wizualizacja C#** , kliknij pozycję **Windows**, a następnie kliknij szablon **aplikacja konsoli** . Nadaj nazwę projektowi `ChangeOSVersionCS`.

3. W Program.cs Dodaj następujący wiersz do innych instrukcji `using` w górnej części pliku:

   ```
   using System.Xml;
   ```

4. W przestrzeni nazw `ChangeOSVersionCS` Zastąp implementację klasy `Program` następującym kodem:

   ```
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

    Polecenie przyjmuje dwa argumenty: ścieżka do manifestu aplikacji (czyli folder, w którym proces kompilacji tworzy manifest, zazwyczaj ProjectName. publish) i nową wersję systemu operacyjnego.

5. Skompiluj projekt. W menu **kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.

6. Skopiuj plik. exe do katalogu, takiego jak `C:\TEMP\ChangeOSVersionVB.exe`.

   Następnie Wywołaj to polecenie w zdarzeniu po kompilacji, aby zmodyfikować manifest aplikacji.

#### <a name="to-invoke-a-post-build-event-to-modify-the-application-manifest"></a>Aby wywołać zdarzenie po kompilacji w celu zmodyfikowania manifestu aplikacji

1. Utwórz aplikację systemu Windows dla projektu do opublikowania. W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.

2. W oknie dialogowym **Nowy projekt** rozwiń pozycję **Wizualizacja C#** , kliknij pozycję **Windows**, a następnie kliknij szablon **Windows Forms aplikacji** . Nadaj nazwę projektowi `CSWinApp`.

3. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.

4. W projektancie projektu Znajdź stronę **Publikowanie** i ustaw **lokalizację publikowania** na `C:\TEMP\`.

5. Opublikuj projekt, klikając pozycję **Opublikuj teraz**.

     Plik manifestu zostanie skompilowany i umieszczony w `C:\TEMP\CSWinApp_1_0_0_0\CSWinApp.exe.manifest`. Aby wyświetlić manifest, kliknij plik prawym przyciskiem myszy, kliknij polecenie **Otwórz za pomocą**, wybierz **z listy opcję Wybierz program**, a następnie kliknij przycisk **Notatnik**.

     Wyszukaj w pliku `<osVersionInfo>` elementu. Na przykład wersja może być:

    ```
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
    ```

6. W projektancie projektu kliknij kartę **zdarzenia kompilacji** , a następnie kliknij przycisk **Edytuj po kompilacji** .

7. W polu **wiersz polecenia zdarzenia po kompilacji** wpisz następujące polecenie:

     `C:\TEMP\ChangeOSVersionCS.exe "$(TargetPath).manifest" 5.1.2600.0`

     Podczas kompilowania projektu to polecenie zmieni minimalną wersję systemu operacyjnego w manifeście aplikacji na 5.1.2600.0.

     Ponieważ makro `$(TargetPath)` wyraża pełną ścieżkę do tworzonego pliku wykonywalnego, `$(TargetPath)`. manifest określi manifest aplikacji utworzony w katalogu bin. Opublikowanie spowoduje skopiowanie tego manifestu do lokalizacji publikowania, która została ustawiona wcześniej.

8. Opublikuj projekt ponownie. Przejdź do strony **Publikowanie** , a następnie kliknij pozycję **Opublikuj teraz**.

     Ponownie Wyświetl manifest. Aby wyświetlić manifest, Otwórz katalog publikowania, kliknij plik prawym przyciskiem myszy, kliknij polecenie **Otwórz za pomocą**, wybierz **z listy opcję Wybierz program**, a następnie kliknij przycisk **Notatnik**.

     Wersja powinna teraz zostać odczytana:

    ```
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
    ```

## <a name="see-also"></a>Zobacz też
 [Strona zdarzenia kompilacji, Projektant projektu (C#)](../ide/reference/build-events-page-project-designer-csharp.md) okno [dialogowe zdarzeń przed kompilacją/kompilacja zdarzenia po kompilacji —](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md) instrukcje: Określanie [kompilowania i kompilowania](../ide/compiling-and-building-in-visual-studio.md) zdarzeń [kompilacji (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md)
