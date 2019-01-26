---
title: Testowanie aplikacji programu SharePoint za pomocą kodowanych testów interfejsu użytkownika
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: a4b79531948310d0f2628b6ade334d6ea9df35ca
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54946021"
---
# <a name="test-sharepoint-applications-with-coded-ui-tests"></a>Testowanie aplikacji programu SharePoint za pomocą kodowanych testów interfejsu użytkownika

Łącznie kodowane testy interfejsu użytkownika w aplikacji programu SharePoint pozwala zweryfikować poprawne działanie całej aplikacji, w tym jego formantów interfejsu użytkownika. Kodowane testy interfejsu użytkownika można zweryfikować wartości i logika interfejsu użytkownika.

Aby dowiedzieć się więcej na temat korzyści z używania kodowanych testów interfejsu użytkownika, zobacz [automatyzacji w użyciu interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md).

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Wymagania**

- Visual Studio Enterprise

## <a name="create-a-coded-ui-test-for-a-sharepoint-app"></a>Tworzenie kodowanego testu interfejsu użytkownika dla aplikacji programu SharePoint

[Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md) dla aplikacji programu SharePoint jest taki sam, jak podczas tworzenia testów dla innych typów aplikacji. Nagrywanie i odtwarzanie jest obsługiwana dla wszystkich kontrolek w **edytowania w Internecie** interfejsu. Interfejs do wybierania kategorii i składniki web Part są wszystkie formanty standardowe sieci web.

![— składniki Web Part programu SharePoint](../test/media/cuit_sharepoint.png)

> [!NOTE]
> W przypadku rejestrowania akcji, sprawdź poprawność działania przed wygenerowaniem kodu. Ponieważ różne zachowania skojarzone z myszy po wskazaniu wskaźnikiem, jest ona włączona domyślnie. Uważaj usunąć nadmiarowe ruchów z kodowanych testów interfejsu użytkownika. Można to zrobić, edytując kod dla testu lub za pomocą [edytora testu interfejsu użytkownika](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

## <a name="test-office-controls-within-a-sharepoint-app"></a>Testowanie kontrolki pakietu Office w ramach aplikacji programu SharePoint

Aby włączyć automatyzacji dla niektórych części sieci web pakietu office w aplikacji programu SharePoint, masz wprowadzenie pewnych zmian kodu.

> [!NOTE]
> Testowanie kontrolki programu Visio i PowerPoint w aplikacji programu SharePoint nie jest obsługiwane.

### <a name="excel-cell-controls"></a>Kontrolki komórki programu Excel

Aby dołączyć kontrolki komórki programu Excel, należy wprowadzić pewne zmiany w kodzie kodowanego testu interfejsu użytkownika.

> [!WARNING]
> Wprowadzanie tekstu w dowolnej komórki programu Excel, a następnie akcję klawiszy Strzałka w nie rejestruje poprawnie. Zaznacz komórki za pomocą myszy.

W przypadku rejestrowania akcji w pustej komórce, należy zmodyfikować kod przez podwójne kliknięcie komórki, a następnie wykonuje operację tekstu. Jest to niezbędne, ponieważ aktywuje kliknij w komórce następuje dowolną akcję klawiatury `textarea` w komórce. Po prostu rejestrowanie `setvalue` w pustej komórce będzie wyszukiwać `editbox` które nie są stosowane, dopóki kliknął komórki. Na przykład:

```csharp
Mouse.DoubliClick(uiItemCell,new Point(31,14));
uiGridKeyboardInputEdit.Text=value;
```

W przypadku rejestrowania akcji w komórce pusty, a następnie nagrywanie pobiera nieco bardziej skomplikowane, ponieważ moment, Dodaj tekst do komórki, nowy \<div > formant jest dodawany jako element podrzędny elementu komórki. Nowy \<div > po prostu wprowadzony tekst zawiera formant. Rejestrator musi zarejestrować akcje na nowym \<div > formant; jednak nie ponieważ nowy \<div > formant nie istnieje do czasu, po wprowadzeniu testu. Musi ręcznie wprowadzić następujące zmiany kodu w celu uwzględnienia tego problemu.

1. Przejdź do inicjowania komórkę i wprowadź `RowIndex` i `ColumnIndex` podstawowe właściwości:

    ```csharp
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. RowIndex] = "3";
    this.mUIItemCell.SearchProperties[HtmlCell.PropertyNames. ColumnIndex] = "3";
    ```

2. Znajdź `HtmlDiv` podrzędnym komórki:

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

3. Dodaj kod dla myszy kliknij dwukrotnie działanie `HtmlDiv`:

    ```csharp
    Mouse.DoubleClick(uIItemPane, new Point(31, 14)); )
    ```

4. Dodaj kod, aby ustawić tekst na `TextArea`:

    ```csharp
    uIGridKeyboardInputEdit.Text = value; }
    ``

## See also

- [Use UI automation to test your code](../test/use-ui-automation-to-test-your-code.md)
- [Create SharePoint solutions](../sharepoint/create-sharepoint-solutions.md)
- [Verify and debug SharePoint code](../sharepoint/verifying-and-debugging-sharepoint-code.md)
- [Build and debug SharePoint solutions](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Profile the performance of SharePoint applications](../sharepoint/profiling-the-performance-of-sharepoint-applications.md)
