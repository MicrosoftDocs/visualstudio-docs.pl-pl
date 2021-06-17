---
title: Tworzenie składników Web Part dla programu SharePoint przy użyciu projektanta
description: W tym przewodniku wizualnie utworzysz element Web Part przy użyciu szablonu projektu visual web part programu SharePoint w programie Visual Studio.
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
ms.openlocfilehash: 55f69875b06428c9bbe179e73dd6ea9b4ef40b8e
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112451"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint-by-using-a-designer"></a>Przewodnik: tworzenie składników Web Part dla programu SharePoint przy użyciu projektanta

Jeśli tworzysz części internetowe dla witryny programu SharePoint, użytkownicy mogą bezpośrednio modyfikować zawartość, wygląd i zachowanie stron w tej witrynie przy użyciu przeglądarki. W tym przewodniku pokazano, jak wizualnie utworzyć element Web Part przy użyciu szablonu projektu visual **web part** programu SharePoint w usłudze Visual Studio.

Zostanie on wyświetlony w widoku kalendarza miesięcznego i polem wyboru dla każdej listy kalendarzy w witrynie. Użytkownicy mogą określić listy kalendarzy, które mają być dołączane do comiesięcznego widoku kalendarza, zaznaczając pola wyboru.

W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie części web part przy użyciu szablonu **projektu Visual Web Part.**
- Projektowanie części internetowej przy użyciu projektanta Visual Web Developer w programie Visual Studio.
- Dodawanie kodu do obsługi zdarzeń kontrolek w części Web Part.
- Testowanie składników Web Part w programie SharePoint.

    > [!NOTE]
    > Na komputerze mogą być wyświetlane różne nazwy lub lokalizacje dla niektórych elementów interfejsu użytkownika Visual Studio w poniższych instrukcjach. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Zobacz [Personalizowanie Visual Studio IDE.](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Obsługiwane wersje systemu Windows i programu SharePoint.

## <a name="create-a-web-part-project"></a>Tworzenie projektu składników Web Part

Najpierw utwórz projekt składników Web Part przy użyciu szablonu projektu **visual web part.**

1. Zacznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] od opcji Uruchom jako **administrator.**

2. Na pasku menu wybierz pozycję **File** New Project  >  **(Plik nowy**  >  **projekt).**
::: moniker range="=vs-2017"

3. W **oknie dialogowym Nowy** projekt w obszarze **Visual C#** lub **Visual Basic** rozwiń pozycję **Office/SharePoint,** a następnie wybierz **kategorię Rozwiązania SharePoint.**

4. Na liście szablonów wybierz szablon **SharePoint 2013 — Visual Web Part,** a następnie wybierz przycisk **OK.**

     Zostanie **wyświetlony Kreator dostosowywania programu SharePoint.** Za pomocą tego kreatora można określić lokację, która będzie używana do debugowania projektu, oraz poziom zaufania rozwiązania.
::: moniker-end
::: moniker range=">=vs-2019"
3. W **oknie dialogowym Tworzenie nowego projektu** wybierz pusty projekt programu *SharePoint** dla określonej zainstalowanej wersji programu SharePoint. Jeśli na przykład masz zainstalowany program SharePoint 2019, wybierz szablon **SharePoint 2019 — pusty** projekt.
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

4. W polu **Nazwa** wprowadź **test TestProject1,** a następnie wybierz **przycisk** Utwórz.

::: moniker-end
5. W **sekcji What is the trust level for this SharePoint solution?** (Jaki jest poziom zaufania dla tego rozwiązania programu SharePoint?) wybierz przycisk **Deploy as a farm solution (Wd wdrażaj jako** rozwiązanie farmy).

6. Wybierz przycisk **Zakończ,** aby zaakceptować domyślną lokalną witrynę programu SharePoint.

## <a name="designing-the-web-part"></a>Projektowanie składników Web Part

Zaprojektuj element Web  Part, dodając kontrolki z przybornika na powierzchni projektanta Visual Web Developer.

1. W projektancie Visual Web Developer wybierz **kartę Projekt,** aby przełączyć się na widok Projekt.

2. Na pasku menu wybierz pozycję **Wyświetl**  >  **przybornik.**

3. W **węźle Standardowa** **przybornika** wybierz kontrolkę **CheckBoxList,** a następnie wykonaj jedną z następujących czynności:

    - Otwórz menu skrótów kontrolki **CheckBoxList,** wybierz pozycję **Kopiuj,** otwórz menu skrótów dla pierwszego wiersza w projektancie, a następnie wybierz pozycję **Wklej**.

    - Przeciągnij **kontrolkę CheckBoxList** z **przybornika** i połącz ją z pierwszym wierszem w projektancie.

4. Powtórz poprzedni krok, ale przenieś przycisk do następnego wiersza projektanta.

5. W projektancie wybierz przycisk **Button1.**

6. Na pasku menu wybierz pozycję **Wyświetl**  >  **okno właściwości.**

     Zostanie **otwarte okno** Właściwości.

7. We właściwości **Text** przycisku wprowadź **update**.

## <a name="handling-the-events-of-controls-on-the-web-part"></a>Obsługa zdarzeń kontrolek w części Web Part

Dodaj kod, który umożliwia użytkownikowi dodawanie kalendarzy do głównego widoku kalendarza.

1. Wykonaj jeden z następujących zestawów czynności:

   - W projektancie kliknij dwukrotnie przycisk **Aktualizuj.**

   - W **oknie** Właściwości **przycisku** Aktualizuj wybierz **przycisk** Zdarzenia. We właściwości **Click** wprowadź **Button1_Click**, a następnie naciśnij klawisz Enter.

     Plik kodu sterowania użytkownika zostanie otwarty w Edytorze kodu i zostanie `Button1_Click` wyświetlony program obsługi zdarzeń. Później dodasz kod do tej procedury obsługi zdarzeń.

2. Dodaj następujące instrukcje na początku pliku kodu sterowania użytkownika.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet1":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet1":::

3. Dodaj następujący wiersz kodu do `VisualWebPart1` klasy . Ten kod deklaruje miesięczną kontrolkę widoku kalendarza.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet2":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet2":::

4. Zastąp `Page_Load` metodę klasy `VisualWebPart1` poniższym kodem. Ten kod wykonuje następujące zadania:

   - Dodaje widok kalendarza miesięcznego do kontrolki użytkownika.

   - Dodaje pole wyboru dla każdej listy kalendarza w witrynie.

   - Określa szablon dla każdego typu elementu wyświetlanego w widoku kalendarza.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet3":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet3":::

5. Zastąp `Button1_Click` metodę klasy `VisualWebPart1` poniższym kodem. Ten kod dodaje elementy z każdego wybranego kalendarza do głównego widoku kalendarza.

     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1usercontrol.ascx.vb" id="Snippet4":::
     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1usercontrol.ascx.cs" id="Snippet4":::

## <a name="test-the-web-part"></a>Testowanie składników Web Part

Po uruchomieniu projektu zostanie otwarta witryna programu SharePoint. Ten element web part jest automatycznie dodawany do galerii składników Web Part w programie SharePoint. Aby przetestować ten projekt, wykonasz następujące zadania:

- Dodaj zdarzenie do każdej z dwóch oddzielnych list kalendarza.
- Dodaj element Web Part do strony składników Web Part.
- Określ listy, które mają być dołączane do widoku kalendarza miesięcznego.

### <a name="to-add-events-to-calendar-lists-on-the-site"></a>Aby dodać zdarzenia do list kalendarza w witrynie

1. W Visual Studio wybierz klawisz **F5.**

     Zostanie otwarta witryna programu SharePoint, Szybkie uruchamianie [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] na stronie pojawi się pasek aplikacji.

2. Na pasku Szybkie uruchamianie w **obszarze Listy** wybierz link **Kalendarz.**

     Zostanie **wyświetlona** strona Kalendarz.

     Jeśli na pasku Szybkie uruchamianie nie zostanie wyświetlony link Kalendarz, wybierz link **Zawartość** witryny. Jeśli na stronie Zawartość witryny nie jest pokazywany **element Kalendarz,** utwórz go.

3. Na stronie Kalendarz wybierz dzień, a następnie wybierz **link** Dodaj w wybranym dniu, aby dodać zdarzenie.

4. W polu **Tytuł** wprowadź Event **(Zdarzenie) w kalendarzu domyślnym**, a następnie wybierz **przycisk Save (Zapisz).**

5. Wybierz link **Zawartość witryny,** a następnie wybierz **kafelek Dodaj** aplikację.

6. Na **stronie Tworzenie** wybierz typ **kalendarza,** nadaj kalendarzowi nazwę, a następnie wybierz **przycisk** Utwórz.

7. Dodaj zdarzenie do nowego kalendarza, nadaj wydarzeniem nazwę **Event (Zdarzenie)** w kalendarzu niestandardowym, a następnie wybierz **przycisk Save (Zapisz).**

### <a name="to-add-the-web-part-to-a-web-part-page"></a>Aby dodać element Web Part do strony składników Web Part

1. Na stronie **Zawartość witryny** otwórz folder **Strony witryny.**

2. Na wstążce wybierz **kartę Pliki,** otwórz menu **Nowy dokument,** a następnie wybierz polecenie **Strona składników Web Part.**

3. Na stronie **Nowa strona składników Web Part** nadaj stronie nazwę **SampleWebPartPage.aspx,** a następnie wybierz **przycisk** Utwórz.

     Zostanie wyświetlona strona składników Web Part.

4. W górnej strefie strony składników Web Part wybierz kartę **Wstawianie,** a następnie wybierz przycisk **Web Part.**

5. Wybierz folder **Niestandardowy,** wybierz część web part **VisualWebPart1,** a następnie wybierz **przycisk** Dodaj.

     Na stronie zostanie wyświetlony element Web Part. W części Web Part są wyświetlane następujące kontrolki:

    - Miesięczny widok kalendarza.

    - Przycisk **Aktualizuj.**

    - Pole **wyboru Kalendarz.**

    - Pole **wyboru Kalendarz** niestandardowy.

### <a name="to-specify-lists-to-include-in-the-monthly-calendar-view"></a>Aby określić listy do dołączyć do widoku kalendarza miesięcznego

W części Web Part określ kalendarze, które chcesz uwzględnić w widoku kalendarza miesięcznego, a następnie wybierz **przycisk** Aktualizuj.

Zdarzenia ze wszystkich określonych kalendarzy są wyświetlane w widoku kalendarza miesięcznego.

## <a name="see-also"></a>Zobacz też

[Tworzenie składników Web Part dla programu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md) 
 [How to: Create a SharePoint Web Part (Tworzyć część Web Part programu SharePoint)](../sharepoint/how-to-create-a-sharepoint-web-part.md) 
 [Przewodnik: tworzenie składników Web Part dla programu SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
