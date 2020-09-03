---
title: 'Przewodnik: powiązanie z danymi w projektant XAML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner.DataBinding
ms.assetid: 1a99aeae-c3ef-407d-ba79-b8055489a43d
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 38434d89544ed290f9adfd077593d7de9bdc1231
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664018"
---
# <a name="walkthrough-binding-to-data-in-xaml-designer"></a>Przewodnik: tworzenie powiązań z danymi w projektancie XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W projektant XAML można ustawić właściwości powiązania danych przy użyciu obszaru kompozycji i okno Właściwości. W przykładzie w tym instruktażu pokazano, jak powiązać dane z kontrolką. W tym przewodniku pokazano, jak utworzyć prostą klasę koszyka zakupów o nazwie [DependencyProperty](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.dependencyproperty.aspx) `ItemCount` , a następnie powiązać `ItemCount` Właściwość z właściwością **Text** formantu [TextBlock](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) .

### <a name="to-create-a-class-to-use-as-a-data-source"></a>Aby utworzyć klasę, która ma być używana jako źródło danych

1. W menu **plik** wybierz polecenie **Nowy**, **projekt**.

2. W oknie dialogowym **Nowy projekt** wybierz węzeł **Visual C#** lub **Visual Basic** , rozwiń węzeł **pulpitu systemu Windows** , a następnie wybierz szablon **Aplikacja WPF** .

3. Nazwij projekt **BindingTest**, a następnie wybierz przycisk **OK** .

4. Otwórz plik MainWindow.xaml.cs (lub MainWindow. XAML. vb) i Dodaj następujący kod. W języku C# Dodaj kod w `BindingTest` przestrzeni nazw (przed końcowym nawiasem zamykającym w pliku). W Visual Basic, po prostu Dodaj nową klasę.

    ```csharp
    public class ShoppingCart : DependencyObject
    {
        public int ItemCount
        {
            get { return (int)GetValue(ItemCountProperty); }
            set { SetValue(ItemCountProperty, value); }
        }

        public static readonly DependencyProperty ItemCountProperty =
             DependencyProperty.Register("ItemCount", typeof(int),
             typeof(ShoppingCart), new PropertyMetadata(0));
    }

    ```

    ```vb
    Public Class ShoppingCart
        Inherits DependencyObject

        Public Shared ReadOnly ItemCountProperty As DependencyProperty = DependencyProperty.Register(
            "ItemCount", GetType(Integer), GetType(ShoppingCart), New PropertyMetadata(0))
        Public Property ItemCount As Integer
            Get
                ItemCount = CType(GetValue(ItemCountProperty), Integer)
            End Get
            Set(value As Integer)
                SetValue(ItemCountProperty, value)
            End Set
        End Property
    End Class
    ```

     Ten kod ustawia wartość 0 jako domyślną liczbę elementów przy użyciu obiektu [metodę PropertyMetadata](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.propertymetadata.aspx) .

5. W menu **plik** wybierz **kompilacja**, **Skompiluj rozwiązanie**.

### <a name="to-bind-the-itemcount-property-to-a-textblock-control"></a>Aby powiązać Właściwość ItemCount z kontrolką TextBlock

1. W Eksplorator rozwiązań otwórz menu skrótów dla MainWindow. XAML i wybierz polecenie **Projektant widoków**.

2. W przyborniku wybierz kontrolkę [Siatka](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx) i Dodaj ją do formularza.

3. Po `Grid` wybraniu w okno właściwości wybierz przycisk **Nowy** obok właściwości **DataContext** .

4. W oknie dialogowym **Wybieranie obiektu** upewnij się, że pole **wyboru Pokaż wszystkie zestawy** jest wyczyszczone, wybierz pozycję **ShoppingCart** w obszarze nazw **BindingTest** , a następnie wybierz przycisk **OK** .

     Na poniższej ilustracji przedstawiono okno dialogowe **Wybieranie obiektu** z wybranym **ShoppingCart** .

     ![Okno dialogowe Wybieranie obiektu](../designers/media/blendselectobject.PNG "BlendSelectObject")

5. W **przyborniku**wybierz `TextBlock` kontrolkę, aby dodać ją do formularza.

6. Po `TextBlock` wybraniu kontrolki w okno właściwości wybierz znacznik właściwości z prawej strony właściwości **Text** , a następnie wybierz pozycję **Utwórz powiązanie danych**. (Znacznik właściwości wygląda jak małe pole).

7. W oknie dialogowym Tworzenie powiązania danych w polu **ścieżka** wybierz właściwość **ItemCount: (Int32)** , a następnie wybierz przycisk **OK** .

     Na poniższej ilustracji przedstawiono okno dialogowe **Tworzenie powiązania danych** z wybraną właściwością **ItemCount** .

     ![Utwórz powiązanie danych — okno dialogowe](../designers/media/xaml-create-data-binding.png "xaml_create_data_binding")

8. Naciśnij klawisz F5, aby kontynuować pracę aplikacji.

     `TextBlock`Kontrolka powinna wyświetlać wartość domyślną 0 jako tekst.

## <a name="see-also"></a>Zobacz też
 [Tworzenie interfejsu użytkownika przy użyciu Projektant XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md) [NIB: okno dialogowe Dodawanie konwertera wartości](https://msdn.microsoft.com/c5f3d110-a541-4b55-8bca-928f77778af8)
