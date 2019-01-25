---
title: 'Przewodnik: Tworzenie kolumny witryny, typu zawartości oraz listy dla SharePoint | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.ListDesigner.GeneralMessageHelp
- Microsoft.VisualStudio.SharePoint.Designers.ListDesigner.ViewModels.ListViewModel.SortingAndGrouping
- VS.SharePointTools.ListDesigner.SortingGrouping
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, list definitions
- SharePoint development in Visual Studio, list instances
- SharePoint development in Visual Studio, fields
- SharePoint development in Visual Studio, content types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9742f314ff3f2e6b980eaa2fd914def3b05e0a51
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874591"
---
# <a name="walkthrough-create-a-site-column-content-type-and-list-for-sharepoint"></a>Przewodnik: Tworzenie kolumny witryny, typu zawartości oraz list dla SharePoint
  Poniższe procedury przedstawiają sposób tworzenia kolumn niestandardowych witryny programu SharePoint — lub *pola*— a także typu zawartości, która korzysta z kolumny witryny. Pokazano również, jak utworzyć listę, która korzysta z nowego typu zawartości.  
  
 Ten instruktaż zawiera następujące zagadnienia:  
  
- [Tworzenie kolumny niestandardowej witryny](#BKMK_CreatingCustSiteCols).  
  
- [Tworzenie niestandardowego typu zawartości](#BKMK_CreateCustContType).  
  
- [Tworzenie listy](#BKMK_CreateList).  
  
- [Tworzenie listy](#BKMK_CreateList).  
  
- [Testowanie aplikacji](#BKMK_TestApp).  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   Obsługiwane wersje systemu Windows i programu SharePoint.
  
-   Program Visual Studio.  
  
## <a name="create-custom-site-columns"></a>Tworzenie kolumny niestandardowej witryny
 W tym przykładzie tworzy listę do zarządzania pacjentów w szpitalu. Najpierw należy utworzyć projekt programu SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] i Dodaj kolumny witryny, w następujący sposób.  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
1.  Na [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **pliku** menu, wybierz **New** > **projektu**.  
  
2.  W **nowy projekt** okno dialogowe, w obszarze **Visual C#** lub **języka Visual Basic**, rozwiń węzeł **SharePoint** węzła, a następnie wybierz polecenie **2010**.  
  
3.  W **szablony** okienku wybierz **projekt programu SharePoint 2010**, Zmień nazwę projektu, aby **Clinic**, a następnie wybierz **OK** przycisk.  
  
     Szablon projektu programu SharePoint 2010 jest pusty projekt, który jest używany w tym przykładzie ma zawierać kolumny witryny i innych elementów projektu, które są dodawane później.  
  
4.  Na **Określanie witryny i poziomu zabezpieczeń dla debugowania** strony, wprowadź adres URL lokalnej witryny programu SharePoint, do której chcesz dodać nowy element pole niestandardowe lub użyj domyślnej lokalizacji (`http://<`*SystemName* `>/)`.  
  
5.  W **co to jest poziom zaufania dla tego rozwiązania programu SharePoint?** sekcji, użyj wartości domyślnej **Wdróż jako rozwiązanie w trybie piaskownicy**.  
  
     Aby uzyskać więcej informacji o trybie piaskownicy oraz rozwiązaniami farmy, zobacz [uwagi dotyczące rozwiązania typu piaskownica](../sharepoint/sandboxed-solution-considerations.md).  
  
6.  Wybierz **Zakończ** przycisku. Projekt powinien teraz znajdować **Eksploratora rozwiązań**.  
  
#### <a name="to-add-site-columns"></a>Aby dodać kolumny witryny  
  
1.  Dodawanie nowej kolumny witryny. Aby to zrobić, w **Eksploratora rozwiązań**, otwórz menu skrótów dla **Clinic**, a następnie wybierz **Dodaj** > **nowy element**.  
  
2.  W **Dodaj nowy element** okna dialogowego wybierz **kolumny witryny**, Zmień nazwę na **nazwa pacjenta**, a następnie wybierz **Dodaj** przycisku.  
  
3.  W kolumnie witryny *Elements.xml* plików, pozostaw **typu** jako **tekstu**i zmień **grupy** ustawienie  **Kolumny witryny kliniki**. Po zakończeniu kolumny witryny *Elements.xml* plik powinien wyglądać podobnie jak w poniższym przykładzie.  
  
    ```xml  
    <Field  
         ID="{f9ba60d1-5631-41fb-b016-a38cf48eef63}"  
         Name="Clinic - Patient Name"  
         DisplayName="Patient Name"  
         Type="Text"  
         Required="FALSE"  
         Group="Clinic Site Columns">  
    </Field>  
    ```  
  
4.  Korzystając z tej samej procedury, należy dodać dwie kolumny witryny do projektu: **Identyfikator pacjentów** (typ = "Integer") i **nazwa lekarzem** (typ = "Text"). Ustaw wartość ich grupy **kolumny witryny kliniki**.  
  
## <a name="create-a-custom-content-type"></a>Tworzenie niestandardowego typu zawartości
 Następnie utwórz typ zawartości — na podstawie typu zawartości kontakty — zawierającej kolumny witryny, które zostały utworzone w poprzedniej procedurze. Użycie typu zawartości na istniejącego typu zawartości, można zaoszczędzić czas, ponieważ podstawowym typem zawartości zapewnia kilka kolumn witryn, do użytku w nowego typu zawartości.  
  
#### <a name="to-create-a-custom-content-type"></a>Aby utworzyć niestandardowy typ zawartości  
  
1.  Dodaj typ zawartości do projektu. Aby to zrobić, w **Eksploratora rozwiązań**, wybierz węzeł projektu  
  
2.  Na pasku menu wybierz **projektu** > **Dodaj nowy element**.  
  
3.  W obszarze **Visual C#** lub **języka Visual Basic**, rozwiń węzeł **SharePoint** węzła, a następnie wybierz **2010** węzła.  
  
4.  W **szablony** okienku wybierz **typu zawartości** szablonu, Zmień nazwę na **informacji pacjenta**, a następnie wybierz **Dodaj** przycisku.  
  
     **Kreator ustawień niestandardowych SharePoint** zostanie otwarty.  
  
5.  W **którego podstawowym typem zawartości powinien tego typu zawartości dziedziczyć** wybierz **skontaktuj się z pomocą** jako typ zawartości, na którym chcesz utworzyć nowy typ zawartości, a następnie wybierz **Zakończ**przycisku.  
  
     W ten sposób zapewnia dostęp do innych kolumn potencjalnie przydatne witryn, skontaktuj się z typu zawartości, oprócz kolumny witryny, które zostały wcześniej zdefiniowane.  
  
6.  Po typie zawartości pojawi się okno projektanta, w **kolumn** kartę, Dodaj trzy lokacji kolumn, które zostały wcześniej zdefiniowane: **Nazwa pacjentów**, **pacjentów identyfikator**, i **nazwa lekarzem**. Aby dodać te kolumny, wybierz na pierwszej liście, na liście kolumn witryn, w obszarze **nazwę wyświetlaną**, a następnie wybierz na liście jedną każdej kolumny witryny w danym momencie.  
  
    > [!TIP]  
    >  Aby wybrać kolumny witryny szybciej, filtrować listę, wprowadzając kilka pierwszych liter nazwy kolumny.  
  
7.  Oprócz trzy kolumny niestandardowej witryny, należy dodać **komentarze** kolumny witryny, listy kolumny witryny.  
  
8.  Wybierz **wymagane** pole wyboru obok **nazwa pacjenta** i **identyfikator pacjenta** kolumny witryny, aby były wymagane pola.  
  
9. Na **Content Type** i upewnij się, że nazwa typu zawartości jest **informacji pacjenta**, a następnie zmień opis, aby **karty informacji o pacjentach**.  
  
10. Zmiana **Nazwa grupy** do **typów zawartości kliniki**i pozostaw inne ustawienia ich wartości domyślne.  
  
11. Na pasku menu wybierz **pliku** > **Zapisz wszystko**, a następnie zamknij projektanta typu zawartości.  
  
## <a name="create-a-list"></a>Utwórz listę
 Teraz Utwórz listę, która używa nowej zawartości kolumny typu i witryny.  
  
#### <a name="to-create-a-list"></a>Aby utworzyć listę  
  
1.  Dodawanie listy do projektu. Aby to zrobić, w **Eksploratora rozwiązań**, wybierz węzeł projektu.  
  
2.  Na pasku menu wybierz **projektu** > **Dodaj nowy element**.  
  
3.  W obszarze **Visual C#** lub **języka Visual Basic**, rozwiń węzeł **SharePoint** węzła, a następnie wybierz **2010** węzła.  
  
4.  W **szablony** okienku wybierz **listy** szablonu, Zmień nazwę na **pacjentów**, a następnie wybierz **Dodaj** przycisku.  
  
5.  Pozostaw **dostosować tę listę na podstawie** jako **domyślne (pustego)**, a następnie wybierz **Zakończ** przycisku.  
  
6.  W Projektancie listy wybierz **typów zawartości** przycisk, aby wyświetlić **ustawienia typu zawartości** okno dialogowe.  
  
7.  Wybierz nowy wiersz, wybierz pozycję **informacji pacjenta** zawartości typu na liście typów zawartości, a następnie wybierz **OK** przycisku.  
  
     W ten sposób dodaje wszystkie kolumny witryny **informacji pacjenta** typu do listy zawartości.  
  
8.  Usuń wszystkie kolumny witryny, na liście, z wyjątkiem następujących czynności:  
  
    -   Identyfikator pacjentów  
  
    -   Nazwa pacjentów  
  
    -   Telefon domowy  
  
    -   Wiadomości e-Mail  
  
    -   Nazwa lekarzem  
  
    -   Komentarze  
  
9. W obszarze **Nazwa wyświetlana kolumny**, wybierz pusty wiersz, Dodawanie kolumny niestandardowej listy, a następnie nadaj mu nazwę **szpitali**. Pozostaw jego typu danych jako **pojedynczy wiersz tekstu**.  
  
     Kolumny listy niestandardowej ma zastosowanie tylko do tej listy. Po dodaniu niestandardowej listy kolumnę do listy nowy typ zawartości listy, w tym wszystkie kolumny, które są dodawane do listy, jest tworzone i Ustaw jako domyślną listę.  
  
    > [!TIP]  
    >  Jeśli wybierzesz kolumny na liście kolumn witryn, istniejącą kolumnę witryny jest używany. Jednak jeśli zostanie wprowadzona wartość nazwy kolumny bez wybierania żadnej kolumny na liście, kolumna Niestandardowa lista zostanie utworzony, nawet jeśli kolumna o takiej samej nazwie już istnieje na liście.  
  
     Opcjonalnie zamiast ustawienie typu danych kolumny niestandardowej listy, aby **pojedynczy wiersz tekstu**, zamiast tego można ustawić typ danych dla tej kolumny do wyszukiwania i jego wartości będzie można pobrać z tabelą ani innej listy. Dla informacji o kolumnach wyszukiwania, zobacz [relacji listy w programie SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=224994) i [wyszukiwań i relacje listy](http://go.microsoft.com/fwlink/?LinkID=224995).  
  
10. Obok pozycji **identyfikator pacjenta** i **nazwa pacjenta** pól, zaznacz **wymagane** pole wyboru.  
  
11. Na **widoków** karty, wybierz pusty wiersz, aby utworzyć widok. Wprowadź **szczegóły pacjenta**.  
  
     Na **widoków** karcie, można określić kolumny, które mają być wyświetlane na liście programu SharePoint.  
  
12. Wybierz nowy **szczegóły pacjenta** wiersza, a następnie wybierz **Ustaw jako domyślny** przycisku.  
  
     Nowy widok jest teraz domyślny widok listy.  
  
13. Dodaj następujące kolumny do **wybrane kolumny** listy w następującej kolejności:  
  
    -   Identyfikator pacjentów  
  
    -   Nazwa pacjentów  
  
    -   Telefon domowy  
  
    -   Wiadomości e-Mail  
  
    -   Nazwa lekarzem  
  
    -   Szpital  
  
    -   Komentarze  
  
14. W **właściwości** wybierz **sortowanie i grupowanie** właściwości, a następnie wybierz przycisk wielokropka ![ikonę wielokropka](../sharepoint/media/ellipsisicon.gif "ikonę wielokropka")do wyświetlenia **sortowanie i grupowanie** okno dialogowe.  
  
15. W **nazwa kolumny** , wybierz **pacjenta nazwa**, upewnij się, że **sortowanie** kolumny ustawiono **rosnąco**, a następnie wybierz polecenie  **OK** przycisku.  
  
## <a name="test-the-application"></a>Testowanie aplikacji
 Teraz, kolumny niestandardowe witryny, typu zawartości oraz listy będzie gotowe, wdróż je w programie SharePoint, a następnie uruchom aplikację do testowania.  
  
#### <a name="to-test-the-application"></a>Aby przetestować aplikację  
  
1.  Na pasku menu wybierz **pliku** > **Zapisz wszystko**.  
  
2.  Wybierz **F5** klawisz, aby uruchomić aplikację.  
  
     Kompilowania aplikacji, a następnie wdrożona w programie SharePoint i aktywować jego funkcji.  
  
3.  Na pasku Szybkie nawigowanie wybierz **pacjentów** łącze, aby wyświetlić **pacjentów** listy.  
  
     Nazwy kolumn na liście powinny być zgodne, które zostały wprowadzone **widoków** karcie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
4.  Wybierz **Dodaj nowy element** link, aby utworzyć kartę informacji pacjenta.  
  
5.  Wprowadź informacje w polach, a następnie wybierz **Zapisz** przycisku.  
  
     Nowy rekord pojawi się na liście.  
  
## <a name="see-also"></a>Zobacz także
 [Tworzenie kolumn witryn, typów zawartości oraz list dla SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)   
 [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Instrukcje: Tworzenie niestandardowego pola typu](http://go.microsoft.com/fwlink/?LinkId=192079)   
 [Typy zawartości](http://go.microsoft.com/fwlink/?LinkId=192080)   
 [Kolumny](http://go.microsoft.com/fwlink/?LinkId=192081)  
