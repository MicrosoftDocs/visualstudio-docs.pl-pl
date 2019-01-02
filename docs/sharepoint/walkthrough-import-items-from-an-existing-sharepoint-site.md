---
title: 'Przewodnik: Importowanie elementów z istniejącej witryny programu SharePoint | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 93e475a82ab862627c957a53ed2b3e2acae88b2d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53834038"
---
# <a name="walkthrough-import-items-from-an-existing-sharepoint-site"></a>Przewodnik: Importowanie elementów z istniejącej witryny programu SharePoint
  W tym instruktażu pokazano, jak importować elementy z istniejącej witryny programu SharePoint do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu programu SharePoint.  
  
 W tym instruktażu pokazano następujące zagadnienia:  
  
- Dostosowywanie witryny programu SharePoint przez dodanie kolumny niestandardowej witryny (znany także jako *pola*.  
  
- Eksportowanie witryny programu SharePoint w pliku wsp.  
  
- Importowanie plików .wsp do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] programu SharePoint przy użyciu WSP importowania projektu.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   Obsługiwane edycje [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] i programu SharePoint.  
  
-   Program Visual Studio.  
  
## <a name="customize-a-sharepoint-site"></a>Dostosowywanie witryny programu SharePoint
 W tym przykładzie utworzysz i dostosować podwitrynę programu SharePoint, dodając nowe kolumny witryny do niego i tworząc inną witrynę do użycia w przyszłości. Później będzie wyeksportować pierwszy podwitryny z plikiem WSP i zaimportowanie kolumny niestandardowej witryny do drugiego podwitryny przy użyciu WSP importowania projektu.  
  
#### <a name="to-create-and-customize-a-sharepoint-site"></a>Do tworzenia i dostosowywania witryny programu SharePoint  
  
1. Otwórz witrynę programu SharePoint, korzystając z przeglądarki internetowej, takiej jak http://<em>Nazwa systemowa</em>/SitePages/Home.aspx.  
  
2. Utwórz podwitryny zniżki w stosunku do głównego witryny programu SharePoint, otwierając **Akcje witryny** menu, a następnie wybierając **nowej lokacji**.  
  
3. W tej witrynie **Utwórz** okna dialogowego wybierz **pustej witryny** typu.  
  
4. W **tytuł** wprowadź **lokacji kolumny Test 1**; w **nazwa adresu URL** wprowadź **columntest1**; pozostaw inne ustawienia domyślne wartości. a następnie wybierz **Utwórz** przycisku.  
  
5. Po jej utworzeniu, przejdź w przeglądarce do lokacji głównej http://<em>Nazwa systemowa</em>/SitePages/Home.aspx.  
  
6. Ponownie utwórz pustą podwitrynę zniżki w stosunku do głównego witryny programu SharePoint, otwierając **Akcje witryny** menu, wybierając **nowej lokacji**, a następnie wybierając **pustej witryny** typu.  
  
7. W **tytuł** wprowadź **2 Test kolumny witryny**; w **nazwa adresu URL** wprowadź **columntest2**; pozostaw inne ustawienia domyślne wartości. a następnie wybierz **Utwórz** przycisku.  
  
8. Przejdź z powrotem do pierwszego podwitryny http://<em>SystemName</em>/columntest1/default.aspx.  
  
9. Na **Akcje witryny** menu, wybierz **ustawienia lokacji** można wyświetlić strony ustawień lokacji.  
  
10. W **galerie** wybierz pozycję **kolumny witryny** łącza.  
  
11. W górnej części **Galeria kolumny witryny** wybierz **Utwórz** przycisku.  
  
12. W **nazwa kolumny** wprowadź **kolumny testu**, Zachowaj wartości domyślne, a następnie wybierz **OK** przycisku.  
  
13. **Kolumny testu** kolumna jest wyświetlana w kolumnach niestandardowy nagłówek w galerii kolumny witryny.  
  
## <a name="exporting-the-sharepoint-site"></a>Eksportowanie witryny programu SharePoint
 Następnie uzyskaj plik Instalatora (wsp) programu SharePoint, który zawiera elementy programu SharePoint i elementy, które chcesz zaimportować do usługi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu programu SharePoint. Jeśli nie masz już plik .wsp, następnie można należy utworzyć z istniejącej witryny programu SharePoint. W tym przykładzie zostaną wyeksportowane domyślnej witryny programu SharePoint w pliku wsp.  
  
> [!IMPORTANT]  
>  Jeśli zostanie wyświetlony błąd środowiska uruchomieniowego, wykonując następującą procedurę, musisz wykonać procedurę na komputerze, który ma dostęp do witryny programu SharePoint.  
  
#### <a name="to-export-an-existing-sharepoint-site"></a>Aby wyeksportować istniejącej witryny programu SharePoint  
  
1.  W witrynie programu SharePoint wybierz **ustawienia lokacji** na **Akcje witryny** kartę, aby wyświetlić stronę ustawień lokacji.  
  
2.  W **Akcje witryny** sekcji strony Ustawienia lokacji wybierz **witrynę Zapisz jako szablon** łącza.  
  
3.  W **nazwy pliku** wprowadź **ExampleSite**, a następnie w **Nazwa szablonu** wprowadź **przykład witryny**.  
  
4.  W tym przykładzie należy pozostawić **dołączanie zawartości** wyczyść pole wyboru.  
  
     Jeśli zaznaczysz to pole [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] zapisuje wszystkie listy i biblioteki dokumentów i ich zawartość w pliku wsp. Mimo że jest to przydatne w pewnych okolicznościach, nie jest to wymagane dla tego przykładu.  
  
5.  Po pomyślnym zakończeniu operacji, wybierz **Galeria rozwiązań** link, aby wyświetlić plik .wsp.  
  
     Aby wyświetlić stronę Galeria rozwiązań nowszy, otwórz **Akcje witryny** menu, wybierz **ustawienia lokacji**, wybierz **przejdź do obszaru Ustawienia lokacji najwyższego poziomu** łącze w  **Administracja zbiorem lokacji** sekcji, a następnie wybierz **rozwiązania** łącze w **galerie** sekcji.  
  
6.  W galerii rozwiązań wybierz **ExampleSite** łącza.  
  
7.  W **pobieranie pliku** okna dialogowego wybierz **Zapisz** przycisk, aby zapisać plik w systemie lokalnym domyślnie w folderze pobrane.  
  
## <a name="import-the-wsp-file"></a>Importuj plik .wsp
 Teraz, gdy masz *.wsp* pliku, który zawiera element, który chcesz ponownie użyć (niestandardową witrynę kolumna kolumny testu), importowanie *.wsp* plik, aby uzyskać do niego dostęp.  
  
#### <a name="to-import-a-wsp-file"></a>Aby zaimportować plik .wsp  
  
1. W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], na pasku menu wybierz **pliku** > **New** > **projektu** do wyświetlenia **nowy projekt**okno dialogowe. Jeśli środowisko IDE jest ustawione do użycia ustawienia programowania Visual Basic, na pasku menu, wybierz opcję **pliku** > **nowy projekt**.  
  
2. Rozwiń **SharePoint** węźle albo **Visual C#** lub **języka Visual Basic**, a następnie wybierz **2010** węzła.  
  
3. Wybierz **Importowanie pakietu rozwiązań programu SharePoint 2010** szablonu w **szablony** okienko, pozostaw nazwę projektu jako WspImportProject1, a następnie wybierz **OK** przycisk.  
  
    **Kreator ustawień niestandardowych SharePoint** pojawia się.  
  
4. Na **Określanie witryny i poziomu zabezpieczeń dla debugowania** wpisz [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] dla drugiego podwitrynę programu SharePoint, utworzony wcześniej. Doda nowe niestandardowe pola elementu http://<em>Nazwa systemowa</em>/columntest2 do danej podwitryny.  
  
5. W **co to jest poziom zaufania dla tego rozwiązania programu SharePoint?** sekcji, pozostaw ustawienie **Wdróż jako rozwiązanie w trybie piaskownicy**.  
  
6. W **Określanie nowego źródła projektu** strony, przejdź do lokalizacji w systemie, w której zapisano *.wsp* wcześniej pliku, a następnie wybierz **dalej** przycisku.  
  
   > [!NOTE]  
   >  Jeśli wybierzesz **Zakończ** przycisku na tej stronie, a wszystkie dostępne elementy w *.wsp* można zaimportować pliku.  
  
7. W **Wybieranie elementów do zaimportowania** polu, usuń zaznaczenie wszystkich pól wyboru na liście, z wyjątkiem **kolumny testu**, a następnie wybierz **Zakończ** przycisku.  
  
    Ponieważ lista zawiera wiele elementów, można wybrać **Ctrl**+**A** kluczy, aby wybrać wszystkie elementy na liście, naciśnij klawisz spacji, aby wyczyścić wszystkie pola wyboru, a następnie wybierz tylko sprawdzanie obok pola **kolumny testu** elementu.  
  
    Po zakończeniu operacji importu, nowy projekt o nazwie **WspImportProject1** utworzeniu zawiera folder o nazwie **pola**. W tym folderze jest kolumny niestandardowej witryny **kolumny testu** i jego pliku definicji *Elements.xml*.  
  
## <a name="deploy-the-project"></a>Wdrażanie projektu
 Na koniec wdrażanie **WspImportProject1** programu SharePoint w drugiej lokacji podrzędnych utworzony wcześniej w celu wyświetlenia kolumny niestandardowej witryny.  
  
#### <a name="to-deploy-the-project"></a>Aby wdrożyć projekt  
  
1.  W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], wybierz **F5** klawisz, aby wdrożyć i uruchomić *.wsp* Importuj projekt.  
  
2.  W witrynie programu SharePoint, otwórz **Akcje witryny** menu, a następnie wybierz **ustawienia lokacji** można wyświetlić strony ustawień lokacji.  
  
3.  W **galerie** wybierz pozycję **kolumny witryny** łącza.  
  
4.  Przewiń w dół do **kolumn niestandardowych** sekcji.  
  
     Należy zauważyć, że kolumny niestandardowej witryny, która został zaimportowany z pierwszej lokacji programu SharePoint pojawia się na liście.  
  
## <a name="see-also"></a>Zobacz także
 [Importowanie elementów z istniejącej witryny programu SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Tworzenie formantów wielokrotnych dla części sieciowych lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
