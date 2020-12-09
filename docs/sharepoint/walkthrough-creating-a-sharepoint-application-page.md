---
title: 'Przewodnik: Tworzenie strony aplikacji SharePoint | Microsoft Docs'
description: W tym instruktażu Utwórz stronę aplikacji (wyspecjalizowaną postać strony ASP.NET), a następnie Debuguj ją przy użyciu lokalnej witryny programu SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 95addb145312de85a3525c228297e7ff9636ea0d
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914884"
---
# <a name="walkthrough-create-a-sharepoint-application-page"></a>Przewodnik: Tworzenie strony aplikacji SharePoint

Strona aplikacji jest wyspecjalizowaną formą strony ASP.NET. Strony aplikacji zawierają zawartość scaloną ze stroną wzorcową programu SharePoint. Aby uzyskać więcej informacji, zobacz [Tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

W tym instruktażu przedstawiono sposób tworzenia strony aplikacji, a następnie debugowania jej przy użyciu lokalnej witryny programu SharePoint. Na tej stronie są wyświetlane wszystkie elementy utworzone lub zmodyfikowane przez każdego użytkownika we wszystkich lokacjach w farmie serwerów.

W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie projektu programu SharePoint.
- Dodawanie strony aplikacji do projektu programu SharePoint.
- Dodawanie formantów ASP.NET do strony aplikacji.
- Dodawanie kodu za kontrolkami ASP.NET.
- Testowanie strony aplikacji.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne

- Obsługiwane wersje systemu Windows i programu SharePoint.

## <a name="create-a-sharepoint-project"></a>Tworzenie projektu programu SharePoint

Najpierw Utwórz **pusty projekt programu SharePoint**. Później dodasz element **strony aplikacji** do tego projektu.

1. Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. Otwórz okno dialogowe **Nowy projekt** , rozwiń węzeł **Office/SharePoint** w języku, którego chcesz użyć, a następnie wybierz węzeł **rozwiązania SharePoint** .

3. W okienku **zainstalowane szablony programu Visual Studio** wybierz szablon **programu SharePoint 2010 i pusty projekt** . Nazwij projekt **MyShareProject**, a następnie wybierz przycisk **OK** .

     Zostanie wyświetlony **Kreator dostosowania programu SharePoint** . Ten Kreator umożliwia wybranie lokacji, która będzie używana do debugowania projektu i poziomu zaufania rozwiązania.

4. Wybierz przycisk opcji **Wdróż jako rozwiązanie farmy** , a następnie wybierz przycisk **Zakończ** , aby zaakceptować domyślną lokalną witrynę programu SharePoint.

## <a name="create-an-application-page"></a>Tworzenie strony aplikacji

Aby utworzyć stronę aplikacji, Dodaj element **strony aplikacji** do projektu.

1. W **Eksplorator rozwiązań** wybierz projekt **MyShareProject** .

2. Na pasku menu wybierz **projekt**  >  **Dodaj nowy element**.

3. W oknie dialogowym **Dodaj nowy element** wybierz **stronę aplikacji (szablon tylko rozwiązanie farmy** ).

4. Nadaj stronie nazwę **SearchItems**, a następnie wybierz przycisk **Dodaj** .

     Projektant Visual Web Developer wyświetla stronę aplikacji w widoku **źródła** , w której można zobaczyć elementy HTML strony. Projektant wyświetla znaczniki dla kilku <xref:System.Web.UI.WebControls.Content> kontrolek. Każda kontrolka mapuje do <xref:System.Web.UI.WebControls.ContentPlaceHolder> kontrolki zdefiniowanej na domyślnej stronie wzorcowej aplikacji.

## <a name="design-the-layout-of-the-application-page"></a>Projektowanie układu strony aplikacji

Element Strona aplikacji umożliwia dodawanie formantów ASP.NET do strony aplikacji przy użyciu projektanta. Ten Projektant jest tym samym projektantem, który jest używany w Visual Web Developer. Dodaj etykietę, listę przycisków radiowych i tabelę do widoku **źródła** projektanta, a następnie ustaw właściwości tak samo jak podczas projektowania dowolnej standardowej strony ASP.NET.

1. Na pasku menu wybierz **Widok**  >  **Przybornik**.

2. W węźle standardowy **przybornika** wykonaj jedną z następujących czynności:

    - Otwórz menu skrótów dla elementu **etykieta** , wybierz **Kopiuj**, otwórz menu skrótów dla wiersza pod kontrolką zawartości **PlaceHolderMain** w projektancie, a następnie wybierz **Wklej**.

    - Przeciągnij element **Label** z **przybornika** na treść kontrolki zawartości **PlaceHolderMain** .

3. Powtórz poprzedni krok, aby dodać element **DropDownList** i element **tabeli** do kontrolki zawartości **PlaceHolderMain** .

4. W projektancie Zmień wartość `Text` atrybutu kontrolki etykieta, aby **wyświetlić wszystkie elementy**.

5. W projektancie Zastąp `<asp:DropDownList>` element następującym kodem XML.

    ```xml
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>
    </asp:DropDownList>
    ```

## <a name="handle-the-events-of-controls-on-the-page"></a>Obsługa zdarzeń formantów na stronie

Obsłuż kontrolki na stronie aplikacji tak samo jak każda strona ASP.NET. W tej procedurze zostanie obsłużyć `SelectedIndexChanged` zdarzenie listy rozwijanej.

1. W menu **Widok** wybierz polecenie **kod**.

     Plik kodu strony aplikacji zostanie otwarty w edytorze kodu.

2. Dodaj następującą metodę do `SearchItems` klasy. Ten kod obsługuje <xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged> zdarzenie, <xref:System.Web.UI.WebControls.DropDownList> wywołując metodę, która zostanie utworzona w dalszej części tego instruktażu.

     [!code-vb[SP_ApplicationPage#5](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#5)]
     [!code-csharp[SP_ApplicationPage#5](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#5)]

3. Dodaj następujące instrukcje na górze pliku kodu strony aplikacji.

     [!code-vb[SP_ApplicationPage#1](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#1)]
     [!code-csharp[SP_ApplicationPage#1](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#1)]

4. Dodaj następującą metodę do `SearchItems` klasy. Ta metoda iteruje przez wszystkie lokacje w farmie serwerów i wyszukuje elementy utworzone lub zmodyfikowane przez bieżącego użytkownika.

     [!code-vb[SP_ApplicationPage#2](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#2)]
     [!code-csharp[SP_ApplicationPage#2](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#2)]

5. Dodaj następującą metodę do `SearchItems` klasy. Ta metoda wyświetla elementy utworzone lub zmodyfikowane przez bieżącego użytkownika w tabeli.

     [!code-vb[SP_ApplicationPage#3](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#3)]
     [!code-csharp[SP_ApplicationPage#3](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#3)]

## <a name="test-the-application-page"></a>Testowanie strony aplikacji

Po uruchomieniu projektu zostanie otwarta witryna programu SharePoint, na której zostanie wyświetlona strona aplikacji.

1. W **Eksplorator rozwiązań** Otwórz menu skrótów dla strony aplikacji, a następnie wybierz polecenie **Ustaw jako element startowy**.

2. Wybierz klawisz **F5** .

     Zostanie otwarta witryna programu SharePoint.

3. Na stronie aplikacja wybierz opcję **zmodyfikowane przeze mnie** .

     Strona aplikacji odświeża i wyświetla wszystkie elementy, które zostały zmodyfikowane we wszystkich lokacjach w farmie serwerów.

4. Na stronie aplikacja wybierz pozycję **utworzone przeze mnie** na liście.

     Strona aplikacji odświeża i wyświetla wszystkie elementy, które zostały utworzone we wszystkich lokacjach w farmie serwerów.

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o stronach aplikacji programu SharePoint, zobacz [Tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

Aby dowiedzieć się więcej na temat projektowania zawartości strony programu SharePoint, można użyć Visual Web Designer z następujących tematów:

- [Tworzenie składników Web Part dla programu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

- [Tworzenie kontrolek wielokrotnego użytku dla części sieci Web lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

## <a name="see-also"></a>Zobacz też

[Instrukcje: Tworzenie strony aplikacji](../sharepoint/how-to-create-an-application-page.md) 
 [Typ strony _layouts aplikacji](/previous-versions/office/aa979604(v=office.14))
