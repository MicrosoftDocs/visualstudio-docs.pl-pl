---
title: Ustawianie unikatowej właściwości automatyzacji dla kontrolek Windows Store do testowania | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 9bdd74ff-2534-4fc7-a5c3-a77bf7843037
caps.latest.revision: 12
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a765896ef8b4eb645c04536105bc2284fc5c3d16
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446052"
---
# <a name="set-a-unique-automation-property-for-windows-store-controls-for-testing"></a>Ustawianie unikatowej właściwości automatyzacji dla kontrolek Sklepu Windows przeznaczonych do testowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli chcesz uruchomić kodowane testy interfejsu użytkownika dla aplikacji opartych na XAML Windows Store, musi mieć unikatowej właściwości automatyzacji, który identyfikował każdy formant.  
  
 Możesz przypisać unikatowej właściwości automatyzacji na podstawie typu kontrolki XAML w aplikacji. Poniżej przedstawiono sposób przypisać ten unikatowej właściwości automatyzacji w następujących sytuacjach:  
  
- [Statyczne definicji XAML formantów](#UniquePropertyWindowsStoreControlsStaticXAML)  
  
- [Przypisz unikatowy usługi automation — właściwości przy użyciu programu Visual Studio i Blend for Visual Studio](#UniquePropertyWindowsStoreControlsExpressionBlend)  
  
- [Użyj DataTemplate](#UniquePropertyWindowsStoreControlsDataTemplate)  
  
- [Korzystanie z szablonu kontrolki](#UniquePropertyWindowsStoreControlsControlTemplate)  
  
- [Kontrolek dynamicznych](#UniquePropertyWindowsStoreControlsDynamicControls)  
  
## <a name="use-methods-to-assign-a-unique-automation-property"></a>Użyj metody, aby przypisać unikatowej właściwości automatyzacji  
  
### <a name="UniquePropertyWindowsStoreControlsStaticXAML"></a> Statyczne definicji XAML  
 Aby określić unikatowej właściwości automatyzacji dla formantu, który jest zdefiniowany w pliku XAML, można ustawić AutomationProperties.AutomationId lub AutomationProperties.Name jawnie lub niejawnie, jak pokazano w poniższych przykładach. Jedną z tych wartości ustawienia zapewnia kontrolę unikatowej właściwości automatyzacji, który może służyć do identyfikowania formantu, tworząc kodowanego interfejsu użytkownika testowego, nagrywanie akcji.  
  
 **Ustaw właściwość niejawnie**  
  
 Ustaw AutomationProperties.AutomationId **ButtonX** przy użyciu właściwości Name w XAML dla formantu.  
  
```xaml  
<Button Name="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />  
  
```  
  
 Ustaw AutomationProperties.Name **ButtonY** przy użyciu właściwości zawartości w XAML dla formantu.  
  
```xaml  
<Button Content="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />  
  
```  
  
 **Ustaw jawnie właściwość**  
  
 Ustaw AutomationProperties.AutomationId **ButtonX** jawnie w XAML dla formantu.  
  
```xaml  
<Button AutomationProperties.AutomationId=“ButtonX” Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />  
  
```  
  
 Ustaw AutomationProperties.Name **ButtonY** jawnie w XAML dla formantu.  
  
```  
<Button AutomationProperties.Name="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />  
```  
  
### <a name="UniquePropertyWindowsStoreControlsExpressionBlend"></a> Przypisz unikatowy usługi automation — właściwości przy użyciu programu Visual Studio i Blend for Visual Studio  
 Aby przypisać unikatowe nazwy elementów interaktywnych, takich jak przyciski, pola listy, pola kombi i pól tekstowych, można użyć programu Visual Studio lub Blend for Visual Studio. Zapewnia to kontrolka unikatową wartość w AutomationProperties.Name.  
  
 **Visual Studio:** Na **narzędzia** menu wskaż **opcje** , a następnie wybierz **edytora tekstów**, następnie **XAML**, a na koniec **różne** .  
  
 Wybierz **automatycznie nazwij elementy interakcyjne przy tworzeniu** , a następnie wybierz **OK**.  
  
 ![XAML — różne opcje](../test/media/cuit-windowsstoreapp-b.png "CUIT_WindowsStoreApp_B")  
  
 **Blend for Visual Studio:** Użyj jednej z następujących metod, w tym celu z programu Blend for Visual Studio.  
  
> [!NOTE]
> Tej metody można używać tylko dla formantów, które są tworzone statycznie przy użyciu XAML.  
  
 **Aby nadać unikatową nazwę istniejących formantów**  
  
 Na **narzędzia** menu, wybierz **nadawać nazwy elementom interaktywnym**, jak pokazano poniżej:  
  
 ![Z menu Narzędzia wybierz polecenie nadawać nazwy elementom interaktywnym](../test/media/cuit-windowsstoreproperty-blend-1.png "CUIT_WindowsStoreProperty_Blend_1")  
  
 **Aby automatycznie nadaj unikatową nazwę do formantów, które tworzysz**  
  
 Na **narzędzia** menu wskaż **opcje**, a następnie wybierz **projektu**. Wybierz **automatycznie nazwij elementy interakcyjne przy tworzeniu** , a następnie wybierz **OK**, jak pokazano poniżej:  
  
 ![Ustaw projekt nadawać nazwy elementom interaktywnym](../test/media/cuit-windowsstoreproeprty-blend-2.png "CUIT_WindowsStoreProeprty_Blend_2")  
  
### <a name="UniquePropertyWindowsStoreControlsDataTemplate"></a> Korzystanie z szablonu danych  
 Można zdefiniować prostego szablonu, za pomocą właściwości ItemTemplate do powiązania wartości w polu listy zmiennych przy użyciu następujących XAML.  
  
```xaml  
  
<ListBox Name="listBox1" ItemsSource="{Binding Source={StaticResource employees}}">  
   <ListBox.ItemTemplate>  
      <DataTemplate>  
         <StackPanel Orientation="Horizontal">  
            <TextBlock Text="{Binding EmployeeName}" />  
            <TextBlock Text="{Binding EmployeeID}" />  
         </StackPanel>  
      </DataTemplate>  
   </ListBox.ItemTemplate>  
</ListBox>  
```  
  
 Za pomocą szablonu i ItemContainerStyle do powiązania wartości do zmiennych, przy użyciu następujących XAML.  
  
```xaml  
  
      <ListBox Name="listBox1" ItemsSource="{Binding Source={StaticResource employees}}">  
            <ListBox.ItemContainerStyle>  
                <Style TargetType="ListBoxItem">  
                    <Setter Property="Template">  
                        <Setter.Value>  
                            <ControlTemplate TargetType="ListBoxItem">  
                                <Grid>  
                                    <Button Content="{Binding EmployeeName}" AutomationProperties.AutomationId="{Binding EmployeeID}"/>  
                                </Grid>  
                            </ControlTemplate>  
                        </Setter.Value>  
                    </Setter>  
                </Style>  
            </ListBox.ItemContainerStyle>           
        </ListBox>  
  
```  
  
 Dla obu tych przykładach należy następnie zastąpić metodę ToString() właściwości ItemSource, jak pokazano, używając następującego kodu. Ten kod sprawdza, czy ustawiono wartość AutomationProperties.Name, a jest unikatowa, ponieważ nie można ustawić unikatowej właściwości automatyzacji dla każdego elementu listy powiązanych danych, za pomocą powiązania. Ustawianie unikatową wartość dla Properties.Name automatyzacji wystarcza w tym przypadku.  
  
> [!NOTE]
> W ten sposób zawartość wewnętrzny elementu listy, można również ustawić na ciąg w klasie pracowników za pośrednictwem powiązania. Jak pokazano w przykładzie, formant przycisku wewnątrz każdego elementu listy jest przypisany identyfikator unikatowy automatyzacji, który jest identyfikatorem pracownika.  
  
```  
  
Employee[] employees = new Employee[]   
{  
   new Employee("john", "4384"),  
   new Employee("margaret", "7556"),  
   new Employee("richard", "8688"),  
   new Employee("george", "1293")  
};  
  
listBox1.ItemsSource = employees;  
  
public override string ToString()  
{  
    return EmployeeName + EmployeeID; // Unique Identification to be set as the AutomationProperties.Name  
}  
  
```  
  
### <a name="UniquePropertyWindowsStoreControlsControlTemplate"></a> Korzystanie z szablonu kontrolki  
 Tak, aby każde wystąpienie określonego typu uzyskuje unikatowej właściwości automatyzacji, jeśli jest zdefiniowana w kodzie, można użyć szablonu kontrolki. Tak, aby AutomationProperty wiąże się z unikatowego Identyfikatora w wystąpienie kontrolki, należy utworzyć szablon. Następujące XAML demonstruje jedno z podejść do utworzenia powiązania z szablonu kontrolki.  
  
```xaml  
  
<Style x:Key="MyButton" TargetType="Button">  
<Setter Property="Template">  
   <Setter.Value>  
<ControlTemplate TargetType="Button">  
   <Grid>  
      <CheckBox HorizontalAlignment="Left" AutomationProperties.AutomationId="{TemplateBinding Content}"></CheckBox>  
      <Button Width="90" HorizontalAlignment="Right" Content="{TemplateBinding Content}" AutomationProperties.AutomationId="{TemplateBinding Content}"></Button>  
   </Grid>  
</ControlTemplate>  
   </Setter.Value>  
</Setter>  
</Style>  
  
```  
  
 Po zdefiniowaniu dwóch wystąpień przycisku przy użyciu tego szablonu kontrolki, identyfikator usługi automation jest równa unikatowy ciąg tekstowy zawartości dla formantów w szablonie, jak pokazano w poniższym XAML.  
  
```xaml  
  
<Button Content=”Button1” Style="{StaticResource MyButton}" Width="140"/>  
<Button Content=”Button2” Style="{StaticResource MyButton}" Width="140"/>  
```  
  
### <a name="UniquePropertyWindowsStoreControlsDynamicControls"></a> Kontrolek dynamicznych  
 W przypadku kontrolek, które są tworzone dynamicznie w kodzie i nieutworzonych statycznie lub za pomocą szablonów w plikach XAML, należy ustawić właściwości zawartości lub nazwa dla kontrolki. To sprawia, że się, że każdy dynamicznej kontroli ma unikatowej właściwości automatyzacji. Na przykład jeśli pole wyboru, które można wyświetlić, wybierz element listy, można ustawić te właściwości, jak pokazano poniżej:  
  
```csharp  
  
private void CreateCheckBox(string txt, StackPanel panel)  
   {  
      CheckBox cb = new CheckBox();  
      cb.Content = txt; // Sets the AutomationProperties.Name  
      cb.Height = 50;  
      cb.Width = 100;  
      cb.Name = "DynamicCheckBoxAid"+ txt; // Sets the AutomationProperties.AutomationId  
      panel.Children.Add(cb);  
    }  
  
```  
