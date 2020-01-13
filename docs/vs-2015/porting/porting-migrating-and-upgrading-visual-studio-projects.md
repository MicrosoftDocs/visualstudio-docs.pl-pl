---
title: Przenoszenie, migrowanie i uaktualnianie projektów | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- Win8ExpressDesktopBlock
- w8trefactor
- VS.ReviewProjectAndSolutionChangesDialog.UpgradeRetarget
- ProjectCompatibilityDlgHelpTopic
- VS.ReviewProjectAndSolutionChangesDialog.Upgrade
helpviewer_keywords:
- conversion, projects
- asset compatibility
- projects, conversion
ms.assetid: bee759bd-6ff5-4c2e-913a-ea7d3c906c29
caps.latest.revision: 108
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 3361b04900e549d037338abfba0911b232c9e1bd
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2020
ms.locfileid: "75919102"
---
# <a name="port-migrate-and-upgrade-visual-studio-projects"></a>Przenoszenie, migrowanie i uaktualnianie projektów programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio, zobacz temat [migracja projektu i dokumentacja uaktualnienia dla programu Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects).

Gdy rozważasz, czy chcesz przejść do nowszej wersji programu Visual Studio, możesz użyć tego artykułu, aby dowiedzieć się, które rozwiązania, projekty, pliki i inne zasoby utworzone w Visual Studio 2013, Visual Studio 2012 lub Visual Studio 2010 SP1 zostaną uruchomione bez modyfikacji Visual Studio 2013 i programu Visual Studio 2015. Można też uzyskać dostęp do tej strony, Jeśli napotkasz komunikat o błędzie podczas próby otwarcia projektu, który nie jest obsługiwany w wersji programu Visual Studio, która została otwarta w programie lub która wymaga zestawu SDK lub rozszerzenia, takiego jak zestaw Azure SDK dla platformy .NET.

Wiele powszechnie używanych zasobów działa tak samo w programie Visual Studio 2015, Visual Studio 2013 i dwóch wcześniejszych wersjach. Na przykład w programie Visual Studio 2015 można otworzyć projekt, który został utworzony w Visual Studio 2013 lub Visual Studio 2012, zmienić go, a następnie otworzyć ponownie w programie Visual Studio 2015. Zmiany zostaną zachowane, a projekt będzie działać tak samo, jak w starszej wersji. Podobnie jest w przypadku wielu zasobów utworzonych w Visual Studio 2010 SP1.

W przypadku Visual Basic w programie Visual Studio 2015 nie wprowadzono żadnych zmian, które nie spowodują, że aplikacja Visual Basic, która została utworzona w Visual Studio 2013 z kompilacji. Zachowanie w czasie wykonywania aplikacji Visual Basic, które są ponownie kompilowane przy użyciu programu Visual Studio 2015, nie zmieni się.

Jeśli używasz programu Visual Studio 2015 razem z Visual Studio 2013, Visual Studio 2012 lub Visual Studio 2010 SP1, możesz tworzyć i modyfikować projekty i pliki w dowolnej wersji. Można przenosić projekty i pliki między wersjami, o ile nie zostaną dodane funkcje, które nie są obsługiwane w co najmniej jednej wersji.

## <a name="project"></a> Projekty

Poniższa lista zawiera opis obsługi programu Visual Studio 2015 i Visual Studio 2013 dla projektów, które zostały utworzone w programie Visual Studio 2012 lub Visual Studio 2010 SP1. Użyj tej listy, aby określić, czy można otworzyć projekt "AS IS" w programie Visual Studio 2015, Visual Studio 2013, Visual Studio 2012 lub Visual Studio 2010 z dodatkiem SP1, czy też musisz zmodyfikować go w celu zapewnienia zgodności.

|Typ projektu|Zgodność|
|---------------------|-------------------|
|Windows Universal apps platformy|Do zainstalowania narzędzi Universal Windows apps, w Instalatorze programu Visual Studio, wybierz **niestandardowe** lub **Modyfikuj**, a następnie wybierz pozycję **narzędzia do programowania aplikacji uniwersalnych Windows**.<br /><br /> Programowanie aplikacji platforma uniwersalna systemu Windows (platformy UWP) dla systemu Windows 10 jest obsługiwane tylko w programie Visual Studio 2015 w systemie Windows 10 lub [!INCLUDE[win81](../includes/win81-md.md)].|
|Aplikacje Windows Store|Tworzenie aplikacji Windows Store, w tym uniwersalnych aplikacji przeznaczonych dla Windows 8.1 i Windows Phone 8.1, jest obsługiwana w [!INCLUDE[win81](../includes/win81-md.md)] i Windows 10. Istniejące [!INCLUDE[win8](../includes/win8-md.md)] projekty mogą w dalszym ciągu być obsługiwane, ale nowe [!INCLUDE[win8](../includes/win8-md.md)] projekty nie mogą być tworzone. [!INCLUDE[win81](../includes/win81-md.md)] projekty można być zależne tylko od niektórych typów odwołań. Aby uzyskać więcej informacji, zobacz [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md). **Uwaga:** [!INCLUDE[win81](../includes/win81-md.md)] projekty tworzone przy użyciu programu visual Studio 2015 lub Visual Studio 2013 nie mogą być otwierane w programie visual Studio 2012. Wynika to z faktu, że projekty [!INCLUDE[win81](../includes/win81-md.md)] utworzone za pomocą programu Visual Studio 2015 i Visual Studio 2013 celu są przeznaczone dla tych wersji, a program Visual Studio 2012 obsługuje tylko [!INCLUDE[win8](../includes/win8-md.md)] projekty przeznaczone do [!INCLUDE[win8](../includes/win8-md.md)].|
|[!INCLUDE[net_v451](../includes/net-v451-md.md)]|Możesz tworzyć i używać tych projektów w programie Visual Studio 2015 i Visual Studio 2013 po zainstalowaniu odpowiedniego pakietu wielowymiarowego. Te projekty nie są obsługiwane w Visual Studio 2010 SP1.|
|[!INCLUDE[net_v45](../includes/net-v45-md.md)]|Możesz tworzyć i otwierać te projekty w programie Visual Studio 2015, Visual Studio 2013 i Visual Studio 2012, ale nie w programie Visual Studio 2010 SP1.|
|BizTalk|Projekty programu BizTalk Server nie są zgodne z programem Visual Studio 2015 lub Visual Studio 2013.|
|Aplikacja lub biblioteka klas C#/Visual Basic Silverlight 4|Jeśli zezwolisz programowi Visual Studio na automatyczne aktualizowanie projektu, możesz go otworzyć w Visual Studio 2013 lub w programie Visual Studio 2012.|
|Formularz sieci Web lub formularz Windows C#/Visual Basic|Możesz otworzyć projekt w Visual Studio 2013 i Visual Studio 2012.|
|Visual Basic 6 i Visual C++ 6|Program Visual Studio 2012 i Visual Studio 2013 nie obsługują debugowania aplikacji utworzonych za pomocą Visual Basic 6 lub C++ Visual 6; Aby debugować te aplikacje, należy użyć wcześniejszych wersji programu Visual Studio.|
|Kodowany test interfejsu użytkownika|Jeśli zezwolisz programowi Visual Studio na automatyczne aktualizowanie projektu, możesz go otworzyć w Visual Studio 2013, Visual Studio 2012 i Visual Studio 2010 z dodatkiem SP1.|
|Język F#|Jeśli zezwolisz programowi Visual Studio na uaktualnienie projektu, który został utworzony w programie Visual Studio 2010 z dodatkiem SP1, możesz go otworzyć w Visual Studio 2013 i Visual Studio 2012. Nie można jednak uaktualnić projektu Silverlight, który został utworzony w starszej wersji programu Visual Studio, aby Visual Studio 2013. Zamiast tego należy utworzyć projekt Silverlight w Visual Studio 2013, a następnie skopiować do niego swój kod. Projekty Silverlight tworzone w Visual Studio 2013 docelowym Silverlight 5.|
|LightSwitch|Jeśli zezwolisz programowi Visual Studio na automatyczne aktualizowanie projektu, możesz go otworzyć tylko w Visual Studio 2013.|
|Pamięć podręczna lokalnej bazy danych|Szablon pamięci podręcznej lokalnej bazy danych i okno dialogowe **Konfiguruj synchronizację danych** nie są uwzględnione w Visual Studio 2013. Za pomocą Visual Studio 2013 do otwierania i uruchamiania projektów utworzonych w programie [!INCLUDE[vs2010](../includes/vs2010-md.md)], jeśli jest zainstalowany program Microsoft Synchronization Services w wersji 1.0, ale jeśli chcesz je zaktualizować w Visual Studio 2013, musisz ręcznie wprowadzić wszystkie zmiany w kodzie. Jako alternatywę, można nadal używać [!INCLUDE[vs2010](../includes/vs2010-md.md)] do utrzymywania i aktualizacji tych projektów.  W nowych wdrożeniach oznacz jako docelowy nowy model synchronizacji dostarczony przez Microsoft Sync Framework. Aby uzyskać informacje, zobacz [Microsoft Sync Framework Developer Center](https://msdn.microsoft.com/sync/default)|
|Platforma ramowa kontrolera widoku modelu|Program Visual Studio 2010 z dodatkiem SP1 obsługuje tylko MVC 2 i MVC 3, Visual Studio 2012 obsługuje tylko MVC 3 i MVC 4, a Visual Studio 2013 obsługuje tylko MVC 4. Aby uzyskać informacje na temat automatycznego uaktualnienia MVC 2 do MCV 3, zobacz [aktualizator aplikacji ASP.NET MVC 3](https://aspnet.codeplex.com/releases/view/59008). Aby uzyskać informacje na temat ręcznego uaktualnienia MVC 2 do MVC 3, zobacz [uaktualnianie ASP.NET MVC 2 Projekct do ASP.NET MVC 3 Tools Update](https://aspnet.codeplex.com/releases/view/59008). Aby uzyskać informacje na temat ręcznego uaktualnienia mvc3 do MVC 4, zobacz [uaktualnianie projektu ASP.NET MVC 3 do ASP.NET MVC 4](/aspnet/whitepapers/mvc4-release-notes). Jeśli projekt jest przeznaczony dla .NET Framework 3.5 z dodatkiem SP1, należy zmienić jego platformę docelową na .NET Framework 4.|
|Modelowanie|Jeśli zezwolisz programowi Visual Studio na automatyczne aktualizowanie projektu, możesz go otworzyć w Visual Studio 2013, Visual Studio 2012 lub Visual Studio 2010 z dodatkiem SP1.<br /><br /> Przy budowaniu projektu modelowania, Team Foundation Build próbuje sprawdzić poprawność warstw w projekcie. W Visual Studio 2013 Team Foundation Build nie może sprawdzić poprawności warstw w projekcie modelowania, który został utworzony w programie Visual Studio 2010 z dodatkiem SP1. Jednak w programie Visual Studio 2010 z dodatkiem SP1 Team Foundation Build może sprawdzać poprawność warstw w projekcie modelowania, który został utworzony w Visual Studio 2013.|
|MPI/Debugowanie klastra|Jeśli ta sama wersja środowiska uruchomieniowego lub narzędzi jest zainstalowana na komputerach z systemem Visual Studio 2013, Visual Studio 2012 lub Visual Studio 2010 z dodatkiem SP1, można otworzyć projekt we wszystkich trzech wersjach.|
|Instalacja MSI (.vdproj)|Tego projektu nie można otworzyć w Visual Studio 2013, ponieważ nie obsługuje tego typu projektu. Zaleca się stosowanie rozwiązania InstallShield Limited Edition for Visual Studio (ISLE), które jest darmowym rozwiązaniem wdrożeniowym i które bezpośrednio obsługuje większość platform systemu Windows i środowisk wykonawczych aplikacji. Możesz też użyć ISLE, aby importować dane i ustawienia z projektów instalatora Visual Studio. .|
|Office 2007 VSTO|W przypadku uaktualniania projektu do pakietu Office 2013 i .NET Framework 4, możesz otworzyć ten projekt w Visual Studio 2013, Visual Studio 2012 lub Visual Studio 2010 SP1.|
|Office 2010 VSTO|Jeśli projekt jest przeznaczony dla .NET Framework 4, można go otworzyć w Visual Studio 2013, Visual Studio 2012 i Visual Studio 2010 z dodatkiem SP1. Wszystkie inne projekty wymagają jednokierunkowego uaktualnienia.|
|Bogate aplikacje internetowe|W przypadku uaktualniania projektu można go otworzyć w Visual Studio 2013, Visual Studio 2012 i Visual Studio 2010 z dodatkiem SP1.|
|SharePoint 2007|Nie można otworzyć tego projektu w Visual Studio 2013. Jeśli jednak ręcznie uaktualnisz projekt do programu SharePoint 2010, możesz go otworzyć w Visual Studio 2013, Visual Studio 2012 i Visual Studio 2010 SP1. Aby uzyskać więcej informacji na temat uaktualniania programu SharePoint 2007, zobacz [Migrowanie z programu sharepoint 2007 do programu sharepoint 2010 dla narzędzia migracji IT Pro](https://channel9.msdn.com/Blogs/matthijs/Migrating-from-SharePoint-2007-to-SharePoint-2010-for-the-IT-Pro) i [SharePoint Enterprise Search dla programu SharePoint Server 2010](/previous-versions/office/developer/sharepoint-2010/ee556856(v%3Doffice.14)).|
|SharePoint 2010|Możesz otworzyć projekt w Visual Studio 2013, Visual Studio 2012 i Visual Studio 2010 z dodatkiem SP1.|
|SketchFlow|Jeśli zezwolisz programowi Visual Studio na uaktualnienie projektu do programu WPF 4.5/Silverlight 5, możesz go otworzyć w programie Visual Studio 2012 i Visual Studio 2013.|
|[!INCLUDE[ssKatmai_exp](../includes/sskatmai-exp-md.md)] Bazy danych|Możesz otworzyć projekt w Visual Studio 2013, Visual Studio 2012 i Visual Studio 2010 z dodatkiem SP1. Jeśli masz plik bazy danych (.mdf), który został utworzony we wcześniejszej wersji programu SQL Server, należy uaktualnić go do [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)] przed użyciem w SQL Server Express LocalDB, ale baza danych nie będzie już zgodna z wcześniejszymi wersjami programu SQL Server. W przypadku braku uaktualnienia można nadal korzystać z bazy danych w Visual Studio 2013, instalując i używając [!INCLUDE[ssKatmai_exp](../includes/sskatmai-exp-md.md)] na tym samym komputerze. Aby uzyskać więcej informacji, zobacz [uaktualnianie plików MDF](../data-tools/upgrade-dot-mdf-files.md).|
|[!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] Express|Jeśli [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] Express jest zainstalowany na komputerach z systemem Visual Studio 2013, Visual Studio 2012 i Visual Studio 2010 z dodatkiem SP1, można otworzyć projekt we wszystkich trzech wersjach.|
|Projekt raportu programu SQL Server|Możesz otworzyć projekt w Visual Studio 2013 i Visual Studio 2012. Dla trybu lokalnego tylko (to znaczy, gdy nie jest podłączony do programu SQL Server), nie będzie można uzyskać środowiska czasu projektowania dla formantów, które są skojarzone z podglądem w [!INCLUDE[vs2010](../includes/vs2010-md.md)], ale projekt będzie działać poprawnie w czasie wykonywania. **Przestroga:**  Jeśli dodasz funkcję specyficzną dla Visual Studio 2013, schemat raportu zostanie automatycznie uaktualniony i nie będzie można otworzyć projektu w programie Visual Studio 2012.|
|Testy jednostkowe|Możesz użyć [!INCLUDE[TCMext](../includes/tcmext-md.md)] w Visual Studio 2013, Visual Studio 2012 i Visual Studio 2010 SP1, aby otworzyć testy, które zostały utworzone w dowolnej z tych wersji.|
|Visual C++|Aby otworzyć C++ projekt, który został utworzony w programie visual Studio 2012 lub visual Studio 2010 z dodatkiem SP1, można użyć Visual Studio 2013. Jeśli chcesz użyć środowiska kompilacji Visual Studio 2013 do skompilowania projektu, który został utworzony w programie Visual Studio 2012, musisz mieć obie wersje programu Visual Studio zainstalowane na tym samym komputerze. Aby uzyskać więcej informacji, zobacz [porady: Uaktualnianie projektów Visual C++ do Visual Studio 2015](../porting/how-to-upgrade-visual-cpp-projects-to-visual-studio-2015.md) i [przewodnik przenoszenia Visual C++ i uaktualniania](https://msdn.microsoft.com/library/f5fbcc3d-aa72-41a6-ad9a-a706af2166fb).|
|Visual Studio 2010 w sieci Web|Jeśli zezwolisz programowi Visual Studio na automatyczne aktualizowanie projektu, możesz go otworzyć w Visual Studio 2013, Visual Studio 2012 i Visual Studio 2010 z dodatkiem SP1.|
|Baza danych Visual Studio 2010 (.dbproj)|W przypadku konwersji projektu do projektu bazy danych narzędzi SQL Server Data Tools można go otworzyć w Visual Studio 2013. Jednak Visual Studio 2013 nie obsługuje tych artefaktów:<br /><br /> -testów jednostkowych<br />-plany generowania danych<br />-pliki porównywania danych<br />-niestandardowe rozszerzenia reguł dla analizy kodu statycznego<br />-server.sqlsettings<br />-pliki .sqlcmd<br />-niestandardowe rozszerzenia wdrażania<br />-projekty częściowe (.files)<br /><br /> Po zainstalowaniu narzędzi danych programu SQL Server, można otworzyć projekt w Visual Studio 2010 SP1 po konwersji. Aby uzyskać więcej informacji, zobacz [programu Microsoft SQL Server Data Tools](https://msdn.microsoft.com/data/tools.aspx).|
|Visual Studio 2010 Visual Database Tools|Możesz otworzyć ten projekt w programie Visual Studio 2013, Visual Studio 2012 i Visual Studio 2010 SP1.|
|Visual Studio Lab Management|Możesz użyć [!INCLUDE[TCMext](../includes/tcmext-md.md)], Visual Studio 2013, Visual Studio 2012 i Visual Studio 2010 SP1, aby otworzyć środowiska, które zostały utworzone w dowolnej z tych wersji. Jednak używana wersja Microsoft Test Manager musi odpowiadać używanej wersji Team Foundation Server, aby można było utworzyć środowiska.|
|Makro programu Visual Studio|Nie można otworzyć tego projektu w Visual Studio 2013, ponieważ nie obsługuje on typu projektu.|
|Visual Studio SDK/VSIX|Po uaktualnieniu projektu Visual Studio SDK do Visual Studio 2013 nie można go otworzyć w programie Visual Studio 2012. Aby uzyskać więcej informacji, zobacz [instrukcje: Migrowanie projektów rozszerzalności programu Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md).|
|Microsoft Azure Tools dla programu Visual Studio|Jeśli używasz narzędzi Microsoft Azure Tools for Visual Studio w wersji 2,1, możesz otworzyć projekt w Visual Studio 2013, Visual Studio 2012 i Visual Studio 2010 SP1. W przypadku projektów przeznaczonych dla wcześniejszych wersji, Jeśli zezwolisz programowi Visual Studio na uaktualnienie projektu do wersji 2,1, możesz otworzyć go w Visual Studio 2013, Visual Studio 2012 i Visual Studio 2010 SP1.|
|Windows Communication Foundation, Windows Presentation Foundation|Możesz otworzyć ten projekt w programie Visual Studio 2013, Visual Studio 2012 i Visual Studio 2010 SP1.|
|Windows Mobile|Nie można otworzyć tego projektu w Visual Studio 2013, ponieważ nie obsługuje on typu projektu.|
|Windows Phone 7.1|Jeśli zezwolisz programowi Visual Studio na uaktualnienie projektu do Windows Phone 8,0, możesz otworzyć go w programie Visual Studio 2012 i Visual Studio 2013.|
|Inne|Większość innych typów projektów można otworzyć w programie Visual Studio 2012, Visual Studio 2013 i Visual Studio 2010 z dodatkiem SP1.|
|Witryny sieci Web programu FrontPage|Nie można otworzyć tego projektu w Visual Studio 2013, ponieważ nie obsługuje on typu projektu.|
|Biblioteka klas przenośnych|Jeśli zezwolisz programowi Visual Studio na automatyczne aktualizowanie projektu, możesz go otworzyć w Visual Studio 2013, Visual Studio 2012 lub Visual Studio 2010 z dodatkiem SP1.<br /><br /> -Projekty ukierunkowane na Silverlight 4 będą ukierunkowane na Silverlight 5.<br />-Projekty ukierunkowane na Windows Phone 7.0 lub Windows Phone 7.5 będą ukierunkowane na Windows Phone 8.<br />-Projekty ukierunkowane na konsolę Xbox 360 nie będą już ukierunkowane konsoli Xbox 360.|
|Projekty platformy Azure, takich jak chmury usługi (z rozszerzeniem ccproj) i projektów usługi Azure Resource Manager (projektów wdrożeń w chmurze) z rozszerzeniem .deployproj|Aby otworzyć tych typów projektów, należy najpierw zainstalować [zestawu Azure SDK dla platformy .NET](https://azure.microsoft.com/downloads/), następnie otworzyć projekt.|

## <a name="troubleshooting-project-compatibility-issues"></a>Rozwiązywanie problemów ze zgodnością projektów
 Oto kilka rzeczy, które można wykonać, gdy projekt nie zostanie otwarty w programie Visual Studio 2015 lub Visual Studio 2013:

- Jeśli spróbujesz otworzyć projekt, który nie jest obsługiwany w programie Visual Studio 2015 lub Visual Studio 2013 i dla którego nie zainstalowano skojarzonej wersji programu Visual Studio, komunikat, że typ projektu nie jest obsługiwany, może być wyświetlany, a typ projektu może być wyświetlany w oknie dialogowym **Przegląd zmian projektu i rozwiązania** w obszarze **nieobsługiwane projekty**. Aby rozwiązać ten problem, otwórz stronę Programy i funkcje w Windows **Panelu sterowania**, wybierz opcję **programu Visual Studio**, a następnie wybierz **zmiany**, **naprawy** . Następnie możesz zainstalować brakującą wersję.

- Jeśli spróbujesz otworzyć projekt aplikacji klasycznej w [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)], wystąpi błąd i wyświetlony zostanie jeden z następujących komunikatów: "Ta wersja programu Visual Studio obsługuje tylko [!INCLUDE[win81](../includes/win81-md.md)] aplikacje" albo "ten projekt jest niezgodny z bieżącą wersją programu Visual Studio". [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] jest ograniczony do tworzenia, testowania i wdrażania programu Windows Store zaprojektowanych dla Windows 8.1. Aby otworzyć projekt aplikacji klasycznej, musisz korzystać z wersji programu Visual Studio obsługującej taki typ projektu.

   Aby uzyskać więcej informacji na temat wersji programu Visual Studio, zobacz [produkty Microsoft Visual Studio](https://visualstudio.microsoft.com/products/)

- Jeśli spróbujesz otworzyć projekt aplikacji Windows Store App w [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] pulpitu, wystąpienie błędu. [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] Desktop nie można tworzyć aplikacje Windows Store. Jeśli chcesz tworzyć aplikacje Windows Store, możesz także zainstalować [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)]. Lub, aby rozwijać aplikacje dla wszystkich platform firmy Microsoft i sieci Web, wypróbuj Visual Studio Professional 2013.

- Jeśli projekt wymaga funkcji, które są specyficzne dla Visual Studio 2013, nie można go otworzyć w starszej wersji.

- Jeśli używasz programu Visual Studio 2012 i chcesz otworzyć projekt, który został utworzony w Visual Studio 2013, możesz mieć możliwość dostosowania systemu projektu w celu uwzględnienia funkcji Visual Studio 2013. Aby dowiedzieć się, jak to zrobić, zobacz [wprowadzanie niestandardowych projektów rozpoznający wersje](../misc/making-custom-projects-version-aware.md).

  Aby uzyskać dodatkowe informacje dotyczące rozwiązywania problemów, zobacz [zgodność programu Visual Studio 2013](https://support.microsoft.com/help/2863286/roundtrip-issues-for-visual-studio-2012-and-visual-studio-2013-preview) artykuł bazy wiedzy.

## <a name="file"></a> Pliki

Poniższa lista wskazuje, czy Visual Studio 2013 obsługuje każdy typ pliku, czy można otworzyć plik w programie Visual Studio 2012 i programie Visual Studio 2010 z dodatkiem SP1 oraz czy należy zmodyfikować go w celu zapewnienia zgodności.

|Typ pliku|Zgodność|
|------------------|-------------------|
|AppManifest, Inbrowsersettings, OutOfBrowserSettings (pliki .xml)|Pliki te można otworzyć w programie Visual Studio 2012, Visual Studio 2013 i Visual Studio 2010 z dodatkiem SP1.|
|Płaskie schematy plików BizTalk|Te schematy można dodać do projektu BizTalk 2013 w Visual Studio 2013. Aby użyć Visual Studio 2013 z projektami BizTalk 2010, które mają płaskie schematy plików, zainstaluj program BizTalk 2013 na komputerze z Visual Studio 2013. Przy pierwszym otwarciu projektu BizTalk 2010 jest on automatycznie uaktualniany do systemu BizTalk 2013 lub Visual Studio 2013 projektu.|
|Pliki definicji raportu (.rdlc) klienta|Pliki te można otworzyć w Visual Studio 2013, a schemat jest automatycznie uaktualniany po dodaniu Visual Studio 2013 funkcji i kontrolek.|
|Zestawy reguł analizy kodu|Pliki te można otworzyć w programie Visual Studio 2012, Visual Studio 2013 i Visual Studio 2010 z dodatkiem SP1.|
|Pliki pakietu aplikacji warstwy danych|Pliki te można otworzyć w Visual Studio 2013, jeśli są w wersji 2,0 lub 2,5.|
|Pliki zrzutu debugera|Pliki te można otworzyć w programie Visual Studio 2012, Visual Studio 2013 i Visual Studio 2010 z dodatkiem SP1.|
|Pliki diagramu Directed Graph Markup Language (DGML)|Pliki te można otworzyć w programie Visual Studio 2012, Visual Studio 2013 i Visual Studio 2010 SP1 bez konieczności zmiany pliku.|
|Pliki Entity Data Model (EDMX)|W Visual Studio 2013 można otworzyć plik EDMX, który jest przeznaczony dla .NET Framework 4,5 lub .NET Framework 4 bez zmiany pliku.|
|Pliki raportów programu Profiler|Pliki raportów profilera (. vsp. vsps,. psess i. vspf) można otworzyć w programie Visual Studio 2012 i Visual Studio 2013. Nie można otworzyć pliku .vspx w Visual Studio 2010 SP1.|
|Plik rozwiązania (.suo)|Aby otworzyć plik rozwiązania, który został utworzony w programie Visual Studio 2012 lub Visual Studio 2010 z dodatkiem SP1, można użyć Visual Studio 2013.|
|SQL Server Compact Edition|Visual Studio 2013 nie obsługuje wersji SQL Server Compact.|
|Pliki SQLX|Aby otworzyć te pliki w Visual Studio 2013, należy wykonać jednokierunkową aktualizację, wdrożyć plik. sqlx w docelowej wersji programu Visual Studio, a następnie ponownie skompilować plik w formacie. dacpac.|
|Pliki dziennika IntelliTrace z [!INCLUDE[vs2010](../includes/vs2010-md.md)]|Pliki te można otworzyć w programie Visual Studio 2012, Visual Studio 2013 i Visual Studio 2010 z dodatkiem SP1.|
|Pliki analizatora pamięci JavaScript (.diagsession)|Pliki utworzone przez starsze wersje programu Visual Studio mogą być wyświetlane w Visual Studio 2013. Jednak w zależności od zebranych informacji pliki utworzone w Visual Studio 2013 mogą nie być otwierane w programie Visual Studio 2012 lub Visual Studio 2010 z dodatkiem SP1.|

## <a name="integration"></a> Zasoby integracji

Jeśli używasz klientów i serwerów z różnych wersji Visual Studio Team Foundation Server, mogą wystąpić problemy ze zgodnością.

|Rodzaj integracji|Zgodność|
|-------------------------|-------------------|
|Audyt kodu i Moja praca|Funkcji Przegląd kodu i Moja praca nie będzie działać, jeśli łączysz klienta [!INCLUDE[esprfound](../includes/esprfound-md.md)] do [!INCLUDE[vstsTfsRosarioLong](../includes/vststfsrosariolong-md.md)].|
|[!INCLUDE[vs_dev11_expwin_long](../includes/vs-dev11-expwin-long-md.md)]|64-bitowego środowiska, takiego Jakmsbuild lub [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] nie może służyć do tworzenia [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacje, które są tworzone w [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)].|

## <a name="see-also"></a>Zobacz także

- [Tworzenie niestandardowych projektów rozpoznający wersje](../misc/making-custom-projects-version-aware.md)
