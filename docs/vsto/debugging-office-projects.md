---
title: Debugowanie projektów pakietu Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel projects [Office development in Visual Studio], debugging
- Word projects [Office development in Visual Studio], debugging
- Outlook [Office development in Visual Studio], debugging
- debugging [Office development in Visual Studio], Outlook projects
- Office projects [Office development in Visual Studio], debugging
- Outlook [Office development in Visual Studio], projects
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6c7320ae6cbd0a6d7baa94835177d2a3a6f222cf
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53647903"
---
# <a name="debug-office-projects"></a>Debugowanie projektów pakietu Office
  Można debugować projektów pakietu Office przy użyciu tego samego programu Microsoft [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] narzędzia, których używasz dla innych [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektów. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Funkcje debugera, takie jak możliwość Wstawianie punktów przerwania i wyświetlić zmienne w **lokalne** okna, są również dostępne podczas debugowania w projektach pakietu Office. Aby uzyskać więcej informacji na temat [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] narzędzia debugowania, zobacz [debugowania w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).  
  
> [!TIP]  
>  Aby uprościć, debugowanie, zamknij wszystkie wystąpienia aplikacji pakietu Office, zanim twórz i Debuguj je.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
> [!NOTE]  
>  Zainteresowanych opracowywaniem rozwiązań, które rozszerzają możliwości pakietu Office w [wiele platform](https://dev.office.com/add-in-availability)? Zapoznaj się z nowym [modelu dodatków pakietu Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Dodatki pakietu Office mieć o niewielkich rozmiarach, w porównaniu do dodatków narzędzi VSTO dla programów i rozwiązań, a następnie utworzyć je przy użyciu niemal dowolnej technologii, takich jak HTML5, JavaScript, CSS3 i XML programowanie dla sieci web.  
  
## <a name="start-and-stop-the-debugger"></a>Uruchamianie i zatrzymywanie debugowania  
 Możesz uruchomić debugowanie projektu programu pakietu Office, tak samo jak w rozpoczęciu debugowania innych [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektów; na przykład, możesz nacisnąć przycisk **F5** klucza. Po rozpoczęciu debugowania projektu dodatku narzędzi VSTO dla programów, jest uruchomiony nowy proces dla docelowych aplikacji pakietu Office i dodatku narzędzi VSTO jest ładowany.  
  
 Po rozpoczęciu debugowania projektu na poziomie dokumentu, dokument lub skoroszyt zostanie otwarty w nowy proces programu Word lub Excel.  
  
 Po zatrzymaniu debugera debuger nagle kończy proces aplikacji lub odłącza, jeśli masz debugera, ustaw można odłączyć. Wszystkie dokumenty, które są otwarte w procesie zakończone aplikacji pakietu Office są również zamknięte bez ostrzeżenia, a wszelkie niezapisane zmiany zostaną utracone. Może to obejmować wszystkich dokumentów lub skoroszytów, które są otwarte, gdy uruchomiona jest debugera.  
  
 Zazwyczaj jest lepszym rozwiązaniem odłączyć od procesu przed zatrzymaniem debugera, aby zakończyć pracę aplikacji pakietu Office w normalny sposób. Możesz również odłączyć od procesu najpierw Jeśli nadal chcesz współpracować z otwartym dokumencie lub arkuszu po zatrzymaniu debugera.  
  
 Jeśli debugujesz dostosowywania poziomie dokumentu dla programu Word, wielokrotnie zatrzymanie debugera i powodują, że program Word zamknąć nagle może prowadzić do szablonu normalnej uszkodzenie. W takim przypadku można usunąć uszkodzony szablonu normalnej i jego zostaną automatycznie odtworzone przy następnym otwarciu programu Word. Wszelkich makra, które były przechowywane w szablonie Normal nie są odtwarzane.  
  
### <a name="debug-office-2013-vsto-add-ins-by-using-either-office-2013-or-office-2016"></a>Debugowanie pakietu Office 2013 VSTO dodatków przy użyciu pakietu Office 2013 lub Office 2016  
 Jeśli używasz programu Visual Studio 2015 i mieć obie wersje programu side-by-side zainstalowanym pakietem Office, pakietu Office 2016 uruchomieniu programu Visual Studio. Jeśli używasz programu Visual Studio 2013, Office 2013 uruchomieniu programu Visual Studio.  
  
 Jeśli chcesz debugować dodatku narzędzi VSTO dla programów przy użyciu różnych wersji pakietu Office (2013 lub 2016), otwórz **projektanta projektu**, a następnie w **debugowania** karty, wybierz polecenie **uruchomienia programu zewnętrznego**przycisku opcji. Następnie przejdź do lokalizacji pliku wykonywalnego odpowiedniej aplikacji pakietu Office.  
  
## <a name="f10-and-f11-behavior"></a>Zachowanie F10 i F11  
 Po rozpoczęciu debugowania projektu pakietu Office **F10** i **F11** nie mają takie samo zachowanie, jak podczas uruchamiania debugowania innych projektów Visual Basic lub C#. W projektach Visual Basic lub C# debuger zatrzymuje się na funkcji main; w projektach pakietu Office Visual Studio nie ma kontroli nad funkcji main aplikacji pakietu Office. Jednak podczas debugowania, **F10** i **F11** mają te same funkcje jak projektów Visual Basic i C#.  
  
## <a name="display-exceptions"></a>Wyświetlić wyjątki  
 Ze względu na sposób, że kod zarządzany wchodzi w interakcję z kodem niezarządzanym programu Visual Studio nie są wyświetlane błędy, które są generowane przez aplikacje Microsoft Office. Na przykład jeśli dodatku narzędzi VSTO utworzone za pomocą narzędzi programistycznych pakietu Office w programie Visual Studio zgłasza wyjątek, aplikacji Microsoft Office jest kontynuowane bez wyświetlania błąd. Aby wyświetlić te błędy, należy ustawić debuger przerywa na wyjątki środowiska uruchomieniowego języka wspólnego. Aby uzyskać więcej informacji, zobacz [Zarządzanie wyjątkami za pomocą debugera](/visualstudio/debugger/managing-exceptions-with-the-debugger).  
  
 Jeśli ustawisz debuger przerywa na wyjątki środowiska uruchomieniowego języka wspólnego, wszystkie wyjątki będą teraz wkroczenia do debugera, w tym te, które mają być obsługiwane i niektóre wyjątki pierwszej szansy ze środowiska wykonawczego, która może nie być odpowiednie dla projektu. Błędy odnoszące się do msosec nie odnaleziono są wyświetlane w każdym projekcie, ale są bezpiecznie zignorować. Wyjątki te msosec nie wpłynie na rozwiązania.  
  
 Można również użyć **spróbuj... CATCH** instrukcji wokół swoje metody, aby przechwytywać wyjątki.  
  
 Domyślnie program Visual Studio również wyświetlana Just-In-Time debugowania błędów dla projektów pakietu Office; można jednak włączyć tę funkcję, aby mogli przeglądać błędy, które są wywoływane. Aby uzyskać więcej informacji, zobacz [debugowania w programie Visual Studio Just-In-Time](/visualstudio/debugger/just-in-time-debugging-in-visual-studio).  
  
## <a name="command-line-arguments"></a>Argumenty wiersza polecenia  
 Jeśli **Akcja uruchamiania** na **debugowania** strona właściwości jest równa **uruchomić projekt**, Visual Studio nie używać argumentów wiersza polecenia podczas debugowania projektu, nawet jeśli masz Ponieważ opcje uruchamiania, należy określić argumenty wiersza polecenia. Jeśli chcesz używać argumentów wiersza polecenia, po rozpoczęciu debugowania, musisz wybrać **Akcja uruchamiania** innych niż **uruchomić projekt**.  
  
## <a name="source-control"></a>Kontrola źródła  
 Debugowanie właściwości nie są współużytkowane przez wielu użytkowników pod kontrolą źródła. Projekty języka Visual Basic i C# zapisanie właściwości debugowania w pliku specyficzne dla użytkownika (*ProjectName*. vbproj.user lub *ProjectName*. csproj.user), a ten plik nie jest pod kontrolą źródła. Jeśli debugowanie jest więcej niż jedna osoba, każda osoba właściwości debugowania ręcznie wprowadzić.  
  
## <a name="debug-cached-datasets-in-a-document-level-project"></a>Debugowanie pamięci podręcznej zestawów danych w projekcie na poziomie dokumentu  
 Za każdym razem, gdy tworzysz projekt, zestaw danych jest opróżniany i utworzona ponownie. Jeśli chcesz debugować buforowany zestaw danych, należy otworzyć dokument poza programem Visual Studio i następnie dołączyć debuger.  
  
## <a name="debug-word-document-projects-based-on-the-word-97-2003-document-doc-format"></a>Projekty dokumentu programu Word debugowania na podstawie dokumentu programu Word 97 – 2003 (* .doc) format  
 Do debugowania projektu dokument programu Word, w oparciu o dokument programu Word 97 – 2003 (*/*.doc *) format, folder projektu należy dodać do listy zaufanych folderów. Aby uzyskać więcej informacji na temat jak to zrobić, zobacz [udzielenia zaufania do dokumentów](../vsto/granting-trust-to-documents.md).  
  
## <a name="debug-disabled-add-ins"></a>Dodatki debugowania wyłączone  
 Aplikacje Microsoft Office może spowodować wyłączenie dodatków narzędzi VSTO dla programów, które nieoczekiwane zachowanie. Aplikacji pakietu Microsoft Office powoduje wyłączenie dodatków narzędzi VSTO, aby uniemożliwić problematycznego kod ładowania każdorazowym uruchomieniu aplikacji. Jednak również jest łatwo spowodować nieoczekiwane zachowanie podczas debugowania typowy. Aby dowiedzieć się, jak ponownie włączyć dodatków narzędzi VSTO dla programów, zobacz [jak: Ponowne włączanie dodatku narzędzi VSTO dla programów, który został wyłączony](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md).  
  
 Istnieją dwa typy wyłączenia, aplikacji Microsoft Office ma być używany dla dodatków narzędzi VSTO: wyłączanie twardych i wyłączanie nietrwałego.  
  
### <a name="hard-disabling"></a>Wyłączanie trudne  
 Wyłączanie ciężko może wystąpić, gdy dodatku narzędzi VSTO powoduje, że aplikacja jest nieoczekiwanie zamykany. Go może również wystąpić na komputerze deweloperskim po zatrzymaniu debugera podczas <xref:Microsoft.Office.Tools.AddIn.Startup> wykonywania obsługi zdarzeń w dodatku VSTO. Gdy dodatku narzędzi VSTO dla programów jest wyłączone twardych, pojawia się w **elementy wyłączone** listy w aplikacji.  
  
 W przypadku aplikacji pakietu Office twardego spowoduje wyłączenie dodatku narzędzi VSTO utworzone za pomocą narzędzi programistycznych pakietu Office w programie Visual Studio, aplikacji powoduje wyłączenie tylko VSTO dodatek, który spowodował awarię. Innych dodatków narzędzi VSTO dla programów utworzone za pomocą narzędzi programistycznych pakietu Office w programie Visual Studio dla tej aplikacji pakietu Office, będą w dalszym ciągu obciążenia.  
  
### <a name="soft-disabling"></a>Wyłączanie miękkie  
 Wyłączanie nietrwałego może wystąpić, gdy dodatku narzędzi VSTO generuje błąd, który nie powoduje nieoczekiwanego zamknięcia aplikacji. Na przykład aplikacja nietrwałe może wyłączyć dodatku narzędzi VSTO dla programów, jeśli wyniku weryfikacji zgłasza wyjątek nieobsługiwany wyjątek podczas <xref:Microsoft.Office.Tools.AddIn.Startup> programu obsługi zdarzeń jest wykonywany. Gdy dodatku narzędzi VSTO dla programów jest wyłączone nietrwałego, pojawia się w **dodatki aplikacji nieaktywne** listy w aplikacji i zmienia wartość **LoadBehavior** wpis rejestru dla dodatku narzędzi VSTO Aby wskazać, że jest załadowany. Aby uzyskać więcej informacji na temat **LoadBehavior** wpis rejestru, zobacz [wpisy rejestru dotyczące dodatków narzędzi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
## <a name="troubleshoot-installation-errors-by-using-the-event-viewer"></a>Rozwiązywanie problemów z błędami instalacji za pomocą Podglądu zdarzeń  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Zapisuje komunikaty w Podglądzie zdarzeń Windows dla wszystkich wyjątków, które są generowane podczas instalowania lub odinstalowania rozwiązań pakietu Office. Te komunikaty służy do instalacji i problemy z wdrażaniem.  
  
## <a name="troubleshoot-startup-errors-by-using-a-log-file-and-error-messages"></a>Rozwiązywanie problemów z uruchamianiem przy użyciu dziennika plików i komunikaty o błędach  
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Można zapisywać wszystkie błędy, które występują podczas uruchamiania dziennika plik i wyświetlić liczbę błędów w oknie komunikatu. Te opcje są domyślnie wyłączone. Opcje można włączyć poprzez utworzenie zmiennych środowiskowych.  
  
 Aby wyświetlić poszczególne błędy w oknie komunikatu, należy utworzyć zmienną środowiskową o nazwie `VSTO_SUPPRESSDISPLAYALERTS` i ustaw ją na 0 (zero). Komunikaty można pominąć, usuwając zmiennej środowiskowej lub ustawiona na 1, (jeden).  
  
 Aby zapisać błędów w pliku dziennika, należy utworzyć zmienną środowiskową o nazwie `VSTO_LOGALERTS` i ustaw ją na 1 (jeden). [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Tworzy plik dziennika w folderze, który zawiera manifest wdrażania dodatku narzędzi VSTO dla programów lub w folderze, który zawiera dokument lub skoroszyt, który jest skojarzony z dostosowania. W przypadku niepowodzenia [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] tworzy plik dziennika w lokalnej *% TEMP %* folderu. Dla dodatków poziomu aplikacji narzędzi VSTO dla programów, domyślną nazwą jest *nazwa dodatku*. vsto.log. W przypadku projektów na poziomie dokumentu jest nazwa pliku dziennika *nazwa dokumentu*. *rozszerzenie*.log, takich jak ExcelWorkbook1.xlsx.log. Aby zatrzymać rejestrowanie błędów, Usuń zmienną środowiskową lub równa 0 (zero).  
  
## <a name="see-also"></a>Zobacz także  
 [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)   
 [Instrukcje: Ponowne włączanie dodatku narzędzi VSTO dla programów, która została wyłączona](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)   
 [Program dodatków narzędzi VSTO](../vsto/programming-vsto-add-ins.md)  
  
  