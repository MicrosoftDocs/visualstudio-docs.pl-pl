---
title: Szablony elementów projektu i projektu programu SharePoint | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 2878bd2092e000cf63c2b4fcb531a502a470203e
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649225"
---
# <a name="sharepoint-project-and-project-item-templates"></a>Szablony projektów i elementów programu SharePoint
  W poniższych sekcjach opisano dostępne szablony projektów i elementów projektu programu SharePoint oraz sposób ich użycia.

## <a name="project-and-project-item-templates-overview"></a>Omówienie szablonów elementów projektu i projektu
 Podczas tworzenia nowego projektu programu SharePoint w programie Visual Studio projekt programu SharePoint jest dodawany do rozwiązania wraz ze wszystkimi elementami projektu wymaganymi przez ten typ projektu. Na przykład w przypadku utworzenia projektu składnika Web Part Silverlight program Visual Studio utworzy rozwiązanie zawierające element projektu visual web part i element projektu aplikacji Silverlight wraz ze wszystkimi plikami wymaganymi przez te elementy projektu. Szablony elementów projektu służą do dodawania elementów projektu do istniejącego projektu programu SharePoint, takich jak dodanie odbiornika zdarzeń, kolumny witryny lub listy.

 Aby uzyskać informacje o podstawach programu SharePoint, zobacz [Bloki konstrukcyjne programu SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ee534971(v=office.14)). Zaawansowani użytkownicy mogą tworzyć niestandardowe szablony elementów projektu i projektu. Aby uzyskać więcej informacji, zobacz [Rozszerzanie systemu projektów programu SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

## <a name="project-templates"></a>Szablony projektów
 Poniżej znajduje się lista szablonów projektów programu SharePoint. Aby wyświetlić szablony projektów programu SharePoint w programie Visual Studio, w oknie dialogowym **Nowy projekt** rozwiń węzeł **programu SharePoint** w obszarze **Visual C#** lub **Visual Basic**, a następnie wybierz pozycję **2010**.

### <a name="sharepoint-2010-project"></a>Projekt programu SharePoint 2010
 Zawartość programu *SharePoint 2010 Project* jest uwzględniona w każdym szablonie projektu programu SharePoint. Projekt programu SharePoint 2010 zawiera:

- Plik projektu.

- Strona właściwości projektu.

- Folder **Odwołania** zawiera listę wszystkich odwołań do zestawu w projekcie.

- Folder **Features** zawierający plik konfiguracyjny *funkcji* używany do wdrażania funkcji na serwerze programu SharePoint.

- Folder **Pakiet zawierający** plik *Package.package,* używany do wdrażania rozwiązania w programie SharePoint.

- Plik key.snk (klucz silnej nazwy), który jest używany do podpisywania zestawu o silnej nazwie, w celu zwiększenia bezpieczeństwa.

### <a name="sharepoint-2010-silverlight-web-part"></a>Część sieci Web programu SharePoint 2010 Silverlight
 Projekty *składników Web Part programu SharePoint 2010 Silverlight* umożliwiają tworzenie składników Web Part dla programu SharePoint, które wyświetlają aplikacje Silverlight. Podczas tworzenia tego projektu można określić, czy dodać do niego nową aplikację Silverlight, czy odwołać się do istniejącej. Aby uzyskać więcej informacji, zobacz [Tworzenie składników Web Part dla programu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) i [Przewodnik: Tworzenie składnika Web Part programu Silverlight, w których są wyświetlane informacje OData dla programu SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).

### <a name="sharepoint-2010-visual-web-part"></a>Visual web part programu SharePoint 2010
 Projekt *wizualnego składnika Web Part programu SharePoint 2010* zawiera plik definicji *Elements.xml,* element **składnika Web Part** i element Kontroli **użytkownika.** Wygląd wizualnego składnika Web Part można zaprojektować, przeciągając lub kopiując kontrolki z zestawu narzędzi Programu Visual Studio na powierzchnię formantu użytkownika. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie składnika Web Part programu SharePoint przy użyciu projektanta](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) i [bloku konstrukcyjnego: składniki Web Part](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

### <a name="import-sharepoint-2010-solution-package"></a>Importowanie pakietu rozwiązań programu SharePoint 2010
 *Importowanie projektów pakietu rozwiązań programu SharePoint 2010* umożliwia importowanie do programu Visual Studio całości lub części istniejącej witryny programu SharePoint 2010, eksportowanego do pliku rozwiązania programu SharePoint *(wsp).* Po zaimportowaniu do programu Visual Studio można dostosować jego elementy i ponownie je wdrożyć. Aby uzyskać więcej informacji, zobacz [Importowanie elementów z istniejącej witryny programu SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).

### <a name="import-reusable-sharepoint-2010-workflow"></a>Importowanie przepływu pracy programu SharePoint 2010 wielokrotnego rozmnażenia
 *Importowanie projektów przepływu pracy wielokrotnegoużytnia programu SharePoint 2010* umożliwia importowanie do programu Visual Studio przepływu pracy wielokrotnego rozstrzyżenia utworzonego w programie SharePoint Designer 2010. Przepływ pracy jest eksportowany z witryny programu SharePoint jako plik *wsp.* Po zaimportowaniu do programu Visual Studio można go dostosować, dodać do niego kod, a następnie wdrożyć w witrynie programu SharePoint. Aby uzyskać więcej informacji, zobacz [Przewodnik: Importowanie przepływu pracy wielokrotnego użytku programu SharePoint Designer do programu Visual Studio.](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)

## <a name="project-item-templates"></a>Szablony elementów projektu
 Poniżej znajduje się lista szablonów elementów projektu programu SharePoint. Szablony elementów projektu dodają pliki do rozwiązania programu SharePoint w celu obsługi funkcji programu SharePoint, takich jak kolumny witryny, listy i typy zawartości. Na przykład dodanie kolumny witryny do rozwiązania dodaje projekt kolumny witryny zawierający plik definicji *Elements.xml.* Dodanie wizualnego składnika Web Part dodaje wizualny projekt składnika Web Part do rozwiązania, który zawiera plik *Elements.xml,* element sterujący użytkownika i element wizualnego składnika Web Part.

 Aby wyświetlić szablony elementów projektu programu SharePoint, w **Eksploratorze rozwiązań**otwórz menu skrótów dla projektu programu SharePoint, a następnie wybierz pozycję **Dodaj**nowy **element**. Rozwiń węzeł **programu SharePoint** w obszarze **Visual C#** lub **Visual Basic**, a następnie wybierz pozycję **2010**.

### <a name="application-page-farm-solution-only"></a>Strona aplikacji (tylko rozwiązanie farmy)
 Element **strony aplikacji (Tylko rozwiązanie farmy)** umożliwia zaprojektowanie [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] strony sieci Web dla witryny programu SharePoint. Strony aplikacji mogą być używane tylko w rozwiązaniach rolniczych. Ten element projektu można dodać tylko do rozwiązań farmy. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie strony aplikacji](../sharepoint/how-to-create-an-application-page.md) i [typ strony aplikacji _layouts](/previous-versions/office/aa979604(v=office.14)).

### <a name="business-data-connectivity-model-farm-solution-only"></a>Model łączności danych biznesowych (tylko rozwiązanie farmy)
 Element **Modelu łączności danych biznesowych (Tylko rozwiązanie farmy)** umożliwia integrację danych biznesowych z programem SharePoint. Dane biznesowe mogą pochodzić z aplikacji [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)]serwera zaplecza, takich jak , Siebel i Service Advertising Protocol (SAP). Modele łączności danych biznesowych mogą być używane tylko w rozwiązaniach farm. Ten element projektu można dodać tylko do rozwiązań farmy. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie modelu BDC](../sharepoint/how-to-create-a-bdc-model.md), [Jak: Użyj pliku zasobu, aby określić zlokalizowane nazwy, właściwości i uprawnienia](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)oraz [Co nowego: Usługi łączności biznesowej](/previous-versions/office/developer/sharepoint-2010/ee534979(v=office.14)).

### <a name="content-type"></a>Typ zawartości
 *Elementy typu zawartości* umożliwiają tworzenie niestandardowych typów zawartości na podstawie istniejącego (podstawowego) typu zawartości, takiego jak dokument, anons lub zadanie. Niestandardowy typ zawartości zawiera te same atrybuty i pola co podstawowy typ zawartości wraz z dowolnymi kolumnami witryny (polami), które definiujesz. Na przykład można utworzyć niestandardowy typ zawartości kontaktu, który jest oparty na podstawowym typie zawartości kontaktu, który jest dostępny w programie SharePoint. Typ zawartości można dostosować, zmieniając istniejące kolumny witryny lub dodając więcej kolumn witryny do kolumn już uwzględnionych w podstawowym typie zawartości.

> [!NOTE]
> Ze względu na ograniczenie programu SharePoint nie można utworzyć typu zawartości rozwiązania farmy na podstawie typu zawartości rozwiązania w trybie piaskownicy.

 Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie kolumny witryny, typu zawartości i listy dla programu SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) i [bloku konstrukcyjnego: Typ zawartości](/previous-versions/office/developer/sharepoint-2010/ee535063(v=office.14)).

### <a name="empty-element"></a>Pusty element
 *Puste elementy* są najczęściej używane do definiowania elementów projektu programu SharePoint, które nie mają szablonu projektu lub elementu projektu w programie Visual Studio. Po dodaniu pustego elementu do projektu tworzony jest węzeł o nazwie EmptyElement[x](where [x] jest unikatowym numerem.\) EmptyElement[x] zawiera pojedynczy plik o nazwie *Elements.xml.* Instrukcje można używać [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] do definiowania żądanych elementów w pliku *Elements.xml*.

### <a name="event-receiver"></a>Odbiornik zdarzeń
 *Odbiorcy zdarzeń* obsługują zdarzenia dla elementów w witrynie programu SharePoint, na przykład gdy element jest dodawany do listy, gdy element sieci Web jest usuwany lub gdy uruchomiono przepływ pracy. Szablon elementu projektu odbiornika zdarzeń umożliwia obsługę

- Lista zdarzeń

- Lista zdarzeń elementu

- Wyświetlanie listy zdarzeń e-mail

- Wydarzenia internetowe

- Lista zdarzeń przepływu pracy

  Element projektu odbiornika zdarzeń tworzy folder **Odbiornik zdarzeń** z plikiem pojedynczej klasy zawierającym programy obsługi zdarzeń dla wszystkich zdarzeń określonych podczas tworzenia projektu w **Kreatorze dostosowywania programu SharePoint**. Klasa odbiornika zdarzeń może obsługiwać zdarzenia występujące w witrynie programu SharePoint, gdy elementy takie jak pliki, pola, elementy, listy, załączniki, składniki Web Part i przepływy pracy są dodawane, aktualizowane, usuwane lub usuwane. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie odbiornika zdarzeń](../sharepoint/how-to-create-an-event-receiver.md) i bloku [konstrukcyjnego: Obsługa zdarzeń](/previous-versions/office/developer/sharepoint-2010/ee535057(v=office.14)).

### <a name="list"></a>List
 Lista jest wystąpieniem definicji podstawowej listy programu SharePoint wielokrotnego użytkowania, takiej jak kalendarz lub lista zadań. Po dodaniu listy do rozwiązania Projektant listy umożliwia dodawanie kolumn witryny do listy i tworzenie niestandardowych kolumn listy. Obejmuje to kolumny witryny z typów zawartości. Można określić *widok* listy, który określa kolumny, które pojawią się na liście. Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie kolumny witryny, typu zawartości i listy dla programu SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) i [bloku konstrukcyjnego: listy i biblioteki dokumentów](/previous-versions/office/developer/sharepoint-2010/ee534985(v=office.14)).

### <a name="module"></a>Moduł
 *Moduły* (których nie [!include[vbprvb](../sharepoint/includes/vbprvb-md.md)] należy mylić z modułami) zawierają wszystkie pliki, które chcesz wdrożyć na serwerze programu SharePoint, takie jak obrazy lub notatki. Element projektu modułu zawiera **węzeł modułu.** Węzeł modułu zawiera dwa szablony elementów projektu: plik definicji XML, który działa jako manifest dla modułu, i plik *sample.txt,* plik zastępczy. Aby uzyskać więcej informacji, zobacz [Używanie modułów do dołączania plików do rozwiązania](../sharepoint/using-modules-to-include-files-in-the-solution.md) i [modułów](/previous-versions/office/developer/sharepoint-2010/ms453137(v=office.14)).

### <a name="sequential-workflow-farm-solution-only"></a>Sekwencyjny przepływ pracy (tylko rozwiązanie farmy)
 *Kolejny przepływ pracy* to seria kroków logiki biznesowej wykonywanych w sekwencji, aż do ukończenia ostatniego kroku. Sekwencyjne przepływy pracy są używane do zarządzania procesami, które obejmują elementy programu SharePoint, takie jak listy i dokumenty. Można utworzyć przepływy pracy na poziomie witryny (globalne) lub przepływy pracy na poziomie listy (lokalne) i wybrać, czy przepływ pracy rozpoczyna się automatycznie, czy ręcznie. Ten element projektu może być używany tylko w rozwiązaniach farmy. Ten element projektu można dodać tylko do rozwiązań farmy. Aby uzyskać więcej informacji, zobacz [Tworzenie rozwiązań przepływu pracy programu SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md), [Przepływy pracy w programie SharePoint Server 2010](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))i [Co nowego: Ulepszenia przepływu pracy](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14)).

### <a name="silverlight-web-part"></a>Część internetowa programu Silverlight
 Elementy projektu *składnika Web Part silverlight* umożliwiają tworzenie składników Web Part dla programu SharePoint, które wyświetlają aplikacje Silverlight. Po dodaniu tego elementu projektu do rozwiązania można wybrać, czy dodać nową aplikację Silverlight, czy odwołać się do istniejącej później. Aby uzyskać więcej informacji, zobacz [Tworzenie składników Web Part dla programu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) i [Przewodnik: Tworzenie składnika Web Part programu Silverlight, w których są wyświetlane informacje OData dla programu SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).

### <a name="site-column"></a>Kolumna Lokacja
 *Kolumna lokacji*, znana również jako *pole,* jest jednym z najbardziej podstawowych elementów, które można dodać do projektu programu SharePoint. Kolumna witryny reprezentuje typ danych, taki jak numer telefonu, komentarz tekstowy lub nazwa miasta kontaktu na liście kontaktów. Aby uzyskać więcej informacji, zobacz [Tworzenie kolumn witryny, typów zawartości i list dla programu SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md) i [Columns](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14)).

### <a name="site-definition-farm-solution-only"></a>Definicja witryny (tylko rozwiązanie farmy)
 Elementy projektu *definicji witryny* zawierają folder definicji witryny, który zawiera następujące pliki:

- Domyślna strona .aspx, używana jako domyślna strona internetowa witryny.

- Plik *onet.xml* definiujący składniki witryny.

- Plik xml webtemp określający konfiguracje definicji witryny wyświetlane w sekcji **Wybór szablonu** na stronie **Nowa witryna programu SharePoint.**

  Po dodaniu definicji witryny należy dodać kod i pliki w celu wprowadzenia funkcji. Ten element projektu może być używany tylko w rozwiązaniach farmy. Ten element projektu można dodać tylko do rozwiązań farmy. Aby uzyskać więcej informacji, zobacz [Tworzenie definicji witryn dla programu SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md) oraz [definicji i konfiguracji witryn .](/previous-versions/office/developer/sharepoint-2010/aa978512(v=office.14))

### <a name="state-machine-workflow-farm-solution-only"></a>Przepływ pracy maszyny stanu (tylko rozwiązanie farmy)
 *Przepływ pracy maszyny stanu* to zestaw stanów logiki biznesowej, przejść i akcji. Kroki w przepływie pracy maszyny stanu nie są wykonywane w sekwencji; zamiast tego są one wyzwalane przez działania i państwa. Podobnie jak sekwencyjny przepływ pracy, przepływy pracy komputera stanu są skojarzone z elementami programu SharePoint, takimi jak listy i dokumenty. Po raz kolejny można utworzyć przepływy pracy na poziomie witryny (globalne) lub przepływy pracy na poziomie listy (lokalne). Można również wybrać, czy przepływ pracy rozpoczyna się automatycznie, czy ręcznie. Ten element projektu może być używany tylko w rozwiązaniach farmy. Ten element projektu można dodać tylko do rozwiązań farmy. Aby uzyskać więcej informacji, zobacz [Tworzenie rozwiązań przepływu pracy programu SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md), [Przepływy pracy w programie SharePoint Server 2010](/previous-versions/office/developer/sharepoint-2010/ms549489(v=office.14))i [Co nowego: Ulepszenia przepływu pracy](/previous-versions/office/developer/sharepoint-2010/ee537015(v=office.14)).

### <a name="user-control-farm-solution-only"></a>Kontrola użytkownika (tylko rozwiązanie farmy)
 *Formant użytkownika* to niestandardowy formant wielokrotnego podawania, do którego można dodawać inne formanty ASP.NET i formanty programu SharePoint. Formant użytkownika można dodać do stron aplikacji i składników Web Part uruchamianych w programie SharePoint. Ten element projektu może być używany tylko w rozwiązaniach farmy. Ten element projektu można dodać tylko do rozwiązań farmy. Aby uzyskać więcej informacji, zobacz [Tworzenie formantów wielokrotnego użytku dla składników Web Part lub stron aplikacji](creating-reusable-controls-for-web-parts-or-application-pages.md).

### <a name="visual-web-part"></a>Wizualny składnik web part
 Element projektu *wizualnego składnika Web Part* zawiera plik definicji *Elements.xml,* element **składnika Web Part** i element Kontroli **użytkownika.** Wygląd wizualnego składnika Web Part można zaprojektować, przeciągając lub kopiując kontrolki z zestawu narzędzi Programu Visual Studio na powierzchnię formantu użytkownika. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie składnika Web Part programu SharePoint przy użyciu projektanta](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) i [bloku konstrukcyjnego: składniki Web Part](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

### <a name="web-part"></a>Web Part
 Składnik *web part* jest formantem po stronie serwera, który działa wewnątrz specjalnego typu strony o nazwie strona składników Web Part. Są one blokami konstrukcyjnymi stron wyświetlanych w witrynie programu SharePoint. Element składnika Web Part udostępnia pliki umożliwiające projektowanie składnika Web Part dla witryny programu SharePoint. Aby uzyskać więcej informacji, zobacz [Jak: Tworzenie składnika Web Part programu SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md) i [bloku konstrukcyjnego: Składniki Web Part](/previous-versions/office/developer/sharepoint-2010/ee535520(v=office.14)).

## <a name="see-also"></a>Zobacz też
- [Opracowywanie rozwiązań programu SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Produkty i technologie programu SharePoint](/previous-versions/office/developer/sharepoint-2010/dd776256(v=office.12))
