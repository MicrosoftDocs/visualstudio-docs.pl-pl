---
title: Uprawnienia użytkownika | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
ms.assetid: 70485ed7-6342-41bf-8250-7a6826e21b98
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aa01cb77e8a003438721984da13f46de350104ea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918993"
---
# <a name="user-permissions-and-visual-studio"></a>Uprawnienia użytkownika i program Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ze względów bezpieczeństwa należy uruchamiać Visual Studio jako zwykły użytkownik w każdym przypadku, gdy jest to możliwe.

> [!WARNING]
> Należy również pamiętać, aby nie kompilować, uruchamiać lub debugować żadnego rozwiązania Visual Studio, które nie pochodzi od zaufanej osoby lub z zaufanej lokalizacji.

 Jako zwykły użytkownik możesz zrobić w środowisku IDE programu Visual Studio prawie wszystko, ale musisz mieć uprawnienia administratora, aby wykonać następujące zadania:

|Obszar|Zadanie|Więcej informacji|
|----------|----------|--------------------------|
|Instalacja|Instalowanie programu Visual Studio.|[Instalowanie programu Visual Studio 2015](../install/install-visual-studio-2015.md)|
||Aktualizacja z wersji próbnej Visual Studio.|[Instrukcje: aktualizacja z wersji próbnej wersji programu Visual Studio](../install/how-to-upgrade-from-a-trial-edition-of-visual-studio.md)|
||Instalowanie, aktualizowanie lub usuwanie lokalnej zawartości Pomocy.|[Instalowanie zawartości lokalnej i zarządzanie nią](../ide/install-and-manage-local-content.md)|
|Typy aplikacji|Tworzenie rozwiązań dla programu SharePoint 2010.|[Wymagania związane z opracowywaniem rozwiązań SharePoint](https://msdn.microsoft.com/library/ae8ff69d-4540-4380-ab0b-845f7108e89c)|
||Uzyskiwanie licencji dewelopera dla programu [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)] .|[Uzyskaj licencję dewelopera (aplikacje do sklepu Windows)](https://msdn.microsoft.com/library/windows/apps/hh974578.aspx)|
|Przybornik|Dodawanie klasycznych kontrolek COM do **przybornika**.|[Korzystanie z przybornika](../ide/using-the-toolbox.md)|
|Dodatki|Instalowanie i używanie dodatków, które zostały napisane przy użyciu klasycznego modelu COM w IDE.|[Tworzenie dodatków i kreatorów](https://msdn.microsoft.com/library/c5a47c21-6668-4de3-898d-afa969317e73)|
|Kompilowanie|Używanie zdarzeń mających miejsce po kompilacji, które rejestrują składnik.|[Ogólne informacje o niestandardowych krokach budowania lub zdarzeniach kompilacji](https://msdn.microsoft.com/library/beb2f017-3e9f-4b2c-9b57-2572fd2628e4)|
||Włączanie etapu rejestracji podczas kompilowania projektów języka C++.|[Ogólne informacje o niestandardowych krokach budowania lub zdarzeniach kompilacji](https://msdn.microsoft.com/library/beb2f017-3e9f-4b2c-9b57-2572fd2628e4)|
|Debugowanie|Debugowanie aplikacji, które działają z podwyższonymi uprawnieniami.|[Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)|
||Debugowanie aplikacji, które działają na innym koncie użytkownika, takich jak witryny sieci Web programu ASP.NET.|[Debugowanie aplikacji ASP.NET i AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)|
||Debugowanie w strefie dla aplikacji przeglądarki XAML (XBAP).|[Host WPF (PresentationHost.exe)](https://msdn.microsoft.com/library/3215bfa1-722c-4ac8-a7c5-bdd02d30afbd)|
||Używanie emulatora do debugowania projektów usług w chmurze dla Microsoft Azure.|[Debugowanie usługi w chmurze w programie Visual Studio](../azure/vs-azure-tools-debug-cloud-services-virtual-machines.md)|
||Konfigurowanie zapory do zdalnego debugowania.|[Konfigurowanie narzędzi zdalnych na urządzeniu](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)|
|Narzędzia wydajności|Profilowanie aplikacji.|[Początkujący Przewodnik dotyczący profilowania wydajności](../profiling/beginners-guide-to-performance-profiling.md)|
|Wdrożenie|Wdrażanie aplikacji internetowej do usług Internet Information Services (IIS) na komputerze lokalnym.|[Wdrażanie aplikacji sieci Web ASP.NET dla dostawcy hostingu przy użyciu programu Visual Studio lub Visual Web Developer: wdrażanie w usługach IIS jako środowisko testowe](https://www.asp.net/web-forms/tutorials/deployment/deployment-to-a-hosting-provider/Deployment-to-a-Hosting-Provider-Deploying-to-IIS-as-a-Test-Environment-5-of-12)|
|Dostarczanie opinii do firmy Microsoft|Zmiana sposobu uczestnictwa w programie konsumenckim programu Visual Studio.|[Instrukcje: wysyłanie opinii](../misc/how-to-send-feedback-about-visual-studio.md)|

## <a name="running-visual-studio-as-an-administrator"></a>Uruchamianie programu Visual Studio jako administrator
 Możesz uruchomić program Visual Studio z uprawnieniami administracyjnymi przy każdym uruchomieniu IDE lub zmodyfikować skrót aplikacji, aby program był zawsze uruchamiany z uprawnieniami administracyjnymi. Aby uzyskać więcej informacji, zobacz Pomoc systemu Windows.

#### <a name="to-run-visual-studio-with-administrative-permissions-on-win8-win81-winserver8-or-winblue_server_2"></a>Aby uruchomić program Visual Studio z uprawnieniami administracyjnymi w systemach [!INCLUDE[win8](../includes/win8-md.md)] ,, [!INCLUDE[win81](../includes/win81-md.md)] [!INCLUDE[winserver8](../includes/winserver8-md.md)] lub [!INCLUDE[winblue_server_2](../includes/winblue-server-2-md.md)]

1. Na ekranie **startowym** wpisz **Visual Studio**. Powinna się pojawić wersja lub wersje programu Visual Studio, które zostały zainstalowane.

2. Wybierz wersję programu Visual Studio, którą chcesz uruchomić, a następnie wywołaj menu podręczne (wyświetla się u dołu ekranu). Wybierz **Uruchom jako administrator**.

     Po uruchomieniu programu Visual Studio **(Administrator)** pojawia się po nazwie produktu na pasku tytułu.

#### <a name="to-run-visual-studio-with-administrative-permissions-on-win7-or-winsvr08_r2"></a>Aby uruchomić program Visual Studio z uprawnieniami administracyjnymi w systemie [!INCLUDE[win7](../includes/win7-md.md)] lub [!INCLUDE[winsvr08_r2](../includes/winsvr08-r2-md.md)]

1. W menu **Start** wybierz polecenie **Wszystkie programy**.

2. W folderze **Microsoft Visual Studio** *wersja* Microsoft Visual Studio wybierz opcję *wersja* **programu Visual Studio** , otwórz menu skrótów, a następnie wybierz polecenie **Uruchom jako administrator**.

     Po uruchomieniu programu Visual Studio **(Administrator)** pojawia się po nazwie produktu na pasku tytułu.

## <a name="see-also"></a>Zobacz też
 Przenoszenie [, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md) [Instalowanie programu Visual Studio 2015](../install/install-visual-studio-2015.md)
