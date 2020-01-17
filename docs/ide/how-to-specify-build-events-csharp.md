---
title: 'Instrukcje: Określanie zdarzeń kompilacji (C#)'
ms.date: 03/21/2019
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: b4ce1ad9-5215-4b6f-b6a2-798b249aa335
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 134a5b7cd4bb0ffc9c00a41df12ed196dd2a9212
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115124"
---
# <a name="how-to-specify-build-events-c"></a>Instrukcje: Określanie zdarzeń kompilacji (C#)

Użyj zdarzeń kompilacji, aby określić polecenia, które są uruchamiane przed rozpoczęciem kompilacji lub po zakończeniu kompilacji. Zdarzenia kompilacji są wykonywane tylko wtedy, gdy kompilacja pomyślnie osiągnie te punkty w procesie kompilacji.

Po skompilowaniu projektu zdarzenia przed kompilacją są dodawane do pliku o nazwie *PreBuildEvent. bat* , a zdarzenia po kompilacji są dodawane do pliku o nazwie *PostBuildEvent. bat*. Aby zapewnić sprawdzanie błędów, należy dodać własne polecenia sprawdzania błędów do kroków kompilacji.

## <a name="specify-a-build-event"></a>Określ zdarzenie kompilacji

1. W **Eksplorator rozwiązań**wybierz projekt, dla którego chcesz określić zdarzenie kompilacji.

2. W menu **projekt** kliknij polecenie **Właściwości**.

3. Wybierz kartę **zdarzenia kompilacji** .

4. W polu **wiersz polecenia zdarzenia przed kompilacją** Określ składnię zdarzenia kompilacji.

   > [!NOTE]
   > Zdarzenia przed kompilacją nie są uruchamiane, jeśli projekt jest aktualny i żadna kompilacja nie zostanie wyzwolona.

5. W polu **wiersz polecenia zdarzenia po kompilacji** Określ składnię zdarzenia kompilacji.

   > [!NOTE]
   > Dodaj instrukcję `call` przed wszystkimi poleceniami po kompilacji, które uruchamiają pliki *. bat* . Na przykład `call C:\MyFile.bat` lub `call C:\MyFile.bat call C:\MyFile2.bat`.

6. W polu **Uruchom zdarzenie po kompilacji** Określ, w jaki sposób mają być uruchamiane zdarzenia po kompilacji.

   > [!NOTE]
   > Aby dodać dłuższą składnię lub wybrać dowolne makra kompilacji z [okna dialogowego zdarzenia sprzed kompilacji/zdarzenia po kompilacji](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md), kliknij przycisk wielokropka ( **...** ), aby wyświetlić pole edycji.

   Składnia zdarzenia kompilacji może zawierać dowolne polecenie, które jest prawidłowe w wierszu polecenia lub pliku *. bat* . Nazwa pliku wsadowego powinna być poprzedzona `call`, aby upewnić się, że wszystkie kolejne polecenia są wykonywane.

   > [!NOTE]
   > Jeśli wydarzenie przed kompilacją lub po kompilacji nie zakończy się pomyślnie, możesz przerwać kompilację, aby zakończyć działanie zdarzenia z kodem innym niż zero (0), co oznacza pomyślne wykonanie akcji.

## <a name="example"></a>Przykład

Poniższa procedura pokazuje, jak ustawić minimalną wersję systemu operacyjnego w manifeście aplikacji przy użyciu polecenia *. exe* , które jest wywoływane z zdarzenia po kompilacji (plik *. exe. manifest* w katalogu projektu). Minimalna wersja systemu operacyjnego to czterocyfrowy numer, taki jak 4.10.0.0. Aby ustawić minimalną wersję systemu operacyjnego, polecenie zmieni sekcję `<dependentOS>` manifestu:

```xml
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

### <a name="create-an-exe-command-to-change-the-application-manifest"></a>Utwórz polecenie. exe, aby zmienić manifest aplikacji

1. Utwórz nowy projekt **aplikacji konsoli** dla tego polecenia. Nazwij projekt **ChangeOSVersionCS**.

2. W *program.cs*Dodaj następujący wiersz do innych dyrektyw `using` w górnej części pliku:

   ```csharp
   using System.Xml;
   ```

3. W przestrzeni nazw `ChangeOSVersionCS` Zastąp implementację klasy `Program` następującym kodem:

   ```csharp
   class Program
   {
      /// <summary>
      /// This function sets the minimum operating system version for a ClickOnce application.
      /// </summary>
      /// <param name="args">
      /// Command Line Arguments:
      /// 0 - Path to application manifest (.exe.manifest)
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

   Polecenie przyjmuje dwa argumenty: ścieżka do manifestu aplikacji (czyli folder, w którym proces kompilacji tworzy manifest, zazwyczaj *ProjectName. publish*) i nową wersję systemu operacyjnego.

4. Skompiluj projekt.

5. Skopiuj plik *. exe* do katalogu, takiego jak *C:\TEMP\ChangeOSVersionVB.exe*.

Następnie Wywołaj to polecenie w zdarzeniu po kompilacji, aby zmodyfikować manifest aplikacji.

### <a name="invoke-a-post-build-event-to-modify-the-application-manifest"></a>Wywołaj zdarzenie po kompilacji, aby zmodyfikować manifest aplikacji

1. Utwórz nowy projekt **aplikacji Windows Forms** i nadaj mu nazwę **CSWinApp**.

2. Po wybraniu projektu w **Eksplorator rozwiązań**w menu **projekt** wybierz polecenie **Właściwości**.

3. W **projektancie projektu**Znajdź stronę **Publikowanie** i ustaw **lokalizację publikowania** na *C:\Temp*.

4. Opublikuj projekt, klikając pozycję **Opublikuj teraz**.

   Plik manifestu został skompilowany i zapisany w *lokalizacji c:\temp\ CSWinApp_1_0_0_0 \cswinapp.exe.manifest*. Aby wyświetlić manifest, kliknij plik prawym przyciskiem myszy, kliknij polecenie **Otwórz za pomocą**, wybierz **z listy opcję Wybierz program**, a następnie kliknij przycisk **Notatnik**.

   Wyszukaj w pliku `<osVersionInfo>` elementu. Na przykład wersja może być:

   ```xml
   <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   ```

5. W **projektancie projektu**kliknij kartę **zdarzenia kompilacji** , a następnie kliknij pozycję **Edytuj po kompilacji**.

6. W polu **wiersz polecenia zdarzenia po kompilacji** wprowadź następujące polecenie:

   `C:\TEMP\ChangeOSVersionCS.exe "$(TargetPath).manifest" 5.1.2600.0`

   Podczas kompilowania projektu to polecenie zmienia minimalną wersję systemu operacyjnego w manifeście aplikacji na 5.1.2600.0.

   Ponieważ makro `$(TargetPath)` wyraża pełną ścieżkę do tworzonego pliku wykonywalnego, `$(TargetPath).manifest` określa manifest aplikacji utworzony w katalogu *bin* . Publikowanie kopiuje ten manifest do lokalizacji publikowania, która została ustawiona wcześniej.

7. Opublikuj projekt ponownie.

   Wersja manifestu powinna teraz zostać odczytana:

   ```xml
   <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
   ```

## <a name="see-also"></a>Zobacz także

- [Strona zdarzenia kompilacji, Projektant projektu (C#)](../ide/reference/build-events-page-project-designer-csharp.md)
- [Zdarzenie przed kompilacją/wiersz polecenia zdarzenia po kompilacji](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Instrukcje: Określanie zdarzeń kompilacji (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md)
- [Kompilowanie i tworzenie kompilacji](../ide/compiling-and-building-in-visual-studio.md)
