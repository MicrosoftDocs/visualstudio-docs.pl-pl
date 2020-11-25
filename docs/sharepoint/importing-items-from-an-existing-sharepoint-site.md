---
title: Importowanie elementów z istniejącej witryny programu SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9c2703bfdd4f47281a1fc19060cb69f8b312e7d2
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2020
ms.locfileid: "95970553"
---
# <a name="import-items-from-an-existing-sharepoint-site"></a>Importuj elementy z istniejącej witryny programu SharePoint
  Szablon projektu Importowanie pakietu rozwiązania SharePoint umożliwia ponowne używanie elementów, takich jak typy zawartości i pola z istniejących witryn programu SharePoint w nowym [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozwiązaniu programu SharePoint. Chociaż można uruchamiać większość zaimportowanych rozwiązań bez modyfikacji, istnieją pewne ograniczenia i problemy, które należy wziąć pod uwagę, szczególnie w przypadku modyfikacji wszelkich elementów po ich zaimportowaniu.

> [!NOTE]
> Aby zaimportować przepływy pracy wielokrotnego użytku, użyj szablonu projektu przepływu pracy wielokrotnego użytku. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Wytyczne dotyczące importowania przepływów pracy wielokrotnego użytku](../sharepoint/guidelines-for-importing-reusable-workflows.md).

## <a name="supported-sharepoint-solutions"></a>Obsługiwane rozwiązania programu SharePoint
 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] w pełni obsługuje importowanie rozwiązań utworzonych w [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] i [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] .

 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] Program nie obsługuje importowania rozwiązań utworzonych w następujących aplikacjach:

- [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)]

- [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)]

- [!INCLUDE[vs_orcas_long](../sharepoint/includes/vs-orcas-long-md.md)]

- Microsoft SharePoint Designer 2007

- [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)]

  Chociaż często można pomyślnie zaimportować rozwiązania utworzone przez te aplikacje, ta funkcja nie jest testowana i nie jest obsługiwana.

## <a name="item-import-restrictions"></a>Ograniczenia importowania elementów
 Chociaż większość elementów programu SharePoint można zaimportować z istniejącego pliku *. wsp* , następujące elementy nie są obsługiwane i mogą wymagać modyfikacji w celu poprawnego działania:

- Jednostki usługi BDC

- Elementy skojarzenia przepływu pracy kodu

- Przepływy pracy kodu

- Wizualne części sieci Web (. ascx)

- Usługi sieci Web (*. asmx*)

- Powiązania typu zawartości

- Odbiorcy zdarzeń

- Definicje list (szablony)

- Definicje lokacji

  Podczas eksportowania rozwiązania z [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] lub [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] , te elementy są automatycznie wykluczane z pliku *. wsp* . Jednak inne pliki *. wsp* wygenerowane z nieobsługiwanych narzędzi mogą zawierać te elementy. (Zobacz sekcję "obsługiwane rozwiązania programu SharePoint" wcześniej w tym temacie).

## <a name="what-happens-when-you-import-a-solution"></a>Co się stanie w przypadku zaimportowania rozwiązania
 Podczas importowania rozwiązania przy użyciu szablonu Importuj pakiet rozwiązania SharePoint program [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Kopiuje całą zawartość pliku *. wsp* i próbuje uzgodnić i zachować tyle skojarzeń i odwołań między importowanymi elementami i ich plikami, jak to możliwe.

 Wszystkie importowane elementy są kopiowane do odpowiednich folderów w **Eksplorator rozwiązań**. Na przykład typy zawartości są wyświetlane w obszarze **typy zawartości** folderu i wystąpienia list są wyświetlane w obszarze **listy wystąpienia**. Pliki skojarzone z zaimportowanym elementem są również kopiowane do folderu elementu. Na przykład wystąpienie importowanej listy zawiera swoje moduły, formularze i strony ASPX.

### <a name="dependent-items"></a>Elementy zależne
 W przypadku wybrania elementu w Kreatorze importowania pakietu rozwiązań programu SharePoint, ale nie jego elementów zależnych, w oknie komunikatu jest wyświetlany komunikat informujący o tym, że elementy zależne muszą być również wybrane przed zaimportowaniem.

### <a name="what-are-features"></a>Co to są funkcje?
 Użytkownicy programu SharePoint Designer mogą widzieć nieoczekiwane pliki o nazwie *Features*, które są wyświetlane w zaimportowanych rozwiązaniach w **Eksplorator rozwiązań.** Chociaż funkcje istniały w rozwiązaniu programu SharePoint Designer, były ukryte z widoku. Funkcje są teraz widoczne w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

 Funkcje są kontenerami dla elementów programu SharePoint. Każda funkcja zachowuje odwołanie do każdego elementu, takie jak typy zawartości i definicje list, które zawiera. Podczas importowania rozwiązania program [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] konfiguruje funkcje dla wszystkich importowanych elementów i próbuje zachować relacje między elementami dla plików. Wszystkie pliki, których odwołania nie mogą zostać rozpoznane, są umieszczane w folderze **inne importowane pliki** .

 Aby uzyskać więcej informacji na temat funkcji, zobacz [opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md) i [Praca z funkcjami](/previous-versions/office/developer/sharepoint-2010/ms460318(v=office.14)).

### <a name="handle-special-cases"></a>Obsługa specjalnych przypadków
 W niektórych przypadkach program Visual Studio nie może uzgodnić elementu z jego plikami zależnymi. Wszystkie pliki, które nie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mogły zostać rozpoznane, są wyświetlane w folderze **inne zaimportowane pliki**. Ponadto ich właściwości **DeploymentType** są ustawiane jako **NoDeployment** , tak że nie są wdrażane przy użyciu rozwiązania.

 Na przykład jeśli zaimportujesz definicję listy ExpenseForms, definicja listy o tej nazwie zostanie wyświetlona w folderze **definicje list** w **Eksplorator rozwiązań** wraz z plikami *Elements.xml* i *Schema.xml* . Jednak skojarzone z nimi ASPX i formularze HTML mogą być umieszczane w folderze o nazwie **ExpenseForms** w folderze **inne importowane pliki** . Aby ukończyć importowanie, przenieś te pliki pod definicję listy ExpenseForms w **Eksplorator rozwiązań** i zmień właściwość **DeploymentType** dla każdego pliku z **NoDeployment** na **elementu**.

 Podczas importowania odbiorców zdarzeń plik *Elements.xml* jest kopiowany do odpowiedniej lokalizacji, ale należy ręcznie dołączyć zestaw do pakietu rozwiązania, aby wdrożyć go w rozwiązaniu. [!INCLUDE[crabout](../sharepoint/includes/crabout-md.md)] jak to zrobić, zobacz [jak: Dodawanie i usuwanie dodatkowych zestawów](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

 Podczas importowania przepływów pracy formularze programu InfoPath są kopiowane do folderu **inne zaimportowane pliki** . Jeśli plik *. wsp* zawiera szablon sieci Web, jest ustawiany jako Strona startowa w **Eksplorator rozwiązań**.

## <a name="import-fields-and-property-bags"></a>Importowanie pól i toreb własności
 Po zaimportowaniu rozwiązania, które ma wiele pól, wszystkie oddzielne definicje pól są scalane w jeden plik *Elements.xml* w węźle **Eksplorator rozwiązań** o nazwie **pola**. Podobnie wszystkie wpisy zbioru właściwości są scalane do pliku *Elements.xml* w węźle o nazwie **PropertyBags**.

 Pola w programie SharePoint są kolumnami określonego typu danych, takimi jak tekst, wartość logiczna lub odnośnik. Aby uzyskać więcej informacji, zobacz [Budowanie bloku: kolumny i typy pól](/previous-versions/office/developer/sharepoint-2010/ee535893(v=office.14)). Torby właściwości umożliwiają dodawanie właściwości do obiektów w programie SharePoint, wszystko z farmy do listy w witrynie programu SharePoint. Torby właściwości są implementowane jako tablica skrótów nazw i wartości właściwości. Aby uzyskać więcej informacji, zobacz [Zarządzanie ustawieniami konfiguracji programu SharePoint](/previous-versions/msp-n-p/ff647766(v=pandp.10)) lub [zbiorem właściwości programu SharePoint](https://archive.codeplex.com/?p=pbs).

## <a name="delete-items-in-the-project"></a>Usuń elementy w projekcie
 Większość elementów w rozwiązaniach programu SharePoint ma jeden lub więcej elementów zależnych. Na przykład wystąpienia list zależą od typów zawartości i typów zawartości zależą od pól. Po zaimportowaniu rozwiązania programu SharePoint program nie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] powiadamia o problemach z odwołaniami w przypadku usunięcia elementu w rozwiązaniu, ale nie jego elementów zależnych, dopóki nie zostanie podjęta próba wdrożenia rozwiązania. Na przykład jeśli zaimportowane rozwiązanie ma wystąpienie listy, które zależy od typu zawartości i usuniesz ten typ zawartości, może wystąpić błąd podczas wdrażania. Ten błąd występuje, gdy element zależny nie jest obecny na serwerze programu SharePoint. Podobnie, jeśli usunięty element ma również powiązany zbiór właściwości, usuń te wpisy zbioru właściwości z pliku **PropertyBags** *Elements.xml* . W związku z tym po usunięciu wszelkich elementów z zaimportowanego rozwiązania i uzyskaniu błędów wdrożenia Sprawdź, czy wszystkie elementy zależne muszą być również usunięte.

## <a name="restore-missing-feature-attributes"></a>Przywróć brakujące atrybuty funkcji
 Podczas importowania rozwiązań niektóre opcjonalne atrybuty funkcji są pomijane z zaimportowanego manifestu funkcji. Jeśli chcesz przywrócić te atrybuty w nowym pliku funkcji, Zidentyfikuj brakujące atrybuty, porównując oryginalny plik funkcji z nowym manifestem funkcji i postępuj zgodnie z instrukcjami w temacie [How to: Dostosowywanie funkcji SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md).

## <a name="deployment-conflict-detection-is-not-performed-on-built-in-list-instances"></a>Wykrywanie konfliktów wdrożenia nie jest wykonywane na wbudowanych wystąpieniach list
 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] nie wykonuje wykrywania konfliktów wdrożenia w przypadku wbudowanych wystąpień list (czyli domyślnych wystąpień list, które są dostarczane z programem SharePoint). Wykrywanie konfliktów nie jest wykonywane, aby uniknąć zastępowania wbudowanych wystąpień list w programie SharePoint. Wbudowane wystąpienia list są nadal wdrażane lub aktualizowane, ale nigdy nie są usuwane ani zastępowane. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Rozwiązywanie problemów z pakietami i wdrażaniem programu SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).

## <a name="import-sharepoint-server-2010-workflows"></a>Importuj przepływy pracy programu SharePoint Server 2010
 Jeśli zaimportujesz przepływ pracy utworzony w programie [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] , nie zostanie on uruchomiony prawidłowo po wdrożeniu. Przepływ pracy nie działa prawidłowo, ponieważ brakuje niektórych zestawów, a  [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] przepływy pracy zawierają formularze programu InfoPath, które nie są obecnie obsługiwane w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozwiązaniach przepływu pracy. Jednak importowane [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] przepływy pracy mogą działać prawidłowo po naprawieniu niektórych elementów, takich jak Dodawanie odwołań do [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] zestawów i ponowne łączenie formularzy programu InfoPath. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Importowanie przepływów pracy programu SharePoint Server 2010](/sharepoint/dev/).

## <a name="item-name-character-limit"></a>Limit znaków nazwy elementu
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ma limit 260 znaków dla nazw projektu i projektu, łącznie z ścieżką. W przypadku importowania rozwiązania, jeśli nazwa elementu przekroczy ten limit, zostanie wyświetlony następujący błąd:

 **Określona ścieżka, nazwa pliku lub obie są zbyt długie. W pełni kwalifikowana nazwa pliku musi być krótsza niż 260 znaków, a nazwa katalogu musi być krótsza niż 248 znaków.**

 Po otrzymaniu tego błędu element nie zostanie utworzony. Ten problem występuje najczęściej w przypadku zaimportowanych modułów. Aby uniknąć tego problemu, wykonaj następujące czynności:

- Użyj krótkich nazw projektu, gdy wprowadzisz je w oknie dialogowym **Dodaj nowy projekt** .

- Utwórz projekt w lokalizacji jak najbliżej folderu głównego, aby skrócić ścieżkę.

## <a name="the-sharepointproductversion-attribute"></a>Atrybut SharePointProductVersion
 Jeśli zaimportujesz rozwiązanie utworzone we wcześniejszej wersji programu SharePoint, takie jak [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] lub [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] , Zmień wartość atrybutu SharePointProductVersion w manifeście pakietu na 12,0 lub Wstaw kontrolkę Menedżer skryptów do wszystkich zaimportowanych stron sieci Web i pozostaw SharePointProductVersion ustawioną na 14,0. W przeciwnym razie zaimportowane formularze sieci Web nie będą wyświetlane w programie SharePoint.

### <a name="background"></a>Tło
 Rozwiązania w [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] i [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] zawierają atrybut o nazwie SharePointProductVersion. Program SharePoint używa tego atrybutu w manifestach pakietu do określenia wersji programu SharePoint, dla której jest przeznaczone rozwiązanie. Dwie prawidłowe wartości to 12,0 i 14,0. Wartość 12,0 wskazuje, że element jest przeznaczony dla [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] lub [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] ; wartość 14,0 wskazuje, że element jest przeznaczony dla [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] lub [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] .

 W celu zwiększenia bezpieczeństwa podczas renderowania stron ASPX [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] i [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] wymagania, że wszystkie aspx lub strony wzorcowe zawierają kontrolkę Menedżer skryptów. Aby uzyskać więcej informacji na temat Menedżera skryptów, zobacz [kontrolka ScriptManager — Omówienie](/previous-versions/bb398863(v=vs.140)). Ponieważ kontrolka Menedżera skryptów była niedostępna w [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] i [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] , należy ją dodać do każdej [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] lub [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] strony uaktualnionej do [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] lub [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] . Strony ASPX korzystające ze standardowej strony wzorcowej nie wymagają kontrolki Menedżera skryptów, ponieważ jeden z nich został już dodany do standardowej strony wzorcowej. Jednak strony ASPX, które nie używają strony wzorcowej lub nie używają niestandardowej strony wzorcowej, muszą dodać kontrolkę skryptu w celu pracy w programie [!INCLUDE[wss_14_short](../sharepoint/includes/wss-14-short-md.md)] lub [!INCLUDE[moss_14_short](../sharepoint/includes/moss-14-short-md.md)] .

 Brak kontrolki Menedżera skryptów może być problemem podczas importowania [!INCLUDE[winshare3](../sharepoint/includes/winshare3-md.md)] [!INCLUDE[offshare7](../sharepoint/includes/offshare7-md.md)] projektu lub do [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] , ponieważ atrybut SharePointProductVersion dla wszystkich nowych projektów jest ustawiony na 14,0. W przypadku wdrożenia uaktualnionego projektu, który ma formularz sieci Web bez Menedżera skryptów, formularz nie będzie wyświetlany w programie SharePoint.

## <a name="see-also"></a>Zobacz też
- [Przewodnik: Importowanie elementów z istniejącej witryny programu SharePoint](../sharepoint/walkthrough-import-items-from-an-existing-sharepoint-site.md)
- [Wytyczne dotyczące importowania przepływów pracy wielokrotnego użytku](../sharepoint/guidelines-for-importing-reusable-workflows.md)
- [Przewodnik: Importowanie przepływu pracy wielokrotnego użytku programu SharePoint Designer do programu Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)
- [Instrukcje: Dodawanie istniejącego pliku modelu BDC do projektu programu SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
