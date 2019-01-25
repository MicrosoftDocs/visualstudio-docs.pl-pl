---
title: Opracowywanie rozwiązań SharePoint | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4384396781172c73056de27fd3c674535571d591
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869021"
---
# <a name="develop-sharepoint-solutions"></a>Opracowywanie rozwiązań SharePoint
  Kilka szablonów typu projektu programu SharePoint są dostępne w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] do tworzenia witryn programu SharePoint oraz elementów witryny. Aby uzyskać listę typów dostępnych projektów, zobacz [SharePoint szablony elementu projektu i projektu](../sharepoint/sharepoint-project-and-project-item-templates.md). Poniżej znajduje się opis elementów i właściwości projektu programu SharePoint.  
  
 Aby uzyskać informacji na temat programu SharePoint 2013 i dodatków programu SharePoint, zobacz [programu SharePoint 2013](https://msdn.microsoft.com/library/jj162979.aspx) i [dodatków programu SharePoint z kompilacji](/sharepoint/dev/sp-add-ins/sharepoint-add-ins).  
  
## <a name="elements-of-a-sharepoint-project"></a>Elementy projektu programu SharePoint
 Węzły w projekcie programu SharePoint są znane jako *elementów programu SharePoint*. Elementy programu SharePoint mogą także zawierać jeden lub więcej podplików określanych jako *pliki elementu programu SharePoint*, takich jak [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] pliki konfiguracyjne, formularze .aspx i inne.  
  
 Zamiast tworzenia projektów przy użyciu szablonów projektów, które są już wypełnione plikami z elementami projektu, możesz użyć **pusty projekt** szablon, aby utworzyć pusty projekt programu SharePoint, a następnie ręcznie dodać elementy projektu. Projekty programu SharePoint mogą również opcjonalnie zawierać jeden lub więcej plików funkcji (do aktywacji w programie SharePoint) i plik pakietu, w którym można rozpowszechnić projekt.  
  
### <a name="special-nodes"></a>Węzły specjalne
 Każdy projekt programu SharePoint zawiera dwa węzły, które nie może być zmieniona, usunięte, wycinanie, skopiowane lub przeciągnięte z projektu. Te węzły są następujące:  
  
- Funkcje    
- Package  
  
  Oba węzły są wyświetlane we wszystkich projektach SharePoint zawsze, nawet jeśli żadna funkcja ani opakowanie są zdefiniowane dla projektu.  
  
#### <a name="features-node"></a>Węzeł funkcji
 **Funkcji** węzeł zawiera jeden lub więcej funkcji projektu SharePoint. Funkcja jest kontenerem rozszerzeń dla programu SharePoint. Po wdrożeniu funkcji do serwera programu SharePoint, mogą być zawarte w definicji witryny lub aktywowane indywidualnie przez administratorów programu SharePoint w witrynach programu SharePoint. Aby uzyskać więcej informacji, zobacz [Praca z funkcjami](http://go.microsoft.com/fwlink/?LinkID=147704).  
  
 Po dodaniu elementu, takiego jak typ zawartości lub wystąpienia listy, do projektu programu SharePoint zostanie dodany do funkcji w **funkcji** węzła. Zakres elementu Określa, czy jest ona dodawana do nowej lub istniejącej funkcji. Jeśli nowy element ma taki sam zakres jak funkcja istniejąca, to jest dodawany do tej funkcji. W przeciwnym razie element jest dodawany do nowej funkcji.  
  
 Aby dodać funkcję ręcznie, wykonaj **Dodaj funkcję** polecenia menu skrótów węzła funkcji. Można wyświetlać lub zmieniać zawartość funkcji przy użyciu projektanta funkcji. Aby uzyskać więcej informacji, zobacz [jak: Dostosowywanie funkcji SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md).  
  
 Gdy funkcja zostanie dodany do projektu programu SharePoint, pojawi się w **Eksploratora rozwiązań** jako węzeł z domyślna nazwa funkcji*x*.feature, gdzie *x* to unikatowa liczba. Po wdrożeniu funkcji do serwera programu SharePoint, administrator programu SharePoint można uaktywnić, udostępniając użytkownikom witryny programu SharePoint.  
  
#### <a name="package-node"></a>Węzeł pakietu
 **Pakietu** węzeł zawiera pojedynczy plik, który służy jako mechanizm rozkładu dla projektu programu SharePoint. Ten plik, nazywany *pakietu rozwiązania*, jest. Na podstawie pliku CAB z. Rozszerzenie WSP. Pakiet rozwiązania jest plikiem rozmieszczenia, wielokrotnego użytku, który zawiera zestaw funkcji, definicji witryny i zestawy, które są stosowane do witryny programu SharePoint i które można włączać lub wyłączać indywidualnie. **Pakietu** węzła również zawsze zawiera plik o nazwie Package.wspdef, [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] pliku definicji pakietu. Po wdrożeniu pakietu do serwera, na którym uruchomiony jest SharePoint, administratora programu SharePoint można go zainstalować i uaktywnić jego funkcje.  
  
 Możesz wyświetlić lub zmienić zawartość pakietu w Projektancie pakietu podwójnie na węzeł pakietu albo otwierając jego menu skrótów, a następnie wybierając **Otwórz**. Aby uzyskać więcej informacji, zobacz [pakietów rozwiązania SharePoint Utwórz](../sharepoint/creating-sharepoint-solution-packages.md).  
  
## <a name="sharepoint-project-and-project-item-properties"></a>Projekt programu SharePoint i właściwości elementu projektu
 Projekty programu SharePoint, podobnie jak inne [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektów, wyświetlanie właściwości w oknie dialogowym właściwości i strony właściwości. Właściwości, które są wyświetlane, zależą od wybranego węzła.  
  
 Po wybraniu projektu SharePoint, elementu projektu lub węzła pliku elementu projektu w **Eksploratora rozwiązań**, następujące właściwości wyświetlają się w oknie dialogowym właściwości lub na stronie właściwości:  
  
### <a name="project-properties"></a>Właściwości projektu
  
|Nazwa właściwości|Opis|  
|-------------------|-----------------|  
|Konfiguracja aktywnego wdrożenia|Określa serię kroków wykonywanych podczas wdrażania. Aby uzyskać więcej informacji, zobacz [jak: Edytowanie konfiguracji wdrażania SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).|  
|Zestaw docelowy wdrażania|Określa, gdzie *zestawy aplikacji SharePoint* znajdują się. Wartości prawidłowej lokalizacji zestawu są albo *GlobalAssemblyCache* (ustawienie domyślne) lub *WebApplication*.<br /><br /> Jeśli *rozwiązanie w trybie piaskownicy* właściwość jest ustawiona na **true**, wówczas właściwość ta jest wyłączona.|  
|Automatycznie wycofać po debugowania|Określa, czy wdrożone rozwiązanie automatycznie wycofuje się z programu SharePoint po uruchomieniu aplikacji w trybie debugowania w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Po wybraniu, rozwiązanie wycofuje się kiedy IDE wraca do widoku projektowania po debugowaniu. Po wyczyszczeniu, rozwiązanie nie wycofuje się. Aby uzyskać więcej informacji, zobacz [wycofywanie rozwiązania](http://go.microsoft.com/fwlink/?LinkId=183819).|  
|Edytuj konfiguracje|Określa konfigurację wdrożenia do użycia w projekcie. Aby uzyskać więcej informacji, zobacz [jak: Edytowanie konfiguracji wdrażania SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) i [wdrażanie, publikowanie oraz aktualizowanie pakietów rozwiązania SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).|  
|Włącz debugowanie programu Silverlight (zamiast debugowanie skryptów)|Po wybraniu, Silverlight debugger dołącza do procesu debugowania. Po zdeklarowaniu, debugger scenariusza dołącza do procesu debugowania. Aby uzyskać więcej informacji, zobacz [omówienie debugowania Silverlight](http://go.microsoft.com/fwlink/?LinkId=179826).|  
|Zawiera zestaw w pakiecie|Określa, czy zestaw projektów jest spakowany w czasie kompilacji, czy nie.|  
|Wiersz polecenia po wdrożeniu|Określa polecenia do uruchomienia po wdrożeniu rozwiązania SharePoint. Linia obsługuje wszystkie polecenia usługi batch, jak również rozdzielczość zmiennych MSBuild. Aby uzyskać więcej informacji, zobacz [jak: Ustawianie poleceń wdrażania SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).|  
|Wiersz polecenia przed wdrożeniem|Określa polecenia do uruchomienia przed wdrożeniem rozwiązania SharePoint. Linia obsługuje wszystkie polecenia usługi batch, jak również rozdzielczość zmiennych MSBuild. Aby uzyskać więcej informacji, zobacz [jak: Ustawianie poleceń wdrażania SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).|  
|Plik projektu|Nazwa pliku zawierającego kompilację, konfigurację i inne informacje o projekcie.|  
|Folder projektu|Lokalizacja pliku projektu w systemie. (Tylko do odczytu).|  
|Rozwiązanie w trybie piaskownicy|Określa, czy projekt powinien być wdrażany jako *rozwiązanie w trybie piaskownicy*, znane również jako *rozwiązań utworzonych przez użytkownika*. Rozwiązania piaskownicy nie są końca wiarygodne. Wartość **true** oznacza, że projekt został wdrożony jako rozwiązanie w trybie piaskownicy, wartość **false** oznacza, że projekt został wdrożony jako rozwiązanie farmy. Aby uzyskać więcej informacji, zobacz [uwagi dotyczące rozwiązania piaskownicy](../sharepoint/sandboxed-solution-considerations.md) i [różnice między piaskownicy oraz rozwiązaniami farmy](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).|  
|Adres URL witryny|Określa [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] docelowej witryny dla tego projektu.|  
|Element startowy|Określa pierwszy element w projekcie do uruchomienia.|  
  
 Po wybraniu pliku elementów SharePoint (takich jak przepływ pracy lub funkcji w węźle funkcji), następujące właściwości wyświetlają się w oknie dialogowym właściwości:  
  
### <a name="project-item-properties"></a>Właściwości elementu projektu
  
|Nazwa właściwości|Opis|  
|-------------------|-----------------|  
|Rozwiązywanie konfliktów wdrożenia|Określa akcję wykonywaną przy wdrażaniu elementu projektu, którego właściwości są identyczne z właściwościami elementu znajdującego się już na serwerze. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z pakowaniem i wdrażaniem SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).|  
|Właściwości funkcji|Określa zestaw wartości (przechowywanych jako pary klucz/wartość) jest uwzględniany w funkcji podczas wdrażania w programie SharePoint. Po wdrożeniu funkcji wartości właściwości są dostępne w kodzie. Aby uzyskać więcej informacji, zobacz [dostarczanie pakowania i informacje o wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|Odbiorca funkcji|Oferuje kod wykonywany po wystąpieniu określonego zdarzenia z elementem projektu zawierającym funkcję. Aby uzyskać więcej informacji, zobacz [dostarczanie pakowania i informacje o wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|Nazwa folderu|Nazwa folderu elementów projektów programu SharePoint.|  
|Odwołania danych wyjściowych projektu|Określa zależność, takich jak zestaw, który element projektu musi zostać uruchomiony. Aby uzyskać więcej informacji, zobacz [dostarczanie pakowania i informacje o wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|Wpisy bezpiecznych kontrolek|Określa formanty, które są bezpieczne dla niezaufanch użytkowników do edycji. Aby uzyskać więcej informacji, zobacz [dostarczanie pakowania i informacje o wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
  
### <a name="project-item-file-properties"></a>Właściwości pliku element projektu
  
|Nazwa właściwości|Opis|  
|-------------------|-----------------|  
|Akcja kompilacji|Określa, jak plik odnosi się do procesów kompilacji i wdrożenia. Aby uzyskać więcej informacji, zobacz [właściwości pliku](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|  
|Kopiuj do katalogu wyjściowego|Określa, czy plik źródłowy zostanie skopiowany do katalogu wyjściowego. Może być jednym z następujących wartości:<br /><br /> -   *Nie Kopiuj*<br />-   *Zawsze Kopiuj*<br />-   *Kopiuj Jeśli nowszy*<br /><br /> Aby uzyskać więcej informacji, zobacz [właściwości pliku](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|  
|Narzędzie niestandardowe|Określa nazwę narzędzia, jeśli istnieje, które przekształca plik w czasie projektowania i umieszcza przekształcenie w innym pliku. Na przykład zestaw danych (.[!INCLUDE[TLA2#tla_xsd](../sharepoint/includes/tla2sharptla-xsd-md.md)]) plik ma domyślne narzędzie niestandardowe. Aby uzyskać więcej informacji, zobacz [właściwości pliku](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|  
|Namespace narzędzie niestandardowe|Przestrzeń nazw, do którego są kopiowane dane wyjściowe narzędzia niestandardowego. Aby uzyskać więcej informacji, zobacz [właściwości pliku](/previous-versions/visualstudio/visual-studio-2010/0c6xyb66\(v\=vs.100\)).|  
|Lokalizacja wdrożenia|Pełna ścieżka pliku na serwerze programu SharePoint. Ta ścieżka składa się z właściwości podrzędnych główny wdrożenia i ścieżka wdrożenia.|  
|Ścieżka do wdrożenia|Ścieżka względna pliku w pliku serwera SharePoint, takich jak Workflow1\\. W pełni kwalifikowanej ścieżki pliku jest tworzona przez dołączenie *Ścieżka rozmieszczania* wartość na końcu *główny wdrożenia* wartość.<br /><br /> Wybranie wartości z *RootFile* dla *typu wdrożenia* zmiany właściwości *główny wdrożenia* właściwości \<SharePointRoot >\\, dając w efekcie w pełni kwalifikowaną ścieżką \<SharePointRoot > \Workflow1\\. Aby uzyskać więcej informacji, zobacz [pakowania i wdrażania rozwiązań programu SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md).|  
|Główny wdrożenia|ciąg. Folder główny, gdzie plik jest wdrożony na serwerze programu SharePoint. Na przykład \<SharePointRoot > \Template\Features\\\<FeatureName >\\.<br /><br /> Wartość *główny wdrożenia* właściwość jest określana przez *typu wdrożenia* ustawienie.|  
|Typ wdrożenia|Typ wdrażania pliku, który określa jego *główny wdrożenia* wartość. Może być jednym z następujących wartości:<br /><br /> NoDeployment:  *\<żadnej wartości >*<br /><br /> ElementManifest: *\<SharePointRoot>\Template\Features\\\<FeatureName>*\\<br /><br /> Plik elementu: *\<SharePointRoot>\Template\Features\\\<FeatureName>\\*<br /><br /> TemplateFile: *\<SharePointRoot>\Template\\*<br /><br /> RootFile: *\<SharePointRoot>\\*<br /><br /> GlobalResource: *\<SharePointRoot>\Resources\\*<br /><br /> ClassResource: *\<ClassResourcePath>\\*<br /><br /> Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.SharePoint.DeploymentType>.|  
|Nazwa pliku|Nazwa pliku lub folderu dla pliku elementu.|  
|Pełna ścieżka|Lokalizacja pliku dla elementu. (Tylko do odczytu).|  
  
## <a name="related-topics"></a>Tematy pokrewne
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Projekt SharePoint oraz szablony elementów projektu](../sharepoint/sharepoint-project-and-project-item-templates.md)|Opisuje projekt programu SharePoint oraz szablony elementów projektu jest dostępne w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[Instrukcje: Dodawanie elementów do projektu programu SharePoint](../sharepoint/how-to-add-items-to-a-sharepoint-project.md)|W tym artykule opisano sposób dodawania nowych lub istniejących elementów do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu programu SharePoint.|  
|[Przewodnik: Tworzenie kolumny witryny, typu zawartości oraz list dla SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|Prowadzi użytkownika krok po kroku podczas tworzenia odbiorcy, pole, typ zawartości, definicji listy i instancji list.|  
|[Instrukcje: Tworzenie obsługiwanego odbiornika](../sharepoint/how-to-create-an-event-receiver.md)|Zawiera opis sposobu dodawania odbiorców zdarzenia dla projektu utworzonego w [instruktażu: Tworzenie kolumny witryny, typu zawartości oraz list dla SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).|  
|[Tworzenie rozwiązań przepływu pracy SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)|W tym artykule opisano sposób tworzenia projektów przepływu pracy zawierający skojarzenie przepływu pracy i formularze inicjacji przepływu pracy.|  
|[Tworzenie stron dla SharePoint](../sharepoint/creating-pages-for-sharepoint.md)|W tym artykule opisano sposób tworzenia stron, takich jak strony aplikacji, stron witryny, strony wzorcowe i układy stron programu SharePoint.|  
|[Tworzenie składników web Part programu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|W tym artykule opisano sposób dodawania formantów, które umożliwiają użytkownikom bezpośrednio modyfikować zawartość, wygląd i zachowanie stron w witrynie programu SharePoint za pomocą przeglądarki.|  
|[Tworzenie formantów wielokrotnych dla części sieciowych lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|W tym artykule opisano sposób tworzenia kontrolki użytkownika, które mogą być wykorzystane przez strony aplikacji i składników Web Part, które są uruchamiane w programie SharePoint.|  
|[Integrowanie danych biznesowych programu SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|W tym artykule opisano sposób integrowania danych z usług sieci Web i aplikacji serwera zaplecza do aplikacji programu SharePoint.|  
|[Tworzenie definicji witryny dla SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md)|Zawiera opis sposobu tworzenia definicji witryny: szablonów, które są używane do tworzenia witryn programu SharePoint.|  
|[Importowanie elementów z istniejącej witryny SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)|W tym artykule opisano sposób importu elementy, takie jak modułów i typów zawartości z istniejącej witryny programu SharePoint do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu programu SharePoint.|  
|[Stosowanie modułów podczas dołączania plików do rozwiązania](../sharepoint/using-modules-to-include-files-in-the-solution.md)|W tym artykule opisano sposób używania modułów, aby wdrożyć pliki z usługi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu do witryny programu SharePoint.|  
|[Przeglądanie połączeń SharePoint za pomocą Eksploratora serwera](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)|Opisuje sposób przeglądania lokalnych witryn programu SharePoint za pomocą Eksploratora serwera.|  
|[Podaj informacji opakowań i wdrażania w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)|Opisuje sposób używania właściwości elementu projektu w celu zapewnienia informacji opakowań i wdrażania projektów, takich jak wpisy kontroli bezpiecznego, odwołania do projektu danych wyjściowych i właściwości funkcji.|  
|[Instrukcje: Dodawanie i usuwanie folderów mapowanych](../sharepoint/how-to-add-and-remove-mapped-folders.md)|Opisuje jak mapowane foldery można dodać do projektu w celu zapewnienia łatwiejszego dostępu do zasobów programu SharePoint.|  
|[Uwagi dotyczące rozwiązania typu piaskownica](../sharepoint/sandboxed-solution-considerations.md)|W tym artykule opisano zagadnienia związane z rozwiązania w trybie piaskownicy.|  
|[Zabezpieczenia dla rozwiązań SharePoint](../sharepoint/security-for-sharepoint-solutions.md)|W tym artykule opisano zagadnienia dotyczące zabezpieczeń związane z opracowywaniem rozwiązań SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].|  
|[Okno dialogowe selektora URL &#40;programowanie SharePoint w programie Visual Studio&#41;](../sharepoint/url-picker-dialog-box-sharepoint-development-in-visual-studio.md)|W tym artykule opisano okno dialogowe, które służy do dodawania ścieżki odwołania do zasobów w projekcie lub na lokalnym serwerze programu SharePoint.|  
  
## <a name="see-also"></a>Zobacz także
 [Rozpoczynanie pracy &#40;programowanie SharePoint w programie Visual Studio&#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)   
 [Przeglądanie połączeń SharePoint za pomocą Eksploratora serwera](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Kompilowanie i debugowanie rozwiązań SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
