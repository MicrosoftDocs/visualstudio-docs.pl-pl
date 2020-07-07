---
title: 'Przewodnik: Importowanie elementów z istniejącej witryny programu SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 46bc2ceacfde599a70b4e84bba134c4a4d5f9757
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2020
ms.locfileid: "86017118"
---
# <a name="walkthrough-import-items-from-an-existing-sharepoint-site"></a>Przewodnik: Importowanie elementów z istniejącej witryny programu SharePoint
  W tym instruktażu przedstawiono sposób importowania elementów z istniejącej witryny programu SharePoint do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu programu SharePoint.

 W tym instruktażu przedstawiono następujące zadania:

- Dostosowywanie witryny programu SharePoint przez dodanie niestandardowej kolumny witryny (znanej również jako *pole*.

- Eksportowanie witryny programu SharePoint do pliku. wsp.

- Importowanie pliku wsp do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] programu SharePoint przy użyciu projektu import. wsp.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Obsługiwane wersje programów [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] i SharePoint.

- Program Visual Studio.

## <a name="customize-a-sharepoint-site"></a>Dostosowywanie witryny programu SharePoint
 W tym przykładzie utworzysz i dostosowano podwitrynę programu SharePoint, dodając do niej nową kolumnę lokacji i tworząc kolejną podlokację do użycia później. Później będziesz eksportować pierwszą podlokację do pliku. wsp, a następnie zaimportować kolumnę niestandardową do drugiej podlokacji przy użyciu projektu importu. wsp.

### <a name="to-create-and-customize-a-sharepoint-site"></a>Aby utworzyć i dostosować witrynę programu SharePoint

1. Otwórz witrynę programu SharePoint przy użyciu przeglądarki sieci Web, takiej jak http://<em>system Name</em>/SitePages/Home.aspx.

2. Utwórz podwitrynę z głównej witryny programu SharePoint, otwierając menu **Akcje witryny** , a następnie wybierając polecenie **Nowa lokacja**.

3. W oknie dialogowym **Tworzenie** witryny wybierz typ **pustej lokacji** .

4. W polu **tytuł** wprowadź **Test kolumna witryny 1**; w polu **nazwa adresu URL** wprowadź **columntest1**; Pozostaw wartości domyślne pozostałych ustawień; a następnie wybierz przycisk **Utwórz** .

5. Po utworzeniu lokacji przejdź z powrotem do witryny głównej w przeglądarce, http://<em>system Name</em>/SitePages/Home.aspx.

6. Ponownie Utwórz pustą lokację z głównej witryny programu SharePoint, otwierając menu **Akcje lokacji** , wybierając polecenie **Nowa lokacja**, a następnie wybierając pusty typ **lokacji** .

7. W polu **tytuł** wprowadź **Test kolumna witryny 2**. w polu **nazwa adresu URL** wprowadź **columntest2**; Pozostaw wartości domyślne pozostałych ustawień; a następnie wybierz przycisk **Utwórz** .

8. Przejdź z powrotem do pierwszej lokacji podrzędnej, http://<em>SystemName</em>/columntest1/default.aspx.

9. W menu **Akcje witryny** wybierz pozycję **Ustawienia witryny** , aby wyświetlić stronę Ustawienia witryny.

10. W sekcji **Galerie** wybierz łącze **kolumny witryny** .

11. W górnej części strony **Galeria kolumn witryny** wybierz przycisk **Utwórz** .

12. W polu **Nazwa kolumny** wprowadź wartość **kolumny test**, Zachowaj pozostałe wartości domyślne, a następnie wybierz przycisk **OK** .

13. Kolumna **kolumna testowa** zostanie wyświetlona pod nagłówkiem kolumny niestandardowe w galerii kolumn witryny.

## <a name="exporting-the-sharepoint-site"></a>Eksportowanie witryny programu SharePoint
 Następnie uzyskaj plik instalacyjny programu SharePoint (wsp), który zawiera elementy programu SharePoint i elementy, które chcesz zaimportować do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu programu SharePoint. Jeśli plik. wsp nie został jeszcze utworzony, należy go utworzyć z istniejącej witryny programu SharePoint. Na potrzeby tego przykładu będziesz eksportować domyślną witrynę programu SharePoint do pliku. wsp.

> [!IMPORTANT]
> Jeśli wystąpi błąd w czasie wykonywania poniższej procedury, należy wykonać procedurę w systemie, który ma dostęp do witryny programu SharePoint.

### <a name="to-export-an-existing-sharepoint-site"></a>Aby wyeksportować istniejącą witrynę programu SharePoint

1. W witrynie programu SharePoint wybierz pozycję **Ustawienia witryny** na karcie **Akcje witryny** , aby wyświetlić stronę Ustawienia witryny.

2. W sekcji **Akcje witryny** na stronie Ustawienia witryny wybierz łącze **Zapisz lokację jako szablon** .

3. W polu **Nazwa pliku** wprowadź **ExampleSite**i w polu **Nazwa szablonu** wprowadź **przykładową witrynę**.

4. Na potrzeby tego przykładu pozostaw wyczyść pole wyboru **Dołącz zawartość** .

     Jeśli zaznaczysz to pole, program [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zapisze wszystkie listy i biblioteki dokumentów oraz ich zawartość do pliku. wsp. Chociaż jest to przydatne w pewnych okolicznościach, nie jest to wymagane w tym przykładzie.

5. Po pomyślnym zakończeniu operacji wybierz łącze **Galeria rozwiązań** , aby wyświetlić plik. wsp.

     Aby wyświetlić stronę galerii rozwiązań później, otwórz menu **Akcje witryny** , wybierz pozycję **Ustawienia witryny**, wybierz łącze **Przejdź do ustawień lokacji najwyższego poziomu** w sekcji **Administracja zbiorem witryn** , a następnie wybierz link **rozwiązania** w sekcji **Galerie** .

6. W galerii rozwiązań wybierz łącze **ExampleSite** .

7. W oknie dialogowym **Pobieranie pliku** wybierz przycisk **Zapisz** , aby zapisać plik w systemie lokalnym, domyślnie w folderze pliki do pobrania.

## <a name="import-the-wsp-file"></a>Zaimportuj plik. wsp
 Teraz, gdy masz plik *. wsp* zawierający element, którego chcesz użyć ponownie (kolumna testu kolumny niestandardowej witryny), zaimportuj plik *. wsp* , aby uzyskać do niego dostęp.

### <a name="to-import-a-wsp-file"></a>Aby zaimportować plik. wsp

1. W programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] na pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt** , aby wyświetlić okno dialogowe **Nowy projekt** . Jeśli środowisko IDE jest ustawione na używanie Visual Basic ustawień deweloperskich, na pasku menu wybierz pozycję **plik**  >  **Nowy projekt**.

2. Rozwiń węzeł **SharePoint** w **Visual C#** lub **Visual Basic**, a następnie wybierz węzeł **2010** .

3. Wybierz szablon **pakiet rozwiązania programu SharePoint 2010** w okienku **Szablony** , pozostaw nazwę projektu jako WspImportProject1, a następnie wybierz przycisk **OK** .

    Zostanie wyświetlony **Kreator dostosowania programu SharePoint** .

4. Na stronie **Określanie poziomu lokacji i zabezpieczeń na potrzeby debugowania** wprowadź nazwę [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] dla drugiej utworzonej wcześniej witryny programu SharePoint. Do tej lokacji zostanie dodany nowy element pola niestandardowego http://o<em>nazwie systemowej</em>/columntest2.

5. W sekcji **co to jest poziom zaufania dla tego rozwiązania programu SharePoint?** pozostaw wybór jako **wdrożony jako rozwiązanie w trybie piaskownicy**.

6. Na stronie **Określanie źródła nowego projektu** przejdź do lokalizacji w systemie, w której wcześniej zapisano plik *. wsp* , a następnie wybierz przycisk **dalej** .

   > [!NOTE]
   > Po wybraniu przycisku **Zakończ** na tej stronie zostaną zaimportowane wszystkie dostępne elementy z pliku *. wsp* .

7. W polu **Wybierz elementy do zaimportowania** Wyczyść wszystkie pola wyboru na liście z wyjątkiem **kolumny test**, a następnie wybierz przycisk **Zakończ** .

    Ponieważ lista zawiera wiele elementów, możesz wybrać **kombinację klawiszy CTRL** + **A** , aby wybrać wszystkie elementy na liście, wybierz klawisz spacji, aby wyczyścić wszystkie pola wyboru, a następnie zaznacz pole wyboru obok elementu **kolumny test** .

    Po zakończeniu operacji importowania zostanie utworzony nowy projekt o nazwie **WspImportProject1** , który zawiera folder o nazwie **Fields**. W tym folderze znajduje się kolumna niestandardowa kolumna **testowa** kolumny i jej plik definicji *Elements.xml*.

## <a name="deploy-the-project"></a>Wdróż projekt
 Na koniec Wdróż **WspImportProject1** w drugiej podwitrynie programu SharePoint utworzonej wcześniej, aby wyświetlić kolumnę niestandardową.

### <a name="to-deploy-the-project"></a>Aby wdrożyć projekt

1. W programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Wybierz klawisz **F5** , aby wdrożyć i uruchomić projekt import *. wsp* .

2. W witrynie programu SharePoint otwórz menu **Akcje witryny** , a następnie wybierz pozycję **Ustawienia witryny** , aby wyświetlić stronę Ustawienia witryny.

3. W sekcji **Galerie** wybierz łącze **kolumny witryny** .

4. Przewiń w dół do sekcji **kolumny niestandardowe** .

     Zwróć uwagę, że na liście zostanie wyświetlona niestandardowa kolumna witryny zaimportowana z pierwszej witryny programu SharePoint.

## <a name="see-also"></a>Zobacz także
- [Importuj elementy z istniejącej witryny programu SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Tworzenie kontrolek wielokrotnego użytku dla części sieci Web lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
