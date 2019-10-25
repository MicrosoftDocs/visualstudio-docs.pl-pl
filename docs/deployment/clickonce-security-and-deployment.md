---
title: Bezpieczeństwo i wdrażanie technologii ClickOnce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployment
- deploying applications [ClickOnce]
- ClickOnce deployment
- publishing, ClickOnce
ms.assetid: abab6d34-c3c2-45c1-a8b6-43c7d3131e7a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 88cb136ca4da6f4ca324726edbdaefbd3a27711c
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2019
ms.locfileid: "72806943"
---
# <a name="clickonce-security-and-deployment"></a>Zabezpieczenia i wdrażanie technologii ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] to technologia wdrażania, która umożliwia tworzenie samoaktualizacji aplikacji opartych na systemie Windows, które mogą być instalowane i uruchamiane z minimalnym interakcją użytkownika. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zapewnia pełną obsługę publikowania i aktualizowania aplikacji wdrożonych z technologią ClickOnce, jeśli opracowano projekty z Visual Basic i wizualizacją C#. Aby uzyskać informacje o wdrażaniu aplikacji wizualnych C++ , zobacz [wdrażanie ClickOnce dla aplikacji wizualnych C++ ](/cpp/windows/clickonce-deployment-for-visual-cpp-applications).

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenie nastąpiło trzy główne problemy związane z wdrażaniem:

- **Problemy związane z aktualizowaniem aplikacji.** Za każdym razem, gdy aplikacja zostanie zaktualizowana przy użyciu programu Microsoft Instalator Windows Deployment, użytkownik może zainstalować aktualizację, plik msp i zastosować go do zainstalowanego produktu; Dzięki wdrożeniu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] można udostępniać aktualizacje automatycznie. Pobierane są tylko te części aplikacji, które zostały zmienione, a następnie pełna, zaktualizowana aplikacja zostanie ponownie zainstalowana z nowego folderu Side-by-side.

- **Wpływ na komputer użytkownika.** W przypadku wdrażania Instalator Windows aplikacje często polegają na współużytkowanych składnikach, z możliwością konfliktów wersji; w przypadku wdrażania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] każda aplikacja jest niezależna i nie może zakłócać działania innych aplikacji.

- **Uprawnienia zabezpieczeń.** Wdrożenie Instalator Windows wymaga uprawnień administracyjnych i zezwala na instalację tylko ograniczonej przez użytkownika; wdrożenie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] umożliwia użytkownikom niebędącym administratorami Instalowanie i udzielanie uprawnień dostępu do kodu niezbędnych dla aplikacji.

  W przeszłości te problemy czasami powodowały, że deweloperzy decydują się na utworzenie aplikacji sieci Web zamiast aplikacji opartych na systemie Windows, co może potrwać rozbudowany interfejs użytkownika w celu ułatwienia instalacji. Przy użyciu aplikacji wdrożonych przy użyciu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]można korzystać z zalet obu technologii.

## <a name="what-is-a-clickonce-application"></a>Co to jest aplikacja ClickOnce?
 Aplikacja [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] to dowolny Windows Presentation Foundation ( *. XBAP*), Windows Forms (*exe*), Aplikacja konsolowa (*exe*) lub rozwiązanie Office ( *. dll*) opublikowane przy użyciu technologii [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Aplikację [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] można opublikować na trzy różne sposoby: ze strony sieci Web, z udziału plików sieciowych lub z nośnika, takiego jak dysk CD-ROM. Aplikacja [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] może zostać zainstalowana na komputerze użytkownika końcowego i uruchomiona lokalnie nawet wtedy, gdy komputer jest w trybie offline lub można go uruchomić w trybie online bez konieczności stałego instalowania wszystkich elementów na komputerze użytkownika końcowego. Aby uzyskać więcej informacji, zobacz [Wybieranie strategii wdrażania ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).

 aplikacje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] mogą być samoobsługowe. mogą wyszukiwać nowsze wersje, gdy staną się dostępne, i automatycznie zamieniać wszelkie zaktualizowane pliki. Deweloper może określić zachowanie aktualizacji; Administrator sieci może również kontrolować strategie aktualizacji, na przykład oznaczając aktualizację jako obowiązkową. Aktualizacje mogą być również przywracane do wcześniejszej wersji przez użytkownika końcowego lub przez administratora. Aby uzyskać więcej informacji, zobacz [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).

 Ponieważ [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje są izolowane, instalowane lub uruchamiane przez aplikację [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nie można przerwać istniejących aplikacji. aplikacje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] są samodzielne. Każda aplikacja [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] jest zainstalowana i uruchamiana z bezpiecznej pamięci podręcznej dla poszczególnych aplikacji. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje są uruchamiane w strefach zabezpieczeń Internetu lub intranetu. W razie potrzeby aplikacja może zażądać podwyższonych uprawnień zabezpieczeń. Aby uzyskać więcej informacji, zobacz [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md).

## <a name="how-clickonce-security-works"></a>Jak działa zabezpieczenia technologii ClickOnce
 Podstawowe zabezpieczenia [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] opierają się na certyfikatach, zasadach zabezpieczeń dostępu kodu i w monicie zaufania ClickOnce.

### <a name="certificates"></a>Certyfikaty
 Certyfikaty Authenticode są używane do weryfikowania autentyczności wydawcy aplikacji. W przypadku wdrażania aplikacji przy użyciu technologii Authenticode Technologia ClickOnce pomaga zapobiegać występowaniu przez szkodliwy program jako legalnego programu pochodzącego z ustalonego, wiarygodnego źródła. Opcjonalnie można również użyć certyfikatów do podpisania aplikacji i manifestów wdrożenia, aby udowodnić, że pliki nie zostały naruszone. Aby uzyskać więcej informacji, zobacz [ClickOnce i Authenticode](../deployment/clickonce-and-authenticode.md). Za pomocą certyfikatów można także skonfigurować komputery klienckie w celu uzyskania listy zaufanych wydawców. Jeśli aplikacja pochodzi od zaufanego wydawcy, można ją zainstalować bez żadnej interakcji z użytkownikiem. Aby uzyskać więcej informacji, zobacz [Omówienie wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md).

### <a name="code-access-security"></a>Zabezpieczenia dostępu kodu
 Zabezpieczenia dostępu kodu pomagają ograniczyć dostęp tego kodu do chronionych zasobów. W większości przypadków można wybrać strefy Internet lub lokalny intranet, aby ograniczyć uprawnienia. Użyj strony **zabezpieczenia** w **ProjectDesigner** , aby zażądać odpowiedniej strefy dla aplikacji. Możesz również debugować aplikacje z ograniczonymi uprawnieniami do emulowania środowiska użytkownika końcowego. Aby uzyskać więcej informacji, zobacz [zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).

### <a name="clickonce-trust-prompt"></a>Monit zaufania ClickOnce
 Jeśli aplikacja żąda więcej uprawnień niż zezwala na to, użytkownik końcowy może być monitowany o podjęcie decyzji o zaufaniu. Użytkownik końcowy może zdecydować, czy aplikacje ClickOnce, takie jak Windows Forms aplikacje, aplikacje Windows Presentation Foundatione, aplikacje konsolowe, aplikacje przeglądarki XAML i rozwiązania pakietu Office, są zaufane do uruchomienia. Aby uzyskać więcej informacji, zobacz [How to: Configure the ClickOnce Trust Prompt Behavior](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md).

## <a name="how-clickonce-deployment-works"></a>Jak działa wdrożenie ClickOnce
 Architektura wdrażania podstawowego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] jest oparta na dwóch plikach manifestu XML: manifest aplikacji i manifest wdrożenia. Pliki służą do opisywania, w jaki sposób są instalowane aplikacje ClickOnce, w jaki sposób są one aktualizowane i kiedy są aktualizowane.

### <a name="publish-clickonce-applications"></a>Publikowanie aplikacji ClickOnce
 Manifest aplikacji opisuje samą aplikację. Obejmuje to zestawy, zależności i pliki, które składają się na aplikację, wymagane uprawnienia i lokalizację, w której będą dostępne aktualizacje. Deweloper aplikacji jest autorem manifestu aplikacji przy użyciu Kreatora publikacji w programie Visual Studio lub Narzędzie tworzenia i edycji manifestów (*Mage. exe*) w [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Aby uzyskać więcej informacji, zobacz [jak: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

 Manifest wdrożenia opisuje sposób wdrażania aplikacji. Obejmuje to lokalizację manifestu aplikacji oraz wersję aplikacji, która powinna być uruchamiana przez klientów.

### <a name="deploy-clickonce-applications"></a>Wdrażanie aplikacji ClickOnce
 Po utworzeniu manifest wdrożenia jest kopiowany do lokalizacji wdrożenia. Może to być serwer sieci Web, sieciowy udział plików lub nośnik, taki jak dysk CD. Manifest aplikacji i wszystkie pliki aplikacji są również kopiowane do lokalizacji wdrożenia określonej w manifeście wdrożenia. Może być taka sama jak lokalizacja wdrożenia lub może być inna. W przypadku korzystania z **Kreatora publikacji** w programie Visual Studio operacje kopiowania są wykonywane automatycznie.

### <a name="install-clickonce-applications"></a>Instalowanie aplikacji ClickOnce
 Po wdrożeniu w lokalizacji wdrożenia użytkownicy końcowi mogą pobrać i zainstalować aplikację, klikając ikonę reprezentującą plik manifestu wdrożenia na stronie sieci Web lub w folderze. W większości przypadków użytkownik końcowy zobaczy proste okno dialogowe z prośbą o potwierdzenie instalacji, po której instalacja zostanie zakończona, a aplikacja zostanie uruchomiona bez dodatkowej interwencji. W przypadkach, gdy aplikacja wymaga podwyższonego poziomu uprawnień lub jeśli aplikacja nie jest podpisana przez zaufany certyfikat, okno dialogowe monituje użytkownika o przyznanie uprawnień, zanim będzie można kontynuować instalację. Chociaż instalacje ClickOnce są przeznaczone dla poszczególnych użytkowników, może być wymagane podniesienie uprawnień, jeśli istnieją wymagania wstępne, które wymagają uprawnień administratora. Aby uzyskać więcej informacji o podniesionych uprawnieniach, zobacz [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md).

 Certyfikaty mogą być zaufane na poziomie komputera lub przedsiębiorstwa, dzięki czemu aplikacje ClickOnce podpisane przy użyciu zaufanego certyfikatu mogą być instalowane w trybie dyskretnym. Aby uzyskać więcej informacji na temat zaufanych certyfikatów, zobacz [Omówienie wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md).

 Aplikację można dodać do menu **Start** użytkownika i do grupy **Dodaj lub usuń programy** w **Panelu sterowania**. W przeciwieństwie do innych technologii wdrażania, nic nie jest dodawane do folderu **Program Files** ani do rejestru, a do instalacji nie są wymagane żadne prawa administracyjne.

> [!NOTE]
> Istnieje również możliwość uniemożliwienia dodawania aplikacji do menu **Start** i **dodawania lub usuwania programów** w efekcie, co sprawia, że zachowuje się jak aplikacja sieci Web. Aby uzyskać więcej informacji, zobacz [Wybieranie strategii wdrażania ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).

### <a name="update-clickonce-applications"></a>Aktualizowanie aplikacji ClickOnce
 Gdy deweloperzy aplikacji tworzą zaktualizowaną wersję aplikacji, generują nowy manifest aplikacji i kopiują pliki do lokalizacji wdrożenia — zazwyczaj jest to folder równorzędny do oryginalnego folderu wdrożenia aplikacji. Administrator aktualizuje manifest wdrożenia, aby wskazywał lokalizację nowej wersji aplikacji.

> [!NOTE]
> Aby wykonać te kroki, można użyć **Kreatora publikacji** w programie Visual Studio.

 Oprócz lokalizacji wdrożenia manifest wdrożenia zawiera również lokalizację aktualizacji (stronę sieci Web lub sieciowy udział plików), w której aplikacja sprawdza dostępność zaktualizowanych wersji. właściwości **publikowania** [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] są używane do określania, kiedy i jak często aplikacja ma sprawdzać dostępność aktualizacji. Zachowanie aktualizacji można określić w manifeście wdrożenia lub można je przedstawić jako opcje użytkownika w interfejsie użytkownika aplikacji za pomocą interfejsów API [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Ponadto właściwości **publikacji** mogą być stosowane w celu wprowadzenia aktualizacji jako obowiązkowe lub przywrócenia wcześniejszej wersji. Aby uzyskać więcej informacji, zobacz [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).

### <a name="third-party-installers"></a>Instalatory innych firm
 Możesz dostosować Instalatora ClickOnce, aby instalować składniki innych firm wraz z Twoją aplikacją. Musisz mieć pakiet redystrybucyjny (plik exe lub MSI) i opisać pakiet z niezależnym od języka manifestem produktu i manifestem pakietu specyficznym dla języka. Aby uzyskać więcej informacji, zobacz [Tworzenie pakietów programu inicjującego](../deployment/creating-bootstrapper-packages.md).

## <a name="clickonce-tools"></a>Narzędzia ClickOnce
 W poniższej tabeli przedstawiono narzędzia, których można użyć do generowania, edytowania, podpisywania i ponownego podpisywania aplikacji i manifestów wdrożenia.

|Narzędzie|Opis|
|----------|-----------------|
|[Strona zabezpieczeń, Projektant projektu](../ide/reference/security-page-project-designer.md)|Podpisuje aplikacje i manifesty wdrożenia.|
|[Strona publikowania, Projektant projektu](../ide/reference/publish-page-project-designer.md)|Generuje i edytuje manifesty aplikacji i wdrażania dla Visual Basic i aplikacji C# wizualnych.|
|[Program *Mage. exe* (narzędzie tworzenia i edycji manifestów)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)|Generuje manifesty aplikacji i wdrażania dla aplikacji Visual Basic, wizualizacji C#i wizualizacji. C++<br /><br /> Podpisuje i ponowne podpisuje aplikacje i manifesty wdrożenia.<br /><br /> Można uruchamiać ze skryptów wsadowych i wiersza polecenia.|
|[*MageUI. exe* (narzędzie tworzenia i edycji manifestów, klient graficzny)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)|Generuje i edytuje manifesty aplikacji i wdrożenia.<br /><br /> Podpisuje i ponowne podpisuje aplikacje i manifesty wdrożenia.|
|[GenerateApplicationManifest —, zadanie](../msbuild/generateapplicationmanifest-task.md)|Generuje manifest aplikacji.<br /><br /> Można uruchamiać z programu MSBuild. Aby uzyskać więcej informacji, zobacz [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md).|
|[GenerateDeploymentManifest —, zadanie](../msbuild/generatedeploymentmanifest-task.md)|Generuje manifest wdrożenia.<br /><br /> Można uruchamiać z programu MSBuild. Aby uzyskać więcej informacji, zobacz [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md).|
|[SignFile —, zadanie](../msbuild/signfile-task.md)|Podpisuje aplikacje i manifesty wdrożenia.<br /><br /> Można uruchamiać z programu MSBuild. Aby uzyskać więcej informacji, zobacz [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md).|
|[Microsoft. Build. Tasks. Deployment. ManifestUtilities](/dotnet/api/microsoft.build.tasks.deployment.manifestutilities)|Utwórz własną aplikację w celu wygenerowania manifestów aplikacji i wdrażania.|

 W poniższej tabeli przedstawiono wersję .NET Framework, która jest wymagana do obsługi aplikacji ClickOnce w tych przeglądarkach.

|Przeglądarka|Wersja programu .NET Framework|
|-------------|----------------------------|
|Internet Explorer|2,0, 3,0, 3,5, 3,5 Z DODATKIEM SP1, 4|
|Firefox|2,0 SP1, 3,5 Z DODATKIEM SP1, 4|

## <a name="see-also"></a>Zobacz także
- [Wdrożenie ClickOnce w systemie Windows Vista](../deployment/clickonce-deployment-on-windows-vista.md)
- [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Bezpieczne aplikacje ClickOnce](../deployment/securing-clickonce-applications.md)
- [Wdrażanie składników COM za pomocą technologii ClickOnce](../deployment/deploying-com-components-with-clickonce.md)
- [Tworzenie aplikacji ClickOnce z poziomu wiersza polecenia](../deployment/building-clickonce-applications-from-the-command-line.md)
- [Debuguj aplikacje ClickOnce używające System. Deployment. Application](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)
