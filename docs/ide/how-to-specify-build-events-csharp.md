---
title: 'Jak: Określanie zdarzeń kompilacji (C#)'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115124"
---
# <a name="how-to-specify-build-events-c"></a>Jak: Określanie zdarzeń kompilacji (C#)

Użyj zdarzeń kompilacji, aby określić polecenia, które są uruchamiane przed rozpoczęciem kompilacji lub po zakończeniu kompilacji. Tworzenie zdarzeń wykonywane tylko wtedy, gdy kompilacja pomyślnie osiągnie te punkty w procesie kompilacji.

Podczas tworzenia projektu zdarzenia przed kompilacją są dodawane do pliku o nazwie *PreBuildEvent.bat,* a zdarzenia po kompilacji są dodawane do pliku o nazwie *PostBuildEvent.bat*. Jeśli chcesz upewnić się, że sprawdzanie błędów, dodaj własne polecenia sprawdzania błędów do kroków kompilacji.

## <a name="specify-a-build-event"></a>Określanie zdarzenia kompilacji

1. W **Eksploratorze rozwiązań**wybierz projekt, dla którego chcesz określić zdarzenie kompilacji.

2. W menu **Projekt** kliknij polecenie **Właściwości**.

3. Wybierz kartę **Zdarzenia kompilacji.**

4. W polu **polecenia Zdarzenia przed kompilacją** określ składnię zdarzenia kompilacji.

   > [!NOTE]
   > Zdarzenia przed kompilacją nie są uruchamiane, jeśli projekt jest aktualny i nie zostanie wyzwolona żadna kompilacja.

5. W polu **polecenia zdarzenia po kompilacji** określ składnię zdarzenia kompilacji.

   > [!NOTE]
   > Dodaj `call` instrukcję przed wszystkimi poleceniami po kompilacji, które uruchamiają pliki *.bat.* Na przykład: `call C:\MyFile.bat` lub `call C:\MyFile.bat call C:\MyFile2.bat`.

6. W polu **Uruchom zdarzenie po kompilacji** określ, w jakich warunkach należy uruchomić zdarzenie po kompilacji.

   > [!NOTE]
   > Aby dodać długą składnię lub wybrać dowolne makra kompilacji z [okna dialogowego wiersza polecenia Zdarzenia przed kompilacją/po utworzeniu,](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)kliknij przycisk wielokropka (**...**), aby wyświetlić pole edycji.

   Składnia zdarzenia kompilacji może zawierać dowolne polecenie prawidłowe w wierszu polecenia lub w pliku *bat.* Nazwa pliku wsadowego powinna być `call` poprzedzona, aby upewnić się, że wszystkie kolejne polecenia są wykonywane.

   > [!NOTE]
   > Jeśli zdarzenie przed kompilacją lub po kompilacji nie zakończy się pomyślnie, można zakończyć kompilację, mając zakończenie akcji zdarzenia z kodem innym niż zero (0), który wskazuje pomyślną akcję.

## <a name="example"></a>Przykład

Poniższa procedura pokazuje, jak ustawić minimalną wersję systemu operacyjnego w manifeście aplikacji przy użyciu polecenia *.exe,* które jest wywoływane ze zdarzenia po kompilacji (pliku *.exe.manifest* w katalogu projektu). Minimalna wersja systemu operacyjnego to czteroczęściowy numer, taki jak 4.10.0.0. Aby ustawić minimalną wersję systemu operacyjnego, polecenie zmieni sekcję `<dependentOS>` manifestu:

```xml
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

### <a name="create-an-exe-command-to-change-the-application-manifest"></a>Tworzenie polecenia exe w celu zmiany manifestu aplikacji

1. Utwórz nowy projekt **aplikacji konsoli** dla polecenia. Nazwij projekt **ChangeOSVersionCS**.

2. W *Program.cs*, dodaj następujący wiersz do `using` innych dyrektyw w górnej części pliku:

   ```csharp
   using System.Xml;
   ```

3. W `ChangeOSVersionCS` obszarze nazw zastąp `Program` implementację klasy następującym kodem:

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

   Polecenie przyjmuje dwa argumenty: ścieżkę manifestu aplikacji (czyli folderu, w którym proces kompilacji tworzy manifest, zazwyczaj *Projectname.publish)* i nową wersję systemu operacyjnego.

4. Skompiluj projekt.

5. Skopiuj plik *exe* do katalogu takiego jak *C:\TEMP\ChangeOSVersionVB.exe*.

Następnie wywołać to polecenie w zdarzeniu po kompilacji, aby zmodyfikować manifest aplikacji.

### <a name="invoke-a-post-build-event-to-modify-the-application-manifest"></a>Wywoływanie zdarzenia po kompilacji w celu zmodyfikowania manifestu aplikacji

1. Utwórz nowy projekt **aplikacji Windows Forms App** i nadaj jej nazwę aplikacji **CSWinApp**.

2. Po wybraniu projektu w **Eksploratorze rozwiązań**w menu **Projekt** wybierz polecenie **Właściwości**.

3. W **Projektancie projektu**znajdź stronę **Publikowania** i ustaw **lokalizację publikowania** na *C:\TEMP*.

4. Opublikuj projekt, klikając pozycję **Publikuj teraz**.

   Plik manifestu jest zbudowany i zapisany w *pliku C:\TEMP\CSWinApp_1_0_0_0\CSWinApp.exe.manifest*. Aby wyświetlić manifest, kliknij plik prawym przyciskiem myszy, kliknij polecenie **Otwórz za pomocą**, wybierz pozycję Wybierz program z **listy**, a następnie kliknij polecenie **Notatnik**.

   Wyszukaj w `<osVersionInfo>` pliku element. Na przykład wersja może być:

   ```xml
   <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   ```

5. W **projektancie projektu**kliknij kartę **Pokaż zdarzenia,** a następnie kliknij pozycję **Edytuj post-build**.

6. W polu **Wiersz polecenia zdarzenia po utworzeniu** wprowadź następujące polecenie:

   `C:\TEMP\ChangeOSVersionCS.exe "$(TargetPath).manifest" 5.1.2600.0`

   Podczas tworzenia projektu to polecenie zmienia minimalną wersję systemu operacyjnego w manifeście aplikacji na 5.1.2600.0.

   Ponieważ `$(TargetPath)` makro wyraża pełną ścieżkę dla tworzonego `$(TargetPath).manifest` pliku wykonywalnego, określa manifest aplikacji utworzony w katalogu *bin.* Publikowanie kopiuje ten manifest do lokalizacji publikowania ustawionej wcześniej.

7. Ponownie opublikuj projekt.

   Wersja manifestu powinna teraz brzmieć:

   ```xml
   <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
   ```

## <a name="see-also"></a>Zobacz też

- [Strona Tworzenie zdarzeń, Projektant projektu (C#)](../ide/reference/build-events-page-project-designer-csharp.md)
- [Okno dialogowe wiersza polecenia Zdarzenia przed kompilacją/po utworzeniu](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Jak: Określanie zdarzeń kompilacji (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md)
- [Kompilowanie i tworzenie kompilacji](../ide/compiling-and-building-in-visual-studio.md)
