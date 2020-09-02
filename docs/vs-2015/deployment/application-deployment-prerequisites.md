---
title: Wymagania wstępne dotyczące wdrażania aplikacji | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64824310"
---
# <a name="application-deployment-prerequisites"></a>Wstępnie wymagane składniki wdrażania aplikacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby upewnić się, że aplikacja zostanie zainstalowana i uruchomiona pomyślnie, musisz najpierw upewnić się, że wszystkie składniki, na których aplikacja jest zależna, są już zainstalowane na komputerze docelowym. Na przykład większość aplikacji utworzonych przy użyciu programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ma zależność od; na [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] komputerze docelowym musi znajdować się poprawna wersja środowiska uruchomieniowego języka wspólnego przed zainstalowaniem aplikacji.  
  
 Te wymagania wstępne można wybrać w **oknie dialogowym wymagania wstępne** i zainstalować .NET Framework i inne redystrybucyjne w ramach instalacji. To rozwiązanie jest *znane jako uruchomienie*. Następnie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje program wykonywalny systemu Windows o nazwie Setup.exe, nazywany także programem *inicjującym*. Program inicjujący jest odpowiedzialny za Instalowanie wymagań wstępnych przed uruchomieniem aplikacji. Aby uzyskać więcej informacji na temat wybierania tych wymagań wstępnych, zobacz [okno dialogowe wymagania wstępne](../ide/reference/prerequisites-dialog-box.md).  
  
 Każde wymaganie wstępne jest pakietem programu inicjującego. Pakiet programu inicjującego to grupa katalogów i plików, które zawierają pliki manifestu opisujące, jak należy zainstalować wymaganie wstępne. Jeśli wymagania wstępne dotyczące aplikacji nie są wyświetlane w **oknie dialogowym wymagań wstępnych**, można utworzyć niestandardowe pakiety programu inicjującego i dodać je w programie Visual Studio. Następnie możesz wybrać wymagania wstępne w **oknie dialogowym wymagania wstępne**. Aby uzyskać więcej informacji, zobacz [Tworzenie pakietów programu inicjującego](../deployment/creating-bootstrapper-packages.md).  
  
 Domyślnie inicjowanie jest włączone dla wdrożenia ClickOnce. Program inicjujący wygenerowany na potrzeby wdrożenia ClickOnce jest podpisany. Można wyłączyć uruchamianie dla składnika, ale należy to zrobić tylko wtedy, gdy masz pewność, że poprawna wersja składnika jest już zainstalowana na wszystkich komputerach docelowych.  
  
## <a name="bootstrapping-and-clickonce-deployment"></a>Inicjowanie i wdrażanie ClickOnce  
 Przed zainstalowaniem aplikacji na komputerze klienckim program [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] przeanalizuje klienta, aby upewnić się, że ma określone wymagania określone w manifeście aplikacji. Należą do nich następujące funkcje:  
  
- Minimalna wymagana wersja środowiska uruchomieniowego języka wspólnego, która jest określona jako zależność zestawu w manifeście aplikacji.  
  
- Minimalna wymagana wersja systemu operacyjnego Windows wymaganego przez aplikację, jak określono w manifeście aplikacji przy użyciu `<osVersionInfo>` elementu. (Zobacz [ \<dependency> element](../deployment/dependency-element-clickonce-application.md))  
  
- Minimalna wersja dowolnego zestawu i wszystkich zestawów, które muszą być wstępnie zainstalowane w globalnej pamięci podręcznej zestawów (GAC), zgodnie z opisem w deklaracji zależności zestawu w manifeście zestawu.  
  
  [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] program może wykryć brakujące wymagania wstępne i zainstalować wstępnie wymagane składniki przy użyciu programu inicjującego. Aby uzyskać więcej informacji, zobacz [How to: Install Preinstallations with ClickOnce Application](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  
  
> [!NOTE]
> Aby zmienić wartości w manifestach generowanych przez narzędzia takie jak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i MageUI.exe, należy edytować manifest aplikacji w edytorze tekstów, a następnie ponownie podpisać aplikacje i manifesty wdrożenia. Aby uzyskać więcej informacji, zobacz [jak: ponowne podpisywanie aplikacji i manifestów wdrożenia](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
 Jeśli używasz programu Visual Studio i ClickOnce do wdrażania aplikacji, pakiety programu inicjującego wybrane domyślnie zależą od wersji .NET Framework w rozwiązaniu. Jeśli jednak zmienisz wersję docelową .NET Framework, musisz ręcznie zaktualizować opcje w **oknie dialogowym wymagania wstępne** .  
  
|.NET Framework docelowe|Wybrane pakiety programu inicjującego|  
|---------------------------|------------------------------------|  
|.NET Framework 4 Client Profile|.NET Framework 4 Client Profile<br /><br /> Instalator Windows w wersji 3.1|  
|Program .NET Framework 4|Program .NET Framework 4<br /><br /> Instalator Windows w wersji 3.1|  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Po wdrożeniu strona Publish.htm generowana przez [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Kreatora publikacji wskazuje na link instalujący tylko aplikację lub link instalujący aplikację oraz składniki programu inicjującego.  
  
 W przypadku wygenerowania programu inicjującego przy użyciu Kreatora publikacji ClickOnce lub strony publikowania w programie Visual Studio Setup.exe zostanie podpisana automatycznie. Jeśli jednak chcesz użyć certyfikatu klienta do podpisania programu inicjującego, możesz podpisać go później.  
  
## <a name="bootstrapping-and-msbuild"></a>Uruchamianie i MSBuild  
 Jeśli nie używasz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , ale kompilujesz aplikacje w wierszu polecenia, możesz utworzyć [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikację inicjującą przy użyciu zadania Microsoft Build Engine (MSBuild). Aby uzyskać więcej informacji, zobacz [GenerateBootstrapper — Task](../msbuild/generatebootstrapper-task.md).  
  
 Alternatywnie w przypadku uruchamiania programu można wstępnie wdrożyć składniki przy użyciu elektronicznego systemu dystrybucji oprogramowania, takiego jak Microsoft Systems Management Server (SMS).  
  
## <a name="bootstrapper-setupexe-command-line-arguments"></a>Argumenty wiersza polecenia programu inicjującego (Setup.exe)  
 Setup.exe generowany przez program [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oraz zadania programu MSBuild obsługują następujący niewielki zestaw argumentów wiersza polecenia. Wszystkie argumenty dostarczone do aplikacji inicjującej wykraczające poza te są przekazywane do Instalatora aplikacji.  
  
 W przypadku zmiany opcji programu inicjującego należy zmienić niepodpisany program inicjujący, a następnie ponownie podpisać plik programu inicjującego.  
  
|Argument wiersza polecenia|Opis|  
|---------------------------|-----------------|  
|**-?,-h,-help**|Wyświetla okno dialogowe pomoc.|  
|**-URL,-ComponentsUrl**|Wyświetla adres URL przechowywanego adresu URL i składników dla tego ustawienia.|  
|**-URL =**`location`|Ustawia adres URL, pod którym będzie wyglądał Setup.exe [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacja.|  
|**-ComponentsUrl =**`location`|Ustawia adres URL, pod którym Setup.exe będzie szukać zależności, takich jak [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .|  
|**-HomeSite =** `true` **&#124;**`false`|Gdy `true` program pobiera zależności z preferowanej lokalizacji w lokacji dostawcy. Spowoduje to zastąpienie ustawienia **-ComponentsUrl** . Gdy `false` program pobiera zależności od adresu URL określonego przez **-ComponentsUrl**.|  
  
## <a name="operating-system-support"></a>Obsługa systemu operacyjnego  
 Program inicjujący programu Visual Studio nie jest obsługiwany w systemie Windows Server 2008 Server Core lub Windows Server 2008 R2 Server Core, który zapewnia środowisko serwera o małym obsłudze z ograniczoną funkcjonalnością. Na przykład opcja instalacji Server Core obsługuje tylko profil podstawowy .NET Framework 3,5, więc funkcje programu Visual Studio, które są zależne od pełnych .NET Framework nie mogą zostać uruchomione.  
  
## <a name="see-also"></a>Zobacz też  
 [Wybieranie strategii wdrażania ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Bezpieczeństwo i wdrażanie technologii ClickOnce](../deployment/clickonce-security-and-deployment.md)
