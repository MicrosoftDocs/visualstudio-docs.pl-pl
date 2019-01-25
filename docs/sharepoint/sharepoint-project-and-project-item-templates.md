---
title: Szablony elementu projektu programu SharePoint i projektu | Dokumentacja firmy Microsoft
ms.date: 02/22/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SPE.FirstWizardPage
- VS.SharePointTools.SPE.ListInstance
- VS.SharePointTools.SPE.ListDefinition
- VS.SharePointTools.SPE.ListDefFromContentType
- VS.SharePointTools.SPE.ContentType
- SPE.Wizard
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, project and project item templates
- SharePoint development in Visual Studio, templates
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3f2479d58dfb8e1e28a2de230c0838ef8c8f3768
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54872202"
---
# <a name="sharepoint-project-and-project-item-templates"></a>Projekt SharePoint oraz szablony elementów projektu
  W poniższych sekcjach opisano dostępnych projektów programu SharePoint i elementu projektu, szablonów i sposobu ich używania. 
  
## <a name="project-and-project-item-templates-overview"></a>Projekt i przegląd szablonów elementów projektu
 Po utworzeniu nowego projektu programu SharePoint w programie Visual Studio projekt programu SharePoint jest dodawany do rozwiązania, które razem z wszystkich elementów projektu, wymagane przez tego typu projektu. Na przykład jeśli tworzysz projekt składnika Web Part Silverlight, Visual Studio tworzy rozwiązanie, które zawiera element wizualny składnik Web Part projektu i elementu projektu aplikacji Silverlight oraz wszystkie pliki, które są wymagane przez te elementy projektu. Szablony elementów projektu są używane do dodawania elementów projektu do istniejącego projektu programu SharePoint, takie jak dodanie odbiorcy zdarzeń kolumny witryny i listy.  
  
 Aby uzyskać informacji na temat podstaw programu SharePoint, zobacz [bloki konstrukcyjne programu SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=179404). Zaawansowani użytkownicy można utworzyć niestandardowy projekt oraz szablony elementów projektu. Aby uzyskać więcej informacji, zobacz [rozszerzanie systemu projektu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
## <a name="project-templates"></a>Szablony projektów
 Poniżej przedstawiono listę szablonów projektu programu SharePoint. Aby wyświetlić szablony projektów programu SharePoint w programie Visual Studio w **nowy projekt** okna dialogowego rozwiń **SharePoint** węźle albo **Visual C#**  lub  **Visual Basic**, a następnie wybierz **2010**.  
  
### <a name="sharepoint-2010-project"></a>Projekt programu SharePoint 2010
 Zawartość *projekt programu SharePoint 2010* znajdują się w każdym szablonie projektu programu SharePoint. Projekt programu SharePoint 2010 zawiera:  
  
-   Plik projektu.  
  
-   Strony właściwości projektu.  
  
-   A **odwołania** folder wyświetlania listy wszystkich odwołań do zestawów w projekcie.  
  
-   A **funkcji** folder, który zawiera *.feature* plik konfiguracji, używany do wdrażania funkcji na serwerze programu SharePoint.  
  
-   A **pakietu** folder, który zawiera *Package.package* plik, używany do wdrażania rozwiązania programu SharePoint.  
  
-   Plik key.snk (klucz silnej nazwy), który jest używany do podpisywania zestawu z mocną nazwą dla podnoszą poziom zabezpieczeń.  
  
### <a name="sharepoint-2010-silverlight-web-part"></a>Składnik web part programu SharePoint 2010 Silverlight
 *Składnik Web Part Silverlight programu SharePoint 2010* projektów umożliwiają tworzenie części sieci web programu SharePoint do wyświetlania aplikacji Silverlight. Podczas tworzenia tego projektu, można określić, czy należy dodać do niej nową aplikację Silverlight lub odwołaj się do istniejącego. Aby uzyskać więcej informacji, zobacz [utworzyć składniki web Part programu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) i [instruktażu: Tworzenie składnika web part programu Silverlight, na który wyświetlającego dane OData dla programu SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).  
  
### <a name="sharepoint-2010-visual-web-part"></a>SharePoint 2010 wizualny składnik web part
 A *składnik Web Part programu SharePoint 2010 Visual* projekt zawiera *Elements.xml* plik definicji **składnika Web Part** elementu, a **kontrolki użytkownika** elementu . Wygląd wizualnego składnika web part można zaprojektować przez przeciąganie lub kopiowanie kontrolki z przybornika programu Visual Studio na powierzchnię kontrolki użytkownika. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie części sieciowej SharePoint za pomocą projektanta](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) i [bloków konstrukcyjnych: Składniki Web Part](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
### <a name="import-sharepoint-2010-solution-package"></a>Importowanie pakietu rozwiązań programu SharePoint 2010
 *Importowanie pakietu rozwiązania programu SharePoint 2010* projektów pozwalają zaimportować całość lub część istniejącej witryny programu SharePoint 2010, wyeksportowane do rozwiązania programu SharePoint (*.wsp*) pliku do programu Visual Studio. Po zaimportowaniu do programu Visual Studio, można dostosować jego elementów i wdróż je ponownie. Aby uzyskać więcej informacji, zobacz [Importowanie elementów z istniejącej witryny SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
### <a name="import-reusable-sharepoint-2010-workflow"></a>Importowanie przepływu pracy wielokrotnego użytku programu SharePoint 2010
 *Importowanie wielokrotnego przepływu pracy programu SharePoint 2010* projektów umożliwiają importowanie przepływu pracy wielokrotnego użytku, deklaratywne utworzone w programie SharePoint Designer 2010 do programu Visual Studio. Przepływ pracy jest eksportowana z witryny programu SharePoint jako *.wsp* pliku. Po zaimportowaniu do programu Visual Studio, można go dostosować, dodać do niego kod i wdrożyć ją w witrynie programu SharePoint. Aby uzyskać więcej informacji, zobacz [instruktażu: Importowanie przepływu pracy wielokrotnego użytku programu SharePoint Designer do Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).  
  
## <a name="project-item-templates"></a>Szablony elementów projektu
 Poniżej przedstawiono listę szablonów elementów projektów programu SharePoint. Szablony elementów projektu Dodaj pliki do rozwiązania programu SharePoint do obsługi funkcji programu SharePoint, takich jak kolumny witryny, listy i typy zawartości. Na przykład dodawania kolumny witryny do rozwiązania dodaje projekt do kolumny witryny, który zawiera *Elements.xml* pliku definicji. Dodanie wizualny składnik web part powoduje dodanie projektu wizualnego składnika web part do rozwiązania, który zawiera *Elements.xml* plik, element kontrolki użytkownika i elementu wizualnego składnika web part.  
  
 Aby wyświetlić szablony elementów projektu programu SharePoint, w **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu programu SharePoint, a następnie wybierz **Dodaj**, **nowy element**. Rozwiń **SharePoint** węźle albo **Visual C#**  lub **języka Visual Basic**, a następnie wybierz **2010**.  
  
### <a name="application-page-farm-solution-only"></a>Strona aplikacji (tylko rozwiązanie farmy)
 **Strona aplikacji (tylko rozwiązanie farmy)** elementu pozwala projektować [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] strony sieci web, witryny programu SharePoint. Strony aplikacji mogą służyć tylko w rozwiązaniach farmy. Ten element projektu można dodać tylko do rozwiązania farmy. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie strony aplikacji](../sharepoint/how-to-create-an-application-page.md) i [układu aplikacji typ strony](http://go.microsoft.com/fwlink/?LinkId=179434).  
  
### <a name="business-data-connectivity-model-farm-solution-only"></a>Model usługi łączności danych biznesowych (tylko rozwiązanie farmy)
 A **modelu łączności danych biznesowych (tylko rozwiązanie farmy)** elementu umożliwia integrowanie danych biznesowych w programie SharePoint. Dane biznesowe mogą pochodzić z serwerów zaplecza aplikacji, takich jak [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)], Siebel i protokół reklamy usługi (SAP, Windows Management Instrumentation). Modeli usługi łączności danych biznesowych mogą służyć tylko w rozwiązaniach farmy. Ten element projektu można dodać tylko do rozwiązania farmy. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie modelu BDC](../sharepoint/how-to-create-a-bdc-model.md), [jak: Korzystanie z pliku zasobu do określania zlokalizowanych nazw, właściwości oraz uprawnień](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md), i [What's New: Usług łączności biznesowej](http://go.microsoft.com/fwlink/?LinkId=179411).  
  
### <a name="content-type"></a>Typ zawartości
 *Typ zawartości* elementy pozwalają tworzyć niestandardowe typy zawartości na podstawie istniejącego typu zawartości (podstawowy) takie jak dokument, anonsu lub zadania. Niestandardowy typ zawartości zawiera te same atrybuty i pola jako podstawowym typem zawartości wraz z dowolnej kolumny witryny (pola) można zdefiniować. Na przykład można utworzyć niestandardowe skontaktuj się z typem zawartości oparty na podstawowym typem zawartości kontaktu, których można użyć w programie SharePoint. Typ zawartości można dostosować, zmieniając istniejące kolumny witryny lub dodając większą liczbę kolumn witryny z tymi, które już uwzględniony w podstawowym typem zawartości.  
  
> [!NOTE]  
>  Ze względu na ograniczenie programu SharePoint nie można utworzyć farmę rozwiązania typu zawartości na podstawie typu zawartości rozwiązania w trybie piaskownicy.  
  
 Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie kolumny witryny, typu zawartości oraz list dla SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) i [bloków konstrukcyjnych: Typ zawartości](http://go.microsoft.com/fwlink/?LinkId=179413).  
  
### <a name="empty-element"></a>Pusty element
 *Puste elementy* są najczęściej używane do definiowania elementów projektu programu SharePoint, które nie mają projektu lub szablonu elementu projektu w programie Visual Studio. Po dodaniu pustego elementu do projektu, węzeł o nazwie EmptyElement [x](where [x] is a unique number\) is created. EmptyElement [x] zawiera pojedynczy plik oznacza to nazwane *Elements.xml.* Użyj [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] instrukcje, aby zdefiniować żądane elementy w *Elements.xml*.  
  
### <a name="event-receiver"></a>Odbiorcy zdarzeń
 *Odbiorcy zdarzeń* obsługi zdarzeń dla elementów w witrynie programu SharePoint, np. gdy element zostanie dodany do listy, w momencie usunięcia elementu sieci web lub podczas uruchamiania przepływu pracy. Szablonu elementu projektu odbiorcy zdarzeń pozwala obsługiwać  
  
- Wyświetl listę zdarzeń  
  
- Wyświetl listę zdarzeń elementów  
  
- Wyświetl listę zdarzeń poczty e-mail  
  
- Zdarzenia sieci Web  
  
- Wyświetl listę zdarzeń przepływu pracy  
  
  Tworzy element projektu odbiorcy zdarzeń **odbiorcy zdarzeń** folderu pliku jednej klasy, który zawiera obsługę zdarzeń dla wszystkich zdarzeń zostały określone podczas tworzenia projektu w **dostosowywania programu SharePoint Kreator**. Klasy odbiorcy zdarzeń może obsługiwać zdarzenia występujące w witrynie programu SharePoint, gdy elementy, takie jak pliki, pola, elementy, list, załączniki, składniki web Part i przepływy pracy są dodawane, aktualizowane, usunięty lub usunięte. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie obsługiwanego odbiornika](../sharepoint/how-to-create-an-event-receiver.md) i [bloków konstrukcyjnych: Obsługa zdarzeń](http://go.microsoft.com/fwlink/?LinkId=179416).  
  
### <a name="list"></a>Lista  
 Lista jest wystąpieniem wielokrotnego użytku podstawowej definicji listy programu SharePoint, takich jak kalendarz lub listy zadań. Po dodaniu listy do rozwiązania, Projektant listy umożliwia dodanie kolumn witryn do listy i tworzenia kolumny niestandardowej listy. Dotyczy to również kolumn witryny z typów zawartości. Można określić *widoku* dla listy, który decyduje o tym, które będą wyświetlane na liście kolumn. Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie kolumny witryny, typu zawartości oraz list dla SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) i [bloków konstrukcyjnych: List i bibliotek dokumentów](http://go.microsoft.com/fwlink/?LinkId=179421).  
  
### <a name="module"></a>Moduł  
 *Moduły* (nie należy mylić z [!include[vbprvb](../sharepoint/includes/vbprvb-md.md)] modułów) zawiera wszystkie pliki, które mają zostać wdrożone do serwera programu SharePoint, takie jak obrazy lub uwagi. Element projektu modułu zawiera **modułu** węzła. Węzeł modułu zawiera dwa szablony elementów projektu: plik definicji XML, który działa jako manifest modułu, a *przykład.txt* pliku, plik symbolu zastępczego. Aby uzyskać więcej informacji, zobacz [użycia modułów, aby dołączyć pliki w rozwiązaniu](../sharepoint/using-modules-to-include-files-in-the-solution.md) i [modułów](http://go.microsoft.com/fwlink/?LinkId=179425).  
  
### <a name="sequential-workflow-farm-solution-only"></a>Sekwencyjny przepływ pracy (tylko rozwiązanie farmy)
 A *sekwencyjnego przepływu pracy* to seria kroków logiki biznesowej, wykonywane w kolejności, aż do zakończenia ostatniego kroku. Sekwencyjne przepływy pracy są używane do zarządzania procesami, obejmujące elementy programu SharePoint, takich jak listy i dokumenty. Można tworzyć przepływy pracy (globalna) na poziomie witryny lub przepływów pracy (local) poziom listy i możesz wybrać, czy przepływ pracy jest uruchamiany automatycznie lub ręcznie. Tego elementu projektu może służyć tylko w rozwiązaniach farmy. Ten element projektu można dodać tylko do rozwiązania farmy. Aby uzyskać więcej informacji, zobacz [tworzenie rozwiązań programu SharePoint przepływ pracy](../sharepoint/creating-sharepoint-workflow-solutions.md), [przepływów pracy w programie SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=260555), i [What's New: Ulepszenia przepływu pracy](http://go.microsoft.com/fwlink/?LinkId=179418).  
  
### <a name="silverlight-web-part"></a>Składnik web part Silverlight
 *Składnik web part Silverlight* elementy projektu umożliwiają tworzenie części sieci web programu SharePoint do wyświetlania aplikacji Silverlight. Po dodaniu tego elementu projektu do rozwiązania, możesz wybrać, czy dodać nową aplikację Silverlight lub istniejącą odwołań w późniejszym czasie. Aby uzyskać więcej informacji, zobacz [utworzyć składniki web Part programu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) i [instruktażu: Tworzenie składnika web part programu Silverlight, na który wyświetlającego dane OData dla programu SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).  
  
### <a name="site-column"></a>Kolumna witryny
 A *kolumny witryny*, znane również jako *pola*, jest jednym z najprostszych elementów, które można dodać do projektu programu SharePoint. Kolumna witryny reprezentuje typ danych, takich jak numer telefonu, tekst komentarza lub nazwę miasta kontakt na liście kontaktów. Aby uzyskać więcej informacji, zobacz [Tworzenie kolumn witryn, typów zawartości oraz list dla SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md) i [kolumn](http://go.microsoft.com/fwlink/?LinkId=226840).  
  
### <a name="site-definition-farm-solution-only"></a>Definicja witryny (tylko rozwiązanie farmy)
 *Definicji witryny* elementy projektu zawierają folder definicji lokacji, która zawiera następujące pliki:  
  
- Domyślna strona .aspx, używana jako domyślna strona sieci web dla lokacji.  
  
- *Onet.xml* pliku, który definiuje składników lokacji.  
  
- Webtemp pliku xml, który określa konfiguracje definicji witryn, które pojawiają się w **wybór szablonu** części **nową witrynę programu SharePoint** strony.  
  
  Po dodaniu definicji witryny, należy dodać kod i pliki do wprowadzenia funkcji. Tego elementu projektu może służyć tylko w rozwiązaniach farmy. Ten element projektu można dodać tylko do rozwiązania farmy. Aby uzyskać więcej informacji, zobacz [Tworzenie definicji witryny dla SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md) i [definicji witryny i konfiguracje](http://go.microsoft.com/fwlink/?LinkId=260554).  
  
### <a name="state-machine-workflow-farm-solution-only"></a>Przepływ pracy automatu stanów (tylko rozwiązanie farmy)
 A *przepływ pracy automatu stanów* to zbiór business logic stany, przejścia i akcje. Kroki opisane w przepływ pracy automatu stanów nie są wykonywane w kolejności; Zamiast tego są wyzwalane przez działania i stanów. Podobnie jak sekwencyjnego przepływu pracy przepływów pracy automatu stanów są skojarzone z elementów programu SharePoint, takich jak listy i dokumenty. Jeszcze raz można tworzyć przepływy pracy (globalna) na poziomie witryny lub przepływów pracy (local) poziom listy. Możesz również wybrać, czy przepływ pracy jest uruchamiany automatycznie lub ręcznie. Tego elementu projektu może służyć tylko w rozwiązaniach farmy. Ten element projektu można dodać tylko do rozwiązania farmy. Aby uzyskać więcej informacji, zobacz [tworzenie rozwiązań programu SharePoint przepływ pracy](../sharepoint/creating-sharepoint-workflow-solutions.md), [przepływów pracy w programie SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=260555), i [What's New: Ulepszenia przepływu pracy](http://go.microsoft.com/fwlink/?LinkId=179418).  
  
### <a name="user-control-farm-solution-only"></a>Kontrolka użytkownika (tylko rozwiązanie farmy)
 A *kontrolki użytkownika* jest formantem niestandardowych, wielokrotnego użytku, do którego można dodać inne kontrolki ASP.NET oraz SharePoint. Kontrolki użytkownika można dodać do strony aplikacji i składników web Part, które są uruchamiane w programie SharePoint. Tego elementu projektu może służyć tylko w rozwiązaniach farmy. Ten element projektu można dodać tylko do rozwiązania farmy. Aby uzyskać więcej informacji, zobacz [tworzenie kontrolek wielokrotnego użytku dla części sieciowych lub stron aplikacji](http://go.microsoft.com/fwlink/?LinkId=226841).  
  
### <a name="visual-web-part"></a>Wizualny składnik web part
 A *wizualny składnik web part* element projektu zawiera *Elements.xml* plik definicji **składnika Web Part** elementu i **kontrolki użytkownika** elementu. Wygląd wizualnego składnika web part można zaprojektować przez przeciąganie lub kopiowanie kontrolki z przybornika programu Visual Studio na powierzchnię kontrolki użytkownika. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie części sieciowej SharePoint za pomocą projektanta](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) i [bloków konstrukcyjnych: Składniki Web Part](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
### <a name="web-part"></a>Web Part
 A *składnika web part* jest formantem po stronie serwera, który działa wewnątrz specjalny typ strony o nazwie strona składników Web Part. Są blokami konstrukcyjnymi stron, które pojawiają się w witrynie programu SharePoint. Element składnika web part zawiera pliki, które umożliwiają projektowanie składnika web part witryny programu SharePoint. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie składnika web part programu SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md) i [bloków konstrukcyjnych: Składniki Web Part](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
## <a name="see-also"></a>Zobacz także
 [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Produkty i technologie SharePoint](http://go.microsoft.com/fwlink/?LinkId=178818)  
