---
title: Wymagania wstępne wdrożenia aplikacji | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8206e199acc3ccb76cf89603d48bed0173129218
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66746058"
---
# <a name="application-deployment-prerequisites"></a>Wymagania wstępne wdrożenia aplikacji

Aby utworzyć swoją aplikację, aby zainstalować i uruchomić się pomyślnie, należy najpierw zainstalować wszystkie składniki, od których aplikacja jest zależna na komputerze docelowym. Na przykład większość aplikacji utworzonych za pomocą [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ma zależność od programu .NET Framework. W tym przypadku poprawną wersję środowiska uruchomieniowego języka wspólnego musi być obecny na komputerze docelowym, zanim aplikacja zostanie zainstalowana.

 Możesz wybrać te warunki wstępne **wstępnie wymagane składniki, okno dialogowe** i zainstaluj jako część instalacji programu .NET Framework i inne redistributable. To rozwiązanie jest znany jako *uruchamianie*. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] generuje program wykonywalny Windows o nazwie *Setup.exe*, znane również jako *programu inicjującego*. Program inicjujący jest odpowiedzialny za instalowanie wymagań wstępnych przed uruchomieniem Twojej aplikacji. Aby uzyskać więcej informacji o wybieraniu tych wymagań wstępnych, zobacz [wstępnie wymagane składniki, okno dialogowe](../ide/reference/prerequisites-dialog-box.md).

 Każdy warunek wstępny jest pakiet programu inicjującego. Pakiet programu inicjującego to grupa katalogów i plików zawierających pliki manifestu, które opisują sposób instalacji wymagań wstępnych. Jeśli Twoje wstępnie wymagane składniki aplikacji nie są wymienione w **okno dialogowe wymagań wstępnych**, można tworzyć niestandardowe pakiety programu inicjującego i dodać je do programu Visual Studio. Można wybrać wstępnie wymagane składniki w **wstępnie wymagane składniki, okno dialogowe**. Aby uzyskać więcej informacji, zobacz [tworzenie pakietów programu inicjującego](../deployment/creating-bootstrapper-packages.md).

 Uruchamianie jest włączone domyślnie dla wdrażania ClickOnce. Program inicjujący, generowany dla wdrażania ClickOnce jest podpisany. Można wyłączyć uruchamianie składnika, ale tylko wtedy, gdy masz pewność, że poprawną wersję składnika jest już zainstalowany na wszystkich komputerach docelowych.

## <a name="bootstrapping-and-clickonce-deployment"></a>Uruchamianie i ClickOnce wdrożenia
 Przed zainstalowaniem aplikacji na komputerze klienckim [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sprawdza, czy klient, aby upewnić się, że ma on wymagania określone w manifeście aplikacji. Obejmują one następujące wymagania:

- Minimalna wymagana wersja środowiska CLR, który jest określony jako zależność od zestawu w manifeście aplikacji.

- Minimalna wymagana wersja systemu operacyjnego Windows, które są wymagane przez aplikację, jak określono w aplikacji manifestu za pomocą `<osVersionInfo>` elementu. (Zobacz [ \<zależności > element](../deployment/dependency-element-clickonce-application.md).)

- Minimalna wersja wszystkich zestawów, które muszą być wstępnie zainstalowane w globalnej pamięci podręcznej zestawów (GAC), jak określono w deklaracji zależności zestawu w manifeście zestawu.

  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] może wykryć brakujących wymagań wstępnych i wymagań wstępnych można zainstalować za pomocą programu inicjującego. Aby uzyskać więcej informacji, zobacz [jak: Instalowanie wymagań wstępnych przy użyciu aplikacji ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).

> [!NOTE]
> Aby zmienić wartości w manifestach wygenerowanych przez narzędzia takie jak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i *MageUI.exe*, należy edytować manifest aplikacji w edytorze tekstów i ponowne podpisywanie manifestów aplikacji i wdrażania. Aby uzyskać więcej informacji, zobacz [jak: Ponowne podpisywanie manifestów aplikacji i wdrożenia](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

 Jeśli używasz programu Visual Studio i technologii ClickOnce do wdrażania aplikacji, pakietów programu inicjującego, które są wybrane domyślnie są zależne od wersji programu .NET Framework w rozwiązaniu. Jednak jeśli zmienisz .NET Framework w wersji docelowej, należy zaktualizować opcje w **wstępnie wymagane składniki, okno dialogowe** ręcznie.

|Target .NET Framework|Wybrany program inicjujący pakietów|
|---------------------------|------------------------------------|
|.NET Framework 4 Client Profile|.NET Framework 4 Client Profile<br /><br /> Instalator Windows 3.1|
|Program .NET Framework 4|Program .NET Framework 4<br /><br /> Instalator Windows 3.1|

 Za pomocą [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia *Publish.htm* strony, wygenerowane przez [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Kreatora publikacji wskazuje albo do łącza, który instaluje tylko aplikację lub Link instalowane aplikacji i uruchomionego składniki.

 Jeśli możesz wygenerować za pomocą Kreatora publikacji technologii ClickOnce lub opublikuj stronę w programie Visual Studio, program inicjujący *Setup.exe* zostanie automatycznie zarejestrowany. Jednak jeśli chcesz zarejestrować program inicjujący za pomocą certyfikatu klienta, można podpisać go później.

## <a name="bootstrapping-and-msbuild"></a>Uruchamianie i MSBuild
 Jeśli nie używasz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ale raczej kompilowania aplikacji w wierszu polecenia, można utworzyć [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Inicjowanie aplikacji za pomocą zadania aparatu Microsoft Build Engine (MSBuild). Aby uzyskać więcej informacji, zobacz [generatebootstrapper — zadanie](../msbuild/generatebootstrapper-task.md).

 Jako alternatywę do uruchomienia można wdrożyć wstępnie składników za pomocą system dystrybucji oprogramowania elektronicznych, takich jak Microsoft Systems Management Server (SMS).

## <a name="bootstrapper-setupexe-command-line-arguments"></a>Argumenty wiersza polecenia programu inicjującego (Setup.exe)
 *Setup.exe* generowane przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i zadania programu MSBuild obsługuje następujący zestaw argumentów wiersza polecenia. Wszystkie inne argumenty są przekazywane do Instalatora aplikacji.

 W przypadku zmiany żadnych opcji programu inicjującego należy zmienić bez znaku program inicjujący i później Zaloguj się w pliku programu inicjującego.

| argument wiersza polecenia | Opis |
| - | - |
| **-?, -h, — pomoc** | Wyświetla okno dialogowe pomocy. |
| **— adres url, - componentsurl** | Pokazuje adres URL przechowywanych i składników adresów url dla tego zestawu w górę. |
| **-url =** `location` | Ustawia adres URL, gdzie *Setup.exe* będzie szukał [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji. |
| **-componentsurl =** `location` | Ustawia adres URL, gdzie *Setup.exe* będzie szukał zależności, takich jak .NET Framework. |
| **-homesite=** `true` **&#124;** `false` | Gdy `true`, pliki do pobrania zależności z preferowanych lokalizacji witryny dostawcy. To ustawienie przesłania **- componentsurl** ustawienie. Gdy `false`, pobiera zależności z adresu URL określonego przez **- componentsurl**. |

## <a name="operating-system-support"></a>Obsługa systemów operacyjnych
 Program inicjujący programu Visual Studio nie jest obsługiwana instalacja Server Core systemu Windows Server 2008 lub Windows Server 2008 R2 Server Core, ponieważ zapewniają środowisku niski konserwacji serwera z ograniczoną funkcjonalnością. Opcja instalacji Server Core obsługuje tylko profilu platformy .NET Framework 3.5 Server Core, którego nie można uruchomić funkcji programu Visual Studio, które są zależne od pełny program .NET Framework.

## <a name="see-also"></a>Zobacz także
- [Wybieranie strategii wdrażania ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
- [Wdrażania i zabezpieczeń ClickOnce](../deployment/clickonce-security-and-deployment.md)