---
title: Architektura dostosowywania na poziomie dokumentu
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VSTOLoader.dll
- formats [Office development in Visual Studio]
- file formats [Office development in Visual Studio]
- vstoee.dll
- managed code extensions [Office development in Visual Studio], definition
- document-level customizations [Office development in Visual Studio]
- AddInLoader.dll
- architecture [Office development in Visual Studio], document-level customizations
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4e07c8ae29c773a1f50fedd68376a062e2203570
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248273"
---
# <a name="architecture-of-document-level-customizations"></a>Architektura dostosowywania na poziomie dokumentu
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] zawiera projekty do tworzenia dostosowań poziomie dokumentu dla programu Microsoft Office Word i Microsoft Office Excel. W tym temacie opisano następujące aspekty dostosowań poziomu dokumentu:  
  
- [Omówienie dostosowywania](#UnderstandingCustomizations)  
  
- [Składniki dostosowania](#Components)  
  
- [Jak działają dostosowania przy użyciu aplikacji Microsoft Office](#HowCustomizationsWork)  
  
  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
  Aby uzyskać ogólne informacje dotyczące tworzenia dostosowań poziomie dokumentu, zobacz [rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md), [wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Word](../vsto/getting-started-programming-document-level-customizations-for-word.md), i [wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md).  
  
##  <a name="UnderstandingCustomizations"></a> Omówienie dostosowywania  
 Korzystając z narzędzia Office developer tools w programie Visual Studio do tworzenia dostosowań poziomie dokumentu, możesz utworzyć zestawu kodu zarządzanego, który jest skojarzony z określonym dokumentem. Dokument lub skoroszyt z połączonego zestawu jest nazywany ma rozszerzenia kodu zarządzanego. Aby uzyskać więcej informacji, zobacz [projektowania i tworzenia rozwiązań dla pakietu Office](../vsto/designing-and-creating-office-solutions.md).  
  
 Gdy użytkownik otwiera dokument, zestaw jest ładowany przez aplikację Microsoft Office. Po załadowaniu zestawu dostosowań mogą reagować na zdarzenia, gdy dokument jest otwarty. Dostosowania można również wywołać modelu obiektów automatyzacji i rozszerzania aplikacji, gdy dokument jest otwarty i może używać dowolnej klasy w [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].  
  
 Zestaw komunikuje się ze składnikami modelu COM. aplikacji za pomocą podstawowego zestawu międzyoperacyjnego aplikacji. Aby uzyskać więcej informacji, zobacz [podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md) i [rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 Jeśli użytkownik otworzy wielu dostosowań na poziomie dokumentu, w tym samym czasie, każdy zestaw jest ładowany w domenie innej aplikacji. Oznacza to, że jedno rozwiązanie, który zachowuje się nieprawidłowo nie może powodować inne rozwiązania, aby zakończyć się niepowodzeniem. Dostosowania na poziomie dokumentu są przeznaczone do pracy z pojedynczego dokumentu w domenie pojedynczej aplikacji. Nie są przeznaczone do komunikacji dla wielu dokumentów. Aby uzyskać więcej informacji o domenach aplikacji, zobacz [domen aplikacji](/dotnet/framework/app-domains/application-domains).  
  
> [!NOTE]  
>  Dostosowania na poziomie dokumentu, które tworzysz przy użyciu narzędzi Office developer tools w programie Visual Studio są przeznaczone do użycia tylko wtedy, gdy aplikacja jest uruchamiana przez użytkownika końcowego. Jeśli aplikacja jest uruchamiana programowo, na przykład za pomocą automatyzacji, dostosowań mogą nie działać zgodnie z oczekiwaniami.  
  
### <a name="design-time-and-run-time-experiences"></a>Środowiska w czasie projektowania i w czasie wykonywania  
 Aby zrozumieć, Architektura dostosowywania na poziomie dokumentu, pomaga to zrozumieć środowiska projektowania rozwiązania i uruchamianie rozwiązania.  
  
#### <a name="design-time"></a>Czas projektowania  
 Środowisko czasu projektowania obejmuje następujące kroki:  
  
1.  Deweloper tworzy projekt poziomu dokumentu w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Projekt zawiera dokument i zestawu, który uruchamia się w dokumencie. Dokument może już istnieć (utworzone przez projektanta) lub można utworzyć nowy dokument wraz z projektu.  
  
2.  Projektant — albo Deweloper, który tworzy projekt, czy ktoś — tworzy końcowy wygląd i działanie dokumentu dla użytkownika końcowego.  
  
#### <a name="runtime"></a>Środowisko uruchomieniowe  
 Środowisko wykonawcze — obejmuje następujące kroki:  
  
1.  Użytkownik końcowy otworzy dokument lub skoroszyt, który zawiera rozszerzenia kodu zarządzanego.  
  
2.  Dokument lub skoroszyt ładuje skompilowanym zestawie.  
  
3.  Zestaw reaguje na zdarzenia, ponieważ użytkownik pracuje w dokumencie lub skoroszycie.  
  
#### <a name="developer-and-end-user-perspective-compared"></a>Perspektywa programistów i użytkowników końcowych w porównaniu  
 Ponieważ Deweloper pracuje się głównie w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]i użytkownika końcowego działa w programie Word lub Excel, istnieją dwa sposoby zrozumienia dostosowań na poziomie dokumentu.  
  
|Perspektywy dewelopera|Perspektywy użytkownika końcowego|  
|-----------------------------|----------------------------|  
|Za pomocą [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], deweloper pisze kod, który jest dostępny dla programów Word i Excel.<br /><br /> Chociaż może się wydawać, że deweloper tworzy plik wykonywalny, który jest uruchamiany program Word lub Excel, proces faktycznie działa odwrotnie. Dokument jest skojarzony z zestawem i zawiera wskaźnik do tego zestawu. Po otwarciu dokumentu programu Word lub Excel lokalizuje zestaw i uruchamia kod w odpowiedzi na wszystkie obsługiwane zdarzenia.|Użytkownikom korzystającym z rozwiązania po prostu otworzyć dokument lub skoroszyt (lub Utwórz nowy dokument z szablonu) tak samo jak każdy inny plik programu Microsoft Office one się otwierają.<br /><br /> Zestaw zawiera dostosowania w dokumencie lub skoroszycie, takie jak automatyczne wypełnianie z bieżącymi danymi lub przedstawiający okno dialogowe, aby zażądać informacji.|  
  
### <a name="supported-document-formats-for-document-level-customizations"></a>Obsługiwane formaty dokumentów w przypadku dostosowań na poziomie dokumentu  
 Kiedy tworzysz projekt dostosowania, można wybrać format dokumentu, który chcesz użyć w projekcie. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 W poniższej tabeli wymieniono formaty dokumentów, których można używać w dostosowań na poziomie dokumentu dla programów Excel i Word.  
  
|Excel|Word|  
|-----------|----------|  
|Skoroszyt programu Excel (*xlsx*)<br /><br /> Skoroszyt programu Excel z włączoną obsługą makr (*.xlsm*)<br /><br /> Skoroszyt binarny programu Excel (*xlsb*)<br /><br /> Skoroszyt programu Excel 97 – 2003 (*xls*)<br /><br /> Szablon programu Excel (*xltx*)<br /><br /> Szablon programu Excel z włączoną obsługą makr (*xltm*)<br /><br /> Szablon programu Excel 97 – 2003 (*xlt*)|Dokument programu Word (*.docx*)<br /><br /> Dokument programu Word z obsługą makr (*docm*)<br /><br /> Dokument programu Word 97 – 2003 (*doc*)<br /><br /> Szablon programu Word (*dotx*)<br /><br /> Szablon programu Word z obsługą makr (*dotm*)<br /><br /> Szablon programu Word 97 – 2003 (*.dot*)|  
  
 Należy projektować rozszerzenia kodu zarządzanego tylko dla dokumentów w obsługiwanych formatów. W przeciwnym razie określonych zdarzeń nie może zostać wywołane, gdy dokument zostanie otwarty w aplikacji. Na przykład <xref:Microsoft.Office.Tools.Excel.Workbook.Open> zdarzeń nie jest inicjowane, gdy używasz rozszerzenia kodu zarządzanego ze skoroszytami zapisany w formacie arkusza kalkulacyjnego programu Excel, XML lub strony sieci web (*.htm*; *.html*) format.  
  
### <a name="support-for-word-documents-that-have-xml-file-name-extensions"></a>Obsługa dokumentów programu Word, które mają rozszerzenia nazwy pliku .xml  
 Szablony projektów dokumentów nie pozwalają na tworzenie projektów, w oparciu o następujące formaty plików:  
  
- Dokument XML programu Word (*\*xml*).  
  
- Dokument XML programu Word 2003 (*\*xml*).  
  
  Chcąc użytkownikom końcowym, użyj opcji dostosowania w tych formatach plików, tworzenie i wdrażanie dostosowania, które korzysta z jednego z obsługiwanych formatów plików określone w powyższej tabeli. Po zainstalowaniu dostosowania, użytkownicy końcowi można zapisać dokument w dokumencie programu Word XML (*\*xml*) format lub dokument programu Word 2003 XML (*\*xml*) format, a Dostosowywanie będą w dalszym ciągu działać zgodnie z oczekiwaniami.  
  
##  <a name="Components"></a> Składniki dostosowania  
 Główne składniki dostosowania są dokumentu i zestawu. Oprócz tych składników istnieje kilka elementów, które odgrywa ważną rolę w sposób aplikacje Microsoft Office wykrycie i załadowanie dostosowań.  
  
### <a name="deployment-manifest-and-application-manifest"></a>Manifesty wdrożenia i manifest aplikacji  
 Dostosowania Użyj manifesty aplikacji i manifestów wdrożenia do identyfikowania i załadować najbardziej aktualną wersję zestawu dostosowywania. Wskazuje bieżący manifest aplikacji manifest wdrożenia. Aplikacja manifestu wskazuje zestaw dostosowania i Określa wpis punktu klasy (lub klasy) do wykonywania w zestawie. Aby uzyskać więcej informacji, zobacz [stosowania i wdrażania manifestów w rozwiązaniach pakietu Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
### <a name="visual-studio-tools-for-office-runtime"></a>Program Visual Studio Tools for Office Runtime  
 Aby uruchomić dostosowań na poziomie dokumentu, które są tworzone przy użyciu narzędzi Office developer tools w programie Visual Studio, musi mieć komputerach użytkowników końcowych [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] zainstalowane. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Obejmuje składniki niezarządzane, które załadować zestaw dostosowania, a także zbiór zestawów zarządzanych. Te zestawy zarządzane zapewniają model obiektu, którego kod dostosowywania używa do automatyzacji i rozszerzania aplikacji hosta.  
  
 Aby uzyskać więcej informacji, zobacz [Visual Studio tools dla pakietu Office runtime ― omówienie](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
##  <a name="HowCustomizationsWork"></a> Jak działają dostosowania przy użyciu aplikacji Microsoft Office  
 Gdy użytkownik otwiera dokument, który jest częścią dostosowywania programu Microsoft Office, aplikacja korzysta z pliku manifestu wdrożenia, połączonego z dokumentu do lokalizowania i ładowania najbardziej aktualną wersję zestawu dostosowywania. Lokalizacja manifestu wdrażania jest przechowywana w niestandardową właściwość dokumentu o nazwie **AssemblyLocation**. Ciąg, który identyfikuje tej lokalizacji są wstawiane do właściwości, podczas kompilowania rozwiązania.  
  
 Wskazuje manifestu wdrożenia do manifestu aplikacji, które następnie wskazuje do najbardziej bieżącego zestawu. Aby uzyskać więcej informacji, zobacz [stosowania i wdrażania manifestów w rozwiązaniach pakietu Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
 Na poniższej ilustracji przedstawiono architekturę podstawowe dostosowanie poziomu dokumentu.  
  
 ![Architektura dostosowywania pakietu office 2007](../vsto/media/office07-custom.png "Architektura dostosowywania pakietu Office 2007")  
  
> [!NOTE]  
>  W rozwiązaniach pakietu Office, których platformą docelową [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], rozwiązania mogą wywoływać model obiektów aplikacji hosta, za pomocą podstawowego zestawu międzyoperacyjnego (PIA) informacje o typie osadzony w zestawie rozwiązania, zamiast wywoływać metodę do PIA bezpośrednio. Aby uzyskać więcej informacji, zobacz [projektowania i tworzenia rozwiązań dla pakietu Office](../vsto/designing-and-creating-office-solutions.md).  
  
### <a name="loading-process"></a>Proces ładowania  
 Gdy użytkownik otwiera dokument, który jest częścią rozwiązania Microsoft Office, wykonywane są następujące kroki.  
  
1.  Aplikacja Microsoft Office sprawdza właściwości niestandardowego dokumentu, aby sprawdzić, czy rozszerzenia kodu zarządzanego, powiązany z dokumentem. Aby uzyskać więcej informacji, zobacz [właściwości niestandardowego dokumentu ― omówienie](../vsto/custom-document-properties-overview.md).  
  
2.  W przypadku rozszerzenia kodu zarządzanego, ładowania aplikacji *VSTOEE.dll*, których ładunki *VSTOLoader.dll*. Są to niezarządzanych bibliotek DLL, które są składnikami programu ładującego dla Visual Studio 2010 Tools dla pakietu Office runtime. Aby uzyskać więcej informacji, zobacz [Visual Studio Tools dla pakietu Office runtime ― omówienie](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
3.  *VSTOLoader.dll* ładuje [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] i uruchomienie zarządzanego część [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
4.  Jeśli dokument zostanie otwarty z lokalizacji innych niż komputer lokalny, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sprawdza, czy lokalizacja dokumentu w **zaufane lokalizacje** listy w **ustawienia Centrum zaufania** dla działania konkretnej aplikacji pakietu Office. Jeśli lokalizację dokumentu nie jest w zaufanej lokalizacji, dostosowanie nie jest zaufany, a proces ładowania zatrzymuje się na nim.  
  
5.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Instaluje rozwiązanie, jeśli nie został jeszcze zainstalowany, pobiera najbardziej aktualną manifestów aplikacji i wdrożenia i wykonuje szereg kontroli zabezpieczeń. Aby uzyskać więcej informacji, zobacz [rozwiązań Secure Office](../vsto/securing-office-solutions.md).  
  
6.  W przypadku dostosowania zaufane do uruchamiania, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] używa manifest wdrożenia i manifest aplikacji, aby sprawdzać dostępność aktualizacji zestawu. Jeśli dostępna jest nowa wersja zestawu, środowisko uruchomieniowe pobiera nową wersję zestawu do [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] pamięci podręcznej na komputerze klienckim. Aby uzyskać więcej informacji, zobacz [wdrożyć rozwiązanie Office](../vsto/deploying-an-office-solution.md).  
  
7.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Tworzy nową domenę aplikacji, w którym można załadować zestawu dostosowywania.  
  
8.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Ładuje zestaw dostosowania do domeny aplikacji.  
  
9. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Wywołania **uruchamiania** programu obsługi zdarzeń w swoim zestawie dostosowywania. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md)  
  
## <a name="see-also"></a>Zobacz także  
 [Architektura rozwiązań pakietu Office w programie Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Visual Studio Tools dla pakietu Office runtime ― omówienie](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)   
 [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)   
 [Przegląd właściwości niestandardowego dokumentu](../vsto/custom-document-properties-overview.md)   
 [Dane w pamięci podręcznej dostosowywane na poziomie dokumentu](../vsto/cached-data-in-document-level-customizations.md)  
  
  