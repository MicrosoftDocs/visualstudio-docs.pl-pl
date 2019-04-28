---
title: Wymagania wstępne wdrożenia aplikacji | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, platform detection
- ClickOnce deployment, prerequisites
- ClickOnce deployment, dependencies
- prerequisites, ClickOnce
- dependencies, ClickOnce
ms.assetid: fc6e047e-ad94-44e8-8ff5-b6d1f4ca7735
caps.latest.revision: 53
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4945efddb91142ce04f5b117129428ec4a054fc3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63427257"
---
# <a name="application-deployment-prerequisites"></a>Wstępnie wymagane składniki wdrażania aplikacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby upewnić się, że Twoja aplikacja zostanie zainstalowana i wykonane pomyślnie, najpierw upewnij się, że wszystkie składniki, od których zależy aplikacja, są już zainstalowane na komputerze docelowym. Na przykład większość aplikacji utworzonych przy użyciu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zależy od [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]; poprawną wersję środowiska uruchomieniowego języka wspólnego musi być obecny na komputerze docelowym, zanim aplikacja zostanie zainstalowana.  
  
 Możesz wybrać te warunki wstępne **wstępnie wymagane składniki, okno dialogowe** i zainstaluj jako część instalacji programu .NET Framework i innych pakietów redystrybucyjnych. To rozwiązanie jest znany jako *uruchamianie*. Następnie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje program wykonywalny Windows o nazwie Setup.exe, znany także jako *programu inicjującego*. Program inicjujący jest odpowiedzialny za instalowanie wymagań wstępnych przed uruchomieniem Twojej aplikacji. Aby uzyskać więcej informacji o wybieraniu tych wymagań wstępnych, zobacz [wstępnie wymagane składniki, okno dialogowe](../ide/reference/prerequisites-dialog-box.md).  
  
 Każdy warunek wstępny jest pakiet programu inicjującego. Pakiet programu inicjującego to grupa katalogów i plików, które zawierają pliki manifestu, które opisują sposób instalacji wstępnie wymaganego składnika. Jeśli Twoje wstępnie wymagane składniki aplikacji nie są wymienione w **okno dialogowe wymagań wstępnych**, można tworzyć niestandardowe pakiety programu inicjującego i dodać je do programu Visual Studio. Można wybrać wstępnie wymagane składniki w **wstępnie wymagane składniki, okno dialogowe**. Aby uzyskać więcej informacji, zobacz [tworzenie pakietów programu inicjującego](../deployment/creating-bootstrapper-packages.md).  
  
 Uruchamianie jest włączone domyślnie dla wdrażania ClickOnce. Program inicjujący, generowany dla wdrażania ClickOnce jest podpisany. Możesz wyłączyć uruchamianie składnika, ale należy to zrobić tylko wtedy, gdy masz pewność, że na wszystkich komputerach docelowych już zainstalowano poprawną wersję składnika.  
  
## <a name="bootstrapping-and-clickonce-deployment"></a>Uruchamianie i wdrażanie technologii ClickOnce  
 Przed zainstalowaniem aplikacji na komputerze klienckim [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] zbada klienta, aby upewnić się, że ma określone wymagania określone w manifeście aplikacji. Należą do nich między innymi:  
  
- Minimalna wymagana wersja środowiska CLR, który jest określony jako zależność od zestawu w manifeście aplikacji.  
  
- Minimalna wymagana wersja systemu operacyjnego Windows, które są wymagane przez aplikację, jak określono w aplikacji manifestu za pomocą `<osVersionInfo>` elementu. (Zobacz [ \<zależności > Element](../deployment/dependency-element-clickonce-application.md))  
  
- Minimalna wersja wszystkie zestawy, które muszą być wstępnie zainstalowane w globalnej pamięci podręcznej zestawów (GAC), jak określono w deklaracji zależności zestawu w manifeście zestawu.  
  
  [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] może wykryć brakujących wymagań wstępnych i wymagań wstępnych można zainstalować za pomocą programu inicjującego. Aby uzyskać więcej informacji, zobacz [jak: Instalowanie wymagań wstępnych przy użyciu aplikacji ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  
  
> [!NOTE]
> Aby zmienić wartości w manifestach wygenerowanych przez narzędzia takie jak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i MageUI.exe, należy edytować manifest aplikacji w edytorze tekstów, a następnie ponownie podpisać manifesty aplikacji i wdrażania. Aby uzyskać więcej informacji, zobacz [jak: Ponowne podpisywanie aplikacji i manifestów wdrożenia](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
 Jeśli używasz programu Visual Studio i technologii ClickOnce do wdrażania aplikacji, pakietów programu inicjującego, które są wybrane domyślnie są zależne od wersji programu .NET Framework w rozwiązaniu. Jednak jeśli zmienisz .NET Framework w wersji docelowej, należy zaktualizować opcje w **wstępnie wymagane składniki, okno dialogowe** ręcznie.  
  
|Target .NET Framework|Wybrany program inicjujący pakietów|  
|---------------------------|------------------------------------|  
|.NET Framework 4 Client Profile|.NET Framework 4 Client Profile<br /><br /> Instalator Windows 3.1|  
|Program .NET Framework 4|Program .NET Framework 4<br /><br /> Instalator Windows 3.1|  
  
 Za pomocą [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożenia, na stronie Publish.htm generowane przez [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Kreatora publikacji wskazuje albo do łącza, który instaluje tylko aplikację lub Link instalowane uruchomionego składników i aplikacji.  
  
 Jeśli program inicjujący jest generowane przy użyciu Kreatora publikacji technologii ClickOnce lub opublikuj stronę w programie Visual Studio, Setup.exe zostanie automatycznie zarejestrowany. Jednak jeśli chcesz zarejestrować program inicjujący za pomocą certyfikatu klienta, można podpisać go później.  
  
## <a name="bootstrapping-and-msbuild"></a>Uruchamianie i MSBuild  
 Jeśli nie używasz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ale kompilowania aplikacji w wierszu polecenia, można utworzyć [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Inicjowanie aplikacji za pomocą zadania aparatu Microsoft Build Engine (MSBuild). Aby uzyskać więcej informacji, zobacz [generatebootstrapper — zadanie](../msbuild/generatebootstrapper-task.md).  
  
 Jako alternatywę do uruchomienia można wdrożyć wstępnie składników za pomocą system dystrybucji oprogramowania elektronicznych, takich jak Microsoft Systems Management Server (SMS).  
  
## <a name="bootstrapper-setupexe-command-line-arguments"></a>Argumenty wiersza polecenia programu inicjującego (Setup.exe)  
 Setup.exe generowane przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i zadania programu MSBuild obsługuje niewielki zestaw następujące argumenty wiersza polecenia. Argumenty dostarczone do bootstrapping aplikacji poza te są przekazywane do Instalatora aplikacji.  
  
 W przypadku zmiany żadnych opcji program inicjujący musi zmienić program inicjujący bez znaku, a następnie zaloguj pliku inicjującego w później.  
  
|Argument wiersza polecenia|Opis|  
|---------------------------|-----------------|  
|**-?, -h, — pomoc**|Wyświetla okno dialogowe pomocy.|  
|**— adres url, - componentsurl**|Pokazuje adres URL przechowywanych i składników adresów url dla tego zestawu w górę.|  
|**-url =** `location`|Ustawia adres URL, gdzie będzie szukał Setup.exe [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji.|  
|**-componentsurl =** `location`|Ustawia adres URL, w którym Setup.exe będzie szukał zależności, takie jak [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].|  
|**-homesite=** `true` **&#124;** `false`|Gdy `true`, pliki do pobrania zależności z preferowanych lokalizacji witryny dostawcy. Ustawienie to zastępuje **- componentsurl** ustawienie. Gdy `false`, pobiera zależności z adresu URL określonego przez **- componentsurl**.|  
  
## <a name="operating-system-support"></a>Obsługa systemu operacyjnego  
 Program inicjujący programu Visual Studio nie jest obsługiwana w systemie Windows Server 2008 Server Core lub systemu Windows Server 2008 R2 Server Core, które zapewniają środowisko niski konserwacji serwera z ograniczoną funkcjonalnością. Na przykład opcja instalacji Server Core obsługuje tylko profilu platformy .NET Framework 3.5 Server Core, więc nie można uruchomić funkcji programu Visual Studio, które są zależne od pełnego środowiska .NET Framework.  
  
## <a name="see-also"></a>Zobacz też  
 [Wybieranie strategii wdrażania ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Wskazówki dotyczące wdrażania i zabezpieczeń ClickOnce](../deployment/clickonce-security-and-deployment.md)
