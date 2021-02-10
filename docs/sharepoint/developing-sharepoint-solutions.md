---
title: Opracowywanie rozwiązań SharePoint | Microsoft Docs
description: Opracowywanie rozwiązań programu SharePoint. Poznaj elementy projektu programu SharePoint. Zrozumienie projektu programu SharePoint i właściwości elementu projektu.
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
ms.openlocfilehash: 2f085f5679db2c5c4a1e3cf0cc8d7bbf7cad58eb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948833"
---
# <a name="develop-sharepoint-solutions"></a>Opracowywanie rozwiązań SharePoint
  Kilka szablonów typów projektów programu SharePoint jest dostępnych w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] do tworzenia witryn i elementów witryny programu SharePoint. Aby uzyskać listę dostępnych typów projektów, zobacz [Szablony projektów i elementów projektu programu SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md). Poniżej znajduje się opis elementów i właściwości projektu programu SharePoint.

 Aby uzyskać informacje na temat dodatków SharePoint 2013 i SharePoint, zobacz [sharepoint 2013](https://www.microsoft.com/microsoft-365/previous-versions/microsoft-sharepoint-2013) i [Build Add-ins programu SharePoint](/sharepoint/dev/sp-add-ins/sharepoint-add-ins).

## <a name="elements-of-a-sharepoint-project"></a>Elementy projektu programu SharePoint
 Węzły w projekcie programu SharePoint są znane jako *elementy programu SharePoint*. Elementy programu SharePoint mogą również zawierać jeden lub więcej podplików, które są nazywane *plikami elementów programu SharePoint*, takimi jak [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] pliki konfiguracji, formularze. aspx i inne.

 Zamiast tworzyć projekty przy użyciu szablonów projektów, które są już wypełnione plikami elementów projektu, można użyć szablonu **pusty projekt** , aby utworzyć pusty projekt programu SharePoint, a następnie ręcznie dodać elementy projektu. Projekty programu SharePoint mogą również opcjonalnie zawierać jeden lub więcej plików funkcji (do aktywacji w programie SharePoint) i plik pakietu, w którym ma zostać rozdystrybuowany projekt.

### <a name="special-nodes"></a>Węzły specjalne
 Każdy projekt programu SharePoint zawiera dwa węzły, których nazwy nie można zmienić, usunąć, wyciąć, skopiować lub przeciągnąć z projektu. Te węzły są następujące:

- Funkcje
- Pakiet

  Oba węzły są zawsze wyświetlane we wszystkich projektach programu SharePoint, nawet jeśli nie zdefiniowano żadnych funkcji ani pakietów dla projektu.

#### <a name="features-node"></a>Węzeł funkcje
 Węzeł **funkcje** zawiera jedną lub więcej funkcji projektu programu SharePoint. Funkcja jest kontenerem rozszerzeń dla programu SharePoint. Po wdrożeniu funkcji na serwerze programu SharePoint można ją uwzględnić w definicjach lokacji lub aktywować indywidualnie przez administratorów programu SharePoint w witrynach programu SharePoint. Aby uzyskać więcej informacji, zobacz [Praca z funkcjami](/previous-versions/office/developer/sharepoint-2010/ms460318(v=office.14)).

 Po dodaniu elementu, takiego jak typ zawartości lub wystąpienie listy, do projektu programu SharePoint jest on dodawany do funkcji w węźle **funkcje** . Zakres elementu określa, czy jest on dodawany do nowej lub istniejącej funkcji. Jeśli nowy element ma taki sam zakres jak istniejąca funkcja, zostanie dodany do tej funkcji. W przeciwnym razie element zostanie dodany do nowej funkcji.

 Aby ręcznie dodać funkcję, wykonaj polecenie **Dodaj funkcję** w menu skrótów węzła funkcji. Zawartość funkcji można wyświetlić lub zmienić za pomocą projektanta funkcji. Aby uzyskać więcej informacji, zobacz [How to: Dostosowywanie funkcji SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md).

 Gdy funkcja jest dodawana do projektu programu SharePoint, jest wyświetlana w **Eksplorator rozwiązań** jako węzeł o domyślnej nazwie funkcja *x*. feature, gdzie *x* jest unikatowym numerem. Po wdrożeniu funkcji na serwerze programu SharePoint Administrator programu SharePoint może ją uaktywnić i udostępnić użytkownikom witryny programu SharePoint.

#### <a name="package-node"></a>Węzeł pakietu
 Węzeł **pakietu** zawiera pojedynczy plik, który służy jako mechanizm dystrybucji dla projektu programu SharePoint. Ten plik, znany jako *pakiet rozwiązania*, to. Na podstawie pliku CAB. Rozszerzenie WSP. Pakiet rozwiązania to możliwy do wdrożenia plik do wielokrotnego użytku, który zawiera zestaw funkcji, definicje witryn i zestawy, które mają zastosowanie do witryn programu SharePoint, a które można włączać lub wyłączać pojedynczo. Węzeł **pakietu** również zawsze zawiera plik o nazwie Package. wspdef, [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] plik definicji pakietu. Po wdrożeniu pakietu na serwerze, na którym działa program SharePoint, administrator programu SharePoint może go zainstalować i aktywować jego funkcje.

 Można wyświetlić lub zmienić zawartość pakietu w projektancie pakietów przez dwukrotne kliknięcie węzła pakietu lub otwarcie jego menu skrótów, a następnie wybranie polecenia **Otwórz**. Aby uzyskać więcej informacji, zobacz [Tworzenie pakietów rozwiązania SharePoint](../sharepoint/creating-sharepoint-solution-packages.md).

## <a name="sharepoint-project-and-project-item-properties"></a>Projekt programu SharePoint i właściwości elementu projektu
 Projekty programu SharePoint, podobnie jak inne [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projekty, wyświetlają właściwości w okno właściwości i na stronie właściwości. Wyświetlane właściwości zależą od wybranego węzła.

 Po wybraniu projektu programu SharePoint, elementu projektu lub węzła pliku elementu projektu w **Eksplorator rozwiązań**, w okno właściwości lub na stronie właściwości są wyświetlane następujące właściwości:

### <a name="project-properties"></a>Właściwości projektu

|Nazwa właściwości|Opis|
|-------------------|-----------------|
|Konfiguracja aktywnego wdrożenia|Określa serię kroków wykonywanych podczas wdrażania. Aby uzyskać więcej informacji, zobacz [How to: Edit a SharePoint Deployment Configuration](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).|
|Cel wdrożenia zestawu|Określa, gdzie znajdują się *zestawy aplikacji programu SharePoint* . Prawidłowymi wartościami lokalizacji zestawu są *GlobalAssemblyCache* (default) lub *WebApplication*.<br /><br /> Jeśli właściwość *rozwiązanie w trybie piaskownicy* ma **wartość PRAWDA**, ta właściwość jest wyłączona.|
|Autowycofywanie po debugowaniu|Określa, czy wdrożone rozwiązanie automatycznie wycofuje się z programu SharePoint po uruchomieniu aplikacji w trybie debugowania w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Po wybraniu rozwiązanie wycofuje się, gdy IDE wraca do widoku projektu po debugowaniu. Po wyczyszczeniu rozwiązanie nie zostanie wycofane. Aby uzyskać więcej informacji, zobacz [wycofywanie rozwiązania](/previous-versions/office/developer/sharepoint-2010/aa543958(v=office.14)).|
|Edytuj konfiguracje|Określa konfigurację wdrożenia, która ma być używana dla projektu. Aby uzyskać więcej informacji, zobacz [jak: edytowanie konfiguracji wdrożenia programu SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) oraz [wdrażanie, publikowanie i uaktualnianie pakietów rozwiązań programu SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).|
|Włącz debugowanie Silverlight (zamiast debugowania skryptów)|Po wybraniu debuger Silverlight dołącza do procesu debugowania. Po wyczyszczeniu, debuger skryptów dołącza do procesu debugowania. Aby uzyskać więcej informacji, zobacz [Omówienie debugowania Silverlight](/previous-versions/windows/).|
|Dołącz zestaw do pakietu|Określa, czy zestaw projektu jest spakowany w czasie kompilacji, czy nie.|
|Wiersz polecenia po wdrożeniu|Określa polecenia do uruchomienia po wdrożeniu rozwiązania programu SharePoint. Ten wiersz obsługuje wszystkie polecenia wsadowe oraz rozdzielczość zmiennych MSBuild. Aby uzyskać więcej informacji, zobacz [How to: Set SharePoint Deployment Commands](../sharepoint/how-to-set-sharepoint-deployment-commands.md).|
|Wiersz polecenia przed wdrożeniem|Określa polecenia do uruchomienia przed wdrożeniem rozwiązania programu SharePoint. Ten wiersz obsługuje wszystkie polecenia wsadowe oraz rozdzielczość zmiennych MSBuild. Aby uzyskać więcej informacji, zobacz [How to: Set SharePoint Deployment Commands](../sharepoint/how-to-set-sharepoint-deployment-commands.md).|
|Plik projektu|Nazwa pliku zawierającego kompilację, konfigurację i inne informacje o projekcie.|
|Folder projektu|Lokalizacja pliku projektu w systemie. (Tylko do odczytu).|
|Rozwiązanie w trybie piaskownicy|Określa, czy projekt powinien zostać wdrożony jako *rozwiązanie w trybie piaskownicy*, znane także jako *rozwiązanie utworzone przez użytkownika*. Rozwiązania w trybie piaskownicy nie są koniecznie wiarygodne. Wartość **true** oznacza, że projekt jest wdrażany jako rozwiązanie w trybie piaskownicy, wartość **false** oznacza, że projekt jest wdrażany jako rozwiązanie farmy. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące rozwiązania w trybie piaskownicy](../sharepoint/sandboxed-solution-considerations.md) oraz [różnice między rozwiązaniami w trybie piaskownicy i farmą](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).|
|Adres URL witryny|Określa [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] lokację docelową dla tego projektu.|
|Element startowy|Określa pierwszy element w projekcie do uruchomienia.|

 Po wybraniu pliku elementu programu SharePoint (takiego jak przepływ pracy lub funkcja w węźle funkcje) w okno Właściwości są wyświetlane następujące właściwości:

### <a name="project-item-properties"></a>Właściwości elementu projektu

|Nazwa właściwości|Opis|
|-------------------|-----------------|
|Rozwiązywanie konfliktów wdrożenia|Określa akcję do wykonania podczas wdrażania elementu projektu, którego właściwości są identyczne z elementami elementu znajdującego się już na serwerze. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z pakietami i wdrażaniem programu SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).|
|Właściwości funkcji|Określa zestaw wartości (przechowywanych jako pary klucz/wartość), które są dołączone do funkcji podczas wdrażania w programie SharePoint. Po wdrożeniu funkcji można uzyskać dostęp do wartości właściwości w kodzie. Aby uzyskać więcej informacji, zobacz [zapewnianie informacji o pakowaniu i wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|Odbiorca funkcji|Zapewnia kod, który jest wykonywany, gdy pewne zdarzenia wystąpią do funkcji zawierającej element projektu. Aby uzyskać więcej informacji, zobacz [zapewnianie informacji o pakowaniu i wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|Nazwa folderu|Nazwa folderu elementu projektu programu SharePoint.|
|Odwołania do danych wyjściowych projektu|Określa zależność, taką jak zestaw, że element projektu musi zostać uruchomiony. Aby uzyskać więcej informacji, zobacz [zapewnianie informacji o pakowaniu i wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|Bezpieczne wpisy kontroli|Określa formanty, które są bezpieczne dla niezaufanych użytkowników do edycji. Aby uzyskać więcej informacji, zobacz [zapewnianie informacji o pakowaniu i wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|

### <a name="project-item-file-properties"></a>Właściwości pliku elementu projektu

|Nazwa właściwości|Opis|
|-------------------|-----------------|
|Akcja kompilacji|Określa, w jaki sposób plik odnosi się do procesów kompilacji i wdrożenia. Aby uzyskać więcej informacji, zobacz [właściwości pliku](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|
|Kopiuj do katalogu wyjściowego|Określa, czy pliki źródłowe zostaną skopiowane do katalogu wyjściowego. Może być jedną z następujących wartości:<br /><br /> -   *Nie Kopiuj*<br />-   *Zawsze Kopiuj*<br />-   *Kopiuj, jeśli nowszy*<br /><br /> Aby uzyskać więcej informacji, zobacz [właściwości pliku](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|
|Niestandardowe narzędzie|Określa nazwę narzędzia (jeśli istnieje), które przekształca plik w czasie projektowania i umieszcza dane wyjściowe transformacji w innym pliku. Na przykład plik zestawu danych (. [!INCLUDE[TLA2#tla_xsd](../sharepoint/includes/tla2sharptla-xsd-md.md)] ) ma domyślne narzędzie niestandardowe. Aby uzyskać więcej informacji, zobacz [właściwości pliku](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|
|Przestrzeń nazw narzędzia niestandardowego|Przestrzeń nazw, do której są kopiowane dane wyjściowe niestandardowego narzędzia. Aby uzyskać więcej informacji, zobacz [właściwości pliku](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|
|Lokalizacja wdrożenia|W pełni kwalifikowana ścieżka pliku na serwerze programu SharePoint. Ta ścieżka składa się z właściwości podrzędnych i ścieżki wdrożenia elementu głównego wdrożenia.|
|Ścieżka wdrożenia|Ścieżka względna pliku w pliku programu SharePoint Server, na przykład Workflow1 \\ . W pełni kwalifikowana ścieżka do pliku jest tworzona przez połączenie wartości *ścieżki wdrożenia* na końcu wartości *głównej wdrożenia* .<br /><br /> Wybranie wartości *RootFile* dla właściwości *typ wdrożenia* spowoduje zmianę właściwości *głównej wdrożenia* na \<SharePointRoot> \\ , co spowodowało w pełni kwalifikowaną ścieżkę \<SharePointRoot> \Workflow1 \\ . Aby uzyskać więcej informacji, zobacz [pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).|
|Katalog główny wdrożenia|Ciąg. Folder główny, w którym plik jest wdrożony na serwerze programu SharePoint. Na przykład \<SharePointRoot> \Template\Features \\ \<FeatureName> \\ .<br /><br /> Wartość właściwości *root wdrożenia* jest określana na podstawie ustawienia *typu wdrożenia* .|
|Typ wdrożenia|Typ wdrożenia pliku, który określa jego wartość *główną wdrożenia* . Może być jedną z następujących wartości:<br /><br /> NoDeployment: *\<no value>*<br /><br /> ElementManifest: *\<SharePointRoot> \Template\Features \\ \<FeatureName>*\\<br /><br /> Elementu: *\<SharePointRoot> \\ \<FeatureName> \Template\Features \\*<br /><br /> TemplateFile: *\<SharePointRoot> \Template \\*<br /><br /> RootFile: *\<SharePointRoot>\\*<br /><br /> GlobalResource: *\<SharePointRoot> \Resources \\*<br /><br /> ClassResource: *\<ClassResourcePath>\\*<br /><br /> Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.SharePoint.DeploymentType>.|
|Nazwa pliku|Nazwa pliku lub folderu dla pliku elementu.|
|Pełna ścieżka|Lokalizacja pliku dla elementu. (Tylko do odczytu).|

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Projekt SharePoint oraz szablony elementów projektu](../sharepoint/sharepoint-project-and-project-item-templates.md)|Zawiera opis projektu programu SharePoint i szablonów elementów projektu dostępnych w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .|
|[Instrukcje: Dodawanie elementów do projektu SharePoint](../sharepoint/how-to-add-items-to-a-sharepoint-project.md)|Opisuje, jak dodać nowe lub istniejące elementy do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu programu SharePoint.|
|[Przewodnik: Tworzenie kolumny witryny, typu zawartości i listy dla programu SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|Prowadzi Cię krok po kroku podczas tworzenia pola klienta, typu zawartości, definicji listy i wystąpienia listy.|
|[Instrukcje: Tworzenie odbiorcy zdarzeń](../sharepoint/how-to-create-an-event-receiver.md)|Opisuje sposób dodawania odbiorcy zdarzeń dla projektu utworzonego w [przewodniku: Tworzenie kolumny witryny, typu zawartości i listy dla programu SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).|
|[Tworzenie rozwiązań przepływu pracy programu SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)|Opisuje sposób tworzenia projektów przepływu pracy, w tym formularzy skojarzenia przepływu pracy i formularzy inicjacji przepływu pracy.|
|[Tworzenie stron dla programu SharePoint](../sharepoint/creating-pages-for-sharepoint.md)|Opisuje sposób tworzenia stron, takich jak strony aplikacji, strony witryny, strony wzorcowe i układy stron programu SharePoint.|
|[Tworzenie składników Web Part dla programu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Opisuje sposób dodawania kontrolek, które umożliwiają użytkownikom bezpośrednie modyfikowanie zawartości, wyglądu i zachowania stron witryny programu SharePoint za pomocą przeglądarki.|
|[Tworzenie kontrolek wielokrotnego użytku dla części sieci Web lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Opisuje sposób tworzenia kontrolek użytkownika, które mogą być używane przez strony aplikacji oraz składniki Web Part, które są uruchamiane w programie SharePoint.|
|[Integrowanie danych firmowych z programem SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Opisuje sposób integrowania danych z usług sieci Web i aplikacji serwera zaplecza z aplikacją programu SharePoint.|
|[Tworzenie definicji witryny dla programu SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md)|Opisuje sposób tworzenia definicji lokacji: szablonów, które są używane do tworzenia witryn programu SharePoint.|
|[Importowanie elementów z istniejącej witryny SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)|Opisuje sposób importowania elementów, takich jak typy zawartości i moduły z istniejącej witryny programu SharePoint do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu programu SharePoint.|
|[Stosowanie z modułów podczas dołączania plików do rozwiązania](../sharepoint/using-modules-to-include-files-in-the-solution.md)|Opisuje sposób użycia modułów do wdrażania plików z [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu w witrynie programu SharePoint.|
|[Przeglądanie połączeń programu SharePoint przy użyciu Eksplorator serwera](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)|Opisuje sposób przeglądania lokalnych witryn programu SharePoint przy użyciu Eksplorator serwera.|
|[Udostępnianie informacji o pakowaniu i wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)|Opisuje sposób użycia właściwości elementu projektu w celu dostarczenia informacji o pakowaniu i wdrożeniu dla projektów, takich jak wpisy kontroli bezpiecznego, odwołania do danych wyjściowych projektu i właściwości funkcji.|
|[Instrukcje: Dodawanie i usuwanie mapowanych folderów](../sharepoint/how-to-add-and-remove-mapped-folders.md)|Opisuje sposób, w jaki mapowane foldery można dodać do projektu, aby zapewnić łatwiejszy dostęp do zasobów programu SharePoint.|
|[Zagadnienia dotyczące rozwiązania w trybie piaskownicy](../sharepoint/sandboxed-solution-considerations.md)|Opisuje problemy związane z rozwiązaniami w trybie piaskownicy.|
|[Zabezpieczenia dla rozwiązań SharePoint](../sharepoint/security-for-sharepoint-solutions.md)|Opisuje zagadnienia dotyczące zabezpieczeń dotyczące opracowywania rozwiązań programu SharePoint w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .|
|[Okno dialogowe selektora adresów URL &#40;programowanie SharePoint w programie Visual Studio&#41;](../sharepoint/url-picker-dialog-box-sharepoint-development-in-visual-studio.md)|Opisuje okno dialogowe, za pomocą którego można dodać odwołania do ścieżek do zasobów w projekcie lub na lokalnym serwerze programu SharePoint.|

## <a name="see-also"></a>Zobacz też
- [Wprowadzenie &#40;programowanie SharePoint w programie Visual Studio&#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)
- [Przeglądanie połączeń programu SharePoint przy użyciu Eksplorator serwera](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [Kompilowanie i debugowanie rozwiązań SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
