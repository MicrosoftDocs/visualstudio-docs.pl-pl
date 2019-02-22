---
title: 'Przewodnik: Importowanie niestandardowej strony wzorcowej oraz strony witryny z obrazem | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 59dad7f376b79b2e8ac773f8cc604204dcd0c908
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56602211"
---
# <a name="walkthrough-import-a-custom-master-page-and-site-page-with-an-image"></a>Przewodnik: Importowanie niestandardowej strony wzorcowej oraz strony witryny z obrazem
  W tym instruktażu pokazano, jak importować niestandardową stronę wzorcową i stronę witryny, która ma obraz w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu programu SharePoint.

 W tym instruktażu przedstawiono sposób wykonywania następujących zadań:

- Utwórz niestandardową stronę wzorcową i stronę witryny przy użyciu obrazu w programie SharePoint Designer.

- Eksportuj niestandardową stronę wzorcową, obrazów i stronę witryny do rozwiązania programu SharePoint (*.wsp*) pliku.

- Importowanie i wdrażanie *.wsp* mezzanine do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu programu SharePoint za pomocą projektu Importowanie pakietu rozwiązań programu SharePoint.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Konieczne jest posiadanie następujących składników w celu przeprowadzenia tego instruktażu:

-   Obsługiwane edycje [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] i programu SharePoint.

-   Program Visual Studio.

-   SharePoint Designer 2010.

## <a name="create-items-in-sharepoint-designer"></a>Tworzenie elementów w programie SharePoint Designer
 W tym przykładzie pokazano, jak utworzyć trzy elementy w programie SharePoint Designer eksportu: niestandardową stronę wzorcową, strony witryny, która odwołuje się niestandardową stronę wzorcową i plikiem obrazu na stronie witryny. Obraz, który jest dodawany do folderu /images/ w programie SharePoint.

#### <a name="to-create-a-custom-master-page-in-sharepoint-designer"></a>Aby utworzyć niestandardową stronę wzorcową w programie SharePoint Designer

1.  W programie SharePoint Designer, w okienku nawigacji wybierz **stronami wzorcowymi** obiekt lokacji.

2.  Na **stronami wzorcowymi** Wstążce, wybierz polecenie **pustą stronę wzorcową**.

3.  Wybierz nowe strony wzorcowej, a następnie na **stronami wzorcowymi** Wstążce, wybierz polecenie **Edytuj plik**.

4.  W dolnej części programu SharePoint Designer wybierz **kodu** kartę.

5.  Zastąp istniejący kod znaczników następującym kodem.

    ```aspx-csharp
    <%@ Master Language="C#" %>
    <%@ Register tagprefix="SharePoint" namespace="Microsoft.SharePoint.WebControls" assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
    <html dir="ltr">
    <head runat="server">
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <SharePoint:RobotsMetaTag runat="server" __designer:Preview="" __designer:Values="<P N='InDesign' T='False' /><P N='ID' T='ctl00' /><P N='Page' ID='1' /><P N='TemplateControl' ID='2' /><P N='AppRelativeTemplateSourceDirectory' R='-1' />"></SharePoint:RobotsMetaTag>
    <title>Web Page</title>
    </head>
    <body>
    <form id="form1" runat="server">
    <asp:ContentPlaceHolder id="ContentPlaceHolderMain"
            runat="server">
          </asp:ContentPlaceHolder>
    </form>
    </body>
    </html>
    ```

6.  Wybierz pozycję Zapisz stronę **stronami wzorcowymi** kartę i Zmień nazwę strony wzorcowej jako **mybasic1.master**.

## <a name="add-an-image-to-the-content-database-in-sharepoint-designer"></a>Dodawanie obrazu do bazy danych zawartości w programie SharePoint Designer
 Teraz możesz dodać obraz do wyświetlania na stronie witryny. Obraz zostanie wdrożony do bazy danych zawartości programu SharePoint.

#### <a name="to-add-an-image-to-the-content-database-in-sharepoint-designer"></a>Aby dodać obraz do bazy danych zawartości w programie SharePoint Designer

1.  W okienku nawigacji wybierz **wszystkie pliki** lokacji obiektu, a następnie, w widoku drzewa wybierz **obrazów** folderu.

2.  Na **wszystkie pliki** Wstążce, wybierz polecenie **plików importu**, wybierz plik wybranych przez użytkownika, a następnie wybierz **OK** przycisku. W tym przykładzie plik o nazwie **myimg1.png**.

     Opcjonalnie możesz utworzyć podfolder, aby ułatwić organizowanie obrazów.

3.  Zamknij **importu** okno dialogowe.

## <a name="create-a-site-page"></a>Tworzenie strony witryny
 Ta strona podstawowej witryny używa niestandardowej strony wzorcowej i wyświetla obraz, który zostało dodane w poprzednim kroku.

#### <a name="to-create-a-site-page"></a>Aby utworzyć stronę witryny

1.  W okienku nawigacji wybierz **stron witryny** obiektu.

2.  Na **stron** Wstążce, wybierz polecenie **strony** przycisku, wybierz polecenie **ASPX** strony typu, a następnie nadaj nowemu plikowi **mycontentpage1.aspx**.

     Opcjonalnie możesz utworzyć podfolder, aby ułatwić organizowanie stron witryny.

3.  Na liście stron witryny, wybierz opcję **MyContentPage1.aspx** aby otworzyć jej stronę właściwości, a następnie w dolnej części strony wybierz **Edytuj plik** łącza.

     Jeśli pojawia się komunikat i mówi, że ta strona nie zawiera żadnych obszarów, które można edytować w trybie awaryjnym i pyta, czy chcesz otworzyć tę stronę w trybie zaawansowanym, wybierz **tak** przycisku.

4.  W dolnej części strony wybierz **kodu** przycisku.

5.  Zastąp istniejący kod znaczników następującym kodem.

    ```aspx-csharp
    <%@ Import Namespace="Microsoft.SharePoint.ApplicationPages" %>
    <%@ Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
    <%@ Register Tagprefix="Utilities" Namespace="Microsoft.SharePoint.Utilities" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
    <%@ Register Tagprefix="asp" Namespace="System.Web.UI" Assembly="System.Web.Extensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" %>
    <%@ Import Namespace="Microsoft.SharePoint" %>
    <%@ Assembly Name="Microsoft.Web.CommandUI, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
    <%@ Page Language="C#" Inherits="Microsoft.SharePoint.WebControls.LayoutsPageBase" MasterPageFile="../_catalogs/masterpage/mybasic1.master" meta:progid="SharePoint.WebPartPage.Document" %>

    <asp:Content ID="Main" ContentPlaceHolderID="ContentPlaceHolderMain" runat="server">
    <img alt="My Image" longdesc="My image from images folder" src="../images/myimg1.png" />
    </asp:Content>
    ```

6.  Zapisz stronę zaktualizowanej witryny.

## <a name="export-the-items-from-sharepoint"></a>Eksportowanie elementów z programu SharePoint
 Eksportować z programu SharePoint do rozwiązania programu SharePoint (*.wsp*) pliku.

#### <a name="to-export-items-from-sharepoint-designer"></a>Aby wyeksportować elementy z programu SharePoint Designer

1.  W programie SharePoint Designer, w okienku nawigacji wybierz **witryny zespołu** obiektu, a następnie na **witryny** Wstążce, wybierz polecenie **Zapisz jako szablon**.

2.  W **Zapisz jako szablon** okna dialogowego wprowadź nazwę pliku i nazwa szablonu, wybierz opcję **dołączanie zawartości** pole wyboru, a następnie wybierz **OK** przycisku.

     Spowoduje to zapisanie zawartości witryny w *.wsp* pliku.

3.  Po rozwiązaniu eksportuje, wybierz **Galeria rozwiązań** łącze, aby wyświetlić listę plików dostępnych rozwiązań.

4.  Otwórz menu skrótów dla nowego *.wsp* , a następnie wybierz **Zapisz element docelowy jako** zapisać go w systemie.

## <a name="import-the-items-into-visual-studio"></a>Importowanie elementów do programu Visual Studio
 Importuj *.wsp* mezzanine do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Po zaimportowaniu zawartości można go dostosować, dodać więcej elementów i następnie wdrożysz go.

#### <a name="to-import-items-from-the-wsp-file-into-visual-studio"></a>Aby importować elementy z pliku .wsp do programu Visual Studio

1. W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], Utwórz **Importowanie pakietu rozwiązań programu SharePoint 2010** projektu.

2. Na **Wybieranie elementów do zaimportowania** w obszarze **modułu** w **typu** kolumny, zaznacz pola wyboru dla tylko plików w poniższej tabeli do zaimportowania.


   | Nazwa pliku | Opis |
   |------------------------|-----------------------------------------------|
   | \_catalogsmasterpage\_ | Niestandardowej strony wzorcowej. |
   | images_ | Plik obrazu w systemie plików programu SharePoint. |
   | SitePages_ | Strona witryny. |


3. Wybierz **Zakończ** przycisk, aby importować wybrane elementy.

4. W **Eksploratora rozwiązań**, wybierz \_catalogsmasterpage\_ węzeł i ustaw wartość jego **Rozwiązywanie konfliktów wdrażania** właściwość **automatyczne** .

    Dzięki temu automatycznie rozwiązać wszystkie konflikty wdrażania.

5. Jeśli nowej strony wzorcowej ma taką samą nazwę jak istniejącej strony, upewnij się, że istniejącej strony nie jest oznaczony jako stronę wzorcową domyślnej lub niestandardowej strony wzorcowej w programie SharePoint Designer.

    Jeśli istniejącej strony wzorcowej jest oznaczona jako domyślna strona wzorcowa lub niestandardowej strony wzorcowej, zostanie wyświetlony błąd wdrażania z informacją, że nie można usunąć strony wzorcowej. Aby uniknąć tego problemu, wykonaj następujące czynności:

   -   Jeśli istniejące strony wzorcowej jest ustawiona jako domyślna strona wzorcowa, tymczasowo ustawić innej strony wzorcowej jako domyślnej strony wzorcowej. Po wdrożeniu plików w programie SharePoint, należy ustawić nowej strony wzorcowej jako domyślnej strony wzorcowej.

   -   Jeśli istniejące strony wzorcowej jest ustawiony jako niestandardowej strony wzorcowej, tymczasowo ustawić innej strony wzorcowej jako niestandardowej strony wzorcowej. Po wdrożeniu plików w programie SharePoint, należy ustawić nowej strony wzorcowej jako niestandardowej strony wzorcowej.

6. Na pasku menu wybierz **kompilacji** > **wdrożyć rozwiązanie**.

7. Otwórz witrynę programu SharePoint, aby wyświetlić elementy wdrożone.

   Alternatywny sposób, aby zaimportować pliki do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] i wdrażać je do programu SharePoint jest dodanie plików w modułach [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Jak: Importowanie tematu lub strony wzorcowej](../sharepoint/how-to-import-a-master-page-or-theme.md) i [używać modułów podczas dołączania plików rozwiązania](../sharepoint/using-modules-to-include-files-in-the-solution.md).

## <a name="see-also"></a>Zobacz także
- [Importowanie elementów z istniejącej witryny programu SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Tworzenie formantów wielokrotnych dla części sieciowych lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
