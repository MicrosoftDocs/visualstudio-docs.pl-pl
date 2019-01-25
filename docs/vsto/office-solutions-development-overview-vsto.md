---
title: Omówienie programowania rozwiązań pakietu Office (VSTO)
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies, Office
- Office development in Visual Studio, about developing solutions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b4b8378b8f0986e7a02955a9aa0e011c12485ca6
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867094"
---
# <a name="office-solutions-development-overview-vsto"></a>Omówienie programowania rozwiązań pakietu Office (VSTO)
  Za pomocą programu Microsoft Office jako fronton dla rozwiązania, możesz korzystać z zalet dobrze znanych interfejsów użytkownika Microsoft Office i narzędzi, takich jak funkcje przetwarzania tekstu w programach Word, funkcje analizy danych programu Excel i funkcje zarządzania pocztą e-mail programu Outlook . Można opracować rozwiązania w programie Visual Studio, aby dostosować aplikacje pakietu Office, a następnie dodaj określonych funkcji, czego potrzebujesz do procesów biznesowych. Na przykład można przekształcić w programie Word generator kontraktu, który składa umów się istniejące elementy, które mogą być wykonane edytowalne i nieedytowalne. Za pomocą programu Excel można utworzyć arkusz automatycznych budżetu dostosowane do różnych projektów. Użytkownicy mogą skorzystać z rozwiązań pakietu office w trybie offline, co sprawia, że złożonych rozwiązań jest praktyczniejsze w taki sposób, niż byłoby ich, jeśli używasz architektury opartej na sieci web.  
  
 Ten temat zawiera omówienie typów rozwiązań dla pakietu Office utworzonych przy użyciu programu Visual Studio Tools dla pakietu Office (VSTO) szablony dostępne w narzędzia Office developer tools w programie Visual Studio. Aby uzyskać ogólne informacje o tym, jak tworzyć aplikacje za pomocą pakietu Office, zobacz [Centrum deweloperów pakietu Office](https://dev.office.com/).  
  
## <a name="choose-an-office-project-type"></a>Wybierz typ projektu pakietu Office  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zawiera następujące typy szablonów projektu do tworzenia aplikacji na podstawie narzędzi VSTO dla pakietu Office:  
  
- **Dostosowania na poziomie dokumentu** są skojarzone z określonym dokumentem.  
  
- **Dodatki narzędzi VSTO dla programów** są skojarzone z samej aplikacji.  
  
  Aby zdecydować, które z tych typów projektów jest najlepsze dla Twojego rozwiązania, pomyśl o tego, czy chcesz, aby kod tylko wtedy, gdy określony dokument jest otwarty lub czy kod, który ma być dostępny zawsze, gdy aplikacja jest uruchomiona. Aby uzyskać więcej informacji na temat szablonów projektu, zobacz [Przegląd szablony projektu pakietu Office](../vsto/office-project-templates-overview.md).  
  
  Zależą od typów projektów, które można utworzyć, na których aplikacje pakietu Office został zainstalowany na komputerze deweloperskim. Aby uzyskać więcej informacji, zobacz [funkcje, które są dostępne przez typ aplikacji i projektów pakietu Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
### <a name="document-level-customizations"></a>Dostosowania na poziomie dokumentów  
 Dostosowania na poziomie dokumentu składają się z zestawu, który jest skojarzony z jednym dokumencie, skoroszyt lub szablon w programie Microsoft Office Word lub Microsoft Office Excel. Zestaw jest ładowany, gdy skojarzony dokument jest otwarty. Funkcje dostosowania, które tworzysz są dostępne tylko wtedy, gdy skojarzony dokument jest otwarty. Dostosowania nie może wprowadzać zmian całej aplikacji, takich jak wyświetlanie nowej karty Wstążki lub elementu menu, gdy dowolny dokument jest otwarty.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zawiera narzędzia ułatwiające tworzenie dostosowań na poziomie dokumentu. Dokument, który można dostosować, znajduje się jako powierzchni projektowej w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], co umożliwia projektowanie dokumentu, przeciągając i upuszczając formanty do go. Wiele innych [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] funkcje są dostępne w projektach na poziomie dokumentu, takich jak formanty Windows Forms, powiązanie danych przeciągania i upuszczania oraz zintegrowany debuger.  
  
 Aby uzyskać więcej informacji na temat dostosowywania zobacz następujące tematy:  
  
-   [Wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)  
  
-   [Wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)  
  
-   [Architektura dostosowywania na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md)  
  
### <a name="vsto-add-ins"></a>Dodatków narzędzi VSTO  
 Dodatki narzędzi VSTO dla programów składają się z zestawu, który jest skojarzony z aplikacją Microsoft Office. Zazwyczaj dodatku narzędzi VSTO jest uruchamiany, gdy skojarzona aplikacja jest uruchomiona, chociaż użytkownicy mogą także ładować dodatków narzędzi VSTO po aplikacja jest już uruchomiona. Funkcje dodatków narzędzi VSTO dla programów, które tworzysz są dostępne dla aplikacji, niezależnie od tego, które są otwarte dokumenty.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zawiera narzędzia ułatwiające tworzenie dodatków narzędzi VSTO. Projekty dodatków zawierają automatycznie wygenerowaną klasę, która reprezentuje dodatku narzędzi VSTO. Ta klasa udostępnia właściwości i zdarzenia, które umożliwia dostęp do modelu obiektów w aplikacji hosta i uruchomienia kodu po dodatku narzędzi VSTO jest ładowany i zamknij. Wiele innych [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] funkcje są dostępne w dodatku narzędzi VSTO projektów, takich jak Windows Forms i zintegrowany debuger.  
  
 Aby uzyskać więcej informacji na temat dodatków narzędzi VSTO dla programów zobacz następujące tematy:  
  
-   [Wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)  
  
-   [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)  
  
## <a name="automate-office-applications-by-using-primary-interop-assemblies"></a>Automatyzowanie aplikacji pakietu Office przy użyciu podstawowych zestawów międzyoperacyjnych  
 Programowe funkcje aplikacji pakietu Office można zastosować do rozwiązania, przez napisanie kodu, który uzyskuje dostęp do aplikacji w modelu obiektów. Modele obiektów są układ klas, które udostępniają funkcje za pośrednictwem różnych właściwości i metody. Model obiektów dla każdej aplikacji pakietu Office jest inny.  
  
 Aby użyć modelu obiektów w aplikacji pakietu Office za pomocą rozwiązania utworzone przy użyciu narzędzi programistycznych pakietu Office w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], należy użyć podstawowego zestawu międzyoperacyjnego (PIA) dla aplikacji. Zestaw PIA umożliwia kodu zarządzanego w rozwiązaniu do interakcji z modelem obiektów opartym na modelu COM aplikacji pakietu Office.  
  
 Konieczne jest posiadanie zestawów Office PIA zainstalowany i zarejestrowany w globalnej pamięci podręcznej na komputerze deweloperskim do wykonywania większości zadań programistycznych. Aby uzyskać więcej informacji, zobacz [Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/configuring-a-computer-to-develop-office-solutions.md). Zestawy PIA pakietu Office nie są wymagane na komputerach użytkowników końcowych do uruchamiania rozwiązań narzędzi VSTO dla pakietu Office. Aby uzyskać więcej informacji, zobacz [projektowania i tworzenia rozwiązań dla pakietu Office](../vsto/designing-and-creating-office-solutions.md).  
  
 Aby uzyskać więcej informacji o używaniu zestawów PIA w rozwiązaniach pakietu Office narzędzi VSTO dla programów zobacz następujące tematy:  
  
-   [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)  
  
-   [Podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md)  
  
## <a name="run-microsoft-vsto-office-solutions-on-end-user-computers"></a>Uruchom rozwiązania Microsoft narzędzi VSTO dla programów na komputerach użytkowników końcowych  
 Podczas tworzenia rozwiązania narzędzi VSTO dla pakietu Office, należy wziąć pod uwagę sposób wymagań związanych z wdrażaniem mogą mieć wpływ na rozwój wybrane opcje.  
  
### <a name="deployment-options"></a>Opcje wdrażania  
 Użyj technologii ClickOnce lub Instalatora Windows, aby wdrożyć rozwiązania, które tworzysz przy użyciu narzędzi programistycznych pakietu Office w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Wdrażanie ClickOnce umożliwia tworzenie rozwiązań samodzielnej aktualizacji, które można instalować i uruchamiać z interakcji z użytkownikiem minimalny. Instalator Windows (*.msi*) pliki mogą być łatwo rozproszone na komputerach użytkowników końcowych lub dystrybuowane za pomocą Systems Management Server (SMS). Aby uzyskać więcej informacji o wdrażaniu rozwiązań narzędzi VSTO dla pakietu Office, zobacz [wdrożyć rozwiązanie Office](../vsto/deploying-an-office-solution.md).  
  
### <a name="install-prerequisites"></a>Instalowanie wstępnie wymaganego oprogramowania  
 Przed uruchomieniem rozwiązania przez użytkowników końcowych tworzone przy użyciu narzędzi programistycznych pakietu Office w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], ich komputery muszą mieć zainstalowane pewne warunki wstępne. Jeśli wdrażasz swoje rozwiązanie przy użyciu technologii ClickOnce lub plik Instalatora Windows, te warunki wstępne można zainstalować za pomocą rozwiązania. Aby uzyskać więcej informacji, zobacz [wymagania wstępne rozwiązania pakietu Office wdrożenia](https://msdn.microsoft.com/9f672809-43a3-40a1-9057-397ce3b5126e) i [jak: Instalowanie wymagań wstępnych na komputerach użytkowników końcowych do uruchamiania rozwiązań pakietu Office](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
### <a name="security"></a>Zabezpieczenia  
 Zabezpieczenia dla rozwiązań pakietu Office VSTO jest wymuszana przez szereg sprawdza, czy [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] sprawia, że podczas instalacji i ładowania rozwiązania. Testy te obejmują sprawdzanie, czy lokalizacja pliku manifestu wdrożenia jest zaufana lub tego, czy certyfikat używany do podpisywania manifestu wdrażania jest zaufany. Aby uzyskać więcej informacji, zobacz [rozwiązań Secure Office](../vsto/securing-office-solutions.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Rozpoczynanie pracy &#40;programowanie Office w Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Architektura dostosowywania na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md)   
 [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)   
 [Wprowadzenie do programowania dostosowań na poziomie dokumentu dla programu Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)   
 [Wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)  
