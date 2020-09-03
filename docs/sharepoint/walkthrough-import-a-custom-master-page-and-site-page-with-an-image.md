---
title: Zaimportuj niestandardową stronę wzorcową & strony witryny z obrazem
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 311124b2e0b81e70c4c2a7b40754207e6c66b749
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015682"
---
# <a name="walkthrough-import-a-custom-master-page-and-site-page-with-an-image"></a>Przewodnik: Importowanie niestandardowej strony wzorcowej i strony witryny z obrazem
  W tym instruktażu przedstawiono sposób importowania niestandardowej strony wzorcowej programu SharePoint i strony witryny z obrazem do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektu programu SharePoint.

 W tym instruktażu przedstawiono sposób wykonywania następujących zadań:

- Utwórz niestandardową stronę wzorcową i stronę witryny przy użyciu obrazu w programie SharePoint Designer.

- Wyeksportuj niestandardową stronę wzorcową, obraz i stronę witryny do pliku rozwiązania programu SharePoint (*wsp*).

- Zaimportuj i Wdróż plik *. wsp* w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projekcie programu SharePoint przy użyciu projektu Importuj pakiet rozwiązania SharePoint.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Aby ukończyć ten przewodnik, należy dysponować następującymi składnikami:

- Obsługiwane wersje programów [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] i SharePoint.

- Programu Visual Studio.

- SharePoint Designer 2010.

## <a name="create-items-in-sharepoint-designer"></a>Tworzenie elementów w programie SharePoint Designer
 Ten przykład pokazuje, jak utworzyć trzy elementy w programie SharePoint Designer do eksportu: niestandardowa strona wzorcowa, Strona witryny odwołująca się do niestandardowej strony wzorcowej oraz plik obrazu, który będzie wyświetlany na stronie witryny. Obraz zostanie dodany do folderu/Images/w programie SharePoint.

#### <a name="to-create-a-custom-master-page-in-sharepoint-designer"></a>Aby utworzyć niestandardową stronę wzorcową w programie SharePoint Designer

1. W oknie Projektant programu SharePoint, w okienku nawigacji, wybierz obiekt **strony wzorcowej** .

2. Na Wstążce **stron wzorcowych** wybierz **pustą stronę wzorcową**.

3. Wybierz nową stronę wzorcową, a następnie na Wstążce **strony wzorcowe** wybierz polecenie **Edytuj plik**.

4. W dolnej części programu SharePoint Designer wybierz kartę **kod** .

5. Zastąp istniejący znacznik następującym znacznikiem.

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

6. Zapisz stronę, wybierz kartę **strony główne** i Zmień nazwę strony wzorcowej na **mybasic1. Master**.

## <a name="add-an-image-to-the-content-database-in-sharepoint-designer"></a>Dodawanie obrazu do bazy danych zawartości w programie SharePoint Designer
 Teraz można dodać obraz do wyświetlania na stronie witryny. Obraz jest wdrażany w bazie danych zawartości programu SharePoint.

#### <a name="to-add-an-image-to-the-content-database-in-sharepoint-designer"></a>Aby dodać obraz do bazy danych zawartości w programie SharePoint Designer

1. W okienku nawigacji wybierz obiekt lokacja **wszystkie pliki** , a następnie w widoku drzewa wybierz folder **obrazy** .

2. Na Wstążce **wszystkie pliki** wybierz pozycję **Importuj pliki**, wybierz wybrany plik, a następnie wybierz przycisk **OK** . W tym przykładzie plik ma nazwę **myimg1.png**.

     Opcjonalnie można utworzyć podfolder, aby ułatwić organizowanie obrazów.

3. Zamknij okno dialogowe **Importowanie** .

## <a name="create-a-site-page"></a>Tworzenie strony witryny
 Ta strona podstawowa witryny używa niestandardowej strony wzorcowej i wyświetla obraz dodany w poprzednim kroku.

#### <a name="to-create-a-site-page"></a>Aby utworzyć stronę witryny

1. W okienku nawigacji wybierz obiekt **strony witryny** .

2. Na Wstążce **stron** wybierz przycisk **Strona** , wybierz typ strony **aspx** , a następnie nadaj mu nazwę nowy plik **mycontentpage1. aspx**.

     Opcjonalnie można utworzyć podfolder, aby ułatwić Organizowanie stron witryny.

3. Na liście strony lokacji wybierz **mycontentpage1. aspx** , aby otworzyć stronę właściwości, a następnie w dolnej części strony wybierz łącze **Edytuj plik** .

     Jeśli zostanie wyświetlony komunikat z informacją, że ta strona nie zawiera żadnych regionów edytowalnych w trybie awaryjnym i pyta, czy chcesz otworzyć tę stronę w trybie zaawansowanym, wybierz przycisk **tak** .

4. W dolnej części strony wybierz przycisk **kod** .

5. Zastąp istniejący znacznik następującym znacznikiem.

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

6. Zapisz zaktualizowaną stronę witryny.

## <a name="export-the-items-from-sharepoint"></a>Eksportuj elementy z programu SharePoint
 Wyeksportuj elementy z programu SharePoint do pliku rozwiązania programu SharePoint (*wsp*).

#### <a name="to-export-items-from-sharepoint-designer"></a>Aby wyeksportować elementy z programu SharePoint Designer

1. W oknie Projektant programu SharePoint w okienku nawigacji wybierz obiekt **Witryna zespołu** , a następnie na Wstążce **lokacja** wybierz pozycję **Zapisz jako szablon**.

2. W oknie dialogowym **Zapisz jako szablon** wprowadź nazwę pliku i nazwę szablonu, zaznacz pole wyboru **Dołącz zawartość** , a następnie wybierz przycisk **OK** .

     Spowoduje to zapisanie zawartości witryny w pliku *. wsp* .

3. Po wyeksportowaniu rozwiązania wybierz łącze **Galeria rozwiązań** , aby wyświetlić listę dostępnych plików rozwiązania.

4. Otwórz menu skrótów dla nowego pliku *. wsp* , a następnie wybierz polecenie **Zapisz obiekt docelowy jako** , aby zapisać go w systemie.

## <a name="import-the-items-into-visual-studio"></a>Importuj elementy do programu Visual Studio
 Zaimportuj plik *. wsp* do programu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Po zaimportowaniu zawartości można ją dostosować, dodać więcej elementów, a następnie wdrożyć ją.

#### <a name="to-import-items-from-the-wsp-file-into-visual-studio"></a>Aby zaimportować elementy z pliku. wsp do programu Visual Studio

1. W programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Utwórz projekt **pakietu rozwiązań programu SharePoint 2010** .

2. Na stronie **Wybierz elementy do zaimportowania** w obszarze **moduł** w kolumnie **Typ** zaznacz pola wyboru dla plików znajdujących się w poniższej tabeli w celu zaimportowania.

   | Nazwa pliku | Opis |
   |------------------------|-----------------------------------------------|
   | \_catalogsmasterpage\_ | Niestandardowa strona wzorcowa. |
   | images_ | Plik obrazu w systemie plików programu SharePoint. |
   | SitePages_ | Strona witryna. |

3. Wybierz przycisk **Zakończ** , aby zaimportować wybrane elementy.

4. W **Eksplorator rozwiązań**wybierz \_ \_ węzeł catalogsmasterpage i ustaw wartość właściwości **Rozwiązywanie konfliktów wdrożenia** na **Automatyczne**.

    Pozwala to zagwarantować, że konflikty wdrożenia są rozwiązywane automatycznie.

5. Jeśli nowa strona główna ma taką samą nazwę jak istniejąca strona, upewnij się, że istniejąca strona nie jest oznaczona jako domyślna Strona główna lub niestandardowa strona wzorcowa w programie SharePoint Designer.

    Jeśli istniejąca strona wzorcowa jest oznaczona jako domyślna Strona główna lub niestandardowa strona wzorcowa, zostanie wyświetlony błąd wdrażania z informacją o tym, że nie można usunąć strony wzorcowej. Aby uniknąć tego problemu, wykonaj następujące czynności:

   - Jeśli istniejąca strona wzorcowa jest ustawiona jako domyślna strona wzorcowa, tymczasowo ustaw inną stronę wzorcową jako domyślną stronę wzorcową. Po wdrożeniu plików w programie SharePoint ustaw nową stronę wzorcową jako domyślną stronę wzorcową.

   - Jeśli istniejąca strona wzorcowa jest ustawiona jako niestandardowa strona wzorcowa, tymczasowo ustaw inną stronę wzorcową jako niestandardową stronę wzorcową. Po wdrożeniu plików w programie SharePoint ustaw nową stronę wzorcową jako niestandardową stronę wzorcową.

6. Na pasku menu wybierz kolejno opcje **kompilacja**  >  **Wdróż rozwiązanie**.

7. Otwórz witrynę programu SharePoint, aby wyświetlić wdrożone elementy.

   Alternatywny sposób importowania plików do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] programu SharePoint i ich wdrażania polega na dodaniu plików do modułów w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Instrukcje: Importowanie strony wzorcowej lub motywu](../sharepoint/how-to-import-a-master-page-or-theme.md) i [używanie modułów do dołączania plików w rozwiązaniu](../sharepoint/using-modules-to-include-files-in-the-solution.md).

## <a name="see-also"></a>Zobacz też
- [Importowanie elementów z istniejącej witryny programu SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Tworzenie kontrolek wielokrotnego użytku dla części sieci Web lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
