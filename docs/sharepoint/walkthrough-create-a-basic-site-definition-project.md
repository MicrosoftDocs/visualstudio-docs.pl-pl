---
title: 'Przewodnik: Tworzenie podstawowego projektu definicji lokacji | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d1c06f4df5d1efe06ad2537bd2e65f2c239f3be2
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016772"
---
# <a name="walkthrough-create-a-basic-site-definition-project"></a>Przewodnik: Tworzenie podstawowego projektu definicji lokacji
  W tym instruktażu pokazano, jak utworzyć podstawową definicję witryny, która zawiera wizualny składnik Web Part z niektórymi kontrolkami. Dla jasności, tworzony składnik Web Part ma tylko kilka kontrolek. Można jednak utworzyć bardziej zaawansowane definicje witryn programu SharePoint, które zawierają więcej funkcji.

 W tym instruktażu przedstawiono następujące zadania:

- Tworzenie definicji lokacji przy użyciu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] szablonu projektu.

- Tworzenie witryny programu SharePoint przy użyciu definicji lokacji w programie SharePoint.

- Dodawanie wizualnego składnika Web Part do rozwiązania.

- Dostosowywanie domyślnej strony. aspx witryny przez dodanie do niej nowego, wizualnego składnika Web Part.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Obsługiwane wersje systemu Microsoft Windows i programu SharePoint. Aby uzyskać więcej informacji, zobacz Wymagania dotyczące opracowywania rozwiązań programu SharePoint.

- Program Visual Studio.

## <a name="create-a-site-definition-solution"></a>Tworzenie rozwiązania definicji lokacji
 Najpierw utwórz projekt definicji lokacji w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

#### <a name="to-create-a-site-definition-project"></a>Aby utworzyć projekt definicji witryny

1. Na pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**. Jeśli środowisko IDE jest ustawione na używanie Visual Basic ustawień deweloperskich, na pasku menu wybierz pozycję **plik**  >  **Nowy projekt**.

    Zostanie wyświetlone okno dialogowe **Nowy projekt**.

2. Rozwiń węzeł **Visual C#** lub węzeł **Visual Basic** , rozwiń węzeł **SharePoint** , a następnie wybierz węzeł **2010** .

3. Na liście **Szablony** wybierz szablon **projektu programu SharePoint 2010** .

4. W polu **Nazwa** wprowadź **TestSiteDef**, a następnie wybierz przycisk **OK** .

    Zostanie wyświetlony **Kreator dostosowania programu SharePoint** .

5. Na stronie **Określanie poziomu lokacji i zabezpieczeń na potrzeby debugowania** wprowadź adres URL witryny programu SharePoint, w której ma być debugowana definicja lokacji, lub Użyj domyślnej lokalizacji (http://<em>system Name</em>/).

6. W sekcji **co to jest poziom zaufania dla tego rozwiązania programu SharePoint?** wybierz przycisk opcji **Wdróż jako farmę** .

    Wszystkie projekty definicji lokacji należy wdrożyć jako rozwiązania farmy. Aby uzyskać więcej informacji o rozwiązaniach w trybie piaskownicy a rozwiązaniach farmy, zobacz [zagadnienia dotyczące rozwiązania w trybie piaskownicy](../sharepoint/sandboxed-solution-considerations.md).

7. Wybierz przycisk **Zakończ** .

    Projekt pojawia się w **Eksplorator rozwiązań**.

8. W **Eksplorator rozwiązań**wybierz węzeł projektu, a następnie na pasku menu wybierz **projekt**  >  **Dodaj nowy element**.

9. W obszarze **Visual C#** lub **Visual Basic**rozwiń węzeł **SharePoint** , a następnie wybierz węzeł **2010** .

10. W okienku **Szablony** wybierz szablon **Definicja witryny** , pozostaw **nazwę** jako **SiteDefinition1**, a następnie wybierz przycisk **Dodaj** .

## <a name="create-a-visual-web-part"></a>Tworzenie wizualnego składnika Web Part
 Następnie utwórz wizualny składnik Web Part, który zostanie wyświetlony na stronie głównej definicji witryny.

#### <a name="to-create-a-visual-web-part"></a>Aby utworzyć wizualny składnik Web Part

1. W **Eksplorator rozwiązań**wybierz przycisk **Pokaż wszystkie pliki** .

2. Wybierz węzeł projektu **SiteDefinition1** , a następnie na pasku menu wybierz kolejno opcje **projekt**  >  **Dodaj nowy element**.

     Zostanie wyświetlone okno dialogowe **Dodawanie nowego elementu**.

3. Rozwiń węzeł **Visual C#** lub węzeł **Visual Basic** , rozwiń węzeł **SharePoint** , a następnie wybierz węzeł **2010** .

4. Na liście szablonów wybierz szablon **Visual Web Part** , Zachowaj nazwę domyślną VisualWebPart1, a następnie wybierz przycisk **Dodaj** .

     Zostanie otwarty plik *VisualWebPart1. ascx* .

5. W dolnej części *VisualWebPart1. ascx*Dodaj następujące znaczniki, aby dodać trzy kontrolki do formularza: pole tekstowe, przycisk i etykieta:

    ```aspx-csharp
    <table>
      <tr>
        <td>
          <asp:TextBox runat="server" ID="tbName"></asp:TextBox>
        </td>
        <td>
          <asp:Button runat="server" ID="btnSubmit" Text = "Change Label Text" OnClick="btnSubmit_Click"></asp:Button>
        </td>
        <td>
          <asp:Label runat="server" ID="lblName"></asp:Label>
        </td>
      </tr>
    </table>
    ```

6. W obszarze *VisualWebPart1. ascx*otwórz plik *VisualWebPart1.ascx.cs* (dla [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] ) lub *VisualWebPart1. ascx. vb* (dla [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ), a następnie Dodaj następujący kod:

     [!code-vb[SP_SimpleSiteDef#1](../sharepoint/codesnippet/VisualBasic/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_SimpleSiteDef#1](../sharepoint/codesnippet/CSharp/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]

     Ten kod dodaje funkcję dla przycisku części sieci Web.

## <a name="add-the-visual-web-part-to-the-default-aspx-page"></a>Dodaj wizualny składnik Web Part do domyślnej strony ASPX
 Następnie Dodaj wizualny składnik Web Part do domyślnej strony ASPX definicji witryny.

#### <a name="to-add-a-visual-web-part-to-the-default-aspx-page"></a>Aby dodać wizualny składnik Web Part do domyślnej strony ASPX

1. Otwórz stronę Default. aspx, a następnie Dodaj następujący wiersz pod `WebPartPages` tagiem:

    ```aspx-csharp
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>
    ```

     Ten wiersz kojarzy nazwę MyWebPartControls z częścią sieci Web i jej kodem. Parametr *Namespace* jest zgodny z przestrzenią nazw, która jest używana w pliku kodu *VisualWebPart1. ascx* .

2. Po `</asp:Content>` elemencie Zastąp całą `ContentPlaceHolderId="PlaceHolderMain"` sekcję i jej zawartość następującym kodem:

    ```aspx-csharp
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">
        <MyWebPartControls:VisualWebPart1 runat="server" />
    </asp:Content>
    ```

     Ten kod tworzy odwołanie do utworzonego wcześniej elementu Visual Web Part.

3. W **Eksplorator rozwiązań**Otwórz menu skrótów dla węzła **SiteDefinition1** , a następnie wybierz polecenie **Ustaw jako element startowy**.

## <a name="deploy-and-run-the-site-definition-solution"></a>Wdrażanie i uruchamianie rozwiązania definicji lokacji
 Następnie wdróż projekt w programie SharePoint, a następnie Uruchom projekt.

#### <a name="to-deploy-and-run-the-site-definition"></a>Aby wdrożyć i uruchomić definicję witryny

- Na pasku menu wybierz kolejno pozycje **kompilacja**  >  **Wdróż TestSiteDef**.

- Wybierz klawisz **F5** .

     Program Visual Studio kompiluje kod, dodaje jego funkcje, pakuje wszystkie pliki do pliku rozwiązania programu SharePoint (WSP) i wdraża plik WSP na serwerze programu SharePoint. Program SharePoint zainstaluje następnie pliki, a następnie uaktywni funkcje.

## <a name="create-a-site-based-on-the-site-definition"></a>Tworzenie witryny na podstawie definicji lokacji
 Następnie utwórz lokację przy użyciu nowej definicji lokacji.

#### <a name="to-create-a-site-by-using-the-site-definition"></a>Aby utworzyć witrynę przy użyciu definicji witryny

1. W witrynie programu SharePoint zostanie wyświetlona strona Nowa witryna programu SharePoint.

2. W sekcji **tytuł i opis** wprowadź **moją nową witrynę** dla tytułu i opis witryny.

3. W sekcji **adres witryny sieci Web** wprowadź **mynewsite** w polu **nazwa adresu URL** .

4. W sekcji **szablon** wybierz kartę **dostosowania programu SharePoint** .

5. Na liście **Wybierz szablon** wybierz pozycję **SiteDefinition1**.

6. Pozostaw wartości domyślne pozostałych ustawień, a następnie wybierz przycisk **Utwórz** .

     Zostanie wyświetlona nowa witryna.

## <a name="test-the-new-site"></a>Przetestuj nową witrynę
 Następnie przetestuj nową lokację, aby sprawdzić, czy działa poprawnie.

#### <a name="to-test-the-new-site"></a>Aby przetestować nową stronę

- Na domyślnej stronie ASPX wprowadź tekst, a następnie wybierz przycisk **zmiany tekstu etykiety** obok pola tekstowego.

     Tekst jest wyświetlany w etykiecie po prawej stronie przycisku.

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Tworzenie odbiorcy zdarzeń](../sharepoint/how-to-create-an-event-receiver.md)
- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)
