---
title: Architektura dodatków narzędzi VSTO
ms.date: 02/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VSTOLoader.dll
- architecture [Office development in Visual Studio], application-level add-ins
- vstoee.dll
- application-level add-ins [Office development in Visual Studio], architecture
- add-ins [Office development in Visual Studio], architecture
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 27017978d01252870b7a92a88f49afe595dc1de8
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863646"
---
# <a name="architecture-of-vsto-add-ins"></a>Architektura dodatków narzędzi VSTO
  Dodatków narzędzi VSTO utworzony przy użyciu narzędzi Office developer tools w programie Visual Studio oferuje funkcje architektury, które podkreślić stabilność i bezpieczeństwo i umożliwia im ściśle współpracować z programem Microsoft Office. W tym temacie opisano następujące aspekty dodatków narzędzi VSTO dla programów:  
  
- [Omówienie dodatków narzędzi VSTO](#UnderstandingAddIns)  
  
- [Składniki dodatków narzędzi VSTO](#AddinComponents)  
  
- [Jak działają dodatków narzędzi VSTO za pomocą aplikacji Microsoft Office](#HowAddinsWork)  
  
  [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
  Aby uzyskać ogólne informacje o tworzeniu dodatków narzędzi VSTO dla programów, zobacz [rozwój rozwiązań Office ― omówienie &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) i [wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md).  
  
##  <a name="UnderstandingAddIns"></a> Omówienie dodatków narzędzi VSTO  
 Korzystając z narzędzia Office developer tools w programie Visual Studio do tworzenia dodatku narzędzi VSTO dla programów, możesz utworzyć zestawu kodu zarządzanego, który jest ładowany przez aplikacji pakietu Microsoft Office. Po załadowaniu zestawu dodatku narzędzi VSTO mogą reagować na zdarzenia, które są wywoływane w aplikacji (na przykład, gdy użytkownik kliknie element menu). Dodatek narzędzi VSTO dla programów można również wywołać modelu obiektów automatyzacji i rozszerzania aplikacji i może używać dowolnej klasy w [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].  
  
 Zestaw komunikuje się ze składnikami modelu COM. aplikacji za pomocą podstawowego zestawu międzyoperacyjnego aplikacji. Aby uzyskać więcej informacji, zobacz [podstawowe zestawy międzyoperacyjne pakietu Office](../vsto/office-primary-interop-assemblies.md) i [rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 W przypadku instalowania wielu dodatków narzędzi VSTO dla aplikacji każdego dodatku narzędzi VSTO jest ładowany w domenie innej aplikacji. Oznacza to, że jeden dodatku narzędzi VSTO który zachowuje się nieprawidłowo nie może spowodować innych dodatków narzędzi VSTO nie powiedzie się. Pozwala ona również od tego, upewnij się, że po zamknięciu aplikacji wszystkie dodatku narzędzi VSTO zestawy są usuwane z pamięci. Aby uzyskać więcej informacji o domenach aplikacji, zobacz [domen aplikacji](/dotnet/framework/app-domains/application-domains).  
  
> [!NOTE]  
>  Dodatków narzędzi VSTO, które tworzysz przy użyciu narzędzi Office developer tools w programie Visual Studio są przeznaczone do użycia tylko wtedy, gdy host aplikacji Microsoft Office jest uruchamiana przez użytkownika końcowego. Jeśli aplikacja jest uruchamiana programowo (na przykład za pomocą automatyzacji), dodatku narzędzi VSTO mogą nie działać zgodnie z oczekiwaniami.  
  
##  <a name="AddinComponents"></a> Składniki dodatków narzędzi VSTO  
 Mimo że zestaw dodatku narzędzi VSTO dla programów główny składnik, jest wiele składników, które odgrywa ważną rolę w jaki sposób aplikacje Microsoft Office wykrycie i załadowanie dodatków narzędzi VSTO.  
  
### <a name="registry-entries"></a>Wpisy rejestru  
 Aplikacje Microsoft Office odnajdywania dodatków narzędzi VSTO dla programów, wyszukując zbiór wpisów rejestru. Aby uzyskać pełną listę wpisów rejestru używane przez dodatków narzędzi VSTO dla programów, zobacz [wpisy rejestru dotyczące dodatków narzędzi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
 Podczas kompilowania rozwiązania programu Visual Studio tworzy wszystkie wymagane wpisy rejestru na komputerze programisty, aby można debugowania i uruchamiania dodatku narzędzi VSTO dla programów. Aby uzyskać więcej informacji, zobacz [rozwiązań kompilacji pakietu Office](../vsto/building-office-solutions.md).  
  
 Użycie technologii ClickOnce do wdrożenia rozwiązania, program instalacyjny generowany przez proces publikowania, automatycznie tworzy klucze rejestru na komputerze użytkownika końcowego. Aby uzyskać więcej informacji, zobacz [wdrażania rozwiązania pakietu Office przy użyciu technologii ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
### <a name="deployment-manifest-and-application-manifest"></a>Manifesty wdrożenia i manifest aplikacji  
 Do identyfikowania i załadować najbardziej aktualną wersję zestawu dodatku narzędzi VSTO dodatków narzędzi VSTO używają manifesty aplikacji i manifestów wdrożenia. Wskazuje bieżący manifest aplikacji manifest wdrożenia. Manifest aplikacji wskazuje zestaw dodatku narzędzi VSTO dla programów i określa klasę punktu wejścia do wykonania w zestawie. Aby uzyskać więcej informacji, zobacz [stosowania i wdrażania manifestów w rozwiązaniach pakietu Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
### <a name="visual-studio-tools-for-office-runtime"></a>Program Visual Studio Tools for Office Runtime  
 Aby uruchomić dodatków narzędzi VSTO dla programów, które są tworzone przy użyciu narzędzi Office developer tools w programie Visual Studio, musi mieć komputerach użytkowników końcowych [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] zainstalowane. Środowisko uruchomieniowe zawiera składniki niezarządzane i zbiór zestawów zarządzanych. Niezarządzane składniki załadować zestawu dodatku narzędzi VSTO. Zestawy zarządzane zapewniają model obiektu, który korzysta z kodu dodatku narzędzi VSTO zautomatyzować i rozszerzyć aplikację hosta.  
  
 Aby uzyskać więcej informacji, zobacz [Visual Studio Tools dla pakietu Office runtime ― omówienie](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
##  <a name="HowAddinsWork"></a> Jak działają dodatków narzędzi VSTO za pomocą aplikacji Microsoft Office  
 Gdy użytkownik uruchamia aplikację Microsoft Office, aplikacja używa pliku manifestu wdrożenia i manifest aplikacji do lokalizowania i ładowania najbardziej aktualną wersję zestawu dodatku narzędzi VSTO. Na poniższej ilustracji przedstawiono architekturę podstawowe tych dodatków narzędzi VSTO dla programów.  
  
 ![Architektura dodatków pakietu office 2007](../vsto/media/office07addin.png "architektura dodatku pakietu Office 2007")  
  
> [!NOTE]  
>  W rozwiązaniach pakietu Office, których platformą docelową [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], rozwiązania mogą wywoływać model obiektów aplikacji hosta, za pomocą informacji o typie PIA osadzone w zestawie rozwiązania, zamiast wywoływać metodę do PIA bezpośrednio. Aby uzyskać więcej informacji, zobacz [projektowania i tworzenia rozwiązań dla pakietu Office](../vsto/designing-and-creating-office-solutions.md).  
  
### <a name="loading-process"></a>Proces ładowania  
 Gdy użytkownik uruchamia aplikację, wykonywane są następujące kroki:  
  
1.  Aplikacja sprawdza się w rejestrze wpisy, które identyfikują dodatków narzędzi VSTO dla programów, które zostały utworzone przy użyciu narzędzi Office developer tools w programie Visual Studio.  
  
2.  Jeśli aplikacja wykryje te wpisy rejestru, biblioteka VSTOEE.dll, która ładuje VSTOLoader.dll ładowania aplikacji. Są to niezarządzanych bibliotek DLL, które są składnikami programu ładującego dla Visual Studio 2010 Tools for Office Runtime. Aby uzyskać więcej informacji, zobacz [Visual Studio Tools dla pakietu Office runtime ― omówienie](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
3.  *VSTOLoader.dll* ładuje [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] i uruchomienie zarządzanego część [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
4.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Sprawdza dostępność aktualizacji manifestu i pobiera najnowsze manifestów aplikacji i wdrożenia.  
  
5.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Wykonuje szereg kontroli zabezpieczeń. Aby uzyskać więcej informacji, zobacz [rozwiązań Secure Office](../vsto/securing-office-solutions.md).  
  
6.  Jeśli dodatek narzędzi VSTO dla programów jest zaufane do uruchamiania, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] używa manifest wdrożenia i manifest aplikacji, aby sprawdzać dostępność aktualizacji zestawu. Jeśli dostępna jest nowa wersja zestawu, środowisko uruchomieniowe pobiera nową wersję zestawu do [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] pamięci podręcznej na komputerze klienckim. Aby uzyskać więcej informacji, zobacz [wdrożyć rozwiązanie Office](../vsto/deploying-an-office-solution.md).  
  
7.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Tworzy nową domenę aplikacji, w którym można załadować zestawu dodatku narzędzi VSTO.  
  
8.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Ładuje zestaw dodatku narzędzi VSTO dla programów do domeny aplikacji.  
  
9. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Wywołania <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> metody w swojej dodatku narzędzi VSTO, jeśli zastępowano go.  
  
     Opcjonalnie można zastąpić tę metodę w celu udostępnienia obiektu w dodatku narzędzi VSTO dla programów do innych rozwiązań programu Microsoft Office. Aby uzyskać więcej informacji, zobacz [wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
10. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Wywołania <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> metody w swojej dodatku narzędzi VSTO, jeśli zastępowano go.  
  
     Opcjonalnie można zastąpić tę metodę, aby rozszerzyć pakietu Microsoft Office, zwracając obiekt, który implementuje interfejs rozszerzalności. Aby uzyskać więcej informacji, zobacz [dostosowywanie funkcji interfejsu użytkownika, korzystając z rozszerzalności interfejsów](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md).  
  
    > [!NOTE]  
    >  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Sprawia, że oddzielne wywołania do <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> metody dla każdego interfejsu rozszerzalności, która jest obsługiwana przez aplikację hosta. Mimo że pierwsze wywołanie do <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> metoda zazwyczaj ma miejsce przed wywołaniem do `ThisAddIn_Startup` metody dodatku narzędzi VSTO dla programów powinna nie należy czynić żadnych założeń o tym, kiedy <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> metoda zostanie wywołana lub ile razy zostanie wywołany.  
  
11. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Wywołania `ThisAddIn_Startup` metody w dodatku VSTO. Ta metoda jest domyślny program obsługi zdarzeń dla <xref:Microsoft.Office.Tools.AddInBase.Startup> zdarzeń. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Architektura rozwiązań pakietu Office w programie Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Architektura dostosowywania na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md)   
 [Visual Studio Tools dla pakietu Office runtime ― omówienie](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Program dodatków narzędzi VSTO](../vsto/programming-vsto-add-ins.md)   
 [Opracowywania rozwiązań pakietu Office](../vsto/developing-office-solutions.md)   
 [Zabezpieczanie rozwiązań pakietu Office](../vsto/securing-office-solutions.md)   
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)  
