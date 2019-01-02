---
title: 'Przewodnik: Tworzenie rozszerzenia projektu SharePoint | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 39432f20620a3c7e6f374b09943fc73c2d4d2903
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53885903"
---
# <a name="walkthrough-create-a-sharepoint-project-extension"></a>Przewodnik: Tworzenie rozszerzenia projektu SharePoint
  W tym instruktażu pokazano, jak można utworzyć rozszerzenia dla projektów programu SharePoint. Rozszerzenie projektu można użyć w celu reagowania na zdarzenia na poziomie projektu na przykład w przypadku projektu jest dodane, usunięte lub zmieniono jego nazwę. Można również dodać właściwości niestandardowe lub reagować po zmianie wartości właściwości. W przeciwieństwie do rozszerzenia elementu projektu projektu rozszerzenia nie może być skojarzony z określonego typu projektu programu SharePoint. Podczas tworzenia rozszerzenia projektu rozszerzenia ładuje po otwarciu dowolnego rodzaju projektu programu SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 W tym przewodniku utworzysz niestandardowego właściwość typu Boolean, który zostanie dodany do każdego projektu programu SharePoint, utworzone w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Po ustawieniu **True**, dodaje nową właściwość lub mapy, obrazy folder zasobów do projektu. Po ustawieniu **False**, folder obrazów zostanie usunięty, jeśli taki istnieje. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie i usuwanie folderów mapowanych](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
 W tym instruktażu pokazano następujące zagadnienia:  
  
-   Tworzenie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozszerzenia dla projektów programu SharePoint, które wykonuje następujące czynności:  
  
    -   Dodaje właściwość niestandardowego projektu do okna właściwości. Właściwość ma zastosowanie do każdego projektu programu SharePoint.  
  
    -   Używa modelu obiektu projektu programu SharePoint, aby dodawać zamapowany folder do projektu.  
  
    -   Używa [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] modelu obiektu automatyzacji (DTE), aby usunąć zmapowany folder z projektu.  
  
-   Tworzenie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pakietu rozszerzenia (VSIX) do wdrażania zestawu rozszerzeń właściwości projektu.  
  
-   Debugowanie i testowanie właściwości projektu.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Potrzebne są następujące składniki na komputerze deweloperskim w celu przeprowadzenia tego instruktażu:  
  
-   Obsługiwane edycje [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)], SharePoint i [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. W tym instruktażu wykorzystano **projekt VSIX** szablonu w [!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)] utworzyć pakiet VSIX do wdrożenia rozszerzenia właściwości projektu. Aby uzyskać więcej informacji, zobacz [Rozszerzanie narzędzi SharePoint w programie Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="create-the-projects"></a>Tworzenie projektów
 Do przeprowadzenia tego instruktażu, należy utworzyć dwa projekty:  
  
- Projekt VSIX do stworzenia pakietu VSIX, aby wdrożyć rozszerzenie projektu.  
  
- Projekt biblioteki klas, który implementuje rozszerzenie projektu.  
  
  Instruktaż należy rozpocząć od utworzenia projektów.  
  
#### <a name="to-create-the-vsix-project"></a>Aby utworzyć projekt VSIX  
  
1.  Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na pasku menu wybierz **pliku** > **New** > **projektu**.  
  
3.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **języka Visual Basic** węzłów, a następnie wybierz **rozszerzalności** węzła.  
  
    > [!NOTE]  
    >  Ten węzeł jest dostępny tylko w przypadku instalowania programu Visual Studio SDK. Aby uzyskać więcej informacji zobacz sekcję wymagania wstępne niniejszego tematu.  
  
4.  W górnej części okna dialogowego wybierz **.NET Framework 4.5** na liście wersji programu .NET Framework, a następnie wybierz **projekt VSIX** szablonu.  
  
5.  W **nazwa** wprowadź **ProjectExtensionPackage**, a następnie wybierz **OK** przycisku.  
  
     **ProjectExtensionPackage** projekt, który jest wyświetlany w **Eksploratora rozwiązań**.  
  
#### <a name="to-create-the-extension-project"></a>Aby utworzyć projekt rozszerzenia  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla węzła rozwiązanie, wybierz pozycję **Dodaj**, a następnie wybierz **nowy projekt**.  
  
2.  W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **języka Visual Basic** węzłów, a następnie wybierz **Windows**.  
  
3.  W górnej części okna dialogowego wybierz **.NET Framework 4.5** na liście wersji programu .NET Framework, a następnie wybierz **biblioteki klas** szablonu projektu.  
  
4.  W **nazwa** wprowadź **ProjectExtension**, a następnie wybierz **OK** przycisku.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dodaje **ProjectExtension** projektu do rozwiązania i otwiera plik domyślny kodu Class1.  
  
5.  Usuń plik kodu Class1 z projektu.  
  
## <a name="configure-the-project"></a>Konfigurowanie projektu
 Przed przystąpieniem do napisania kodu w celu tworzenie rozszerzenia projektu, Dodaj pliki kodu i odwołania do zestawów do projektu rozszerzenia.  
  
#### <a name="to-configure-the-project"></a>Aby skonfigurować projekt  
  
1.  Dodaj plik kodu, który nosi nazwę **właściwości niestandardowej** do projektu ProjectExtension.  
  
2.  Otwórz menu skrótów dla **ProjectExtension** projektu, a następnie wybierz **Dodaj odwołanie**.  
  
3.  W **Menadżer odwołań - właściwości niestandardowej** okna dialogowego wybierz **Framework** węzeł, a następnie zaznacz pole wyboru obok zestawów elementy System.ComponentModel.Composition i przestrzeń nazw System.Windows.Forms.  
  
4.  Wybierz **rozszerzenia** węzeł, zaznacz pole wyboru obok zestawów Microsoft.VisualStudio.SharePoint i EnvDTE, a następnie wybierz **OK** przycisku.  
  
5.  W **Eksploratora rozwiązań**w obszarze **odwołania** folder **ProjectExtension** projektu, wybierz **EnvDTE**.  
  
6.  W **właściwości** oknie zmiany **Osadź typy współdziałania** właściwości **False**.  
  
## <a name="define-the-new-sharepoint-project-property"></a>Zdefiniuj nowe właściwości projektu programu SharePoint
 Utwórz klasę, która określa rozszerzenie projektu i zachowaniem nowe właściwości projektu. Aby zdefiniować nowe rozszerzenia projektu, klasa implementuje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interfejsu. Zawsze, gdy chcesz zdefiniować rozszerzenie dla projektu programu SharePoint, należy zaimplementować ten interfejs. Ponadto Dodaj <xref:System.ComponentModel.Composition.ExportAttribute> do klasy. Ten atrybut umożliwia [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] wykrycie i załadowanie swoje <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> implementacji. Przekaż <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> typu konstruktora atrybutu.  
  
#### <a name="to-define-the-new-sharepoint-project-property"></a>Aby zdefiniować właściwość projektu programu SharePoint  
  
1.  Wklej następujący kod do pliku kodu właściwości niestandardowej.  
  
     [!code-vb[SPExt_ProjectExtension#1](../sharepoint/codesnippet/VisualBasic/projectextension/customproperty.vb#1)]
     [!code-csharp[SPExt_ProjectExtension#1](../sharepoint/codesnippet/CSharp/projectextension/customproperty.cs#1)]  
  
## <a name="build-the-solution"></a>Skompiluj rozwiązanie
 Następnie Kompiluj rozwiązanie, aby upewnić się, że kompiluje bez błędów.  
  
#### <a name="to-build-the-solution"></a>Aby skompilować rozwiązanie  
  
1.  Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**.  
  
## <a name="create-a-vsix-package-to-deploy-the-project-property-extension"></a>Utwórz pakiet VSIX do wdrożenia rozszerzenia właściwości projektu
 Aby wdrożyć rozszerzenie projektu, należy użyć projektu VSIX w rozwiązaniu, aby utworzyć pakiet VSIX. Najpierw należy skonfigurować pakiet VSIX modyfikując plik source.extension.vsixmanifest, który znajduje się w projekcie VSIX. Następnie należy utworzyć pakiet VSIX przez utworzenie rozwiązania.  
  
#### <a name="to-configure-and-create-the-vsix-package"></a>Aby skonfigurować i utworzyć pakiet VSIX  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla pliku source.extension.vsixmanifest, a następnie wybierz **Otwórz** przycisku.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otwiera plik w Projektancie manifestu. Informacje wyświetlane w **metadanych** karta pojawia się również w **rozszerzenia i aktualizacje**. Wszystkie pakiety VSIX wymagają pliku extension.vsixmanifest. Aby uzyskać więcej informacji na temat tego pliku, zobacz [odwołania 1.0 schematu rozszerzenia VSIX](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
2.  W **nazwa produktu** wprowadź **niestandardowa właściwość projektu**.  
  
3.  W **Autor** wprowadź **Contoso**.  
  
4.  W **opis** wprowadź **właściwość niestandardowa projektu programu SharePoint, która włącza/wyłącza mapowania folderu zasobów obrazów do projektu**.  
  
5.  Wybierz **zasoby** kartę, a następnie wybierz **New** przycisku.  
  
     **Dodaj nowy zasób** pojawi się okno dialogowe.  
  
6.  W **typu** wybierz **Microsoft.VisualStudio.MefComponent**.  
  
    > [!NOTE]  
    >  Ta wartość odpowiada `MEFComponent` elementu w pliku extension.vsixmanifest. Ten element Określa nazwę zestawu rozszerzeń w pakiecie VSIX. Aby uzyskać więcej informacji, zobacz [MEFComponent — Element (schemat VSX)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\)).  
  
7.  W **źródła** wybierz **projekt w bieżącym rozwiązaniu** przycisku opcji.  
  
8.  W **projektu** wybierz **ProjectExtension**.  
  
     Ta wartość Określa nazwę zestawu, który tworzysz w projekcie.  
  
9. Wybierz **OK** zamknąć **Dodaj nowy zasób** okno dialogowe.  
  
10. Na pasku menu wybierz **pliku** > **Zapisz wszystko** kiedy zakończyć, a następnie zamknij projektanta manifestu.  
  
11. Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**, a następnie upewnij się, że projekt kompiluje bez błędów.  
  
12. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **ProjectExtensionPackage** projektu, a następnie wybierz **Otwórz Folder w Eksploratorze plików** przycisku.  
  
13. W **Eksploratora plików**Otwórz folder wyjściowy kompilacji dla projektu ProjectExtensionPackage, a następnie sprawdź, czy folder zawiera plik o nazwie ProjectExtensionPackage.vsix.  
  
     Domyślnie folderem wyjściowym kompilacji jest... folderze \bin\Debug w folderze, który zawiera plik projektu.  
  
## <a name="test-the-project-property"></a>Testowanie właściwości projektu
 Teraz możesz przystąpić do testowania właściwości niestandardowego projektu. Najłatwiej przeprowadzić debugowanie i testowanie nowe rozszerzenie właściwości projektu w eksperymentalnym wystąpieniu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. To wystąpienie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] jest tworzona po uruchomieniu VSIX lub innych projektów rozszerzalności. Po debugowania projektu, można zainstalować rozszerzenia w systemie i następnie kontynuuj debugować i testować je w regularnym wystąpieniu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
#### <a name="to-debug-and-test-the-extension-in-an-experimental-instance-of-visual-studio"></a>Aby debugować i testować rozszerzenia w eksperymentalnym wystąpieniu programu Visual Studio  
  
1.  Uruchom ponownie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] przy użyciu poświadczeń administracyjnych, a następnie otwórz rozwiązanie ProjectExtensionPackage.  
  
2.  Uruchom kompilację debugowania projektu, przez wybranie **F5** klucza lub na pasku menu, wybierając **debugowania** > **Rozpocznij debugowanie**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Instaluje rozszerzenia do %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom Property\1.0 projekt i uruchamia doświadczalne wystąpienie programu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
3.  W doświadczalnym wystąpieniu programu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], Utwórz projekt programu SharePoint w taki sposób, aby uzyskać rozwiązanie farmy i użyj wartości domyślnych dla innych wartości w kreatorze.  
  
    1.  Na pasku menu wybierz **pliku** > **New** > **projektu**.  
  
    2.  W górnej części **nowy projekt** okna dialogowego wybierz **.NET Framework 3.5** na liście wersji programu .NET Framework.  
  
         Rozszerzenia narzędzi programu SharePoint wymagają funkcji w tej wersji programu [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].  
  
    3.  W obszarze **szablony** węzła, rozwiń **Visual C#** lub **języka Visual Basic** węzła, wybierz **programu SharePoint** węzła, a następnie wybierz polecenie **2010** węzła.  
  
    4.  Wybierz **projekt programu SharePoint 2010** szablonu, a następnie wprowadź **ModuleTest** jako nazwę projektu.  
  
4.  W **Eksploratora rozwiązań**, wybierz **ModuleTest** węzeł projektu.  
  
     Nową właściwość niestandardową **Folder Obrazy mapy** pojawia się w **właściwości** okna z wartością domyślną **False**.  
  
5.  Zmień wartość tej właściwości, aby **True**.  
  
     Folderu zasobów obrazów jest dodawany do projektu programu SharePoint.  
  
6.  Zmień wartość właściwości z powrotem do **False**.  
  
     Jeśli wybierzesz **tak** znajdujący się w **Usuń folder obrazów?** okno dialogowe, obrazów, zasób folder zostanie usunięty z projektu programu SharePoint.  
  
7.  Zamknij wystąpienie doświadczalne programu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Zobacz także
 [Rozszerzanie projektów SharePoint](../sharepoint/extending-sharepoint-projects.md)   
 [Instrukcje: Dodawanie właściwości do projektów SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Konwertowanie pomiędzy typami systemu projektu SharePoint a innymi typami projektu Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Zapisywanie danych w rozszerzeniach systemu projektu SharePoint](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Kojarzenie danych niestandardowych z rozszerzeniami narzędzi SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
