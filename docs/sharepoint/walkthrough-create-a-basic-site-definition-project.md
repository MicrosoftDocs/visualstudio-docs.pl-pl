---
title: 'Przewodnik: Tworzenie podstawowego projektu definicji witryny | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 078fcc4d30613e4fe19b493150ce4570196b73ac
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56608880"
---
# <a name="walkthrough-create-a-basic-site-definition-project"></a>Przewodnik: Tworzenie podstawowego projektu definicji witryny
  W tym instruktażu dowiesz się, jak utworzyć definicję podstawową witryny, zawierający wizualny składnik Web part za pomocą niektóre kontrolki. Dla jasności wizualny składnik Web part, które tworzysz ma tylko kilka formantów. Można jednak utworzyć bardziej złożone definicje witryn programu SharePoint, które zawierają więcej funkcji.

 W tym instruktażu pokazano następujące zagadnienia:

- Tworzenie definicji witryny za pomocą [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] szablonu projektu.

- Tworzenie witryny programu SharePoint przy użyciu definicji lokacji w programie SharePoint.

- Dodawanie wizualny składnik Web part do rozwiązania.

- Dostosowywanie strony default.aspx witryny przez dodanie nowych wizualny składnik Web part do niego.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

-   Obsługiwane wersje systemu Microsoft Windows i programu SharePoint. Aby uzyskać więcej informacji zobacz wymagania dotyczące opracowywania rozwiązań programu SharePoint.

-   Program Visual Studio.

## <a name="create-a-site-definition-solution"></a>Tworzenie rozwiązania definicji witryny
 Najpierw utwórz projekt definicji witryny w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

#### <a name="to-create-a-site-definition-project"></a>Aby utworzyć projekt definicji witryny

1. Na pasku menu wybierz **pliku** > **New** > **projektu**. Jeśli środowisko IDE jest ustawione do użycia ustawienia programowania Visual Basic, na pasku menu, wybierz opcję **pliku** > **nowy projekt**.

    **Nowy projekt** pojawi się okno dialogowe.

2. Rozwiń **Visual C#**  węzła lub **języka Visual Basic** węzła, rozwiń węzeł **SharePoint** węzła, a następnie wybierz **2010** węzła.

3. W **szablony** wybierz **projekt programu SharePoint 2010** szablonu.

4. W **nazwa** wprowadź **TestSiteDef**, a następnie wybierz **OK** przycisku.

    **Kreator ustawień niestandardowych SharePoint** pojawia się.

5. Na **Określanie witryny i poziomu zabezpieczeń dla debugowania** strony, wprowadź adres URL witryny programu SharePoint, w którym chcesz debugować definicji witryny lub użyj domyślnej lokalizacji (http://<em>Nazwa systemowa</em>/).

6. W **co to jest poziom zaufania dla tego rozwiązania programu SharePoint?** wybierz pozycję **Wdróż jako rozwiązanie farmy** przycisku opcji.

    Wszystkie witryna definicji projektów musi zostać wdrożony jako rozwiązania farmy. Aby uzyskać więcej informacji dotyczących rozwiązań sandbox w porównaniu z rozwiązaniami farmy, zobacz [uwagi dotyczące rozwiązania typu piaskownica](../sharepoint/sandboxed-solution-considerations.md).

7. Wybierz **Zakończ** przycisku.

    Projekt, który pojawia się w **Eksploratora rozwiązań**.

8. W **Eksploratora rozwiązań**, wybierz węzeł projektu, a następnie na pasku menu wybierz **projektu** > **Dodaj nowy element**.

9. W obszarze **Visual C#** lub **języka Visual Basic**, rozwiń węzeł **SharePoint** węzła, a następnie wybierz **2010** węzła.

10. W **szablony** okienku wybierz **definicji witryny** szablonu, pozostaw **nazwa** jako **SiteDefinition1**, a następnie wybierz polecenie  **Dodaj** przycisku.

## <a name="create-a-visual-web-part"></a>Utwórz wizualny składnik web part
 Następnie należy utworzyć wizualny składnik Web part na stronie głównej definicji witryny.

#### <a name="to-create-a-visual-web-part"></a>Aby utworzyć wizualny składnik web part

1.  W **Eksploratora rozwiązań**, wybierz **Pokaż wszystkie pliki** przycisku.

2.  Wybierz **SiteDefinition1** węzła projektu, a następnie na pasku menu wybierz **projektu** > **Dodaj nowy element**.

     **Dodaj nowy element** pojawi się okno dialogowe.

3.  Rozwiń **Visual C#**  węzła lub **języka Visual Basic** węzła, rozwiń węzeł **SharePoint** węzła, a następnie wybierz **2010** węzła.

4.  Z listy szablonów wybierz **wizualny składnik Web Part** szablonu, zachowaj domyślną nazwę VisualWebPart1, a następnie wybierz **Dodaj** przycisku.

     *VisualWebPart1.ascx* plik zostanie otwarty.

5.  W dolnej części *VisualWebPart1.ascx*, Dodaj następujący kod do dodawania trzech formantów do formularza: pole tekstowe, przycisk i etykietę:

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

6.  W obszarze *VisualWebPart1.ascx*, otwórz *VisualWebPart1.ascx.cs* pliku (dla [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)]) lub *VisualWebPart1.ascx.vb* (dla [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), a następnie dodaj Poniższy kod:

     [!code-vb[SP_SimpleSiteDef#1](../sharepoint/codesnippet/VisualBasic/testsitedefvb/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.vb#1)]
     [!code-csharp[SP_SimpleSiteDef#1](../sharepoint/codesnippet/CSharp/testsitedef/sitedefinition/visualwebpart1/visualwebpart1usercontrol.ascx.cs#1)]

     Ten kod dodaje funkcjonalność dotyczącą składnika web part, kliknij przycisk.

## <a name="add-the-visual-web-part-to-the-default-aspx-page"></a>Dodaj wizualny składnik web part do domyślnej strony ASPX
 Następnie dodaj wizualny składnik Web part do domyślnej strony ASPX — definicji witryny.

#### <a name="to-add-a-visual-web-part-to-the-default-aspx-page"></a>Aby dodać wizualny składnik web part do domyślnej strony ASPX

1.  Otwórz stronę default.aspx, a następnie dodaj następujący wiersz w obszarze `WebPartPages` tag:

    ```aspx-csharp
    <%@ Register Tagprefix="MyWebPartControls" Namespace="TestSiteDef.VisualWebPart1" Assembly="$SharePoint.Project.AssemblyFullName$" %>
    ```

     Ten wiersz kojarzy nazwę MyWebPartControls za pomocą składnika Web part i jego kodu. *Namespace* parametr odpowiada przestrzeni nazw, który jest używany w *VisualWebPart1.ascx* pliku kodu.

2.  Po `</asp:Content>` elementu, Zastąp całą `ContentPlaceHolderId="PlaceHolderMain"` sekcji i jego zawartość następującym kodem:

    ```aspx-csharp
    <asp:Content ID="Content1" ContentPlaceHolderId="PlaceHolderMain" runat="server">
        <MyWebPartControls:VisualWebPart1 runat="server" />
    </asp:Content>
    ```

     Ten kod tworzy odwołanie do wizualny składnik Web part, który został utworzony wcześniej.

3.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla **SiteDefinition1** węzła, a następnie wybierz **Ustaw jako element startowy**.

## <a name="deploy-and-run-the-site-definition-solution"></a>Wdrażanie i uruchamianie rozwiązania definicji witryny
 Następnie wdrażanie projektu programu SharePoint, a następnie uruchomić projekt.

#### <a name="to-deploy-and-run-the-site-definition"></a>Aby wdrożyć i uruchomić definicję witryny

-   Na pasku menu wybierz **kompilacji** > **wdrażanie TestSiteDef**.

-   Wybierz **F5** klucza.

     Program Visual Studio kompiluje kod, dodaje jej funkcje, pakiety wszystkie pliki w plik rozwiązania (WSP) programu SharePoint i wdrażania z plikiem WSP do serwera programu SharePoint. Program SharePoint następnie instaluje pliki, a następnie aktywuje funkcje.

## <a name="create-a-site-based-on-the-site-definition"></a>Tworzenie witryny na podstawie definicji witryny
 Następnie utwórz lokację przy użyciu nowych definicji witryny.

#### <a name="to-create-a-site-by-using-the-site-definition"></a>Aby utworzyć witrynę przy użyciu definicji witryny

1.  W witrynie programu SharePoint zostanie wyświetlona strona nową witrynę programu SharePoint.

2.  W **tytuł i opis** sekcji, wprowadź **Moje nowej lokacji** tytuł i opis witryny.

3.  W **adres witryny sieci Web** sekcji, wprowadź **MojaNowaWitryna** w **nazwa adresu URL** pole.

4.  W **szablonu** wybierz pozycję **dostosowania SharePoint** kartę.

5.  W **wybierz szablon** wybierz **SiteDefinition1**.

6.  Pozostaw inne ustawienia ich wartości domyślne, a następnie wybierz **Utwórz** przycisku.

     Pojawi się nowa lokacja.

## <a name="test-the-new-site"></a>Testuj nową stronę
 Następnie przetestuj nowej lokacji, aby sprawdzić, czy działa poprawnie.

#### <a name="to-test-the-new-site"></a>Aby przetestować nową stronę

-   Na stronie domyślnej ASPX wprowadź jakiś tekst, a następnie wybierz **tekst etykiety zmiany** przycisk znajdujący się obok pola tekstowego.

     Tekst jest wyświetlany w etykiecie po prawej stronie przycisku.

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Tworzenie obsługiwanego odbiornika](../sharepoint/how-to-create-an-event-receiver.md)
- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)
