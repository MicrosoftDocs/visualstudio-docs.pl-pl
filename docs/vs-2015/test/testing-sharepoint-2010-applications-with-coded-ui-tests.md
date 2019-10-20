---
title: Testowanie aplikacji programu SharePoint 2010 przy użyciu kodowanych testów interfejsu użytkownika | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 51b53778-469c-4cc9-854c-4e4992d6389b
caps.latest.revision: 32
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2f9df50094676eea5694a29362772c9c44fa456b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660383"
---
# <a name="testing-sharepoint-2010-applications-with-coded-ui-tests"></a>Testowanie aplikacji SharePoint 2010 za pomocą kodowanych testów interfejsu użytkownika
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dołączenie kodowanych testów interfejsu użytkownika w aplikacji SharePoint umożliwia sprawdzenie, czy cała aplikacja, w tym jej kontrolki interfejsu użytkownika, działa poprawnie. Kodowane testy interfejsu użytkownika mogą również sprawdzać wartości i logikę w interfejsie użytkowników.

 **Requirements**

- Visual Studio Enterprise

## <a name="what-else-should-i-know-about-coded-ui-tests"></a>Co jeszcze muszę wiedzieć o kodowanych testach interfejsu użytkownika?
 Aby dowiedzieć się więcej o zaletach korzystania z kodowanych testów interfejsu użytkownika, zobacz [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md) i [testowania ciągłego dostarczania w programie Visual Studio 2012 — Rozdział 5 Automatyzowanie testów systemu](http://go.microsoft.com/fwlink/?LinkID=255196).

 **Uwagi**

- ![Prerequsite](../test/media/prereq.png "Ignoruj") Kodowane testy interfejsu użytkownika dla aplikacji programu SharePoint są obsługiwane tylko przez program SharePoint 2010.

- ![Prerequsite](../test/media/prereq.png "Ignoruj") Obsługa formantów Visio i PowerPoint 2010 w aplikacji SharePoint nie jest obsługiwana.

## <a name="creating-a-coded-ui-test-for-your-sharepoint-app"></a>Tworzenie kodowanego testu interfejsu użytkownika dla aplikacji programu SharePoint
 [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate) dla aplikacji programu SharePoint 2010 jest takie samo jak tworzenie testów dla innych typów aplikacji. Nagrywanie i odtwarzanie jest obsługiwane dla wszystkich kontrolek w interfejsie edycji sieci Web. Interfejs do wybierania kategorii i części sieci Web to standardowe formanty sieci Web.

 ![Części sieci Web programu SharePoint](../test/media/cuit-sharepoint.png "CUIT_SharePoint")

> [!NOTE]
> Jeśli rejestrujesz akcję, zweryfikuj akcje przed wygenerowaniem kodu. Ponieważ istnieje kilka zachowań skojarzonych z przesuwaniem myszy, jest on domyślnie włączony. Należy zachować ostrożność, aby usunąć nadmiarowe aktywa z kodowanych testów interfejsu użytkownika. Można to zrobić, edytując kod dla testu lub korzystając z [edytora kodowanego testu interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

## <a name="including-testing-of-office-2010-controls-within-your-sharepoint-app"></a>Obejmuje Testowanie formantów pakietu Office 2010 w aplikacji SharePoint
 Aby włączyć automatyzację niektórych części sieci Web pakietu Office 2010 w aplikacji SharePoint, musisz wprowadzić pewne drobne modyfikacje kodu.

> [!WARNING]
> Obsługa formantów Visio i PowerPoint 2010 nie jest obsługiwana.

### <a name="excel-2010-cell-controls"></a>Kontrolki komórki w programie Excel 2010
 Aby dołączyć kontrolki komórki programu Excel, musisz wprowadzić pewne zmiany w kodzie kodowanego testu interfejsu użytkownika.

> [!WARNING]
> Wprowadzenie tekstu w dowolnej komórce programu Excel, po którym następuje akcja klawisza Strzałka, nie rejestruje się poprawnie. Użyj myszy, aby zaznaczyć komórki.

 Jeśli rejestrujesz akcje w pustej komórce, musisz zmodyfikować kod przez dwukrotne kliknięcie komórki, a następnie wykonanie operacji ustawiania tekstu. Jest to potrzebne, ponieważ kliknięcie komórki, a po niej każda akcja klawiatury aktywuje `textarea` w komórce. Po prostu nagrywanie `setvalue` w pustej komórce spowoduje wyszukanie `editbox`, które nie są obecne, dopóki nie zostanie kliknięta komórka. Na przykład:

```csharp
Mouse.DoubliClick(uiItemCell,new Point(31,14));
uiGridKeyboardInputEdit.Text=value;
```

 Jeśli rejestrujesz akcje w niepustej komórce, nagranie pobiera nieco bardziej skomplikowane, ponieważ chwilę dodasz tekst do komórki, nowy formant \<div > zostanie dodany jako element podrzędny komórki. Nowa kontrolka > \<div zawiera tekst, który właśnie został wprowadzony. Rejestrator musi rejestrować akcje na nowej kontrolce > \<div. jednak nie jest to możliwe, ponieważ Nowa kontrolka > \<div nie istnieje, dopóki nie zostanie wprowadzony test. Aby obsłużyć ten problem, należy ręcznie wprowadzić następujące zmiany w kodzie.

1. Przejdź do inicjowania komórki i ustaw `RowIndex` i `ColumnIndex` właściwości podstawowe:

    ```csharp
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. RowIndex] = "3";
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. ColumnIndex] = "3";
    ```

2. Znajdź `HtmlDiv` podrzędny komórki:

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

3. Dodaj kod dla akcji dwukrotnego kliknięcia przycisku myszy na `HtmlDiv`:

    ```csharp
    Mouse.DoubleClick(uIItemPane, new Point(31, 14)); )
    ```

4. Dodaj kod, aby ustawić tekst na `TextArea`:

    ```csharp
    uIGridKeyboardInputEdit.Text = value; }
    ```

## <a name="enabling-coded-ui-testing-of-silverlight-web-parts-in-your-sharepoint-2010-app"></a>Włączanie testów kodowanego interfejsu użytkownika dla części sieci Web Silverlight w aplikacji SharePoint 2010
 Testowanie programu Silverlight nie jest obsługiwane w programie Visual Studio 2012 i nowszych. Jeśli jednak chcesz przetestować części sieci Web Silverlight w aplikacji SharePoint 2010, możesz zainstalować oddzielną wtyczkę Silverlight z galerii programu Visual Studio.

#### <a name="setting-up-your-machine"></a>Konfigurowanie maszyny

1. Upewnij się, że masz zainstalowany program Visual Studio 2012,1 lub nowszy.

2. Zainstaluj [wtyczkę testową interfejsu użytkownika Microsoft Visual Studio dla programu Silverlight](http://visualstudiogallery.msdn.microsoft.com/28312a61-9451-451a-990c-c9929b751eb4).

3. Zainstaluj [programu Fiddler](http://www.fiddler2.com/fiddler2/). Jest to po prostu narzędzie, które przechwytuje i rejestruje ruch HTTP.

4. Pobierz [projekt fiddlerXap](https://40jajy3iyl373v772m19fybm-wpengine.netdna-ssl.com/wp-content/uploads/sites/6/2019/02/FiddlerXapProxy.zip). Rozpakuj go, skompiluj i uruchom skrypt "CopySLHelper. bat", aby zainstalować pomocniczą bibliotekę DLL, która jest wymagana do testowania części sieci Web programu Silverlight w przypadku korzystania z narzędzia programu Fiddler.

   Po skonfigurowaniu maszyny w celu rozpoczęcia testowania aplikacji SharePoint 2010 przy użyciu części sieci Web Silverlight wykonaj następujące kroki:

#### <a name="testing-silverlight-web-parts"></a>Testowanie części sieci Web Silverlight

1. Uruchom programu Fiddler.

2. Wyczyść pamięć podręczną przeglądarki. Jest to konieczne, ponieważ plik XAP, który zawiera Biblioteka DLL pomocnika automatyzacji interfejsu użytkownika Silverlight, jest zazwyczaj buforowany. Musimy upewnić się, że zmodyfikowany plik XAP został pobrany, więc czyścimy pamięć podręczną przeglądarki.

3. Otwórz stronę sieci Web.

4. Rozpocznij Rejestrator i Generuj kod, taki jak dla regularnego testowania aplikacji sieci Web.

5. Należy upewnić się, że wygenerowany kod odwołuje się do pliku Microsoft. VisualStudio. TestTools. UITest. Extension. Silverlight. dll.

     Aby uzyskać więcej informacji, zobacz [testowanie interfejsu użytkownika SharePoint 2010 przy użyciu programu Visual Studio 2012](http://blogs.msdn.com/b/visualstudioalm/archive/2012/11/01/ui-testing-sharepoint-2010-with-visual-studio-2012.aspx)

## <a name="external-resources"></a>Zasoby zewnętrzne

### <a name="blogs"></a>Blogi
 [Testowanie interfejsu użytkownika programu SharePoint 2010 z programem Visual Studio 2012](http://blogs.msdn.com/b/visualstudioalm/archive/2012/11/01/ui-testing-sharepoint-2010-with-visual-studio-2012.aspx)

 [Informacje o logice wyszukiwania dla formantów Silverlight w kodowanym teście interfejsu użytkownika](http://blogs.msdn.com/b/tapas_sahoos_blog/archive/2010/11/16/understanding-the-search-logic-for-silverlight-controls-in-coded-ui-test.aspx)

 [Pobieranie właściwości kontrolki Silverlight](http://blogs.msdn.com/b/tapas_sahoos_blog/archive/2010/11/16/fetching-property-of-a-silverlight-control.aspx)

 [Indeks zawartości dla kodowanego testu interfejsu użytkownika](http://blogs.msdn.com/b/mathew_aniyan/archive/2010/02/11/content-index-for-coded-ui-test.aspx)

### <a name="guidance"></a>Wskazówki
 [Testowanie w celu ciągłego dostarczania przy użyciu programu Visual Studio 2012 — Rozdział 5 Automatyzowanie testów systemu](http://go.microsoft.com/fwlink/?LinkID=255196)

### <a name="forum"></a>Forum
 [Blog programu Visual Studio ALM + Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=254496)

## <a name="see-also"></a>Zobacz też
 [Korzystanie z automatyzacji interfejsu użytkownika do testowania](../test/use-ui-automation-to-test-your-code.md) [wydajności sieci Web i testów obciążenia w kodzie programu sharepoint 2010 i 2013](https://msdn.microsoft.com/library/20c2e469-0e4e-4296-a739-c0e8fff36e54) [Tworzenie rozwiązań SharePoint](https://msdn.microsoft.com/library/4bfb1e59-97c9-4594-93f8-3068b4eb9631) [Sprawdzanie i debugowanie kodu programu](https://msdn.microsoft.com/library/b5f3bce2-6a51-41b1-a292-9e384bae420c) SharePoint [Tworzenie i debugowanie programu SharePoint Rozwiązania](https://msdn.microsoft.com/library/c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae) [profilowania wydajności aplikacji programu SharePoint](https://msdn.microsoft.com/library/61ae02e7-3f37-4230-bae1-54a498c2fae8)
