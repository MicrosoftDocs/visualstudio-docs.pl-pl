---
title: 'Przewodnik: Tworzenie strony aplikacji SharePoint | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 749ec5f7f7bd68911accb33e4e8631b42de8e630
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62778635"
---
# <a name="walkthrough-create-a-sharepoint-application-page"></a>Przewodnik: Tworzenie strony aplikacji SharePoint

Na stronie aplikacji jest formą specjalistyczne strony ASP.NET. Strony aplikacji zawierają treści, która jest połączone ze stroną wzorcową programu SharePoint. Aby uzyskać więcej informacji, zobacz [tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

W tym instruktażu dowiesz się, jak utworzyć witrynę aplikacji, a następnie ją debugować używając lokalnej witryny programu SharePoint. Ta strona pokazuje wszystkie elementy, które każdy użytkownik ma utworzone lub zmodyfikowane we wszystkich witrynach w farmie serwerów.

W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie projektu programu SharePoint.
- Dodawanie strony aplikacji do projektu programu SharePoint.
- Dodawanie formantów ASP.NET na stronie aplikacji.
- Dodając kodu związanego z formantami ASP.NET.
- Testowanie strony aplikacji.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne

- Obsługiwane wersje systemu Windows i programu SharePoint.

## <a name="create-a-sharepoint-project"></a>Utwórz projekt programu SharePoint

Najpierw utwórz **pusty projekt programu SharePoint**. Później dodasz **strony aplikacji** do tego projektu.

1. Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Otwórz **nowy projekt** okna dialogowego rozwiń **Office/SharePoint** węzła dla języka, który chcesz użyć, a następnie wybierz **rozwiązań programu SharePoint** węzła.

3. W **zainstalowane szablony programu Visual Studio** okienku wybierz **SharePoint 2010 — pusty projekt** szablonu. Nadaj projektowi nazwę **MySharePointProject**, a następnie wybierz **OK** przycisku.

     **Kreator ustawień niestandardowych SharePoint** pojawia się. Ten kreator umożliwia wybór lokacji, który będzie używany do debugowania projektu i poziomu zaufania rozwiązania.

4. Wybierz **Wdróż jako rozwiązanie farmy** przycisk opcji, a następnie wybierz **Zakończ** przycisk, aby zaakceptować domyślne lokalnej witryny programu SharePoint.

## <a name="create-an-application-page"></a>Tworzenie strony aplikacji

Aby utworzyć stronę aplikacji, należy dodać **strony aplikacji** do projektu.

1. W **Eksploratora rozwiązań**, wybierz **MySharePointProject** projektu.

2. Na pasku menu wybierz **projektu** > **Dodaj nowy element**.

3. W **Dodaj nowy element** okna dialogowego wybierz **strona aplikacji (tylko rozwiązanie farmy** szablonu.

4. Nazwij stronę **SearchItems**, a następnie wybierz **Dodaj** przycisku.

     Projektant Visual Web Developer wyświetla witrynę aplikacji w **źródła** widok, w którym można zobaczyć elementy HTML strony. Projektant wyświetla znaczniki dla kilku <xref:System.Web.UI.WebControls.Content> kontrolki. Każdy formant mapy do <xref:System.Web.UI.WebControls.ContentPlaceHolder> kontrolki, która jest zdefiniowana w domyślnej stronie wzorcowej aplikacji.

## <a name="design-the-layout-of-the-application-page"></a>Projektowanie układu strony aplikacji

Element strona aplikacji umożliwia użycie projektanta do dodawania formantów ASP.NET na stronie aplikacji. Projektant jest tego samego projektanta, które są używane w Visual Web Developer. Dodaj etykietę, listę przycisków radiowych i tabelę do **źródła** Widok projektanta, a następnie ustaw właściwości tak samo jak podczas projektowania dowolnej standardowej strony ASP.NET.

1. Na pasku menu wybierz **widoku** > **przybornika**.

2. W węźle standardowy **przybornika**, wykonaj jedną z następujących czynności:

    - Otwórz menu skrótów dla **etykiety** elementu, wybierz polecenie **kopiowania**, otwórz menu skrótów dla linii poniżej **PlaceHolderMain** zawartości formantu w projektancie, a następnie Wybierz **Wklej**.

    - Przeciągnij **etykiety** elementu z **przybornika** na treść **PlaceHolderMain** formantu zawartości.

3. Powtórz poprzedni krok, aby dodać **DropDownList** elementu i **tabeli** elementu do **PlaceHolderMain** formantu zawartości.

4. W projektancie, zmień wartość `Text` atrybut formant etykiety, aby **pokazać wszystkie elementy**.

5. W oknie Projektant zastępuje `<asp:DropDownList>` element z następujący kod XML.

    ```xml
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>
    </asp:DropDownList>
    ```

## <a name="handle-the-events-of-controls-on-the-page"></a>Obsługa zdarzeń formantów na stronie

Obsługuje formanty na stronie aplikacji, tak samo jak dowolnej strony ASP.NET. W tej procedurze, będziesz obsługiwać `SelectedIndexChanged` zdarzenie z listy rozwijanej.

1. Na **widoku** menu, wybierz **kodu**.

     Plik kodu strony aplikacji zostanie otwarty w edytorze kodu.

2. Dodaj następującą metodę do `SearchItems` klasy. Ten kod obsługuje <xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged> zdarzenia <xref:System.Web.UI.WebControls.DropDownList> przez wywołanie metody, która zostanie utworzona w dalszej części tego przewodnika.

     [!code-vb[SP_ApplicationPage#5](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#5)]
     [!code-csharp[SP_ApplicationPage#5](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#5)]

3. Dodaj następujące instrukcje na górze pliku kodu strony aplikacji.

     [!code-vb[SP_ApplicationPage#1](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#1)]
     [!code-csharp[SP_ApplicationPage#1](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#1)]

4. Dodaj następującą metodę do `SearchItems` klasy. Ta metoda wykonuje iterację przez wszystkie lokacje w farmie serwerów i wyszukuje elementów utworzonych lub zmodyfikowanych przez bieżącego użytkownika.

     [!code-vb[SP_ApplicationPage#2](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#2)]
     [!code-csharp[SP_ApplicationPage#2](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#2)]

5. Dodaj następującą metodę do `SearchItems` klasy. Ta metoda Wy Wyświetla elementy utworzone lub zmodyfikowane przez bieżącego użytkownika w tabeli.

     [!code-vb[SP_ApplicationPage#3](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#3)]
     [!code-csharp[SP_ApplicationPage#3](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#3)]

## <a name="test-the-application-page"></a>Testowanie strony aplikacji

Kiedy uruchamiasz projekt, otwiera się witryna SharePoint i zostanie wyświetlona strona aplikacji.

1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla strony aplikacji, a następnie wybierz **Ustaw jako element startowy**.

2. Wybierz **F5** klucza.

     Otwiera się witryna SharePoint.

3. Na stronie aplikacji wybierz **zmodyfikowane przeze mnie** opcji.

     Strona aplikacji odświeża i wyświetla wszystkie elementy, które zostały zmodyfikowane we wszystkich witrynach w farmie serwerów.

4. Na stronie aplikacji wybierz **utworzone przeze mnie** na liście.

     Strona aplikacji odświeża i wyświetla wszystkie elementy, które zostały utworzone we wszystkich witrynach w farmie serwerów.

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji dotyczących stron aplikacji programu SharePoint, zobacz [tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

Możesz dowiedzieć się więcej o projektowaniu zawartości strony SharePoint przy użyciu Visual Web Designer w tych tematach:

- [Tworzenie składników web Part programu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

- [Tworzenie formantów wielokrotnych dla części sieciowych lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

## <a name="see-also"></a>Zobacz także

[Instrukcje: Tworzenie strony aplikacji](../sharepoint/how-to-create-an-application-page.md)
[układu aplikacji typ strony](http://go.microsoft.com/fwlink/?LinkID=169274)
