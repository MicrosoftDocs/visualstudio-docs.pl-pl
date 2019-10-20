---
title: Wiązanie z danymi w projektancie XAML
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner.DataBinding
dev_langs:
- CSharp
- VB
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7aace70ce773c9051367bf88bea1d798eb069bcf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668625"
---
# <a name="walkthrough-bind-to-data-in-xaml-designer"></a>Przewodnik: wiązanie z danymi w projektancie XAML

W projektant XAML można ustawić właściwości powiązania danych przy użyciu obszaru kompozycji i okno Właściwości. W przykładzie w tym instruktażu pokazano, jak powiązać dane z kontrolką. W tym przewodniku pokazano, jak utworzyć prostą klasę koszyka, która ma element [DependencyProperty](xref:Windows.UI.Xaml.DependencyProperty) o nazwie `ItemCount`, a następnie powiązać Właściwość `ItemCount` z właściwością **Text** formantu [TextBlock](xref:Windows.UI.Xaml.Controls.TextBlock) .

## <a name="to-create-a-class-to-use-as-a-data-source"></a>Aby utworzyć klasę, która ma być używana jako źródło danych

1. W menu **plik** wybierz **Nowy** **projekt** > .

1. W oknie **dialogowym Nowy projekt** wybierz węzeł **Wizualizacja C#**  lub **Visual Basic** , rozwiń węzeł **pulpit systemu Windows** , a następnie wybierz szablon **Aplikacja WPF** .

1. Nazwij projekt **BindingTest**, a następnie wybierz przycisk **OK** .

1. Otwórz plik **MainWindow.XAML.cs** (lub **MainWindow. XAML. vb**) i Dodaj następujący kod. W C#programie Dodaj kod w przestrzeni nazw `BindingTest` (przed końcowym nawiasem zamykającym w pliku). W Visual Basic, po prostu Dodaj nową klasę.

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

   Ten kod ustawia wartość 0 jako domyślną liczbę elementów przy użyciu obiektu [metodę PropertyMetadata](xref:Windows.UI.Xaml.PropertyMetadata) .

1. W menu **plik** wybierz polecenie **Kompiluj** > **Kompiluj rozwiązanie**.

## <a name="to-bind-the-itemcount-property-to-a-textblock-control"></a>Aby powiązać Właściwość ItemCount z kontrolką TextBlock

1. W Eksplorator rozwiązań otwórz menu skrótów dla **MainWindow. XAML** i wybierz polecenie **Projektant widoków**.

1. W przyborniku wybierz kontrolkę [Siatka](xref:Windows.UI.Xaml.Controls.Grid) i Dodaj ją do formularza.

1. Po wybraniu `Grid` w okno Właściwości wybierz przycisk **Nowy** obok właściwości **DataContext** .

1. W oknie dialogowym **Wybieranie obiektu** upewnij się, że pole **wyboru Pokaż wszystkie zestawy** jest wyczyszczone, wybierz pozycję **ShoppingCart** w obszarze nazw **BindingTest** , a następnie wybierz przycisk **OK** .

     Na poniższej ilustracji przedstawiono okno dialogowe **Wybieranie obiektu** z wybranym **ShoppingCart** .

     ![Okno dialogowe Wybieranie obiektu](../designers/media/blendselectobject.png)

1. W **przyborniku**Wybierz kontrolkę `TextBlock`, aby dodać ją do formularza.

1. Po wybraniu kontrolki `TextBlock` w okno Właściwości wybierz znacznik właściwości z prawej strony właściwości **Text** , a następnie wybierz pozycję **Utwórz powiązanie danych**. (Znacznik właściwości wygląda jak małe pole).

1. W oknie dialogowym Tworzenie powiązania danych w polu **ścieżka** wybierz właściwość **ItemCount: (Int32)** , a następnie wybierz przycisk **OK** .

     Na poniższej ilustracji przedstawiono okno dialogowe **Tworzenie powiązania danych** z wybraną właściwością **ItemCount** .

     ![Utwórz powiązanie danych — okno dialogowe](../designers/media/xaml_create_data_binding.png)

1. Naciśnij klawisz **F5** , aby uruchomić aplikację.

     Kontrolka `TextBlock` powinna wyświetlać wartość domyślną 0 jako tekst.

## <a name="see-also"></a>Zobacz także

- [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
- [Okno dialogowe Dodawanie konwertera wartości](https://msdn.microsoft.com/library/c5f3d110-a541-4b55-8bca-928f77778af8)