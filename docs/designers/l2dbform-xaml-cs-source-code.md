---
title: Kod źródłowy L2DBForm.XAML.CS
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: sample
ms.assetid: 5a40dad3-6763-4576-b3ad-874df3f2c8d9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a99effa4820b33e860d44889bc67ba48ee9b590a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53960501"
---
# <a name="l2dbformxamlcs-source-code"></a>Kod źródłowy L2DBForm.xaml.cs

Ten temat zawiera zawartość i opis kodu źródłowego języka C# w pliku *L2DBForm.xaml.cs*. Klasy częściowe L2XDBForm zawarte w tym pliku można podzielić na trzy logiczne sekcje: elementy członkowskie danych i `OnRemove` i `OnAddBook` procedury obsługi zdarzeń kliknięcia przycisku.

## <a name="data-members"></a>Elementy członkowskie danych

Dwie prywatne składowe danych są używane do kojarzenia tej klasy, aby zasoby okna używane w *L2DBForm.xaml*.

-   Zmienna przestrzeni nazw `myBooks` jest inicjowany do `"http://www.mybooks.com"`.

-   Element członkowski `bookList` jest inicjowana w Konstruktorze ciąg CDATA w *L2DBForm.xaml* o następujący wiersz:

    ```csharp
    bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;
    ```

## <a name="onaddbook-event-handler"></a>Program obsługi zdarzeń OnAddBook

Ta metoda zawiera trzy następujące instrukcje:

-   Pierwsza instrukcja warunkowego jest używany do sprawdzania poprawności danych wejściowych.

-   Druga instrukcja tworzy nową <xref:System.Xml.Linq.XElement> z ciągu wartości które użytkownik wprowadził w **Dodawanie nowej książki** sekcji interfejsu użytkownika.

-   Ostatnią instrukcją dodaje ten nowy element książki do dostawcy danych w *L2DBForm.xaml*. W związku z tym dane dynamiczne powiązanie automatycznie aktualizuje interfejsu użytkownika za pomocą tego nowego elementu; bardzo dostarczone przez użytkownika jest wymagany żaden kod.

## <a name="onremove-event-handler"></a>Program obsługi zdarzeń OnRemove

`OnRemove` Program obsługi jest bardziej skomplikowane niż `OnAddBook` obsługi dwóch powodów. Po pierwsze ponieważ nieprzetworzonym kodzie XML zawiera zachowanych biały znak, dopasowania oddzielane należy również usunąć wpis książki. Po drugie dla wygody zaznaczoną opcję spowodowało na usunięty element jest resetowany do poprzedniego na liście.

Jednak pracy core usunięcia elementu zaznaczoną książkę odbywa się przez tylko dwóch instrukcji:

-   Po pierwsze element książki, skojarzone z aktualnie wybranego elementu w polu listy są pobierane:

    ```csharp
    XElement selBook = (XElement)lbBooks.SelectedItem;
    ```

-   Następnie ten element zostanie usunięty z dostawcy danych:

    ```csharp
    selBook.Remove();
    ```

Ponownie wiązania danych dynamicznego gwarantuje interfejsu użytkownika programu jest automatycznie aktualizowana.

## <a name="example"></a>Przykład

### <a name="code"></a>Kod

```csharp
using System;
using System.Linq;
using System.Collections;
using System.Collections.Generic;
using System.Diagnostics;
using System.Text;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Input;
using System.Xml;
using System.Xml.Linq;

namespace LinqToXmlDataBinding {
    /// <summary>
    /// Interaction logic for L2XDBForm.xaml
    /// </summary>

    public partial class L2XDBForm : System.Windows.Window
    {
        XNamespace mybooks = "http://www.mybooks.com";
        XElement bookList;

        public L2XDBForm()
        {
            InitializeComponent();
            bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;
        }

        void OnRemoveBook(object sender, EventArgs e)
        {
            int index = lbBooks.SelectedIndex;
            if (index < 0) return;

            XElement selBook = (XElement)lbBooks.SelectedItem;
            //Get next node before removing element.
            XNode nextNode = selBook.NextNode;
            selBook.Remove();

            //Remove any matching newline node.
            if (nextNode != null && nextNode.ToString().Trim().Equals(""))
            { nextNode.Remove(); }

            //Set selected item.
            if (lbBooks.Items.Count > 0)
            {  lbBooks.SelectedItem = lbBooks.Items[index > 0 ? index - 1 : 0]; }
        }

        void OnAddBook(object sender, EventArgs e)
        {
            if (String.IsNullOrEmpty(tbAddID.Text) ||
                String.IsNullOrEmpty(tbAddValue.Text))
            {
                MessageBox.Show("Please supply both a Book ID and a Value!", "Entry Error!");
                return;
            }
            XElement newBook = new XElement(
                                mybooks + "book",
                                new XAttribute("id", tbAddID.Text),
                                tbAddValue.Text);
            bookList.Add("  ", newBook, "\r\n");
        }
    }
}
```

### <a name="comments"></a>Komentarze

Dla skojarzonego źródła XAML te programy obsługi, zobacz [kod źródłowy L2DBForm.xaml](../designers/l2dbform-xaml-source-code.md).

## <a name="see-also"></a>Zobacz także

- [Przewodnik: Elementu linqtoxmldatabinding — przykład](../designers/walkthrough-linqtoxmldatabinding-example.md)
- [Kod źródłowy L2DBForm.xaml](../designers/l2dbform-xaml-source-code.md)