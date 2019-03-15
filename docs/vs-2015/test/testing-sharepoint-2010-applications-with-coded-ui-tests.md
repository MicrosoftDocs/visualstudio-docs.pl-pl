---
title: Testowanie aplikacji SharePoint 2010 za pomocą kodowanych testów interfejsu użytkownika | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 51b53778-469c-4cc9-854c-4e4992d6389b
caps.latest.revision: 32
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6f512ac0788128db87269407c10ae400268283f5
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57873547"
---
# <a name="testing-sharepoint-2010-applications-with-coded-ui-tests"></a>Testowanie aplikacji SharePoint 2010 za pomocą kodowanych testów interfejsu użytkownika
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Łącznie kodowane testy interfejsu użytkownika w aplikacji programu SharePoint pozwala zweryfikować poprawne działanie całej aplikacji, w tym jego formantów interfejsu użytkownika. Kodowane testy interfejsu użytkownika można zweryfikować wartości i logika interfejsu użytkownika.  
  
 **Wymagania**  
  
-   Visual Studio Enterprise  
  
## <a name="what-else-should-i-know-about-coded-ui-tests"></a>Co jeszcze muszę wiedzieć o kodowane testy interfejsu użytkownika?  
 Aby dowiedzieć się więcej na temat korzyści z używania kodowanych testów interfejsu użytkownika, zobacz [Użyj interfejsu użytkownika do testów Your kodu automatyzacji](../test/use-ui-automation-to-test-your-code.md) i [testowanie dostarczania ciągłego w programie Visual Studio 2012 – rozdział 5 Automatyzacja testów systemu](http://go.microsoft.com/fwlink/?LinkID=255196).  
  
 **Uwagi**  
  
-   ![Wymagań wstępnych](../test/media/prereq.png "wstępnie wymagany składnik") kodowanych testów interfejsu użytkownika dla aplikacji programu SharePoint są obsługiwane tylko przez program SharePoint 2010.  
  
-   ![Wymagań wstępnych](../test/media/prereq.png "wstępnie wymagany składnik") pomocy technicznej dla programu Visio i PowerPoint 2010 kontrolek w aplikacji programu SharePoint nie jest obsługiwane.  
  
## <a name="creating-a-coded-ui-test-for-your-sharepoint-app"></a>Tworzenie kodowanego testu interfejsu użytkownika dla aplikacji programu SharePoint  
 [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) dla aplikacji SharePoint 2010 jest taka sama, jak podczas tworzenia testów dla innych typów aplikacji. Nagrywanie i odtwarzanie jest obsługiwana dla wszystkich kontrolek w interfejsie edytowania w Internecie. Interfejs do wybierania kategorii i składniki web Part są wszystkie formanty standardowe sieci web.  
  
 ![Składniki web Part programu SharePoint](../test/media/cuit-sharepoint.png "CUIT_SharePoint")  
  
> [!NOTE]
>  W przypadku rejestrowania akcji, sprawdź poprawność działania przed wygenerowaniem kodu. Ponieważ różne zachowania skojarzone z myszy po wskazaniu wskaźnikiem, jest ona włączona domyślnie. Uważaj usunąć nadmiarowe ruchów z kodowanych testów interfejsu użytkownika. Można to zrobić, edytując kod dla testu lub za pomocą [edytora testu interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).  
  
## <a name="including-testing-of-office-2010-controls-within-your-sharepoint-app"></a>W tym testowanie pakietu Office 2010 formantów w aplikacji programu SharePoint  
 Aby włączyć automatyzacji dla niektórych pakietu office 2010 składników web Part w aplikacji programu SharePoint, masz wprowadzenie pewnych zmian kodu.  
  
> [!WARNING]
>  Obsługa kontrolek Visio i PowerPoint 2010 nie jest obsługiwane.  
  
### <a name="excel-2010-cell-controls"></a>Formanty komórki programu Excel 2010  
 Aby dołączyć kontrolki komórki programu Excel, należy wprowadzić pewne zmiany w kodzie kodowanego testu interfejsu użytkownika.  
  
> [!WARNING]
>  Wprowadzanie tekstu w dowolnej komórki programu Excel, a następnie akcję klawiszy Strzałka w nie rejestruje poprawnie. Zaznacz komórki za pomocą myszy.  
  
 W przypadku rejestrowania akcji w pustej komórce, należy zmodyfikować kod przez podwójne kliknięcie komórki, a następnie wykonuje operację tekstu. Jest to niezbędne, ponieważ aktywuje kliknij w komórce, następuje dowolną akcję klawiatury `textarea` w komórce. Po prostu rejestrowanie `setvalue` w pustej komórce będzie wyszukiwać `editbox` które nie są stosowane, dopóki kliknął komórki. Na przykład:  
  
```csharp  
Mouse.DoubliClick(uiItemCell,new Point(31,14));  
uiGridKeyboardInputEdit.Text=value;  
```  
  
 W przypadku rejestrowania akcji w komórce pusty, a następnie nagrywanie pobiera nieco bardziej skomplikowane, ponieważ moment, Dodaj tekst do komórki, nowy \<div > formant jest dodawany jako element podrzędny elementu komórki. Nowy \<div > po prostu wprowadzony tekst zawiera formant. Rejestrator musi zarejestrować akcje na nowym \<div > formant; jednak nie ponieważ nowy \<div > formant nie istnieje do czasu, po wprowadzeniu testu. Musi ręcznie wprowadzić następujące zmiany kodu w celu uwzględnienia tego problemu.  
  
1.  Przejdź do inicjowania komórkę i wprowadź `RowIndex` i `ColumnIndex` podstawowe właściwości:  
  
    ```csharp  
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. RowIndex] = "3";   
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. ColumnIndex] = "3";  
    ```  
  
2.  Znajdź `HtmlDiv` podrzędnym komórki:  
  
    ```csharp  
    private UITestControl getControlToDoubleClick(HtmlCell cell)   
    {   
         if (String.IsNullOrEmpty(cell.InnerText)) return cell;   
         HtmlDiv pane = new HtmlDiv(cell);   
         pane.FilterProperties[HtmlDiv.PropertyNames.InnerText] = cell.InnerText;   
         // Class is an important property in finding pane   
         pane.FilterProperties[HtmlDiv.PropertyNames.Class] = "cv-nwr";   
         UITestControlCollection panes = pane.FindMatchingControls();   
         return panes[0];   
    }  
  
    ```  
  
3.  Dodaj kod dla myszy kliknij dwukrotnie działanie `HtmlDiv`:  
  
    ```csharp  
    Mouse.DoubleClick(uIItemPane, new Point(31, 14)); )  
    ```  
  
4.  Dodaj kod, aby ustawić tekst na `TextArea`:  
  
    ```csharp  
    uIGridKeyboardInputEdit.Text = value; }  
    ```  
  
## <a name="enabling-coded-ui-testing-of-silverlight-web-parts-in-your-sharepoint-2010-app"></a>Włączanie testowania kodowanego interfejsu użytkownika programu Silverlight składników web Part w aplikacji SharePoint 2010  
 Testowanie Silverlight nie jest obsługiwana w programie Visual Studio 2012 i nowszych. Ale jeśli chcesz przetestować składniki web Part programu Silverlight w aplikacji SharePoint 2010, dodatek plug-in Silverlight oddzielne można zainstalować z galerii Visual Studio.  
  
#### <a name="setting-up-your-machine"></a>Konfigurowanie komputera  
  
1. Upewnij się, że masz programu Visual Studio 2012.1 lub nowszej.  
  
2. Zainstaluj [wtyczka testowania interfejsu użytkownika programu Microsoft Visual Studio dla programu Silverlight](http://visualstudiogallery.msdn.microsoft.com/28312a61-9451-451a-990c-c9929b751eb4).  
  
3. Zainstaluj [Fiddler](http://www.fiddler2.com/fiddler2/). Jest to po prostu narzędziem, które powoduje przechwycenie i dzienniki ruchu HTTP.  
  
4. Pobierz [projektu fiddlerXap](https://40jajy3iyl373v772m19fybm-wpengine.netdna-ssl.com/wp-content/uploads/sites/6/2019/02/FiddlerXapProxy.zip). Rozpakuj go, a następnie skompiluj go i uruchom skrypt "CopySLHelper.bat", aby zainstalować pomocnika biblioteki DLL, która jest wymagana do testowania składników web Part programu Silverlight, przy użyciu narzędzia Fiddler.  
  
   Po skonfigurowaniu komputera, aby rozpocząć testowanie aplikacji SharePoint 2010 przy użyciu składników web Part programu Silverlight, wykonaj następujące kroki:  
  
#### <a name="testing-silverlight-web-parts"></a>Testowanie składników web Part Silverlight  
  
1.  Uruchom narzędzie Fiddler.  
  
2.  Wyczyść pamięć podręczną przeglądarki. Jest to konieczne, ponieważ plik XAP, który zawiera DLL pomocnika automatyzacji interfejsu użytkownika programu Silverlight, zwykle jest buforowana. Mamy upewnij się, że zmodyfikowany plik XAP jest pobierana, dzięki czemu wyczyszczeniu pamięci podręcznej przeglądarki.  
  
3.  Otwórz stronę sieci web.  
  
4.  Uruchom Rejestrator i generowania kodu, tak jak w przypadku testowania aplikacji sieci web w regularnych.  
  
5.  Należy się upewnić, że wygenerowany kod odwołuje się do Microsoft.VisualStudio.TestTools.UITest.Extension.Silverlight.dll.  
  
     Aby uzyskać więcej informacji, zobacz [interfejsu użytkownika testowania programu SharePoint 2010 przy użyciu programu Visual Studio 2012](http://blogs.msdn.com/b/visualstudioalm/archive/2012/11/01/ui-testing-sharepoint-2010-with-visual-studio-2012.aspx)  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
  
### <a name="blogs"></a>Blogi  
 [SharePoint 2010 przy użyciu programu Visual Studio 2012 testów interfejsu użytkownika](http://blogs.msdn.com/b/visualstudioalm/archive/2012/11/01/ui-testing-sharepoint-2010-with-visual-studio-2012.aspx)  
  
 [Opis logiki wyszukiwania dla kontrolek Silverlight w kodowanego testu interfejsu użytkownika](http://blogs.msdn.com/b/tapas_sahoos_blog/archive/2010/11/16/understanding-the-search-logic-for-silverlight-controls-in-coded-ui-test.aspx)  
  
 [Pobieranie właściwości formantu Silverlight](http://blogs.msdn.com/b/tapas_sahoos_blog/archive/2010/11/16/fetching-property-of-a-silverlight-control.aspx)  
  
 [Indeks zawartości dla kodowanego testu interfejsu użytkownika](http://blogs.msdn.com/b/mathew_aniyan/archive/2010/02/11/content-index-for-coded-ui-test.aspx)  
  
### <a name="guidance"></a>Wskazówki  
 [Testowanie dostarczania ciągłego w programie Visual Studio 2012 — rozdział 5 automatyzację testów systemowych](http://go.microsoft.com/fwlink/?LinkID=255196)  
  
### <a name="forum"></a>Forum  
 [Visual Studio ALM + Team Foundation Server Blog](http://go.microsoft.com/fwlink/?LinkID=254496)  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)   
 [Wydajności sieci Web i obciążeniowy aplikacji SharePoint 2010 i 2013](http://msdn.microsoft.com/library/20c2e469-0e4e-4296-a739-c0e8fff36e54)   
 [Tworzenie rozwiązań SharePoint](http://msdn.microsoft.com/library/4bfb1e59-97c9-4594-93f8-3068b4eb9631)   
 [Weryfikowanie i debugowanie kodu programu SharePoint](http://msdn.microsoft.com/library/b5f3bce2-6a51-41b1-a292-9e384bae420c)   
 [Kompilowanie i debugowanie rozwiązań SharePoint](http://msdn.microsoft.com/library/c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae)   
 [Profilowanie wydajności aplikacji SharePoint](http://msdn.microsoft.com/library/61ae02e7-3f37-4230-bae1-54a498c2fae8)
