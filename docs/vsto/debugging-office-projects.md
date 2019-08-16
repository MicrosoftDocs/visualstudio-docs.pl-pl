---
title: Debugowanie projektów pakietu Office
ms.date: 08/14/2019
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2a0bf47afe3937d0c5550286efd50c8055ae5f47
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551651"
---
# <a name="debug-office-projects"></a>Debugowanie projektów pakietu Office
  Można debugować projekty pakietu Office przy użyciu tych samych narzędzi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] firmy Microsoft, które są [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] używane w innych projektach. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]funkcje debugera, takie jak możliwość wstawiania punktów przerwania i wyświetlania zmiennych w oknie **lokalne** , są również dostępne podczas debugowania projektów pakietu Office. Aby uzyskać więcej informacji [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] na temat narzędzi debugowania, zobacz [debugowanie w programie Visual Studio](../debugger/debugging-in-visual-studio.md).

> [!TIP]
> Aby uprościć debugowanie, przed skompilowaniem i debugowaniem Zamknij wszystkie otwarte wystąpienia aplikacji pakietu Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="start-and-stop-the-debugger"></a>Uruchamianie i zatrzymywanie debugera
 Możesz rozpocząć debugowanie projektu pakietu Office tak samo jak rozpoczęcie debugowania innych [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektów. na przykład możesz nacisnąć klawisz **F5** . Po rozpoczęciu debugowania projektu dodatku programu VSTO zostanie uruchomiony nowy proces dla aplikacji pakietu Office, który zostanie załadowany.

 Po rozpoczęciu debugowania projektu na poziomie dokumentu, dokument lub skoroszyt zostanie otwarty w nowym procesie programu Word lub Excel.

 Po zatrzymaniu debugera debuger kończy proces aplikacji w nieoczekiwany sposób lub odłącza się, jeśli masz debuger ustawiony do odłączenia. Wszystkie inne dokumenty, które są otwierane w zakończonym procesie aplikacji pakietu Office, również są zamykane bez ostrzeżenia, a wszystkie niezapisane zmiany zostaną utracone. Może to obejmować wszystkie dokumenty lub skoroszyty, które są otwierane, gdy debuger jest uruchomiony.

 Zazwyczaj lepiej jest odłączyć od procesu przed zatrzymaniem debugera, aby można było zamknąć aplikację pakietu Office w zwykły sposób. Możesz również odłączyć od procesu, jeśli nadal chcesz korzystać z otwartego dokumentu lub arkusza po zatrzymaniu debugera.

 W przypadku debugowania dostosowania na poziomie dokumentu dla programu Word, wielokrotne zatrzymanie debugera i spowodowanie nagłego zamknięcia programu Word może prowadzić do uszkodzenia normalnego szablonu. W takim przypadku można usunąć uszkodzony szablon Normal. zostanie on automatycznie odtworzony po następnym otwarciu programu Word. Jednak wszystkie makra, które były przechowywane w szablonie Normal, nie są tworzone ponownie.

### <a name="debug-office-2013-vsto-add-ins-by-using-either-office-2013-or-office-2016"></a>Debugowanie dodatków VSTO pakietu Office 2013 przy użyciu pakietu Office 2013 lub Office 2016
 Jeśli używasz programu Visual Studio 2015 i obie wersje pakietu Office są zainstalowane obok siebie, program Visual Studio uruchamia pakiet Office 2016. Jeśli używasz Visual Studio 2013, program Visual Studio uruchamia pakiet Office 2013.

 Jeśli chcesz debugować dodatek VSTO przy użyciu innej wersji pakietu Office (2013 lub 2016), Otwórz **projektanta projektu**, a następnie na karcie **debugowanie** wybierz przycisk opcji **Uruchom program zewnętrzny** . Następnie przejdź do lokalizacji odpowiedniego pliku wykonywalnego aplikacji pakietu Office.

## <a name="f10-and-f11-behavior"></a>Zachowanie F10 i F11
 Po rozpoczęciu debugowania projektu pakietu Office **F10** i **F11** nie mają takiego samego zachowania jak podczas uruchamiania debugowania innych Visual Basic lub C# projektów. W Visual Basic lub C# projektach debuger zatrzyma funkcję Main; w projektach pakietu Office Program Visual Studio nie ma kontroli nad główną funkcją aplikacji pakietu Office. Jednak podczas debugowania, **F10** i **F11** mają takie same funkcje jak w Visual Basic i C# projektach.

## <a name="display-exceptions"></a>Wyświetl wyjątki
 Ze względu na sposób, w jaki kod zarządzany współdziała z niezarządzanym kodem, program Visual Studio nie wyświetla błędów zgłaszanych przez Microsoft Office aplikacji. Na przykład jeśli dodatek VSTO utworzony przy użyciu narzędzi programistycznych pakietu Office w programie Visual Studio zgłosi wyjątek, aplikacja Microsoft Office kontynuuje działanie bez wyświetlania błędu. Aby wyświetlić te błędy, ustaw debuger do przerwania w przypadku wyjątków środowiska uruchomieniowego języka wspólnego. Aby uzyskać więcej informacji, zobacz [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md).

 Jeśli ustawisz debuger do przerw w wyjątkach środowiska uruchomieniowego języka wspólnego, wszystkie wyjątki zostaną teraz zerwane w debugerze, w tym o obsługiwanych i pewnych wyjątkach pierwszej szansie od samego środowiska uruchomieniowego, które mogą nie być odpowiednie dla Twojego projektu. Błędy odwołujące się do msosec nie są wyświetlane w każdym projekcie, ale są bezpieczne do ignorowania. Te wyjątki msosec nie wpłyną na Twoje rozwiązanie.

 Możesz również użyć **try... Instrukcje catch** dotyczące metod przechwytywania wyjątków.

 Domyślnie program Visual Studio nie wyświetla także błędów debugowania just-in-Time dla projektów pakietu Office; można jednak włączyć tę funkcję, aby wyświetlić zgłoszone błędy. Aby uzyskać więcej informacji, zobacz [debugowanie just in Time w programie Visual Studio](../debugger/just-in-time-debugging-in-visual-studio.md).

## <a name="command-line-arguments"></a>Argumenty wiersza polecenia
 Jeśli **Akcja uruchamiania** na stronie właściwości **debugowania** jest ustawiona na **Uruchom projekt**, program Visual Studio nie używa argumentów wiersza polecenia podczas debugowania projektu, nawet jeśli określono argumenty wiersza polecenia jako opcje uruchamiania. Jeśli chcesz użyć argumentów wiersza polecenia podczas uruchamiania debugowania, musisz wybrać **akcję uruchamiania** inną niż **początkowy projekt**.

## <a name="source-control"></a>Kontrola źródła
 Właściwości debugowania nie są współużytkowane przez wielu użytkowników w ramach kontroli źródła. Visual Basic i C# projekty przechowują właściwości debugowania w pliku specyficznym dla użytkownika (*ProjectName*. vbproj. user lub *ProjectName*. csproj. user), a ten plik nie znajduje się pod kontrolą źródła. Jeśli debugowanie jest więcej niż jedna osoba, każda osoba musi ręcznie wprowadzić właściwości debugowania.

## <a name="debug-cached-datasets-in-a-document-level-project"></a>Debuguj buforowane zestawy danych w projekcie na poziomie dokumentu
 Za każdym razem, gdy kompilujesz projekt, zestaw danych jest opróżniany i tworzony ponownie. Jeśli chcesz debugować buforowany zestaw danych, musisz otworzyć dokument poza programem Visual Studio, a następnie dołączyć debuger.

## <a name="debug-word-document-projects-based-on-the-word-97-2003-document-doc-format"></a>Debuguj projekty dokumentów programu Word na podstawie formatu dokumentu programu Word 97-2003 (*. doc)
 Aby debugować projekt dokumentu programu Word na podstawie formatu dokumentu programu Word */* 97-2003 (doc *), należy dodać folder projektu do listy zaufanych folderów. Aby uzyskać więcej informacji o tym, jak to zrobić, zobacz [Grant Trust to Documents](../vsto/granting-trust-to-documents.md).

## <a name="debug-disabled-add-ins"></a>Debuguj wyłączone dodatki
 Aplikacje Microsoft Office mogą wyłączyć dodatki VSTO, które zachowywać się nieoczekiwanie. Aplikacja Microsoft Office wyłącza Dodatki VSTO, aby zapobiec ładowaniu problematycznego kodu przy każdym uruchomieniu aplikacji. Jest to jednak łatwe w obsłudze nieoczekiwane zachowanie podczas typowego debugowania. Aby uzyskać informacje o tym, jak ponownie włączyć dodatki narzędzi VSTO, zobacz [How to: Ponownie włącz dodatek narzędzi VSTO, który został wyłączony](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md).

 Istnieją dwa typy wyłączania, które są używane przez aplikacje Microsoft Office dla dodatków narzędzi VSTO: trwałe wyłączanie i wyłączanie.

### <a name="hard-disabling"></a>Stałe wyłączanie
 Twarde wyłączenie może wystąpić, gdy dodatek VSTO powoduje nieoczekiwane zamknięcie aplikacji. Może również wystąpić na komputerze deweloperskim, jeśli zostanie zatrzymany debuger podczas <xref:Microsoft.Office.Tools.AddIn.Startup> wykonywania programu obsługi zdarzeń w dodatku VSTO. Gdy dodatek narzędzi VSTO zostanie trwale wyłączony, pojawia się na liście **Wyłączone elementy** w aplikacji.

 Jeśli aplikacja pakietu Office spowoduje wyłączenie dodatku VSTO utworzonego przy użyciu narzędzi programistycznych pakietu Office w programie Visual Studio, aplikacja wyłączy tylko dodatek narzędzi VSTO, który spowodował awarię. Inne dodatki VSTO utworzone przy użyciu narzędzi programistycznych pakietu Office w programie Visual Studio dla aplikacji pakietu Office będą nadal ładowane.

### <a name="soft-disabling"></a>Wyłączanie nietrwałe
 Wyłączenie nietrwałe może wystąpić, gdy dodatek VSTO generuje błąd, który nie powoduje nieoczekiwanego zamknięcia aplikacji. Na przykład aplikacja może uniemożliwić wyłączenie dodatku VSTO, jeśli zgłasza nieobsługiwany wyjątek podczas <xref:Microsoft.Office.Tools.AddIn.Startup> wykonywania programu obsługi zdarzeń. Gdy dodatek narzędzi VSTO jest wyłączony, pojawia się na liście **dodatków nieaktywnych aplikacji** w aplikacji, a aplikacja zmienia wartość wpisu rejestru **LOADBEHAVIOR** dla dodatku VSTO, aby wskazać, że jest on zwolniony. Aby uzyskać więcej informacji na temat wpisu rejestru **LoadBehavior** , zobacz [wpisy rejestru dla dodatków narzędzi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

## <a name="troubleshoot-installation-errors-by-using-the-event-viewer"></a>Rozwiązywanie problemów z błędami instalacji przy użyciu Podgląd zdarzeń
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Zapisuje komunikaty do Podgląd zdarzeń w systemie Windows dla wszystkich wyjątków zgłaszanych podczas instalowania lub odinstalowywania rozwiązań pakietu Office. Te komunikaty umożliwiają rozwiązywanie problemów z instalacją i wdrażaniem.

## <a name="troubleshoot-startup-errors-by-using-a-log-file-and-error-messages"></a>Rozwiązywanie problemów z błędami uruchamiania przy użyciu pliku dziennika i komunikatów o błędach
 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Może zapisywać wszystkie błędy, które występują podczas uruchamiania do pliku dziennika lub wyświetlają każdy błąd w oknie komunikatu. Domyślnie te opcje są wyłączone. Możesz włączyć opcje, tworząc zmienne środowiskowe.

 Aby wyświetlić każdy błąd w oknie komunikatu, Utwórz zmienną środowiskową o nazwie `VSTO_SUPPRESSDISPLAYALERTS` i ustaw ją na 0 (zero). Możesz pominąć komunikaty, usuwając zmienną środowiskową lub ustawiając ją na 1 (jeden).

 Aby zapisać błędy w pliku dziennika, Utwórz zmienną środowiskową o nazwie `VSTO_LOGALERTS` i ustaw ją na 1 (jeden). [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Tworzy plik dziennika w folderze zawierającym manifest wdrożenia dla dodatku VSTO lub w folderze zawierającym dokument lub skoroszyt, który jest skojarzony z dostosowaniem. Jeśli to się nie powiedzie, program [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] tworzy plik dziennika w lokalnym folderze *% temp%* . W przypadku dodatków VSTO na poziomie aplikacji domyślna nazwa to *Nazwa dodatku*. VSTO. log. W przypadku projektów na poziomie dokumentu nazwa pliku dziennika jest nazwą *dokumentu*. *rozszerzenie*. log, takie jak ExcelWorkbook1. xlsx. log. Aby zatrzymać rejestrowanie błędów, Usuń zmienną środowiskową lub ustaw ją na 0 (zero).

## <a name="see-also"></a>Zobacz także

- [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)
- [Instrukcje: Ponownie włącz dodatek narzędzi VSTO, który został wyłączony](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)
- [Dodatki narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md)