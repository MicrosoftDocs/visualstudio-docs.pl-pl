---
title: 'Przewodnik: Powiązanie z danymi w Projektancie XAML | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner.DataBinding
ms.assetid: 1a99aeae-c3ef-407d-ba79-b8055489a43d
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a7a27b2744247bba78575b0387a958bda5990d8c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60071619"
---
# <a name="walkthrough-binding-to-data-in-xaml-designer"></a>Przewodnik: Powiązanie z danymi w Projektancie XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W Projektancie XAML można ustawić właściwości powiązania danych, przy użyciu obszaru roboczego i w oknie właściwości. W przykładzie w tym przewodniku pokazano, jak powiązać dane z kontrolką. W szczególności instruktażu przedstawiono sposób tworzenia prostego klasy koszyka zakupów, która ma [DependencyProperty](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.dependencyproperty.aspx) o nazwie `ItemCount`, a następnie wiążą `ItemCount` właściwości **tekstu** właściwości z [TextBlock](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) kontroli.  
  
### <a name="to-create-a-class-to-use-as-a-data-source"></a>Aby utworzyć klasę, aby użyć jako źródła danych  
  
1. Na **pliku** menu, wybierz **New**, **projektu**.  
  
2. W **nowy projekt** okno dialogowe, wybierz opcję **Visual C#** lub **języka Visual Basic** węzła, rozwiń węzeł **pulpitu Windows** węzła, a następnie Wybierz **aplikacji WPF** szablonu.  
  
3. Nadaj projektowi nazwę **BindingTest**, a następnie wybierz **OK** przycisku.  
  
4. Otwórz plik MainWindow.xaml.cs (lub MainWindow.xaml.vb) i Dodaj następujący kod. W języku C#, Dodaj kod w `BindingTest` przestrzeni nazw (przed ostatnim zamykającym w pliku). W języku Visual Basic wystarczy dodać nową klasę.  
  
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
  
     Ten kod ustawia wartość 0 jako domyślna liczba elementów za pomocą [PropertyMetadata](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.propertymetadata.aspx) obiektu.  
  
5. Na **pliku** menu, wybierz **kompilacji**, **Kompiluj rozwiązanie**.  
  
### <a name="to-bind-the-itemcount-property-to-a-textblock-control"></a>Aby powiązać właściwości: ItemCount kontrolkę TextBlock  
  
1. W Eksploratorze rozwiązań Otwórz menu skrótów dla pliku MainWindow.xaml, a następnie wybierz **Projektant widoków**.  
  
2. W przyborniku wybierz [siatki](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx) kontroli i dodać go do formularza.  
  
3. Za pomocą `Grid` zaznaczone, w oknie dialogowym właściwości wybierz **New** znajdujący się obok **DataContext** właściwości.  
  
4. W **Wybieranie obiektu** okna dialogowego pole, upewnij się, że **Pokaż wszystkie zestawy** jest wyczyszczone pole wyboru, wybierz polecenie **ShoppingCart** w obszarze **BindingTest** przestrzeni nazw, a następnie wybierz **OK** przycisku.  
  
     Poniższa ilustracja przedstawia **Wybieranie obiektu** okno dialogowe z **ShoppingCart** wybrane.  
  
     ![Okno dialogowe Wybieranie obiektu](../designers/media/blendselectobject.PNG "BlendSelectObject")  
  
5. W **przybornika**, wybierz `TextBlock` formantu, aby dodać go do formularza.  
  
6. Za pomocą `TextBlock` formant zaznaczony w oknie dialogowym właściwości wybierz znacznik właściwości po prawej stronie **tekstu** właściwości, a następnie wybierz **Utwórz powiązanie danych**. (Znacznik właściwości wygląda jak małe pole.)  
  
7. W przypadku tworzenia powiązania danych okno dialogowe, w **ścieżki** wybierz **: ItemCount: (int32)** właściwości, a następnie wybierz **OK** przycisk.  
  
     Poniższa ilustracja przedstawia **Utwórz powiązanie danych** okno dialogowe z **: ItemCount** wybrane właściwości.  
  
     ![Utwórz powiązanie danych — okno dialogowe](../designers/media/xaml-create-data-binding.png "xaml_create_data_binding")  
  
8. Naciśnij klawisz F5, aby uruchomić aplikację.  
  
     `TextBlock` Kontroli powinny pokazywać wartość domyślna 0 jako tekst.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)   
 [NIB: Dodaj konwerter wartości — okno dialogowe](http://msdn.microsoft.com/c5f3d110-a541-4b55-8bca-928f77778af8)
