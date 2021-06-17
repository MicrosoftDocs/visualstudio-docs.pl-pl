---
title: Tworzenie rozwiązań SharePoint | Microsoft Docs
description: Opracowywanie rozwiązań programu SharePoint. Poznaj elementy projektu programu SharePoint. Informacje o właściwościach projektu i elementu projektu programu SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
f1_keywords:
- VS.SharePointTools.Project.ProjectProperties
- VS.SharePointTools.Project.ProjectItemProperties
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, overview
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f839f4148054b4e10a7fc1703aa8f03549bdbf36
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112899"
---
# <a name="develop-sharepoint-solutions"></a>Opracowywanie rozwiązań programu SharePoint

  W programie dostępnych jest kilka szablonów typów projektów programu SharePoint do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tworzenia witryn programu SharePoint i elementów witryny. Aby uzyskać listę dostępnych typów projektów, zobacz Szablony projektów i elementów [projektu programu SharePoint.](../sharepoint/sharepoint-project-and-project-item-templates.md) Poniżej znajduje się opis elementów i właściwości projektu programu SharePoint.

 Aby uzyskać informacje na temat dodatków programu SharePoint, zobacz [Build SharePoint add-ins](/sharepoint/dev/sp-add-ins/sharepoint-add-ins)(Tworzenie dodatków programu SharePoint).

## <a name="elements-of-a-sharepoint-project"></a>Elementy projektu programu SharePoint

 Węzły w projekcie programu SharePoint są nazywane *elementami programu SharePoint.* Elementy programu SharePoint mogą również zawierać jeden lub więcej podplików, nazywanych plikami elementów programu *SharePoint,* takimi jak pliki [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] konfiguracji, formularze aspx i inne.

 Zamiast tworzyć projekty przy użyciu szablonów projektów, które zostały już  wypełnione plikami elementów projektu, możesz użyć szablonu Pusty projekt, aby utworzyć pusty projekt programu SharePoint, a następnie ręcznie dodać elementy projektu. Projekty programu SharePoint mogą również opcjonalnie zawierać jeden lub więcej plików funkcji (do aktywacji w programie SharePoint) i plik pakietu, w którym ma zostać dystrybuowany projekt.

### <a name="special-nodes"></a>Węzły specjalne

 Każdy projekt programu SharePoint zawiera dwa węzły, których nie można zmienić, usunąć, wytnij, skopiować ani przeciągać z projektu. Te węzły są następujące:

- Funkcje
- Pakiet

  Oba węzły są zawsze wyświetlane we wszystkich projektach programu SharePoint, nawet jeśli dla projektu nie zdefiniowano żadnych funkcji ani pakietów.

#### <a name="features-node"></a>Węzeł Funkcje

 Węzeł **Funkcje** zawiera co najmniej jedną cechę projektu SharePoint. Funkcja to kontener rozszerzeń dla programu SharePoint. Po wdrożeniu funkcji na serwerze programu SharePoint może ona zostać uwzględniona w definicjach witryn lub aktywowana indywidualnie przez administratorów programu SharePoint w witrynach programu SharePoint. Aby uzyskać więcej informacji, zobacz [Praca z funkcjami](/previous-versions/office/developer/sharepoint-2010/ms460318(v=office.14)).

 Po dodaniu elementu, takiego jak typ zawartości lub wystąpienie listy, do projektu programu SharePoint jest on dodawany do funkcji w **węźle Funkcje.** Zakres elementu określa, czy jest on dodawany do nowej, czy istniejącej funkcji. Jeśli nowy element ma ten sam zakres co istniejąca funkcja, zostanie dodany do tej funkcji. W przeciwnym razie element zostanie dodany do nowej funkcji.

 Aby ręcznie dodać funkcję, wykonaj polecenie **Dodaj funkcję** w menu skrótów węzła funkcji. Zawartość funkcji można wyświetlać lub zmieniać za pomocą Projektanta funkcji. Aby uzyskać więcej informacji, [zobacz Jak dostosować funkcję programu SharePoint.](../sharepoint/how-to-customize-a-sharepoint-feature.md)

 Po dodaniu funkcji do projektu programu SharePoint jest **ona** wyświetlana w Eksplorator rozwiązań jako węzeł o domyślnej nazwie Feature *x.feature,* gdzie *x* jest unikatową liczbą. Po wdrożeniu funkcji w programie SharePoint Server administrator programu SharePoint może ją aktywować, udostępniac ją użytkownikom witryny programu SharePoint.

#### <a name="package-node"></a>Węzeł pakietu

 Węzeł **Pakiet** zawiera pojedynczy plik, który służy jako mechanizm dystrybucji dla projektu SharePoint. Ten plik, znany jako pakiet *rozwiązania,* jest .CAB oparty na pliku . Rozszerzenie programu WSP. Pakiet rozwiązania to wdrażalny plik wielokrotnego użytku, który zawiera zestaw funkcji, definicji witryn i zestawów, które dotyczą witryn programu SharePoint i które można włączać lub wyłączać pojedynczo. Węzeł **Pakiet** zawsze zawiera również plik o nazwie Package.wspdef, plik definicji [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] pakietu. Po wdrożeniu pakietu na serwerze z uruchomionym programem SharePoint administrator programu SharePoint może go zainstalować i aktywować jego funkcje.

 Zawartość pakietu można wyświetlić lub zmienić w Projektancie pakietów, klikając dwukrotnie węzeł pakietu lub otwierając jego menu skrótów, a następnie wybierając **polecenie Otwórz**. Aby uzyskać więcej informacji, zobacz Create SharePoint solution packages (Tworzenie [pakietów rozwiązań programu SharePoint).](../sharepoint/creating-sharepoint-solution-packages.md)

## <a name="sharepoint-project-and-project-item-properties"></a>Właściwości projektu i elementu projektu programu SharePoint

 Projekty programu SharePoint, podobnie jak inne projekty, wyświetlają właściwości w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] okno Właściwości stronie właściwości. Wyświetlane właściwości zależą od wybranego węzła.

 Po wybraniu projektu programu SharePoint, elementu projektu lub węzła pliku elementu projektu w programie **Eksplorator rozwiązań** na stronie okno Właściwości lub stronie właściwości zostaną wyświetlone następujące właściwości:

### <a name="project-properties"></a>Właściwości projektu

|Nazwa właściwości|Opis|
|-------------------|-----------------|
|Konfiguracja aktywnego wdrażania|Określa serię kroków wykonywanych podczas wdrażania. Aby uzyskać więcej informacji, [zobacz Jak edytować konfigurację wdrożenia programu SharePoint.](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)|
|Miejsce docelowe wdrożenia zestawu|Określa, *gdzie znajdują się zestawy aplikacji programu SharePoint.* Prawidłowe wartości lokalizacji zestawu to *GlobalAssemblyCache* (ustawienie domyślne) lub *WebApplication*.<br /><br /> Jeśli właściwość *Rozwiązanie w trybie piaskownicy* jest **ustawiona na wartość true**, ta właściwość jest wyłączona.|
|Automatyczne wycofywanie po debugowaniu|Określa, czy wdrożone rozwiązanie automatycznie wycofuje się z programu SharePoint po uruchomieniu aplikacji w trybie debugowania w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Po wybraniu rozwiązanie wycofuje się, gdy po debugowaniu ide wróci do widoku projektu. Po wyczyszczeniu rozwiązanie nie jest wycofywane. Aby uzyskać więcej informacji, zobacz [Wycofywanie rozwiązania](/previous-versions/office/developer/sharepoint-2010/aa543958(v=office.14)).|
|Edytowanie konfiguracji|Określa konfigurację wdrożenia do użycia w projekcie. Aby uzyskać więcej informacji, zobacz [Temat Jak edytować konfigurację](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) wdrożenia programu SharePoint oraz [Wdrażanie, publikowanie i uaktualnianie pakietów rozwiązań programu SharePoint.](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)|
|Włączanie debugowania programu Silverlight (zamiast debugowania skryptu)|Po wybraniu debuger programu Silverlight jest dołączany do procesu debugowania. Po wyczyszczeniu debuger skryptu jest dołączany do procesu debugowania. Aby uzyskać więcej informacji, zobacz [Silverlight Debugging Overview (Omówienie debugowania programu Silverlight).](/previous-versions/windows/)|
|Dołączanie zestawu do pakietu|Określa, czy zestaw projektu jest spakowany w czasie kompilacji, czy nie.|
|Wiersz polecenia po wdrożeniu|Określa polecenia do uruchomienia po wdrożeniu rozwiązania SharePoint. Ten wiersz obsługuje wszystkie polecenia wsadowe, a także rozdzielczość zmiennych MSBuild. Aby uzyskać więcej informacji, zobacz How to: Set SharePoint Deployment Commands (Jak [ustawić polecenia wdrażania programu SharePoint).](../sharepoint/how-to-set-sharepoint-deployment-commands.md)|
|Wiersz polecenia przed wdrożeniem|Określa polecenia do uruchomienia przed wdrożeniem rozwiązania SharePoint. Ten wiersz obsługuje wszystkie polecenia wsadowe, a także rozdzielczość zmiennych MSBuild. Aby uzyskać więcej informacji, zobacz How to: Set SharePoint Deployment Commands (Jak [ustawić polecenia wdrażania programu SharePoint).](../sharepoint/how-to-set-sharepoint-deployment-commands.md)|
|Plik projektu|Nazwa pliku zawierającego kompilację, konfigurację i inne informacje o projekcie.|
|Folder projektu|Lokalizacja pliku projektu w systemie. (Tylko do odczytu).|
|Rozwiązanie w trybie piaskownicy|Określa, czy projekt ma zostać wdrożony jako rozwiązanie w trybie *piaskownicy*, nazywane również rozwiązaniem *utworzonym przez użytkownika.* Rozwiązania w trybie piaskownicy nie muszą być wiarygodne. Wartość true **oznacza,** że projekt jest wdrażany jako rozwiązanie w piaskownicy, a wartość **false** oznacza, że projekt jest wdrażany jako rozwiązanie farmy. Aby uzyskać więcej informacji, zobacz [Sandboxed Solution Considerations](../sharepoint/sandboxed-solution-considerations.md) and Differences Between Sandboxed and Farm Solutions (Zagadnienia dotyczące rozwiązań w piaskownicy i różnice [między rozwiązaniami w trybie piaskownicy i farmy).](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)|
|Adres URL witryny|Określa [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] lokację docelową dla tego projektu.|
|Element startowy|Określa pierwszy element w projekcie do uruchomienia.|

 Po wybraniu pliku elementu programu SharePoint (na przykład przepływu pracy lub funkcji w węźle Funkcje) w oknie okno Właściwości:

### <a name="project-item-properties"></a>Właściwości elementu projektu

|Nazwa właściwości|Opis|
|-------------------|-----------------|
|Rozwiązywanie konfliktów wdrożenia|Określa akcję do podjęcia podczas wdrażania elementu projektu, którego właściwości są identyczne z właściwościami elementu już na serwerze. Aby uzyskać więcej informacji, zobacz [Troubleshooting SharePoint Packaging and Deployment (Rozwiązywanie problemów z pakowaniem i wdrażaniem programu SharePoint).](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)|
|Właściwości funkcji|Określa zestaw wartości (przechowywanych jako pary klucz/wartość) dołączony do funkcji podczas wdrażania w programie SharePoint. Po wdrożeniu funkcji możesz uzyskać dostęp do wartości właściwości w kodzie. Aby uzyskać więcej informacji, zobacz [Dostarczanie informacji o pakowaniu i wdrażaniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|Odbiornik funkcji|Dostarcza kod, który jest wykonywany, gdy wystąpią pewne zdarzenia elementu projektu zawierającego funkcję. Aby uzyskać więcej informacji, zobacz [Dostarczanie informacji o pakowaniu i wdrażaniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|Nazwa folderu|Nazwa folderu elementu projektu programu SharePoint.|
|Odwołania do danych wyjściowych projektu|Określa zależność, taką jak zestaw, która musi być uruchamiana przez element projektu. Aby uzyskać więcej informacji, zobacz [Dostarczanie informacji o pakowaniu i wdrażaniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|Wpisy bezpiecznej kontroli|Określa kontrolki, które są bezpieczne dla niezaufanych użytkowników do edycji. Aby uzyskać więcej informacji, zobacz [Dostarczanie informacji o pakowaniu i wdrażaniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|

### <a name="project-item-file-properties"></a>Właściwości pliku elementu projektu

|Nazwa właściwości|Opis|
|-------------------|-----------------|
|Akcja kompilacji|Określa, w jaki sposób plik odnosi się do procesów kompilacji i wdrażania. Aby uzyskać więcej informacji, zobacz [Właściwości pliku](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|
|Kopiowanie do katalogu wyjściowego|Określa, czy pliki źródłowe zostaną skopiowane do katalogu wyjściowego. Może być jedną z następujących wartości:<br /><br /> -   *Nie kopiuj*<br />-   *Kopiuj zawsze*<br />-   *Kopiuj, jeśli nowsze*<br /><br /> Aby uzyskać więcej informacji, zobacz [Właściwości pliku](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|
|Narzędzie niestandardowe|Określa nazwę narzędzia, jeśli takie, które przekształca plik w czasie projektowania i umieszcza dane wyjściowe przekształcenia w innym pliku. Na przykład plik zestawu danych (. [!INCLUDE[TLA2#tla_xsd](../sharepoint/includes/tla2sharptla-xsd-md.md)] ) ma domyślne narzędzie niestandardowe. Aby uzyskać więcej informacji, zobacz [Właściwości pliku](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|
|Przestrzeń nazw narzędzi niestandardowych|Przestrzeń nazw, do której są kopiowane dane wyjściowe narzędzia niestandardowego. Aby uzyskać więcej informacji, zobacz [Właściwości pliku](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|
|Lokalizacja wdrożenia|W pełni kwalifikowana ścieżka pliku na serwerze programu SharePoint. Ta ścieżka składa się z właściwości podrzędnych Katalog główny wdrożenia i Ścieżka wdrożenia.|
|Ścieżka wdrożenia|Ścieżka względna pliku w pliku programu SharePoint Server, taka jak \\ Workflow1. W pełni kwalifikowana ścieżka pliku jest tworzona  przez ujednarzenie wartości Ścieżka wdrożenia do końca *wartości katalogu głównego* wdrożenia.<br /><br /> Wybranie wartości *RootFile* dla właściwości *Typ*  wdrożenia zmienia właściwość Katalog główny wdrożenia na , co spowoduje w pełni kwalifikowaną ścieżkę \<SharePointRoot> \\ \<SharePointRoot> \Workflow1. \\ Aby uzyskać więcej informacji, zobacz [Packaging and Deploying SharePoint Solutions](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)(Pakowanie i wdrażanie rozwiązań SharePoint).|
|Katalog główny wdrożenia|Ciąg. Folder główny, w którym plik jest wdrażany w programie SharePoint Server. Na przykład \<SharePointRoot> \Template\Features \\ \<FeatureName> \\ .<br /><br /> Wartość właściwości Katalog *główny wdrożenia* jest określana przez *ustawienie Typ* wdrożenia.|
|Typ wdrożenia|Typ wdrożenia pliku, który określa jego wartość *katalogu głównego* wdrożenia. Może być jedną z następujących wartości:<br /><br /> NoDeployment (NoDeployment): *\<no value>*<br /><br /> ElementManifest: *\<SharePointRoot> \Template\Features \\ \<FeatureName>*\\<br /><br /> ElementFile: *\<SharePointRoot> \Template\Features \\ \<FeatureName> \\*<br /><br /> TemplateFile: *\<SharePointRoot> \Template \\*<br /><br /> RootFile: *\<SharePointRoot>\\*<br /><br /> GlobalResource: *\<SharePointRoot> \Resources \\*<br /><br /> ClassResource: *\<ClassResourcePath>\\*<br /><br /> Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.SharePoint.DeploymentType>.|
|Nazwa pliku|Nazwa pliku lub folderu dla pliku elementu.|
|Pełna ścieżka|Lokalizacja pliku dla elementu. (Tylko do odczytu).|

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Projekt SharePoint oraz szablony elementów projektu](../sharepoint/sharepoint-project-and-project-item-templates.md)|Opisuje szablony projektów i elementów projektu programu SharePoint dostępne w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .|
|[Instrukcje: Dodawanie elementów do projektu SharePoint](../sharepoint/how-to-add-items-to-a-sharepoint-project.md)|Opisuje sposób dodawania nowych lub istniejących elementów do projektu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] programu SharePoint.|
|[Przewodnik: tworzenie kolumny witryny, typu zawartości i listy dla programu SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|Prowadzi użytkownika krok po kroku w tworzeniu pola klienta, typu zawartości, definicji listy i wystąpienia listy.|
|[How to: Create an Event receiver (Tworzyć odbiornik zdarzeń)](../sharepoint/how-to-create-an-event-receiver.md)|Opisuje sposób dodawania odbiorcy zdarzeń dla projektu utworzonego w [przewodniku: Tworzenie kolumny witryny,](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)typu zawartości i listy dla programu SharePoint.|
|[Tworzenie rozwiązań przepływu pracy programu SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)|Opisuje sposób tworzenia projektów przepływu pracy, które obejmują formularze skojarzenia przepływu pracy i formularze inicjacji przepływu pracy.|
|[Tworzenie stron dla programu SharePoint](../sharepoint/creating-pages-for-sharepoint.md)|Opisuje sposób tworzenia stron, takich jak strony aplikacji, strony witryny, strony wzorcowe i układy stron dla programu SharePoint.|
|[Tworzenie składników Web Part dla programu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Opisuje sposób dodawania kontrolek, które umożliwiają użytkownikom bezpośrednie modyfikowanie zawartości, wyglądu i zachowania stron witryny programu SharePoint przy użyciu przeglądarki.|
|[Tworzenie kontrolek wielokrotnego użytku dla składników Web Part lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Opisuje sposób tworzenia kontrolek użytkownika, które mogą być używane przez strony aplikacji i składniki Web Part uruchamianych w programie SharePoint.|
|[Integrowanie danych biznesowych z programem SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Opisuje sposób integrowania danych z usług sieci Web i aplikacji serwera back-end w aplikacji programu SharePoint.|
|[Tworzenie definicji witryn dla programu SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md)|Opisuje sposób tworzenia definicji witryn: szablonów używanych do tworzenia witryn programu SharePoint.|
|[Importowanie elementów z istniejącej witryny SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)|Opisuje sposób importowania elementów, takich jak typy zawartości i moduły z istniejącej witryny programu SharePoint, do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu programu SharePoint.|
|[Stosowanie z modułów podczas dołączania plików do rozwiązania](../sharepoint/using-modules-to-include-files-in-the-solution.md)|Opisuje sposób wdrażania plików z projektu w witrynie programu SharePoint przy [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] użyciu modułów.|
|[Przeglądanie połączeń programu SharePoint przy użyciu Eksplorator serwera](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)|Opisuje sposób przeglądania lokalnych witryn programu SharePoint przy użyciu Eksplorator serwera.|
|[Podaj informacje o pakowaniu i wdrażaniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)|Opisuje sposób użycia właściwości elementu projektu w celu zapewnienia informacji o pakowaniu i wdrażaniu dla projektów, takich jak wpisy bezpiecznej kontroli, odwołania do danych wyjściowych projektu i właściwości funkcji.|
|[Jak dodawać i usuwać zamapowane foldery](../sharepoint/how-to-add-and-remove-mapped-folders.md)|Opisuje, jak można dodać zamapowane foldery do projektu, aby zapewnić łatwiejszy dostęp do zasobów programu SharePoint.|
|[Zagadnienia dotyczące rozwiązania w trybie piaskownicy](../sharepoint/sandboxed-solution-considerations.md)|Opisuje problemy związane z rozwiązaniami w trybie piaskownicy.|
|[Zabezpieczenia dla rozwiązań SharePoint](../sharepoint/security-for-sharepoint-solutions.md)|W tym artykule opisano zagadnienia dotyczące zabezpieczeń podczas tworzenia rozwiązań programu SharePoint w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .|
|[Okno dialogowe s wyboru adresu URL &#40;tworzenia aplikacji SharePoint w programie Visual Studio&#41;](../sharepoint/url-picker-dialog-box-sharepoint-development-in-visual-studio.md)|Opisuje okno dialogowe, które umożliwia dodawanie odwołań do ścieżek do zasobów w projekcie lub na lokalnym serwerze programu SharePoint.|

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do tworzenia &#40;SharePoint w usłudze Visual Studio&#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)
- [Przeglądanie połączeń programu SharePoint przy użyciu Eksplorator serwera](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [Kompilowanie i debugowanie rozwiązań SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Pakuj i wdrażaj rozwiązania SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
