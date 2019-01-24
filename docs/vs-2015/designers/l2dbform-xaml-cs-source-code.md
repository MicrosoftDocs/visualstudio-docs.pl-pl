---
title: Kod źródłowy L2DBForm.XAML.CS | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 5a40dad3-6763-4576-b3ad-874df3f2c8d9
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a63234a820c4f3cffae65342bad0b7fd439edfff
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54769956"
---
# <a name="l2dbformxamlcs-source-code"></a>Kod źródłowy L2DBForm.XAML.CS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten temat zawiera zawartość i opis kodu źródłowego języka C# w pliku L2DBForm.xaml.cs. Klasy częściowe L2XDBForm zawarte w tym pliku można podzielić na trzy logiczne sekcje: elementy członkowskie danych i `OnRemove` i `OnAddBook` procedury obsługi zdarzeń kliknięcia przycisku.  
  
## <a name="data-members"></a>Elementy członkowskie danych  
 Dwie prywatne składowe danych są używane do kojarzenia tej klasy, aby zasoby, okno L2DBForm.xaml.  
  
-   Zmienna przestrzeni nazw `myBooks` jest inicjowany do `"http://www.mybooks.com"`.  
  
-   Element członkowski `bookList` jest inicjowana w Konstruktorze ciąg CDATA w L2DBForm.xaml o następujący wiersz:  
  
    ```  
    bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;  
    ```  
  
## <a name="onaddbook-event-handler"></a>Program obsługi zdarzeń OnAddBook  
 Ta metoda zawiera trzy następujące instrukcje:  
  
-   Pierwsza instrukcja warunkowego jest używany do sprawdzania poprawności danych wejściowych.  
  
-   Druga instrukcja tworzy nową <xref:System.Xml.Linq.XElement> z ciągu wartości które użytkownik wprowadził w **Dodawanie nowej książki** sekcji interfejsu użytkownika.  
  
-   Ostatnią instrukcją dodaje ten nowy element książki do dostawcy danych w L2DBForm.xaml. W związku z tym dane dynamiczne powiązanie automatycznie aktualizuje interfejsu użytkownika za pomocą tego nowego elementu; bardzo dostarczone przez użytkownika jest wymagany żaden kod.  
  
## <a name="onremove-event-handler"></a>Program obsługi zdarzeń OnRemove  
 `OnRemove` Program obsługi jest bardziej skomplikowane niż `OnAddBook` obsługi dwóch powodów. Po pierwsze ponieważ nieprzetworzonym kodzie XML zawiera zachowanych biały znak, dopasowania oddzielane należy również usunąć wpis książki. Po drugie dla wygody zaznaczoną opcję spowodowało na usunięty element jest resetowany do poprzedniego na liście.  
  
 Jednak pracy core usunięcia elementu zaznaczoną książkę odbywa się przez tylko dwóch instrukcji:  
  
- Po pierwsze element książki, skojarzone z aktualnie wybranego elementu w polu listy są pobierane:  
  
  ```  
  XElement selBook = (XElement)lbBooks.SelectedItem;   
  ```  
  
- Następnie ten element zostanie usunięty z dostawcy danych:  
  
  ```  
  selBook.Remove();  
  ```  
  
  Ponownie wiązania danych dynamicznego gwarantuje interfejsu użytkownika programu jest automatycznie aktualizowana.  
  
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
 Dla skojarzonego źródła XAML te programy obsługi, zobacz [kod źródłowy L2DBForm.xaml](../designers/l2dbform-xaml-source-code.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: LinqToXmlDataBinding Example](../designers/walkthrough-linqtoxmldatabinding-example.md)   
 [Kod źródłowy L2DBForm.xaml](../designers/l2dbform-xaml-source-code.md)
