---
title: Powiąż z danymi w Projektancie XAML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner.DataBinding
dev_langs:
- CSharp
- VB
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: f0d9ccd32c8f616e6f998bcd1f31773460c89a20
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53866127"
---
# <a name="walkthrough-bind-to-data-in-xaml-designer"></a>Przewodnik: Powiąż z danymi w Projektancie XAML

W Projektancie XAML można ustawić właściwości powiązania danych, przy użyciu obszaru roboczego i w oknie właściwości. W przykładzie w tym przewodniku pokazano, jak powiązać dane z kontrolką. W szczególności instruktażu przedstawiono sposób tworzenia prostego klasy koszyka zakupów, która ma [DependencyProperty](/uwp/api/Windows.UI.Xaml.DependencyProperty) o nazwie `ItemCount`, a następnie wiążą `ItemCount` właściwości **tekstu** właściwości z [TextBlock](/uwp/api/Windows.UI.Xaml.Controls.TextBlock) kontroli.

## <a name="to-create-a-class-to-use-as-a-data-source"></a>Aby utworzyć klasę, aby użyć jako źródła danych

1. Na **pliku** menu, wybierz **New** > **projektu**.

1. W **nowy projekt** okno dialogowe, wybierz opcję **Visual C#** lub **języka Visual Basic** węzła, rozwiń węzeł **pulpitu Windows** węzła, a następnie Wybierz **aplikacji WPF** szablonu.

1. Nadaj projektowi nazwę **BindingTest**, a następnie wybierz **OK** przycisku.

1. Otwórz **MainWindow.xaml.cs** (lub **MainWindow.xaml.vb**) i Dodaj następujący kod. W języku C#, Dodaj kod w `BindingTest` przestrzeni nazw (przed ostatnim zamykającym w pliku). W języku Visual Basic wystarczy dodać nową klasę.

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

   Ten kod ustawia wartość 0 jako domyślna liczba elementów za pomocą [PropertyMetadata](/uwp/api/Windows.UI.Xaml.PropertyMetadata) obiektu.

1. Na **pliku** menu, wybierz **kompilacji** > **Kompiluj rozwiązanie**.

## <a name="to-bind-the-itemcount-property-to-a-textblock-control"></a>Aby powiązać właściwości: ItemCount kontrolkę TextBlock

1. W Eksploratorze rozwiązań Otwórz menu skrótów dla **MainWindow.xaml** i wybierz polecenie **Projektant widoków**.

1. W przyborniku wybierz [siatki](/uwp/api/Windows.UI.Xaml.Controls.Grid) kontroli i dodać go do formularza.

1. Za pomocą `Grid` zaznaczone, w oknie dialogowym właściwości wybierz **New** znajdujący się obok **DataContext** właściwości.

1. W **Wybieranie obiektu** okna dialogowego pole, upewnij się, że **Pokaż wszystkie zestawy** jest wyczyszczone pole wyboru, wybierz polecenie **ShoppingCart** w obszarze **BindingTest** przestrzeni nazw, a następnie wybierz **OK** przycisku.

     Poniższa ilustracja przedstawia **Wybieranie obiektu** okno dialogowe z **ShoppingCart** wybrane.

     ![Wybierz obiekt — okno dialogowe](../designers/media/blendselectobject.png)

1. W **przybornika**, wybierz `TextBlock` formantu, aby dodać go do formularza.

1. Za pomocą `TextBlock` formant zaznaczony w oknie dialogowym właściwości wybierz znacznik właściwości po prawej stronie **tekstu** właściwości, a następnie wybierz **Utwórz powiązanie danych**. (Znacznik właściwości wygląda jak małe pole.)

1. W przypadku tworzenia powiązania danych okno dialogowe, w **ścieżki** wybierz **: ItemCount: (int32)** właściwości, a następnie wybierz **OK** przycisk.

     Poniższa ilustracja przedstawia **Utwórz powiązanie danych** okno dialogowe z **: ItemCount** wybrane właściwości.

     ![Utwórz powiązanie danych — okno dialogowe](../designers/media/xaml_create_data_binding.png)

1. Naciśnij klawisz **F5** do uruchomienia aplikacji.

     `TextBlock` Kontroli powinny pokazywać wartość domyślna 0 jako tekst.

## <a name="see-also"></a>Zobacz także

- [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
- [Dodaj konwerter wartości — okno dialogowe](https://msdn.microsoft.com/library/c5f3d110-a541-4b55-8bca-928f77778af8)