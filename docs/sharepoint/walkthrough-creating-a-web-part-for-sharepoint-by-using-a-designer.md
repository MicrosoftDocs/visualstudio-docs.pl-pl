---
title: Tworzenie składnika Web Part dla programu SharePoint przy użyciu narzędzia Projektant
description: W tym instruktażu należy utworzyć składnik Web Part wizualnie przy użyciu szablonu projektu Visual Web Part programu SharePoint w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 02a0eb7c9279aef1fd2821d44a6f3cc4a0008356
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847755"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint-by-using-a-designer"></a>Przewodnik: Tworzenie składnika Web Part dla programu SharePoint przy użyciu narzędzia Projektant

Jeśli tworzysz składniki Web Part dla witryny programu SharePoint, użytkownicy będą mogli bezpośrednio modyfikować zawartość, wygląd i zachowanie stron w tej witrynie za pomocą przeglądarki. W tym instruktażu pokazano, jak utworzyć składnik Web Part wizualnie przy użyciu szablonu projektu **Visual Web Part** programu SharePoint w programie Visual Studio.

Tworzony składnik Web Part wyświetla widok kalendarza miesięcznego i pole wyboru dla każdej listy kalendarzy w witrynie. Użytkownicy mogą określić listę kalendarzy do uwzględnienia w widoku kalendarza miesięcznego, zaznaczając pola wyboru.

W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie składnika Web Part przy użyciu szablonu projektu **Visual Web Part** .
- Projektowanie składnika Web Part za pomocą projektanta Visual Web Developer w programie Visual Studio.
- Dodawanie kodu do obsługi zdarzeń formantów w części sieci Web.
- Testowanie części sieci Web w programie SharePoint.

    > [!NOTE]
    > W przypadku niektórych elementów interfejsu użytkownika dla programu Visual Studio na komputerze mogą być wyświetlane różne nazwy lub lokalizacje. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Obsługiwane wersje systemu Windows i programu SharePoint.

## <a name="create-a-web-part-project"></a>Tworzenie projektu części sieci Web

Najpierw utwórz projekt składnika Web Part przy użyciu szablonu projektu **Visual Web Part** .

1. Zacznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] od użycia opcji **Uruchom jako administrator** .

2. Na pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**.

     Zostanie wyświetlone okno dialogowe **Nowy projekt**.

3. W oknie dialogowym **Nowy projekt** w obszarze **Visual C#** lub **Visual Basic** rozwiń węzeł **Office/SharePoint**, a następnie wybierz kategorię **rozwiązania SharePoint** .

4. Na liście szablonów wybierz szablon **SharePoint 2013-Visual Web Part** , a następnie wybierz przycisk **OK** .

     Zostanie wyświetlony **Kreator dostosowania programu SharePoint** . Za pomocą tego kreatora można określić lokację, która będzie używana do debugowania projektu i poziomu zaufania rozwiązania.

5. W sekcji **co to jest poziom zaufania dla tego rozwiązania programu SharePoint?** wybierz przycisk opcji **Wdróż jako farmę** .

6. Wybierz przycisk **Zakończ** , aby zaakceptować domyślną lokalną witrynę programu SharePoint.

## <a name="designing-the-web-part"></a>Projektowanie składnika Web Part

Zaprojektuj składnik Web Part poprzez dodanie kontrolek z **przybornika** do powierzchni projektanta Visual Web Developer.

1. W programie Visual Web Developer Designer wybierz zakładkę **projekt** , aby przełączyć się do widok Projekt.

2. Na pasku menu wybierz **Widok**  >  **Przybornik**.

3. W węźle **Standardowy** **przybornika** Wybierz kontrolkę **formant CheckBoxList** , a następnie wykonaj jedną z następujących czynności:

    - Otwórz menu skrótów dla kontrolki **formant CheckBoxList** , wybierz polecenie **Kopiuj**, otwórz menu skrótów dla pierwszego wiersza w projektancie, a następnie wybierz **Wklej**.

    - Przeciągnij kontrolkę **formant CheckBoxList** z **przybornika** i Połącz formant z pierwszym wierszem w projektancie.

4. Powtórz poprzedni krok, ale Przenieś przycisk do następnego wiersza projektanta.

5. W Projektancie wybierz przycisk **Button1** .

6. Na pasku menu wybierz   >  **okno właściwości** widoku.

     Zostanie otwarte okno **Właściwości** .

7. We właściwości **Text** przycisku wprowadź **Update**.

## <a name="handling-the-events-of-controls-on-the-web-part"></a>Obsługa zdarzeń formantów w części sieci Web

Dodaj kod, który umożliwia użytkownikowi dodawanie kalendarzy do widoku kalendarza głównego.

1. Wykonaj jeden z następujących zestawów czynności:

   - W projektancie kliknij dwukrotnie przycisk **Aktualizuj** .

   - W oknie **Właściwości** dla przycisku **Aktualizuj** wybierz przycisk **zdarzenia** . We właściwości **kliknij** wprowadź **Button1_Click**, a następnie wybierz klawisz ENTER.

     Plik kodu kontrolnego użytkownika otwiera się w edytorze kodu i `Button1_Click` pojawia się procedura obsługi zdarzeń. Później dodasz kod do tej procedury obsługi zdarzeń.

2. Dodaj następujące instrukcje na górze pliku kodu kontrolki użytkownika.

     [!code-vb[SP_VisualWebPart#1](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_VisualWebPart#1](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]

3. Dodaj następujący wiersz kodu do `VisualWebPart1` klasy. Ten kod deklaruje formant widoku kalendarza miesięcznego.

     [!code-vb[SP_VisualWebPart#2](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#2)]
     [!code-csharp[SP_VisualWebPart#2](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#2)]

4. Zastąp `Page_Load` metodę `VisualWebPart1` klasy następującym kodem. Ten kod wykonuje następujące zadania:

   - Dodaje widok kalendarza miesięcznego do kontrolki użytkownika.

   - Dodaje pole wyboru dla każdej listy kalendarzy w witrynie.

   - Określa szablon dla każdego typu elementu, który pojawia się w widoku kalendarza.

     [!code-vb[SP_VisualWebPart#3](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#3)]
     [!code-csharp[SP_VisualWebPart#3](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#3)]

5. Zastąp `Button1_Click` metodę `VisualWebPart1` klasy następującym kodem. Ten kod dodaje elementy z każdego wybranego kalendarza do widoku kalendarza głównego.

     [!code-vb[SP_VisualWebPart#4](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb#4)]
     [!code-csharp[SP_VisualWebPart#4](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs#4)]

## <a name="test-the-web-part"></a>Testowanie składnika Web Part

Po uruchomieniu projektu zostanie otwarta witryna programu SharePoint. Składnik Web Part jest automatycznie dodawany do galerii składników Web Part w programie SharePoint. Aby przetestować ten projekt, należy wykonać następujące zadania:

- Dodaj zdarzenie do każdej z dwóch oddzielnych list kalendarzy.
- Dodaj składnik Web Part do strony składnika Web Part.
- Określ listy do uwzględnienia w widoku kalendarza miesięcznego.

### <a name="to-add-events-to-calendar-lists-on-the-site"></a>Aby dodać zdarzenia do list kalendarza w witrynie

1. W programie Visual Studio, wybierz klawisz **F5** .

     Zostanie otwarta witryna programu SharePoint, a [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] na stronie zostanie wyświetlony pasek Szybkie uruchamianie.

2. Na pasku Szybkie uruchamianie w obszarze **listy** wybierz łącze **Kalendarz** .

     Zostanie wyświetlona strona **Kalendarz** .

     Jeśli na pasku Szybkie uruchamianie nie zostanie wyświetlony link do kalendarza, wybierz link **zawartość witryny** . Jeśli na stronie zawartość witryny nie jest wyświetlany element **Calendar** , utwórz go.

3. Na stronie kalendarz wybierz dzień, a następnie wybierz link **Dodaj** w wybranym dniu, aby dodać zdarzenie.

4. W polu **tytuł** wprowadź **zdarzenie w kalendarzu domyślnym**, a następnie wybierz przycisk **Zapisz** .

5. Wybierz łącze **zawartość witryny** , a następnie wybierz kafelek **Dodaj aplikację** .

6. Na stronie **Tworzenie** wybierz typ **kalendarza** , nazwij kalendarz, a następnie wybierz przycisk **Utwórz** .

7. Dodaj zdarzenie do nowego kalendarza, nazwij **zdarzenie zdarzenia w kalendarzu niestandardowym**, a następnie wybierz przycisk **Zapisz** .

### <a name="to-add-the-web-part-to-a-web-part-page"></a>Aby dodać składnik Web Part do strony składnika Web Part

1. Na stronie **zawartość witryny** Otwórz folder **strony witryny** .

2. Na wstążce wybierz kartę **pliki** , otwórz menu **Nowy dokument** , a następnie wybierz polecenie **strona składników Web Part** .

3. Na stronie **Nowy składnik Web Part** nadaj stronie nazwę **SampleWebPartPage. aspx**, a następnie wybierz przycisk **Utwórz** .

     Zostanie wyświetlona strona składnik Web Part.

4. W górnej części strony składnika Web Part wybierz kartę **Wstawianie** , a następnie wybierz przycisk **składnik Web Part** .

5. Wybierz folder **niestandardowy** , wybierz składnik Web Part **VisualWebPart1** , a następnie wybierz przycisk **Dodaj** .

     Składnik Web Part pojawia się na stronie. Następujące kontrolki są wyświetlane na części sieci Web:

    - Widok kalendarza miesięcznego.

    - Przycisk **Aktualizuj** .

    - Pole wyboru **kalendarza** .

    - Pole wyboru **Kalendarz niestandardowy** .

### <a name="to-specify-lists-to-include-in-the-monthly-calendar-view"></a>Aby określić listy do uwzględnienia w widoku kalendarza miesięcznego

W składniku Web Part Określ kalendarze, które mają zostać uwzględnione w widoku kalendarza miesięcznego, a następnie wybierz przycisk **Aktualizuj** .

Zdarzenia ze wszystkich określonych kalendarzy są wyświetlane w widoku kalendarza miesięcznego.

## <a name="see-also"></a>Zobacz też

[Tworzenie składników Web Part dla programu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) 
 [Instrukcje: Tworzenie składnika Web Part](../sharepoint/how-to-create-a-sharepoint-web-part.md) 
 programu SharePoint [Przewodnik: Tworzenie składnika Web Part dla programu SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
