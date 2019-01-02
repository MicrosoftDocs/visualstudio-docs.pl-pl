---
title: Visual Studio Tools dla pakietu Office runtime ― omówienie
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio], about Office runtime
- VSTOLoader.dll
- runtime loader [Office development in Visual Studio]
- Office runtime [Office development in Visual Studio], assemblies
- Office runtime [Office development in Visual Studio]
- runtime [Office development in Visual Studio], assemblies
- vstoee.dll
- Visual Studio Tools for Office runtime
- Office solutions [Office development in Visual Studio], runtime
- solutions [Office development in Visual Studio], runtime
- versions [Office development in Visual Studio], runtime
- assemblies [Office development in Visual Studio], runtime
- runtime [Office development in Visual Studio], about VSTO runtime
- solution loader [Office development in Visual Studio]
- runtime [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bdae6b7f08ec442d7bca0b0aa3b46b8825385767
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53878786"
---
# <a name="visual-studio-tools-for-office-runtime-overview"></a>Visual Studio Tools dla pakietu Office runtime ― omówienie
  Do uruchamiania rozwiązań, które są tworzone przy użyciu narzędzia Microsoft Office developer tools w programie Visual Studio, Visual Studio 2010 Tools dla pakietu Office runtime musi być zainstalowany na komputerach użytkowników końcowych. Aby uzyskać więcej informacji, zobacz [jak: Zainstalować Visual Studio Tools for Office runtime pakiet redystrybucyjny](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md). Visual Studio 2010 Tools dla pakietu Office runtime składa się z dwóch głównych składników:  
  
- Rozszerzenia pakietu Office dla środowiska .NET Framework. To zarządzane zestawy tworzące warstwę komunikacji między rozwiązaniem a aplikacją pakietu Microsoft Office. Aby uzyskać więcej informacji, zobacz [opis rozszerzeń pakietu Office dla .NET Framework](#officeextensions).  
  
- Moduł ładujący rozwiązanie dla pakietu Office. To zestaw niezarządzanych bibliotek DLL, przy użyciu których aplikacje pakietu Office ładują środowisko uruchomieniowe i rozwiązanie. Aby uzyskać więcej informacji, zobacz [zrozumieć modułu ładującego rozwiązanie Office](#UnmanagedLoader).  
  
  Środowisko uruchomieniowe można zainstalować na kilka różnych sposobów. Składniki środowiska dodawane podczas jego instalacji zależą od konfiguracji komputera. Aby uzyskać więcej informacji, zobacz [Visual Studio Tools for Office Runtime ― scenariusze instalacji](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).  
  
##  <a name="officeextensions"></a> Opis rozszerzeń pakietu Office dla programu .NET Framework  
 Visual Studio 2010 Tools dla pakietu Office runtime zawierają rozszerzenia pakietu Office dla .NET Framework 3.5 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] i nowszych. Rozwiązania przeznaczone dla poszczególnych wersji środowiska .NET Framework używają rozszerzeń odpowiednich dla danej wersji.  
  
 Rozszerzenia te składają się z zestawów, przy użyciu których rozwiązania automatyzują aplikacje pakietu Office i poszerzają ich funkcjonalność. Podczas tworzenia projektu pakietu Office program Visual Studio automatycznie dodaje odwołania do zestawów używanych dla typu projektu oraz docelowego środowiska .NET Framework projektu. Aby uzyskać więcej informacji na temat zestawów w rozszerzeniach pakietu Office, zobacz [zestawy w Visual Studio Tools for Office runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).  
  
### <a name="design-differences-in-the-office-extensions"></a>Różnice konstrukcyjne między rozszerzeniami pakietu Office  
 Większość typów używanych w rozszerzeniach pakietu Office dla środowiska .NET Framework 3.5 to klasy. Są te same klasy, które występowały w poprzednich wersjach [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Natomiast większość typów używanych w rozszerzeniach pakietu Office dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszych interfejsów. Na przykład kiedy środowiskiem docelowym [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym, <xref:Microsoft.Office.Tools.Excel.Worksheet> i <xref:Microsoft.Office.Tools.Word.Document> typy są interfejsami zamiast klasami.  
  
 W większości przypadków kod pisany w rozwiązaniach pakietu Office jest taka sama czy Twoje rozwiązanie jest przeznaczone dla programu .NET Framework 3.5 lub [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Jednak niektóre funkcje wymagają kodu dopasowanego do cech wersji środowiska .NET Framework. Aby uzyskać więcej informacji, zobacz [Migrowanie rozwiązań pakietu Office do wersji programu .NET Framework 4 lub nowszej](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).  
  
### <a name="interfaces-in-the-office-extensions-for-the-net-framework-4-or-later"></a>Interfejsy w rozszerzeniach pakietu Office dla programu .NET Framework 4 lub nowszego  
 Większość interfejsów w rozszerzenia pakietu Office dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej nie mają być implementowana przez kod użytkownika. Jedyne interfejsy, które można zaimplementować bezpośrednio, mają nazwy rozpoczynające się od litery **I**, takich jak <xref:Microsoft.Office.Tools.Excel.ISmartTagExtension>.  
  
 Wszystkie interfejsy, które nie zaczynają się od litery **I** są implementowane wewnętrznie przez Visual Studio 2010 Tools dla pakietu Office runtime i interfejsy te mogą się zmienić w przyszłych wydaniach. Aby utworzyć obiekty, które implementują te interfejsy, należy użyć metod dostarczonych przez `Globals.Factory` obiektu w projekcie. Na przykład, aby pobrać obiekt, który implementuje <xref:Microsoft.Office.Tools.Excel.SmartTag> interfejsu, należy użyć `Globals.Factory.CreateSmartTag` metody. Aby uzyskać więcej informacji na temat `Globals.Factory`, zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
### <a name="enable-type-equivalence-and-embedded-types-in-projects-that-target-the-net-framework-4-or-later"></a>Włączanie równoważności typów oraz typów osadzonych w projektach przeznaczonych dla programu .NET Framework 4 lub nowszy  
 Ponieważ model obiektu rozszerzeń pakietu Office dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszym są oparte na interfejsach, można użyć funkcji równoważności typu w językach Visual C# i Visual Basic w programie Visual Studio do osadzenia informacji o typie z [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] w rozwiązaniu . Ta funkcja umożliwia rozwiązań pakietu Office i [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] do wersji niezależnie od siebie nawzajem. Na przykład, jeśli rozwiązanie używa <xref:Microsoft.Office.Tools.Word.Document> interfejs jako osadzonego typu, a następna wersja środowiska uruchomieniowego dodaje elementy członkowskie do <xref:Microsoft.Office.Tools.Word.Document> interfejsu, rozwiązanie będzie współpracowało z następną wersją środowiska uruchomieniowego. Jeśli rozwiązanie nie korzysta z <xref:Microsoft.Office.Tools.Word.Document> interfejsu jako osadzonego typu, rozwiązanie przestanie działać z następną wersją środowiska uruchomieniowego.  
  
 Domyślnie funkcja równoważności typu nie jest włączona podczas tworzenia projektu Office współpracującego [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej. Aby włączyć tę funkcję, należy ustawić **Osadź typy współdziałania** właściwość następujące odwołania zestawów w swoim projekcie **True**:  
  
- Microsoft.Office.Tools.dll  
  
- Microsoft.Office.Tools.Common.dll  
  
- Microsoft.Office.Tools.Excel.dll  
  
- Microsoft.Office.Tools.Outlook.dll  
  
- Microsoft.Office.Tools.Word.dll  
  
  Wprowadzenie tej zmiany spowoduje, że informacje o typie dla wszystkich typów środowisk uruchomieniowych używanych w projekcie zostaną podczas kompilowania projektu osadzane w zestawie rozwiązania. Tych informacji osadzonego typu, a nie informacji o typie w przywoływanych zestawach są używane przez rozwiązanie w czasie wykonywania.  
  
##  <a name="UnmanagedLoader"></a> Omówienie modułu ładującego rozwiązanie Office  
 Visual Studio Tools for Office runtime zawiera kilka niezarządzanych bibliotek DLL, dla których aplikacje pakietu Office ładują środowisko uruchomieniowe i rozwiązania pakietu Office. Nigdy nie powinna zajść konieczność bezpośredniej pracy z tymi bibliotekami, jednak wiedza o ich przeznaczeniu może pomóc lepiej zrozumieć architekturę rozwiązań opartych na pakiecie Office.  
  
 Aby uzyskać informacje o używaniu tych składników podczas procesu ładowania, zobacz [Architektura dostosowywania na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md) i [architektury VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
### <a name="vstoeedll"></a>VSTOEE.dll  
 Gdy użytkownik otwiera dostosowywania poziomie dokumentu lub uruchamia dodatek narzędzi VSTO dla programów, aplikacji pakietu Office wywołuje bibliotekę do *VSTOEE.dll* do wykonywania zadań niezbędnych do załadowania [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
 *Biblioteka VSTOEE.dll* zapewniają, że poprawną wersję [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] jest ładowany do rozwiązania oraz zainstalowanej wersji pakietu Office. Chociaż wiele wersji [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] można zainstalować na tym samym komputerze, tylko jedno wystąpienie *VSTOEE.dll* jest zainstalowany w danym momencie. Jest to *VSTOEE.dll* było dołączone do najnowszej wersji środowiska uruchomieniowego zainstalowanego na komputerze. Aby uzyskać więcej informacji o różnych wersjach [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] który może służyć do innych rozwiązań, zobacz [uruchamianie rozwiązań w różnych wersjach pakietu Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md).  
  
### <a name="vstoloaderdll"></a>VSTOLoader.dll  
 Po *VSTOEE.dll* ładuje odpowiednią wersję [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], *VSTOLoader.dll* wykonuje większość pracy, które są wymagane do załadowania zestawu rozwiązania. *VSTOLoader.dll* wykonuje kilka rzeczy:  
  
- Tworzy domenę aplikacji dla każdego zestawu rozwiązania.  
  
- Wykonuje zbiór testów kontrolnych zabezpieczeń w celu sprawdzenia, czy zestaw rozwiązania ma pozwolenie na działanie.  
  
- Ładuje wersje rozszerzeń pakietu Office dla środowiska .NET Framework wymaganego przez rozwiązanie.  
  
  *VSTOLoader.dll* wpływa również kilka rzeczy, które są specyficzne dla dodatków narzędzi VSTO dla programów:  
  
- Implementuje <xref:Extensibility.IDTExtensibility2> interfejsu. <xref:Extensibility.IDTExtensibility2> to interfejs modelu COM, który muszą implementować wszystkie dodatki narzędzi VSTO dla aplikacji pakietu Microsoft Office. Ten interfejs definiuje metody wywoływane przez aplikację do komunikacji z dodatku narzędzi VSTO.  
  
- Implementuje imanagedaddin — interfejs. Ten interfejs jest używany przez aplikacje pakietu Office, aby ułatwić obciążenia dodatków narzędzi VSTO. Aby uzyskać więcej informacji, zobacz [imanagedaddin — interfejs](../vsto/imanagedaddin-interface.md).  
  
## <a name="understand-the-32-bit-and-64-bit-versions-of-the-runtime"></a>Zrozumienie 32-bitowych i 64-bitowe wersje środowiska uruchomieniowego  
 Istnieją osobne 64-bitowe i 32-bitowe wersje Visual Studio 2010 Tools dla pakietu Office runtime. Te wersje środowiska uruchomieniowego są używane do uruchamiania rozwiązań w 64-bitowe i 32-bitowe wersje pakietu Office. Pokazano w poniższej tabeli wersji środowiska wykonawczego jest wymagana dla każdej kombinacji systemu Windows i pakietu Office.  
  
|Wydanie systemu Windows|Wydanie pakietu Microsoft Office|Wymagana wersja środowiska Visual Studio Tools for Office Runtime|  
|------------------------|---------------------------------|--------------------------------------------------------------------|  
|32-bitowa|32-bitowa|32-bitowa|  
|64-bitowy|32-bitowa|64-bitowy|  
|64-bitowy|64-bitowy|64-bitowy|  
  
 Po zainstalowaniu pakietu Office, wymaganą wersję [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] jest instalowany razem z pakietem Office. Na przykład po zainstalowaniu 64-bitowa wersja pakietu Office na 64-bitowej wersji systemu Windows, 64-bitową wersję [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] jest również instalowany. Aby uzyskać więcej informacji o instalowaniu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] z pakietem Office, zobacz [Visual Studio Tools for Office Runtime ― scenariusze instalacji](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).  
  
 64-bitowej wersji pakietu Office, mogą również uruchamiać rozwiązania pakietu Office, które zostały utworzone przy użyciu szablonów projektu dla systemu Microsoft Office 2007 w programie Visual Studio 2008. Nie obsługują one jednak rozwiązań dla pakietu Office utworzonych przy użyciu szablonów projektów programu Microsoft Office 2003 w środowisku Visual Studio 2008 ani rozwiązań dla pakietu Office utworzonych w programie Visual Studio 2005. Aby uzyskać więcej informacji, zobacz [uruchamianie rozwiązań w różnych wersjach pakietu Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md).  
  
## <a name="repair-the-visual-studio-2010-tools-for-office-runtime"></a>Napraw program Visual Studio 2010 Tools dla pakietu Office runtime  
 Jeśli zachodzi potrzeba naprawy środowiska uruchomieniowego, otwórz **programy i funkcje** lub **apletu Dodaj lub usuń programy** w Panelu sterowania wybierz **programu Microsoft Visual Studio 2010 Tools for Office Runtime**na liście programów, a następnie kliknij przycisk **Odinstaluj**. Zostanie uruchomiony program instalacyjny, który umożliwi naprawę środowiska. Jeśli klikniesz **zmiany**, nie są podane opcji naprawy środowiska uruchomieniowego.  
  
## <a name="see-also"></a>Zobacz także  
 [Visual Studio Tools dla pakietu Office Runtime ― scenariusze instalacji](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)   
 [Zestawy w Visual Studio Tools for Office runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)   
 [Architektura rozwiązań pakietu Office w programie Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Architektura dostosowywania na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md)   
 [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Uaktualnianie i migracja rozwiązań pakietu Office](../vsto/upgrading-and-migrating-office-solutions.md)  
