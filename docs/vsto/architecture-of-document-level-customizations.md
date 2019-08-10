---
title: Architektura dostosowań na poziomie dokumentu
ms.date: 02/02/2017
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f5028f5a9b16ecfc2461c0d29cbedb44be70a64c
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926559"
---
# <a name="architecture-of-document-level-customizations"></a>Architektura dostosowań na poziomie dokumentu
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]obejmuje projekty służące do tworzenia dostosowań na poziomie dokumentu dla programów Microsoft Office Word i Microsoft Office Excel. W tym temacie opisano następujące aspekty dostosowywania na poziomie dokumentu:

- [Omówienie dostosowań](#UnderstandingCustomizations)

- [Składniki dostosowań](#Components)

- [Jak dostosowania współpracują z aplikacjami Microsoft Office](#HowCustomizationsWork)

  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

  Aby uzyskać ogólne informacje na temat tworzenia dostosowań na poziomie dokumentu, zobacz temat programowanie [rozwiązań pakietu Office — omówienie &#40;&#41;](../vsto/office-solutions-development-overview-vsto.md), [wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)i rozpoczynanie [pracy Programowanie dostosowań na poziomie dokumentu dla programu Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md).

## <a name="UnderstandingCustomizations"></a>Omówienie dostosowań
 Korzystając z narzędzi deweloperskich pakietu Office w programie Visual Studio, można utworzyć zestaw kodu zarządzanego skojarzony z określonym dokumentem. Dokument lub skoroszyt z połączonym zestawem jest nazywany rozszerzeniami kodu zarządzanego. Aby uzyskać więcej informacji, zobacz [projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md).

 Gdy użytkownik otworzy dokument, zestaw jest ładowany przez aplikację Microsoft Office. Po załadowaniu zestawu dostosowanie może reagować na zdarzenia, gdy dokument jest otwarty. Dostosowanie może również wywołać model obiektów w celu zautomatyzowania i rozbudowania aplikacji, gdy dokument jest otwarty i może korzystać z dowolnej klasy w [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].

 Zestaw komunikuje się ze składnikami COM aplikacji za pomocą podstawowego zestawu międzyoperacyjnego aplikacji. Aby uzyskać więcej informacji, zobacz [zestawy podstawowych międzyoperacyjnych pakietu Office](../vsto/office-primary-interop-assemblies.md) i [programowanie&#41;rozwiązań pakietu Office — omówienie &#40;](../vsto/office-solutions-development-overview-vsto.md).

 Jeśli użytkownik otworzy jednocześnie wiele dostosowań na poziomie dokumentu, każdy zestaw jest ładowany w innej domenie aplikacji. Oznacza to, że jedno rozwiązanie, które zachowuje się nieprawidłowo nie może spowodować niepowodzenia innych rozwiązań. Dostosowania na poziomie dokumentu są przeznaczone do pracy z pojedynczym dokumentem w jednej domenie aplikacji. Nie są one przeznaczone do komunikacji między dokumentami. Aby uzyskać więcej informacji na temat domen aplikacji, zobacz [domeny aplikacji](/dotnet/framework/app-domains/application-domains).

> [!NOTE]
> Dostosowania na poziomie dokumentu tworzone przy użyciu narzędzi Office Developer Tools w programie Visual Studio są przeznaczone do użycia tylko wtedy, gdy aplikacja jest uruchamiana przez użytkownika końcowego. Jeśli aplikacja jest uruchamiana programowo, na przykład przy użyciu automatyzacji, dostosowanie może nie zadziałać zgodnie z oczekiwaniami.

### <a name="design-time-and-run-time-experiences"></a>Środowiska czasu projektowania i czasu wykonywania
 Aby poznać architekturę dostosowań na poziomie dokumentu, można zrozumieć środowiska projektowania rozwiązań i uruchamiania rozwiązania.

#### <a name="design-time"></a>Czas projektowania
 Środowisko czasu projektowania obejmuje następujące kroki:

1. Deweloper tworzy projekt na poziomie dokumentu w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Projekt zawiera dokument i zestaw, który działa za dokumentem. Dokument może już istnieć (utworzony przez projektanta) lub można utworzyć nowy dokument wraz z projektem.

2. Projektant — Deweloper, który tworzy projekt lub kogoś innego — tworzy końcowy wygląd i sposób działania dokumentu dla użytkownika końcowego.

#### <a name="runtime"></a>Środowisko uruchomieniowe
 Środowisko uruchomieniowe obejmuje następujące kroki:

1. Użytkownik końcowy otwiera dokument lub skoroszyt, który ma rozszerzenia kodu zarządzanego.

2. Dokument lub skoroszyt ładuje skompilowany zestaw.

3. Zestaw reaguje na zdarzenia, ponieważ użytkownik pracuje w dokumencie lub skoroszycie.

#### <a name="developer-and-end-user-perspective-compared"></a>Porównanie perspektyw dla deweloperów i użytkowników końcowych
 Ponieważ deweloper działa głównie w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]programie, a użytkownik końcowy działa w programie Word lub Excel, istnieją dwa sposoby interpretacji dostosowań na poziomie dokumentu.

|Perspektywa dewelopera|Perspektywa użytkownika końcowego|
|-----------------------------|----------------------------|
|Korzystając [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]z programu, deweloperzy zapisują kod, który jest dostępny dla programów Word i Excel.<br /><br /> Chociaż może wydawać się, że deweloper tworzy plik wykonywalny z uruchomionym programem Word lub Excel, proces rzeczywiście działa w inny sposób. Dokument jest skojarzony z zestawem i zawiera wskaźnik do tego zestawu. Gdy dokument zostanie otwarty, program Word lub Excel lokalizuje zestaw i uruchamia kod w odpowiedzi na wszystkie obsłużone zdarzenia.|Osoby korzystające z rozwiązania po prostu otwierają dokument lub skoroszyt (lub tworzą nowy dokument z szablonu) tak samo jak w przypadku otwierania dowolnego innego pliku Microsoft Office.<br /><br /> Zestaw zawiera dostosowania w dokumencie lub skoroszycie, takie jak automatyczne wypełnianie go bieżącymi danymi lub wyświetlanie okna dialogowego, w którym można zażądać informacji.|

### <a name="supported-document-formats-for-document-level-customizations"></a>Obsługiwane formaty dokumentów dla dostosowań na poziomie dokumentu
 Podczas tworzenia projektu dostosowania można wybrać format dokumentu, który ma być używany w projekcie. Aby uzyskać więcej informacji, zobacz [jak: Utwórz projekty pakietu Office w programie](../vsto/how-to-create-office-projects-in-visual-studio.md)Visual Studio.

 Poniższa tabela zawiera listę formatów dokumentów, których można użyć w przypadku dostosowań na poziomie dokumentu dla programów Excel i Word.

|Excel|Word|
|-----------|----------|
|Skoroszyt programu Excel (*xlsx*)<br /><br /> Skoroszyt z obsługą makr programu Excel (*xlsm*)<br /><br /> Skoroszyt binarny programu Excel (*XLSB*)<br /><br /> Skoroszyt programu Excel 97-2003 (*xls*)<br /><br /> Szablon programu Excel ( *. XLTX*)<br /><br /> Szablon programu Excel z obsługą makr ( *. xltm*)<br /><br /> Szablon programu Excel 97-2003 ( *. xlt*)|Dokument programu Word (*docx*)<br /><br /> Dokument programu Word z obsługą makr ( *. docm*)<br /><br /> Dokument programu Word 97-2003 (*doc*)<br /><br /> Szablon programu Word ( *. dotx*)<br /><br /> Szablon z obsługą makr programu Word ( *. dotm*)<br /><br /> Szablon programu Word 97-2003 ( *. dot*)|

 Rozszerzenia kodu zarządzanego należy projektować tylko dla dokumentów w obsługiwanych formatach. W przeciwnym razie niektóre zdarzenia mogą nie zostać zgłoszone, gdy dokument zostanie otwarty w aplikacji. Na przykład <xref:Microsoft.Office.Tools.Excel.Workbook.Open> zdarzenie nie jest zgłaszane w przypadku używania rozszerzeń kodu zarządzanego ze skoroszytami zapisanymi w formacie arkusza kalkulacyjnego XML programu Excel lub na stronie sieci Web ( *. htm*; *. html*) Formatowanie.

### <a name="support-for-word-documents-that-have-xml-file-name-extensions"></a>Obsługa dokumentów programu Word z rozszerzeniami nazw plików XML
 Szablony projektów na poziomie dokumentu nie umożliwiają tworzenia projektów opartych na następujących formatach plików:

- Dokument XML programu Word ( *\*XML*).

- Dokument XML programu Word 2003 ( *\*XML*).

  Jeśli chcesz, aby użytkownicy końcowi korzystali z dostosowań w tych formatach plików, skompiluj i Wdróż dostosowanie, które używa jednego z obsługiwanych formatów plików określonych w powyższej tabeli. Po zainstalowaniu dostosowania użytkownicy końcowi mogą zapisać dokument w formacie Word XML Document ( *\*XML*) lub Word 2003 XML Document Format ( *\*XML*), a dostosowanie będzie nadal działało zgodnie z oczekiwaniami.

## <a name="Components"></a>Składniki dostosowań
 Głównymi składnikami dostosowania są dokumenty i zestawy. Oprócz tych składników istnieje kilka innych części, które odgrywają ważną rolę w sposobie odnajdywania i pobierania przez aplikacje Microsoft Office aplikacji.

### <a name="deployment-manifest-and-application-manifest"></a>Manifest wdrożenia i manifest aplikacji
 Dostosowania używają manifestów wdrożenia i manifestów aplikacji do identyfikowania i ładowania najnowszej wersji zestawu do dostosowania. Manifest wdrożenia wskazuje bieżący manifest aplikacji. Manifest aplikacji wskazuje zestaw dostosowania i określa klasę punktu wejścia (lub klasy) do wykonania w zestawie. Aby uzyskać więcej informacji, zobacz [manifesty aplikacji i wdrożenia w rozwiązaniach pakietu Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).

### <a name="visual-studio-tools-for-office-runtime"></a>Visual Studio Tools dla środowiska uruchomieniowego pakietu Office
 Aby uruchomić dostosowania na poziomie dokumentu, które są tworzone przy użyciu narzędzi deweloperskich pakietu Office w programie Visual Studio, na [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] komputerach użytkowników końcowych musi być zainstalowany program. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Obejmuje składniki niezarządzane, które ładują zestaw dostosowań, a także zestaw zestawów zarządzanych. Te zarządzane zestawy udostępniają model obiektów, który jest używany przez kod dostosowania do automatyzowania i zwiększania poziomu aplikacji hosta.

 Aby uzyskać więcej informacji, zobacz [Omówienie programu Visual Studio Tools for Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="HowCustomizationsWork"></a>Jak dostosowania współpracują z aplikacjami Microsoft Office
 Gdy użytkownik otwiera dokument, który jest częścią dostosowania Microsoft Office, aplikacja używa manifestu wdrożenia, który jest połączony z dokumentem w celu zlokalizowania i załadowania najnowszej wersji zestawu dostosowywania. Lokalizacja manifestu wdrożenia jest przechowywana w niestandardowej właściwości dokumentu o nazwie **AssemblyLocation**. Ciąg identyfikujący tę lokalizację jest wstawiany do właściwości podczas kompilowania rozwiązania.

 Manifest wdrożenia wskazuje manifest aplikacji, który następnie wskazuje na najnowszy zestaw. Aby uzyskać więcej informacji, zobacz [manifesty aplikacji i wdrożenia w rozwiązaniach pakietu Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).

 Na poniższej ilustracji przedstawiono podstawową architekturę dostosowywania na poziomie dokumentu.

 ![Architektura dostosowywania pakietu Office 2007](../vsto/media/office07-custom.png "Architektura dostosowywania pakietu Office 2007")

> [!NOTE]
> W rozwiązaniach pakietu Office, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]które są przeznaczone dla rozwiązań, wywołania do modelu obiektów aplikacji hosta za pomocą informacji o typie podstawowego zestawu międzyoperacyjnego (PIA), które są osadzone w zestawie rozwiązania, zamiast bezpośredniego wywoływania Pia. Aby uzyskać więcej informacji, zobacz [projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md).

### <a name="loading-process"></a>Proces ładowania
 Poniższe kroki są wykonywane, gdy użytkownik otworzy dokument, który jest częścią rozwiązania Microsoft Officeowego.

1. Aplikacja Microsoft Office sprawdza właściwości dokumentu niestandardowego, aby sprawdzić, czy istnieją rozszerzenia kodu zarządzanego skojarzone z dokumentem. Aby uzyskać więcej informacji, zobacz [niestandardowe właściwości dokumentu — Omówienie](../vsto/custom-document-properties-overview.md).

2. Jeśli istnieją rozszerzenia kodu zarządzanego, aplikacja ładuje *VSTOEE. dll*, który ładuje *VSTOLoader. dll*. Są to niezarządzane biblioteki DLL, które są składnikami modułu ładującego dla programu Visual Studio 2010 Tools for Office Runtime. Aby uzyskać więcej informacji, zobacz [Visual Studio Tools dla środowiska uruchomieniowego pakietu Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).

3. *VSTOLoader. dll* ładuje [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] i uruchamia [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]zarządzaną część.

4. Jeśli dokument jest otwarty z lokalizacji innej niż komputer lokalny, program [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sprawdza, czy lokalizacja dokumentu znajduje się na liście **zaufanych lokalizacji** w **ustawieniach Centrum zaufania** dla danej aplikacji pakietu Office. Jeśli lokalizacja dokumentu nie znajduje się w zaufanej lokalizacji, dostosowanie nie jest zaufane i proces ładowania zostanie zatrzymany w tym miejscu.

5. Program [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] zainstaluje rozwiązanie, jeśli nie zostało jeszcze zainstalowane, pobiera najnowsze manifesty aplikacji i wdrażania oraz wykonuje serię kontroli zabezpieczeń. Aby uzyskać więcej informacji, zobacz [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md).

6. Jeśli dostosowanie jest zaufane do uruchomienia, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] używa manifestu wdrożenia i manifestu aplikacji, aby sprawdzić dostępność aktualizacji zestawu. Jeśli zostanie udostępniona nowa wersja zestawu, środowisko uruchomieniowe pobierze nową wersję zestawu do [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] pamięci podręcznej na komputerze klienckim. Aby uzyskać więcej informacji, zobacz [wdrażanie rozwiązania biurowego](../vsto/deploying-an-office-solution.md).

7. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Tworzy nową domenę aplikacji, w której ma zostać załadowany zestaw dostosowywania.

8. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Ładuje zestaw dostosowywania do domeny aplikacji.

9. Wywołuje program obsługi zdarzeń uruchamiania w zestawie dostosowywania. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).

## <a name="see-also"></a>Zobacz także
- [Architektura rozwiązań pakietu Office w programie Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Visual Studio Tools dla środowiska uruchomieniowego pakietu Office — omówienie](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)
- [Przegląd właściwości dokumentu niestandardowego](../vsto/custom-document-properties-overview.md)
- [Dane w pamięci podręcznej w dostosowaniu na poziomie dokumentu](../vsto/cached-data-in-document-level-customizations.md)
