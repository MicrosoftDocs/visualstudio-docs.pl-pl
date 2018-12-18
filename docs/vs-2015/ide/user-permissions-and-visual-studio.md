---
title: Uprawnienia użytkownika | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
ms.assetid: 70485ed7-6342-41bf-8250-7a6826e21b98
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 83a45aaebbf621a5ae84a0ae4bdf3379697a47e9
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062861"
---
# <a name="user-permissions-and-visual-studio"></a>Uprawnienia użytkownika i program Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ze względów bezpieczeństwa należy uruchamiać Visual Studio jako zwykły użytkownik w każdym przypadku, gdy jest to możliwe.

> [!WARNING]
>  Należy również pamiętać, aby nie kompilować, uruchamiać lub debugować żadnego rozwiązania Visual Studio, które nie pochodzi od zaufanej osoby lub z zaufanej lokalizacji.

 Jako zwykły użytkownik możesz zrobić w środowisku IDE programu Visual Studio prawie wszystko, ale musisz mieć uprawnienia administratora, aby wykonać następujące zadania:

|Obszar|Zadanie|Więcej informacji|
|----------|----------|--------------------------|
|Instalacja|Instalowanie programu Visual Studio.|[Instalowanie programu Visual Studio 2015](../install/install-visual-studio-2015.md)|
||Aktualizacja z wersji próbnej Visual Studio.|[Instrukcje: aktualizacja z wersji próbnej wersji programu Visual Studio](../install/how-to-upgrade-from-a-trial-edition-of-visual-studio.md)|
||Instalowanie, aktualizowanie lub usuwanie lokalnej zawartości Pomocy.|[Instalowanie zawartości lokalnej i zarządzanie nią](../ide/install-and-manage-local-content.md)|
|Typy aplikacji|Tworzenie rozwiązań dla programu SharePoint 2010.|[Wymagania związane z opracowywaniem rozwiązań SharePoint](http://msdn.microsoft.com/library/ae8ff69d-4540-4380-ab0b-845f7108e89c)|
||Pobieranie licencji deweloperskiej dla [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)].|[Uzyskaj licencję dewelopera (aplikacje Windows Store)](http://go.microsoft.com/fwlink/?LinkID=241313)|
|Przybornik|Dodawanie klasycznych formantów COM do **przybornika**.|[Korzystanie z przybornika](../ide/using-the-toolbox.md)|
|Dodatki|Instalowanie i używanie dodatków, które zostały napisane przy użyciu klasycznego modelu COM w IDE.|[Tworzenie dodatków i kreatorów](http://msdn.microsoft.com/library/c5a47c21-6668-4de3-898d-afa969317e73)|
|Kompilowanie|Używanie zdarzeń mających miejsce po kompilacji, które rejestrują składnik.|[Ogólne informacje o niestandardowych krokach budowania lub zdarzeniach kompilacji](http://msdn.microsoft.com/library/beb2f017-3e9f-4b2c-9b57-2572fd2628e4)|
||Włączanie etapu rejestracji podczas kompilowania projektów języka C++.|[Ogólne informacje o niestandardowych krokach budowania lub zdarzeniach kompilacji](http://msdn.microsoft.com/library/beb2f017-3e9f-4b2c-9b57-2572fd2628e4)|
|Debugowanie|Debugowanie aplikacji, które działają z podwyższonymi uprawnieniami.|[Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)|
||Debugowanie aplikacji, które działają na innym koncie użytkownika, takich jak witryny sieci Web programu ASP.NET.|[Debugowanie aplikacji ASP.NET i AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)|
||Debugowanie w strefie dla aplikacji przeglądarki XAML (XBAP).|[Host WPF (PresentationHost.exe)](http://msdn.microsoft.com/library/3215bfa1-722c-4ac8-a7c5-bdd02d30afbd)|
||Używanie emulatora do debugowania projektów usług w chmurze dla systemu Microsoft Azure.|[Debugowanie usługi Chmurowej w programie Visual Studio](http://go.microsoft.com/fwlink/?LinkId=266725)|
||Konfigurowanie zapory do zdalnego debugowania.|[Konfigurowanie narzędzi zdalnych na urządzeniu](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)|
|Narzędzia wydajności|Profilowanie aplikacji.|[Profilowanie wydajności — przewodnik dla początkujących](../profiling/beginners-guide-to-performance-profiling.md)|
|wdrażania|Wdrażanie aplikacji internetowej do usług Internet Information Services (IIS) na komputerze lokalnym.|[Wdrażanie aplikacji sieci Web ASP.NET u dostawcy hostingu przy użyciu programu Visual Studio lub Visual Web Developer: Wdrażanie w usługach IIS jako środowisku testowym](http://go.microsoft.com/fwlink/?LinkId=266478)|
|Dostarczanie opinii do firmy Microsoft|Zmiana sposobu uczestnictwa w programie konsumenckim programu Visual Studio.|[Porady: wysyłanie opinii](../misc/how-to-send-feedback-about-visual-studio.md)|

## <a name="running-visual-studio-as-an-administrator"></a>Uruchamianie programu Visual Studio jako administrator
 Możesz uruchomić program Visual Studio z uprawnieniami administracyjnymi przy każdym uruchomieniu IDE lub zmodyfikować skrót aplikacji, aby program był zawsze uruchamiany z uprawnieniami administracyjnymi. Aby uzyskać więcej informacji, zobacz Pomoc systemu Windows.

#### <a name="to-run-visual-studio-with-administrative-permissions-on-includewin8includeswin8-mdmd-includewin81includeswin81-mdmd-includewinserver8includeswinserver8-mdmd-or-includewinblueserver2includeswinblue-server-2-mdmd"></a>Aby uruchomić program Visual Studio z uprawnieniami administracyjnymi [!INCLUDE[win8](../includes/win8-md.md)], [!INCLUDE[win81](../includes/win81-md.md)], [!INCLUDE[winserver8](../includes/winserver8-md.md)], lub [!INCLUDE[winblue_server_2](../includes/winblue-server-2-md.md)]

1.  Na **Start** ekranu, wpisz **programu Visual Studio**. Powinna się pojawić wersja lub wersje programu Visual Studio, które zostały zainstalowane.

2.  Wybierz wersję programu Visual Studio, którą chcesz uruchomić, a następnie wywołaj menu podręczne (wyświetla się u dołu ekranu). Wybierz **Uruchom jako administrator**.

     Po uruchomieniu programu Visual Studio **(Administrator)** pojawia się po nazwie produktu na pasku tytułu.

#### <a name="to-run-visual-studio-with-administrative-permissions-on-includewin7includeswin7-mdmd-or-includewinsvr08r2includeswinsvr08-r2-mdmd"></a>Aby uruchomić program Visual Studio z uprawnieniami administracyjnymi [!INCLUDE[win7](../includes/win7-md.md)] lub [!INCLUDE[winsvr08_r2](../includes/winsvr08-r2-md.md)]

1.  Na **Start** menu, wybierz **wszystkie programy**.

2.  W **programu Microsoft Visual Studio** *wersji* wybierz folder **programu Visual Studio** *wersji* Otwórz menu skrótów, a następnie wybierz  **Uruchom jako administrator**.

     Po uruchomieniu programu Visual Studio **(Administrator)** pojawia się po nazwie produktu na pasku tytułu.

## <a name="see-also"></a>Zobacz też
 [Przenoszenie, migrowanie i uaktualnianie projektów programu Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md) [instalowania programu Visual Studio 2015](../install/install-visual-studio-2015.md)
