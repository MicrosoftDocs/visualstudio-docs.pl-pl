---
title: Kod źródłowy L2DBForm.xaml.cs | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 5a40dad3-6763-4576-b3ad-874df3f2c8d9
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3f783161865092f714955b65e6f2fa4791741cbe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664287"
---
# <a name="l2dbformxamlcs-source-code"></a>Kod źródłowy L2DBForm.xaml.cs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten temat zawiera treść i Opis kodu źródłowego C# w pliku L2DBForm.xaml.cs. Klasa częściowa L2XDBForm znajdująca się w tym pliku może zostać podzielona na trzy sekcje logiczne: elementy członkowskie danych i `OnRemove` `OnAddBook` przycisk i kliknij opcję programy obsługi zdarzeń.

## <a name="data-members"></a>Elementy członkowskie danych
 Dwa prywatne elementy członkowskie danych są używane do kojarzenia tej klasy z zasobami okna używanymi w kod źródłowy L2DBForm. XAML.

- Zmienna przestrzeni nazw `myBooks` jest inicjowana do `"http://www.mybooks.com"` .

- Element członkowski `bookList` jest inicjowany w konstruktorze do ciągu CDATA w kod źródłowy L2DBForm. XAML z następującym wierszem:

    ```
    bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;
    ```

## <a name="onaddbook-event-handler"></a>Procedura obsługi zdarzeń OnAddBook
 Ta metoda zawiera trzy następujące instrukcje:

- Pierwsza Instrukcja warunkowa służy do sprawdzania poprawności danych wejściowych.

- Druga instrukcja tworzy nową wartość <xref:System.Xml.Linq.XElement> ciągu wprowadzoną przez użytkownika w sekcji **Dodaj nowy** interfejs użytkownika książki (UI).

- Ostatnia instrukcja dodaje nowy element książki do dostawcy danych w kod źródłowy L2DBForm. XAML. W związku z tym dynamiczne powiązanie danych automatycznie zaktualizuje interfejs użytkownika przy użyciu tego nowego elementu; nie jest wymagany żaden dodatkowy kod dostarczony przez użytkownika.

## <a name="onremove-event-handler"></a>Procedura obsługi zdarzeń OnRemove
 `OnRemove`Program obsługi jest bardziej skomplikowany niż `OnAddBook` program obsługi z dwóch przyczyn. Po pierwsze, ponieważ nieprzetworzony kod XML zawiera zachowany biały znak, należy również usunąć pasujące znaki nowego wiersza z wpisem książki. Po drugie, jako wygoda, wybór, który został usunięty z usuniętego elementu, jest resetowany do poprzedniej z nich na liście.

 Jednak podstawowe zadania usuwania wybranego elementu księgi są wykonywane tylko przez dwie instrukcje:

- Najpierw zostanie pobrany element Book skojarzony z aktualnie wybranym elementem w polu listy:

  ```
  XElement selBook = (XElement)lbBooks.SelectedItem;
  ```

- Następnie ten element zostanie usunięty z dostawcy danych:

  ```
  selBook.Remove();
  ```

  Po ponownym rozwiązaniu danych dynamicznych gwarantuje, że interfejs użytkownika programu jest automatycznie aktualizowany.

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

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
 Dla skojarzonego źródła XAML dla tych programów obsługi zobacz [kod źródłowy kod źródłowy L2DBForm. XAML](../designers/l2dbform-xaml-source-code.md).

## <a name="see-also"></a>Zobacz też
 [Przewodnik: elementu LinqToXmlDataBinding — przykład](../designers/walkthrough-linqtoxmldatabinding-example.md) [kod źródłowy L2DBForm. XAML kod źródłowy](../designers/l2dbform-xaml-source-code.md)
