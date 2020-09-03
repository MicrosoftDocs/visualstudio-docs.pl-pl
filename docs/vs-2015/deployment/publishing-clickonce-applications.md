---
title: Publikowanie aplikacji ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 209aac56f4648554ce619cbe31cef19a8ab1fed7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85531797"
---
# <a name="publishing-clickonce-applications"></a>Publikowanie aplikacji ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas publikowania [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji po raz pierwszy, publikowanie właściwości można ustawić za pomocą Kreatora publikacji. Tylko niektóre właściwości są dostępne w Kreatorze; wszystkie inne właściwości są ustawione na wartości domyślne.  
  
 Kolejne zmiany właściwości publikowania są wprowadzane na stronie **Opublikuj** w **projektancie projektu**.  
  
## <a name="publish-wizard"></a>Kreator publikacji  
 Aby ustawić podstawowe ustawienia publikowania aplikacji, można użyć Kreatora publikacji. Obejmuje to następujące właściwości publikowania:  
  
- Lokalizacja folderu publikowania — gdzie program Visual Studio skopiuje pliki (komputer lokalny, sieciowy udział plików, serwer FTP lub witryna sieci Web)  
  
- Lokalizacja folderu instalacji — z którego użytkownicy końcowi będą instalować (sieciowy udział plików, serwer FTP, witryna sieci Web, dysk CD/DVD)  
  
- Dostępność w trybie online lub offline — Jeśli użytkownicy końcowi mają dostęp do aplikacji z lub bez połączenia sieciowego  
  
- Częstotliwość aktualizacji — jak często aplikacja sprawdza dostępność nowych aktualizacji.  
  
  Aby uzyskać więcej informacji, zobacz [jak: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
## <a name="publish-page"></a>Strona publikowania  
 Strona **Publikowanie** **projektanta projektu** służy do konfigurowania właściwości wdrażania ClickOnce. W poniższej tabeli przedstawiono listę tematów  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Porady: określanie lokalizacji kopiowania plików przez program Visual Studio](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)|Opisuje sposób ustawiania miejsca, w którym program Visual Studio umieszcza pliki aplikacji i manifesty.|  
|[Instrukcje: określanie lokalizacji, z której użytkownicy końcowi będą przeprowadzać instalacje](../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)|Opisuje sposób ustawiania lokalizacji, w której użytkownicy przejdą do pobierania i instalowania aplikacji.|  
|[Instrukcje: określanie trybu offline lub online instalowania za pomocą technologii ClickOnce](../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)|Opisuje, jak określić, czy aplikacja będzie dostępna w trybie offline, czy w trybie online.|  
|[Instrukcje: ustawienie wersji publikacji technologii ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md)|Opisuje sposób ustawiania właściwości **wersji publikacji** ClickOnce, która określa, czy publikowana aplikacja będzie traktowana jako aktualizacja.|  
|[Instrukcje: automatyczne zwiększenie wersji publikacji ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)|Opisuje, jak automatycznie zwiększać numer poprawki **PublishVersion** przy każdym publikowaniu aplikacji.|  
  
 Aby uzyskać więcej informacji, zobacz [Publikowanie strony, Projektant projektu](../ide/reference/publish-page-project-designer.md)  
  
### <a name="application-files-dialog-box"></a>Okno dialogowe pliki aplikacji  
 To okno dialogowe pozwala określić, w jaki sposób pliki w projekcie są klasyfikowane do publikowania, pobierania dynamicznego i aktualizowania. Zawiera ona siatkę, która wyświetla listę plików projektu, które nie są domyślnie wykluczone lub które mają grupę pobierania.  
  
 Aby wykluczać pliki, oznaczyć pliki jako pliki danych lub wymagania wstępne oraz utworzyć grupy plików dla instalacji warunkowej w interfejsie użytkownika programu Visual Studio, zobacz [How to: Określanie, które pliki są publikowane przez ClickOnce](../deployment/how-to-specify-which-files-are-published-by-clickonce.md). Możesz również oznaczyć pliki danych za pomocą Mage.exe. Aby uzyskać więcej informacji, zobacz [jak to zrobić: Dołączanie pliku danych do aplikacji ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
### <a name="prerequisites-dialog-box"></a>Wstępnie wymagane składniki — Okno dialogowe  
 To okno dialogowe określa, które składniki wymagane wstępnie są zainstalowane, a także ich instalację. Aby uzyskać więcej informacji, zobacz [temat How to: Install Preinstallations with ClickOnce Application](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md) i [wymagania wstępne](../ide/reference/prerequisites-dialog-box.md).  
  
### <a name="application-updates-dialog-box"></a>Okno dialogowe aktualizacje aplikacji  
 To okno dialogowe określa, jak instalacja aplikacji ma sprawdzać dostępność aktualizacji. Aby uzyskać więcej informacji, zobacz [jak: Zarządzanie aktualizacjami aplikacji ClickOnce](../deployment/how-to-manage-updates-for-a-clickonce-application.md).  
  
### <a name="publish-options-dialog-box"></a>Opcje publikowania — okno dialogowe  
 Opcje publikowania okna dialogowego określa opcje wdrażania aplikacji.  
  
|Tytuł|Opis|
|-|-|  
|[Porady: zmienianie języka publikacji dla aplikacji ClickOnce](../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)|Opisuje, jak określić język i kulturę w celu dopasowania do wersji zlokalizowanej.|  
|[Instrukcje: określanie nazwy menu Start dla aplikacji ClickOnce](../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)|Opisuje, jak zmienić nazwę wyświetlaną aplikacji ClickOnce.|  
|[Instrukcje: określanie linku do pomocy technicznej](../deployment/how-to-specify-a-link-for-technical-support.md)|Opisuje sposób ustawiania właściwości **adres URL pomocy technicznej** , która identyfikuje stronę sieci Web lub udział plików, w którym użytkownicy mogą przechodzić w celu uzyskania informacji o aplikacji.|  
|[Porady: określanie adresu URL pomocy technicznej dla indywidualnych wstępnie wymaganych składników wdrożenia ClickOnce](../deployment/how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment.md)|Pokazano, jak ręcznie zmodyfikować manifest aplikacji w taki sposób, aby obejmował poszczególne adresy URL pomocy technicznej dla każdego wymaganego elementu.|  
|[Instrukcje: określanie strony publikowania dla aplikacji ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)|Opisuje sposób generowania i publikowania domyślnej strony sieci Web (publish.htm) wraz z aplikacją|  
|[Instrukcje: dostosowywanie domyślnej strony internetowej technologii ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)|Opisuje sposób dostosowywania strony sieci Web, która jest automatycznie generowana i publikowana razem z aplikacją.|  
|[Porady: włączenie funkcji AutoStart dla instalacji z dysku CD](../deployment/how-to-enable-autostart-for-cd-installations.md)|Opisuje sposób włączania autostartu, dzięki czemu aplikacja ClickOnce jest uruchamiana automatycznie po wstawieniu nośnika.|  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Instrukcje: tworzenie skojarzeń plików dla aplikacji ClickOnce](../deployment/how-to-create-file-associations-for-a-clickonce-application.md)|Opisuje sposób dodawania obsługi rozszerzenia nazwy pliku do aplikacji ClickOnce.|  
|[Porady: pobieranie informacji o ciągu zapytania w aplikacji ClickOnce w trybie online](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)|Pokazuje, jak pobrać parametry przesłane w adresie URL używanym do uruchamiania aplikacji ClickOnce.|  
|[Instrukcje: wyłączanie aktywacji adresu URL aplikacji ClickOnce za pomocą Projektanta](../deployment/how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer.md)|Opisuje, jak zmusić użytkowników do uruchamiania aplikacji z menu **Start** za pomocą projektanta.|  
|[Porady: wyłączanie aktywacji adresu URL aplikacji ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md)|Opisuje, jak zmusić użytkowników do uruchamiania aplikacji z menu **Start** .|  
|[Wskazówki: pobieranie zestawów na żądanie przy użyciu wdrażania interfejsu API ClickOnce za pomocą Projektanta](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md)|Wyjaśnia, jak pobierać zestawy aplikacji tylko wtedy, gdy są one najpierw używane przez aplikację przy użyciu narzędzia Projektant.|  
|[Przewodnik: pobieranie zestawów na żądanie przy użyciu wdrażania interfejsu API ClickOnce](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api.md)|Wyjaśnia, jak pobierać zestawy aplikacji tylko wtedy, gdy są one najpierw używane przez aplikację.|  
|[Wskazówki: pobieranie zestawów satelickich na żądanie przy użyciu wdrażania interfejsu API ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)|W tym artykule opisano sposób oznaczania zestawów satelickich jako opcjonalnych i pobrania tylko zestawu, który jest wymagany przez komputer kliencki dla bieżących ustawień kultury.|  
|[Wskazówki: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)|Wyjaśnia, jak używać narzędzi .NET Framework do wdrażania aplikacji ClickOnce.|  
|[Przewodnik: ręczne wdrażanie aplikacji ClickOnce, które nie wymagają ponownego podpisywania i zachowują informacje o znakowaniu](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required?view=vs-2015)|Wyjaśnia, jak używać narzędzi .NET Framework do wdrażania aplikacji ClickOnce bez ponownego podpisywania manifestów.|  
|[NIB: jak zoptymalizować aplikację dla określonego typu procesora CPU](https://msdn.microsoft.com/294a75d2-4279-4b72-8298-2bea05be907a)|Wyjaśnia sposób publikowania dla procesora 64-bitowego przez zmianę **docelowej właściwości procesora CPU** lub **docelowej platformy** w projekcie.|  
|[Przewodnik: Włączanie aplikacji ClickOnce do uruchamiania w wielu .NET Framework wersjach](https://msdn.microsoft.com/7f4383af-ed87-4853-b4d4-02a3967a5fd9)|Wyjaśnia, w jaki sposób umożliwić aplikacji ClickOnce zainstalowanie i uruchomienie na wielu wersjach platformy NET Framework.|  
|[Przewodnik: tworzenie niestandardowego Instalatora dla aplikacji ClickOnce](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md)|Wyjaśnia, jak utworzyć instalatora niestandardowego w celu zainstalowania aplikacji ClickOnce.|  
|[Instrukcje: publikowanie aplikacji WPF przy użyciu włączonej funkcji stylów wizualnych](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md)|Zawiera instrukcje krok po kroku dotyczące rozwiązywania błędu, który pojawia się podczas próby opublikowania aplikacji WPF z włączonymi stylami wizualizacji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo i wdrażanie technologii ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [ClickOnce — Odwołanie](../deployment/clickonce-reference.md)
