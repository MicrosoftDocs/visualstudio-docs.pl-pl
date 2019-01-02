---
title: Importowanie elementów z istniejącej witryny programu SharePoint | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.WSPImport.SelectionDependency
- VS.SharepointTools.WSPImport.SpecifyProjectSource
- VS.SharePointTools.WSPImport.SelectionItemsToImport
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, importing .wsp files
- importing items [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6345e6650c815242db661cef52b78db31d447b06
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53918157"
---
# <a name="import-items-from-an-existing-sharepoint-site"></a>Importowanie elementów z istniejącej witryny programu SharePoint
  Importowanie pakietu rozwiązań programu SharePoint szablon projektu umożliwia ponowne używanie elementów, takich jak typy zawartości i pola z istniejącej witryny programu SharePoint, w nowym [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozwiązania programu SharePoint. Chociaż można uruchomić najbardziej importowanych rozwiązania bez żadnych modyfikacji, istnieją pewnych ograniczeń i zagadnień, które należy wziąć pod uwagę, zwłaszcza wtedy, gdy modyfikować elementów po ich zaimportowaniu.  
  
> [!NOTE]  
>  Aby zaimportować przepływów danych wielokrotnego użytku, należy użyć szablonu projektu Importowanie przepływu pracy wielokrotnego użytku. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Wytyczne dotyczące importowania wielokrotnych przepływów danych](../sharepoint/guidelines-for-importing-reusable-workflows.md).  
  
## <a name="supported-sharepoint-solutions"></a>Obsługiwane rozwiązań SharePoint
 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] Importowanie rozwiązania utworzone w w pełni obsługuje [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] i [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].  
  
 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] nie obsługuje importowania rozwiązania utworzone w następujących aplikacjach:  
  
- [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)]  
  
- [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]  
  
- [!INCLUDE[vs_orcas_long](../sharepoint/includes/vs-orcas-long-md.md)]  
  
- Program Microsoft SharePoint Designer 2007  
  
- [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)]  
  
  Mimo że można często pomyślnie importować rozwiązań utworzonych przez te aplikacje, te funkcje jest nie przetestowane i nie jest obsługiwane.  
  
## <a name="item-import-restrictions"></a>Ograniczenia importu elementu
 Mimo że większość elementów programu SharePoint mogą zostać zaimportowane z istniejącego *.wsp* pliku, następujące elementy nie są obsługiwane i mogą wymagać modyfikacji działał prawidłowo:  
  
- Jednostki usługi łączności danych biznesowych  
  
- Kod elementy skojarzenia przepływu pracy  
  
- Przepływy pracy kodu  
  
- Wizualnego składnika Web Part (.ascx)  
  
- Usługi sieci Web (*.asmx*)  
  
- Powiązania typu zawartości  
  
- Odbiorcy zdarzeń  
  
- Definicje list (szablonów)  
  
- Definicje witryny  
  
  Podczas eksportowania rozwiązania z [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] lub [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)], te elementy są automatycznie wykluczane z *.wsp* pliku. Jednak inne *.wsp* pliki wygenerowane z nieobsługiwaną narzędzi może zawierać tych elementów. (Zobacz "Obsługiwane rozwiązania programu SharePoint" wcześniej w tym temacie).  
  
## <a name="what-happens-when-you-import-a-solution"></a>Co się dzieje w przypadku importowania rozwiązania
 Podczas importowania rozwiązania przy użyciu szablonu Importowanie pakietu rozwiązania programu SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kopiuje wszystkie zawartości *.wsp* zaimportowany plik i próbuje uzgodnić i zachować dowolną liczbę skojarzeń i odwołania między elementy i ich pliki, jak to możliwe.  
  
 Wszystkie zaimportowane elementy skopiować do odpowiednich folderów w **Eksploratora rozwiązań**. Na przykład, typy zawartości pojawiają się w folderze **typy zawartości** i wystąpienia listy są wyświetlane w obszarze **listy wystąpień**. Plików skojarzonych z importowany element również są kopiowane do folderu elementu. Na przykład wystąpienie listy importowanych obejmuje jego moduły, formularze i stron ASPX.  
  
### <a name="dependent-items"></a>Elementy zależne
 Jeśli wybierzesz element w Kreatorze Importowanie pakietu rozwiązań programu SharePoint, ale nie jego elementów zależnych okno komunikatu informujące o tym, że elementy zależne należy również zaznaczyć przed zaimportowaniem  
  
### <a name="what-are-features"></a>Jakie są funkcje?
 Program SharePoint Designer, użytkownicy mogą zobaczyć nieoczekiwany plikach o nazwie *funkcji*, pojawiają się w swoich rozwiązaniach importowanych w **Eksploratora rozwiązań.** Chociaż funkcje istniał w rozwiązaniu programu SharePoint Designer, zostały one ukryte w widoku. Funkcje są teraz widoczne w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
 Funkcje są kontenerami dla elementów programu SharePoint. Każda funkcja przechowuje odwołania do każdego elementu, takie jak typy zawartości i definicje list, które zawiera. Podczas importowania rozwiązania, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Ustawia funkcje wszystkie zaimportowane elementy i podejmuje próbę utrzymania relacji elementu funkcji dla plików. Wszystkie pliki, nie można rozpoznać odwołania do której są umieszczane w **inne zaimportowane pliki** folderu.  
  
 Aby uzyskać więcej informacji o funkcjach, zobacz [rozwiązań SharePoint opracowywanie](../sharepoint/developing-sharepoint-solutions.md) i [Praca z funkcjami](http://go.microsoft.com/fwlink/?LinkID=147704).  
  
### <a name="handle-special-cases"></a>Obsługa szczególnych przypadków
 W niektórych przypadkach program Visual Studio nie można uzgodnić elementu z jego plików zależnych. Wszystkie pliki, które [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nie można rozpoznać pojawiają się w folderze **inne zaimportowane pliki**. Ponadto ich **DeploymentType** właściwości są ustawione na **NoDeployment** tak, aby nie są wdrażane za pomocą rozwiązania.  
  
 Na przykład po zaimportowaniu definicji listy ExpenseForms definicji listy o tej nazwie pojawia się w obszarze **listy definicji** folderu w **Eksploratora rozwiązań** wraz z jego  *Elements.XML* i *Schema.xml* plików. Jednak jego powiązanych formularzy ASPX, jak i HTML można umieścić w folderze o nazwie **ExpenseForms** w obszarze **inne zaimportowane pliki** folderu. Aby ukończyć importowanie, przenosić tych plików, w ramach definicji listy ExpenseForms w **Eksploratora rozwiązań** i zmień **DeploymentType** właściwości dla każdego pliku z **NoDeployment** do **plik elementu**.  
  
 Podczas importowania odbiorcy zdarzeń *Elements.xml* plik jest kopiowany do poprawnej lokalizacji, ale musisz ręcznie dołączyć zestawu w pakiecie rozwiązań, dzięki czemu wdrażania za pomocą rozwiązania. [!INCLUDE[crabout](../sharepoint/includes/crabout-md.md)] jak to zrobić, zobacz [jak: Dodawanie i usuwanie zestawów dodatkowych](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
 Podczas importowania przepływów pracy, formularzy programu InfoPath są kopiowane do **inne zaimportowane pliki** folderu. Jeśli *.wsp* plik zawiera szablon sieci Web, jest ona ustawiona jako stronę startową w **Eksploratora rozwiązań**.  
  
## <a name="import-fields-and-property-bags"></a>Pola importowania i zbiory właściwości
 Podczas importowania rozwiązania, który ma wiele pól, wszystkie definicje osobnego pola są scalane w jednym *Elements.xml* plik w węźle w **Eksploratora rozwiązań** o nazwie **pola** . Podobnie, wszystkie wpisy zbioru właściwości są scalane w *Elements.xml* pliku pod węzeł o nazwie **PropertyBags**.  
  
 Pola w programie SharePoint są kolumn typu określone dane, takie jak tekst, Boolean lub wyszukiwania. Aby uzyskać więcej informacji, zobacz [bloków konstrukcyjnych: Kolumny i typy pól](http://go.microsoft.com/fwlink/?LinkId=182304). Zbiory właściwości umożliwiają dodawanie właściwości do obiektów w programie SharePoint, wszystkie elementy z farmy serwerów do listy w witrynie programu SharePoint. Zbiory właściwości są implementowane jako tabelę mieszania nazw właściwości i wartości. Aby uzyskać więcej informacji, zobacz [Zarządzanie konfiguracją programu SharePoint](http://go.microsoft.com/fwlink/?LinkId=182296) lub [ustawienia zbioru właściwości SharePoint](http://go.microsoft.com/fwlink/?LinkId=182297).  
  
## <a name="delete-items-in-the-project"></a>Usuwanie elementów projektu
 Większość elementów w rozwiązaniach programu SharePoint ma jeden lub więcej elementów zależnych. Na przykład wystąpienia listy są zależne od typów zawartości i typy zawartości są zależne od pola. Po zaimportowaniu rozwiązania programu SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nie powiadamia użytkownika o problemach odwołania w przypadku usunięcia elementu w rozwiązaniu, ale nie elementy zależne, dopóki próba wdrożenia rozwiązania. Na przykład jeśli rozwiązanie importowanych ma wystąpienie listy, który zależy od typu zawartości i usunięcie tego typu zawartości, na wdrożenie może wystąpić błąd. Ten błąd występuje, jeśli elementu zależnego nie znajduje się na serwerze programu SharePoint. Podobnie, jeśli usuniętego elementu ma również zbiór powiązanych właściwości, następnie usuń te wpisy zbiór właściwości z **PropertyBags** *Elements.xml* pliku. W związku z tym jeśli otrzymujesz błędy związane z wdrażaniem Usuń wszystkie elementy z zaimportowanych rozwiązania, sprawdź wszystkie elementy zależne muszą również zostaną usunięte.  
  
## <a name="restore-missing-feature-attributes"></a>Przywracanie brakujących atrybutów funkcji
 Podczas importowania rozwiązań, niektóre atrybuty opcjonalna funkcja zostały pominięte w manifeście funkcji zaimportowane. Jeśli chcesz przywrócić te atrybuty w nowym pliku funkcji, identyfikowanie brakujących atrybutów, porównując oryginalnego pliku funkcji do nowego manifestu funkcji i postępuj zgodnie z instrukcjami w temacie [jak: Dostosowywanie funkcji SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md).  
  
## <a name="deployment-conflict-detection-is-not-performed-on-built-in-list-instances"></a>Wykrywanie konfliktów wdrożenia nie jest wykonywana na wbudowane wystąpienia listy
 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] nie powoduje wykonania wykrywania konfliktów wdrożenia na wbudowane wystąpienia listy (oznacza to, domyślna lista wystąpienia, które pochodzą z programem SharePoint). Aby uniknąć zastąpienia wbudowane wystąpienia listy w programie SharePoint odbywa się nie wykonuje wykrywanie konfliktów. Listy wbudowanych, których wystąpienia są nadal wdrożone zaktualizowane, ale są nigdy nie usunięto lub zastąpione. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Rozwiązywanie problemów z pakowaniem i wdrażaniem SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).  
  
## <a name="import-sharepoint-server-2010-workflows"></a>Importowanie przepływów pracy programu SharePoint Server 2010
 Jeśli importujesz przepływ pracy w [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)], nie będzie ona działać poprawnie po wdrożeniu. Przepływ pracy nie działa poprawnie, ponieważ brak jest niektórych zestawów i [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] przepływy pracy zawierają formularze programu InfoPath, które nie są obecnie obsługiwane w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozwiązań przepływu pracy. Jednak zaimportować [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] przepływów pracy, może również działać poprawnie po zmianie niektóre elementy, takie jak dodanie odwołania do [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] zestawów i ponowne łączenie formularzy programu InfoPath. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Importowanie przepływów pracy programu SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=182226).  
  
## <a name="item-name-character-limit"></a>Limit liczby znaków nazwy elementów
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] obowiązuje limit 260 znaków całkowitą dla projektu i nazw elementów projektu, łącznie ze ścieżką. Podczas importowania rozwiązania, jeśli nazwa elementu przekracza ten limit, zostanie wyświetlony błąd:  
  
 **Określona ścieżka i nazwa pliku jest za długa. W pełni kwalifikowanej nazwy pliku musi być mniejsza niż 260 znaków, a nazwy katalogu musi być mniejsza niż 248 znaków.**  
  
 Jeśli ten błąd nie zostanie utworzony element. Ten problem występuje w większości przypadków z zaimportowanych modułów. Aby uniknąć tego problemu, wykonaj następujące czynności:  
  
-   Użyj krótkich nazw dla projektu, po wprowadzeniu je w **Dodaj nowy projekt** okno dialogowe.  
  
-   Utwórz projekt w lokalizacji co blisko folderu głównego, jak to możliwe, aby skrócić ścieżkę.  
  
## <a name="the-sharepointproductversion-attribute"></a>Atrybut SharePointProductVersion
 Jeśli importujesz rozwiązania utworzone we wcześniejszej wersji programu SharePoint, takich jak [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] lub [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)], zmień wartość atrybutu SharePointProductVersion w manifeście pakietu do 12.0 lub wstawić kontrolki Menedżera skryptów do wszystkich importowanych aplikacji sieci Web strony i pozostaw SharePointProductVersion Ustaw 14.0. W przeciwnym razie importowanych formularzy sieci Web nie będą wyświetlane w programie SharePoint.  
  
### <a name="background"></a>Tło  
 Rozwiązania w [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] i [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] dołączyć atrybut o nazwie SharePointProductVersion. Program SharePoint używa tego atrybutu w swoich manifestach pakietu można określić wersji rozwiązania jest przeznaczony dla programu SharePoint. Dwa prawidłowe wartości to 12.0 i 14.0. Wartość 12.0 wskazuje, że element jest przeznaczony dla [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] lub [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]; wartość 14.0 wskazuje, że element jest przeznaczony dla [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] lub [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].  
  
 Aby zwiększyć bezpieczeństwo podczas renderowania stron ASPX [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] i [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] wymagają, że wszystkie ASPX lub stron wzorcowych zawierają kontrolki Menedżera skryptów. Aby uzyskać więcej informacji na temat Menedżera skryptów zobacz [— informacje o formancie ScriptManager](http://go.microsoft.com/fwlink/?LinkID=169399). Ponieważ kontrolki Menedżera skryptów nie jest dostępna w [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] i [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)], jeden z nich muszą zostać dodane do żadnego [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] lub [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] strona, która została uaktualniona do [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] lub [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)]. Strony ASPX, które używają standardowych strony wzorcowej nie wymagają kontrolki Menedżera skryptów, ponieważ już jest dodawany do standardowej strony wzorcowej. Jednak stron ASPX, które nie korzystają z strony wzorcowej lub wykorzystujące niestandardową stronę wzorcową należy dodać formant script Aby móc pracować w [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] lub [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)].  
  
 Brak kontrolki Menedżera skryptów może to stanowić problem podczas importowania [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] lub [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] projektu do [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)], ponieważ 14.0 ma ustawioną wartość atrybutu SharePointProductVersion wszystkich nowych projektów. W przypadku wdrożenia uaktualniony projekt, który ma formularza sieci Web bez Menedżera skryptów formularza nie będą wyświetlane w programie SharePoint.  
  
## <a name="see-also"></a>Zobacz także
 [Przewodnik: Importowanie elementów z istniejącej witryny programu SharePoint](../sharepoint/walkthrough-import-items-from-an-existing-sharepoint-site.md)   
 [Wytyczne dotyczące importowania wielokrotnych przepływów danych](../sharepoint/guidelines-for-importing-reusable-workflows.md)   
 [Przewodnik: Importowanie przepływu pracy wielokrotnego użytku programu SharePoint Designer do Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)   
 [Instrukcje: Dodawanie istniejącego modelu BDC do projektu programu SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)  
