---
title: 'Przewodnik: Tworzenie składnika Web Part dla SharePoint za pomocą projektanta | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fa5817bb7c20cf58457281667dda76ac43608647
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875344"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint-by-using-a-designer"></a>Przewodnik: Tworzenie składnika web part programu SharePoint przy użyciu narzędzia Projektant

Jeśli tworzysz składniki web Part witryny programu SharePoint, użytkownicy bezpośrednio można modyfikować zawartość, wygląd i zachowanie stron w tej witrynie za pomocą przeglądarki. W tym instruktażu pokazano, jak utworzyć składnik web part wizualnie za pomocą programu SharePoint **wizualny składnik Web Part** szablonu projektu w programie Visual Studio.

Składnik web part, którą utworzysz Wyświetla miesięczny widok kalendarza i pola wyboru dla każdej listy kalendarza w witrynie. Użytkownicy mogą określić, które listy kalendarza do uwzględnienia w miesięcznym widoku kalendarza, wybierając pole wyboru.

W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie składnika web part za pomocą **wizualny składnik Web Part** szablonu projektu.
- Projektowanie składnika web part za pomocą projektanta Visual Web Developer w programie Visual Studio.
- Dodawanie kodu do obsługi zdarzeń formantów w części sieci web.
- Testowanie części sieci web w programie SharePoint.

    > [!NOTE]
    > Komputer może wyświetlać różne nazwy lub lokalizacje dla niektórych elementów interfejsu użytkownika dla programu Visual Studio, w poniższych instrukcjach. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Obsługiwane wersje systemu Windows i programu SharePoint.

## <a name="create-a-web-part-project"></a>Tworzenie projektu części sieci web

Najpierw utwórz projekt składnika WebPart za pomocą **wizualny składnik Web Part** szablonu projektu.

1. Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] przy użyciu **Uruchom jako Administrator** opcji.

2. Na pasku menu wybierz **pliku** > **New** > **projektu**.

     **Nowy projekt** pojawi się okno dialogowe.

3. W **nowy projekt** okno dialogowe, w obszarze **Visual C#** lub **języka Visual Basic**, rozwiń węzeł **Office/SharePoint**, a następnie wybierz polecenie  **Rozwiązania programu SharePoint** kategorii.

4. Z listy szablonów wybierz **SharePoint 2013 — wizualny składnik Web Part** szablonu, a następnie wybierz **OK** przycisku.

     **Kreator ustawień niestandardowych SharePoint** pojawia się. Za pomocą tego kreatora, można określić witryny, które będzie używane do debugowania projektu i poziomu zaufania rozwiązania.

5. W **co to jest poziom zaufania dla tego rozwiązania programu SharePoint?** wybierz pozycję **Wdróż jako rozwiązanie farmy** przycisku opcji.

6. Wybierz **Zakończ** przycisk, aby zaakceptować domyślne lokalnej witryny programu SharePoint.

## <a name="designing-the-web-part"></a>Projektowanie składnika web part

Projektowanie składnika web part przez dodanie formantów z **przybornika** do powierzchni projektanta Visual Web Developer.

1. W Projektancie Visual Web Developer wybierz **projektowania** kartę, aby przełączyć do widoku projektu.

2. Na pasku menu wybierz **widoku** > **przybornika**.

3. W **standardowa** węźle **przybornika**, wybierz **CheckBoxList** sterowania, a następnie wykonaj jedną z następujących czynności:

    - Otwórz menu skrótów dla **CheckBoxList** sterowania, wybierz **kopiowania**, otwórz menu skrótów dla pierwszego wiersza w projektancie, a następnie wybierz **Wklej**.

    - Przeciągnij **CheckBoxList** z kontrolować **przybornika**i Połącz formant do pierwszego wiersza w projektancie.

4. Powtórz poprzedni krok, ale przenieść przycisk do następnego wiersza projektanta.

5. W projektancie, wybierz **Button1** przycisku.

6. Na pasku menu wybierz **widoku** > **okno właściwości**.

     **Właściwości** zostanie otwarte okno.

7. W **tekstu** właściwości przycisku, wprowadź **aktualizacji**.

## <a name="handling-the-events-of-controls-on-the-web-part"></a>Obsługa zdarzeń formantów w części sieci web

Dodaj kod, który umożliwia użytkownikowi dodanie kalendarze w widoku kalendarza głównego.

1. Wykonaj jeden z następujących zestawów czynności:

   - W projektancie, kliknij dwukrotnie **aktualizacji** przycisku.

   - W **właściwości** okno **aktualizacji** przycisku, wybierz polecenie **zdarzenia** przycisku. W **kliknij** właściwości wprowadź **Button1_Click**, a następnie naciśnij klawisz Enter.

     Pliku kodu formanu użytkownika zostanie otwarty w edytorze kodu i `Button1_Click` pojawia się program obsługi zdarzeń. Później dodasz kod do tego programu obsługi zdarzeń.

2. Dodaj następujące instrukcje na górze pliku kodu formanu użytkownika.

     [!code-vb[SP_VisualWebPart#1](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_VisualWebPart#1](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]

3. Dodaj następujący wiersz kodu w celu `VisualWebPart1` klasy. Ten kod deklaruje kontrolę widoku kalendarza miesięcznego.

     [!code-vb[SP_VisualWebPart#2](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#2)]
     [!code-csharp[SP_VisualWebPart#2](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#2)]

4. Zastąp `Page_Load` metody `VisualWebPart1` klasy z następującym kodem. Kod będzie wykonywał następujące zadania:

   - Dodaje widok kalendarza miesięcznego do kontrolki użytkownika.

   - Dodaje pole wyboru dla każdej listy kalendarza w witrynie.

   - Określa szablon dla każdego typu elementu, który pojawia się w widoku kalendarza.

     [!code-vb[SP_VisualWebPart#3](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#3)]
     [!code-csharp[SP_VisualWebPart#3](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#3)]

5. Zastąp `Button1_Click` metody `VisualWebPart1` klasy z następującym kodem. Ten kod dodaje elementy z każdego wybranego kalendarza do nadrzędnego widoku kalendarza.

     [!code-vb[SP_VisualWebPart#4](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#4)]
     [!code-csharp[SP_VisualWebPart#4](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#4)]

## <a name="test-the-web-part"></a>Testowanie części sieci web

Kiedy uruchamiasz projekt, otwiera się witryna SharePoint. Składnik web part jest automatycznie dodawane do galerii Web Part w programie SharePoint. Aby przetestować ten projekt, wykonasz następujące zadania:

- Dodaj zdarzenie do każdego z dwóch osobnych list kalendarza.
- Dodaj składnik web part do strony składników web part.
- Określ listy do dołączenia w widoku kalendarza miesięcznego.

### <a name="to-add-events-to-calendar-lists-on-the-site"></a>Aby dodać zdarzenia do list kalendarza na stronie

1. W programie Visual Studio, wybierz **F5** klucza.

     Otwiera się witryna SharePoint i [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] na stronie zostanie wyświetlony pasek szybkiego uruchamiania.

2. Na pasku Szybkie uruchamianie w ramach **Wyświetla**, wybierz **kalendarza** łącza.

     **Kalendarza** zostanie wyświetlona strona.

     Jeśli użytkownik nie pojawi się łącze kalendarza na pasku szybkiego uruchamiania, wybierz opcję **zawartość witryny** łącza. Jeśli strona zawartości strony nie pokazuje **kalendarza** , należy go utworzyć.

3. Na stronie kalendarza wybierz dzień, a następnie wybierz **Dodaj** łącze w wybranym dniu, aby dodać wydarzenie.

4. W **tytuł** wprowadź **zdarzenia kalendarza domyślnego**, a następnie wybierz **Zapisz** przycisku.

5. Wybierz **zawartość witryny** łącze, a następnie wybierz **Dodaj aplikację** kafelka.

6. Na **Utwórz** wybierz **kalendarza** wpisz, nadaj nazwę kalendarzowi, a następnie wybierz **Utwórz** przycisku.

7. Dodaj zdarzenie do nowego kalendarza, określ nazwę zdarzenia **wydarzenia niestandardowego kalendarza**, a następnie wybierz **Zapisz** przycisku.

### <a name="to-add-the-web-part-to-a-web-part-page"></a>Aby dodać składnik web part do strony składników web part

1. Na **zawartość witryny** otwartą stronę **stron witryny** folderu.

2. Na Wstążce, wybierz **pliki** otwartą kartą **nowy dokument** menu, a następnie wybierz **strona składników Web Part** polecenia.

3. Na **nowej strony składników Web Part** strony, nazwij stronę **SampleWebPartPage.aspx**, a następnie wybierz **Utwórz** przycisku.

     Zostanie wyświetlona strona składników web part.

4. W strefie górnej strony składników web part, wybierz **Wstaw** kartę, a następnie wybierz **składnika Web Part** przycisku.

5. Wybierz **niestandardowe** folderu, wybierz **VisualWebPart1** składnika web part, a następnie wybierz **Dodaj** przycisku.

     Składnik web part jest wyświetlany na stronie. W części sieci web wyświetlane są następujące formanty:

    - Widok kalendarza miesięcznego.

    - **Aktualizacji** przycisku.

    - A **kalendarza** pole wyboru.

    - A **kalendarz niestandardowy** pole wyboru.

### <a name="to-specify-lists-to-include-in-the-monthly-calendar-view"></a>Aby określić listy zawarte w miesięcznym widoku kalendarza

W składniku web part, określ kalendarze, które chcesz uwzględnić w widoku kalendarza miesięcznego, a następnie wybierz **aktualizacji** przycisku.

Zdarzenia ze wszystkich kalendarzy określonych przez użytkownika są wyświetlane w widoku kalendarza miesięcznego.

## <a name="see-also"></a>Zobacz także

[Tworzenie składników web Part programu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)  
[Instrukcje: Tworzenie składnika web part programu SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)  
[Przewodnik: Tworzenie składnika web part programu SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
