---
title: Publikowanie aplikacji ClickOnce | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Options
- Microsoft.VisualStudio.Publish.ClickOnceProvider.PublishWizard.Help
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, publishing
- ClickOnce applications, publishing
- applications [Visual Studio], ClickOnce deployment
- deploying applications [ClickOnce], publishing ClickOnce applications
ms.assetid: eb6dfe79-f54c-4331-8e36-073688e70973
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 52a6e91783a66adc09046ef6f193074e22c8dc6f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53823492"
---
# <a name="publishing-clickonce-applications"></a>Publikowanie aplikacji ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas publikowania [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] właściwości publikowania aplikacji po raz pierwszy, można ustawić za pomocą Kreatora publikacji. Tylko niektóre właściwości są dostępne w Kreatorze; wszystkie pozostałe właściwości są ustawione na wartości domyślne.  
  
 Kolejne zmiany do publikowania właściwości są dokonywane na **Publikuj** strony w **projektanta projektu**.  
  
## <a name="publish-wizard"></a>Kreator publikacji  
 W Kreatorze publikacji można użyć do skonfigurowania podstawowych ustawień do publikowania aplikacji. Dane te obejmują następujące właściwości publikacji:  
  
- Lokalizacja folderu publikowania — gdzie Visual Studio skopiuje pliki (komputer lokalny, sieciowego udziału plików, serwer FTP lub witryny sieci Web)  
  
- Lokalizacja folderu instalacji — gdzie użytkownicy będą instalować z (sieciowym udziale plików, serwer FTP, witryny sieci Web, dysk CD/DVD)  
  
- Online lub Offline dostępność — Jeśli użytkownicy końcowi mogą uzyskiwać dostęp do aplikacji, z lub bez połączenia sieciowego  
  
- Zaktualizuj częstotliwość — jak często Aplikacja sprawdza dostępność nowych aktualizacji.  
  
  Aby uzyskać więcej informacji, zobacz [jak: Publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
## <a name="publish-page"></a>Strona publikowania  
 **Publikuj** strony **projektanta projektu** służy do konfigurowania właściwości dla wdrażania ClickOnce. Poniższa tabela zawiera listę tematów  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: Określanie lokalizacji kopiowania plików w programie Visual Studio](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)|W tym artykule opisano sposób ustawiania, gdzie program Visual Studio umieści pliki aplikacji i manifestów.|  
|[Instrukcje: Określ lokalizację, w której użytkownicy końcowi będą przeprowadzać instalacje](../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)|Opisuje sposób ustawiania lokalizacji, z którego użytkownicy używają do pobrania i zainstalowania aplikacji.|  
|[Instrukcje: Określanie ClickOnce w trybie Offline lub Online instalowania tryb](../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)|W tym artykule opisano, jak określić, czy aplikacja będzie dostępna w trybie offline lub online.|  
|[Instrukcje: ClickOnce ustawienie wersji publikacji](../deployment/how-to-set-the-clickonce-publish-version.md)|W tym artykule opisano sposób ustawiania ClickOnce **opublikować wersję** właściwość, która określa, czy w przypadku publikowania aplikacji będzie traktowane jako aktualizację.|  
|[Instrukcje: Automatyczne ClickOnce zwiększenie wersji publikacji](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)|Opisuje sposób automatycznie zwiększ numer poprawki **PublishVersion** każdorazowo, możesz opublikować aplikację.|  
  
 Aby uzyskać więcej informacji, zobacz [strona publikowania, Projektant projektu](../ide/reference/publish-page-project-designer.md)  
  
### <a name="application-files-dialog-box"></a>Okno dialogowe pliki aplikacji  
 To okno dialogowe umożliwia określenie, jak pliki w projekcie są podzielone na publikowanie, dynamicznego pobierania i aktualizowania. Zawiera ona siatki, który wyświetla listę plików projektu, które nie zostały wyłączone domyślnie, lub które mają grupa pobierania.  
  
 Aby wykluczyć pliki, oznaczyć pliki jako pliki danych lub wymagania wstępne i tworzyć grupy plików instalacji warunkowe w interfejsie użytkownika programu Visual Studio, zobacz [jak: Określanie plików publikowanych za pomocą technologii ClickOnce](../deployment/how-to-specify-which-files-are-published-by-clickonce.md). Można również oznaczyć pliki danych przy użyciu Mage.exe. Aby uzyskać więcej informacji, zobacz [jak: Uwzględnianie pliku danych w aplikacji ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
### <a name="prerequisites-dialog-box"></a>Wstępnie wymagane składniki — Okno dialogowe  
 To okno dialogowe określa, które wstępnie wymagane składniki są zainstalowane, a także jak są one zainstalowane. Aby uzyskać więcej informacji, zobacz [jak: Instalowanie wymagań wstępnych przy użyciu aplikacji ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md) i [wstępnie wymagane składniki, okno dialogowe](../ide/reference/prerequisites-dialog-box.md).  
  
### <a name="application-updates-dialog-box"></a>Okno dialogowe aktualizacji aplikacji  
 To okno dialogowe określa, jak instalacja aplikacji ma sprawdzać dostępność aktualizacji. Aby uzyskać więcej informacji, zobacz [jak: Zarządzanie aktualizacjami dla aplikacji ClickOnce](../deployment/how-to-manage-updates-for-a-clickonce-application.md).  
  
### <a name="publish-options-dialog-box"></a>Okno dialogowe Opcje publikowania  
 Okno dialogowe opcji publikowania Określa opcje wdrażania aplikacji.  
  
|||  
|-|-|  
|[Instrukcje: Zmiana języka publikacji dla aplikacji ClickOnce](../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)|Opisuje sposób określania języka i kultury, aby dopasować zlokalizowanej wersji.|  
|[Instrukcje: Określanie nazwy Menu Start dla aplikacji ClickOnce](../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)|W tym artykule opisano, jak zmienić nazwę wyświetlaną dla aplikacji ClickOnce.|  
|[Instrukcje: Określanie Linku do pomocy technicznej](../deployment/how-to-specify-a-link-for-technical-support.md)|W tym artykule opisano sposób ustawiania **adres URL pomocy technicznej** właściwość, która identyfikuje strony sieci Web lub udziału plików, gdzie użytkownicy mogą przejść w celu uzyskania informacji o aplikacji.|  
|[Instrukcje: Określ adres URL pomocy technicznej dla indywidualnych wstępnie wymaganych składników wdrożenia ClickOnce](../deployment/how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment.md)|Pokazano, jak ręcznie zmienić manifest aplikacji, aby uwzględnić adresy URL poszczególnych pomocy technicznej dla poszczególnych wymagań wstępnych.|  
|[Instrukcje: Określanie strony publikowania dla aplikacji ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)|W tym artykule opisano sposób generowania i opublikować domyślna strona internetowa (publish.htm) wraz z aplikacji|  
|[Instrukcje: Dostosowywanie ClickOnce domyślnej strony sieci Web](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)|Opisuje sposób dostosowywania strony sieci Web, która jest automatycznie generowany i opublikowanych wraz z aplikacji.|  
|[Instrukcje: Włączenie funkcji AutoStart dla instalacji z dysku CD](../deployment/how-to-enable-autostart-for-cd-installations.md)|W tym artykule opisano, jak włączyć automatyczne uruchamianie aplikacji ClickOnce jest uruchamiane automatycznie, gdy znajduje się nośnik.|  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: Tworzenie skojarzeń plików dla aplikacji ClickOnce](../deployment/how-to-create-file-associations-for-a-clickonce-application.md)|W tym artykule opisano sposób dodawania obsługi rozszerzenia nazw plików dla aplikacji ClickOnce.|  
|[Instrukcje: Pobieranie informacji o ciągu zapytania w aplikacji ClickOnce w trybie Online](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)|Pokazuje, jak pobrać parametry przekazywane w adresie URL, używanych do uruchamiania aplikacji ClickOnce.|  
|[Instrukcje: Wyłączanie aktywacji adresu URL aplikacji ClickOnce przy użyciu narzędzia Projektant](../deployment/how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer.md)|Opisuje sposób wymuszenie użytkowników, aby uruchomić aplikację z **Start** menu przy użyciu projektanta.|  
|[Instrukcje: Wyłączanie aktywacji adresu URL aplikacji ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md)|Opisuje sposób wymuszenie użytkowników, aby uruchomić aplikację z **Start** menu.|  
|[Przewodnik: Pobieranie zestawów na żądanie z wdrożeniem ClickOnce interfejsu API przy użyciu narzędzia Projektant](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md)|Wyjaśnia, jak można pobrać zestawów aplikacji tylko wtedy, gdy najpierw są one używane przez aplikację za pomocą projektanta.|  
|[Przewodnik: Pobieranie zestawów na żądanie przy użyciu wdrażania interfejsu API ClickOnce](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api.md)|Wyjaśnia, jak można pobrać zestawów aplikacji tylko wtedy, gdy najpierw są one używane przez aplikację.|  
|[Przewodnik: Pobieranie zestawów satelickich na żądanie przy użyciu wdrażania interfejsu API ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)|Opisuje sposób oznaczania zestawy satelickie jako opcjonalną i Pobierz tylko zestaw na komputerze klienckim musi uzyskać bieżące ustawienia kultury.|  
|[Przewodnik: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)|W tym temacie omówiono wdrażanie aplikacji ClickOnce przy użyciu narzędzia .NET Framework.|  
|[Przewodnik: Ręczne wdrażanie aplikacji ClickOnce, które nie wymagają ponownego podpisywania i zachowują informacje o znakowaniu](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required?view=vs-2015)|Wyjaśnia, jak wdrożyć aplikację ClickOnce bez ponownego podpisywania manifestów za pomocą narzędzia .NET Framework.|  
|[NIB: Instrukcje: Optymalizowanie aplikacji dla określonego typu procesora CPU](http://msdn.microsoft.com/en-us/294a75d2-4279-4b72-8298-2bea05be907a)|Opisano sposób publikowania dla 64-bitowy procesor, zmieniając **Procesora docelowego** lub **platformę docelową** właściwość w projekcie.|  
|[Przewodnik: Włączanie aplikacji ClickOnce uruchomić przy użyciu wielu wersji programu .NET Framework](http://msdn.microsoft.com/en-us/7f4383af-ed87-4853-b4d4-02a3967a5fd9)|Wyjaśnia, jak umożliwić aplikacji ClickOnce zainstalować i uruchomić przy użyciu wielu wersji programu .NET Framework.|  
|[Przewodnik: Tworzenie niestandardowego Instalatora dla aplikacji ClickOnce](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md)|Wyjaśnia sposób tworzenia niestandardowego Instalatora, aby zainstalować aplikację ClickOnce.|  
|[Instrukcje: Publikowanie aplikacji WPF przy użyciu włączonej funkcji stylów wizualnych](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md)|Zawiera instrukcje krok po kroku, aby rozwiązać błąd, który jest wyświetlany, gdy spróbujesz opublikować aplikację WPF, która ma włączonej funkcji stylów wizualnych.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrażania i zabezpieczeń ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Dokumentacja ClickOnce](../deployment/clickonce-reference.md)



