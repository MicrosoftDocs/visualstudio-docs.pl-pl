---
title: Tworzenie języka specyficznego dla domeny opartego na formularzach Windows | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 452318ff-8ecf-46d0-8ca0-4013d0cdafaf
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2caee9a39df18bfed0dc48a9c0266721500ddeca
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59654944"
---
# <a name="creating-a-windows-forms-based-domain-specific-language"></a>Tworzenie języka specyficznego dla domeny opartego na formularzach systemu Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows Forms służy do wyświetlania stanu modelu języka specyficznego dla domeny (DSL), zamiast DSL diagram. Ten temat przeprowadzi Cię przez powiązanie formularza Windows DSL, przy użyciu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wizualizacji i modelowania SDK.  

 ![DSL&#45;Wpf&#45;2](../modeling/media/dsl-wpf-2.png "DSL-Wpf-2")  
Wystąpienia elementu DSL, przedstawiający interfejs użytkownika Windows formularza i Eksploratora modelu.  

## <a name="creating-a-windows-forms-dsl"></a>Tworzenie formularzy Windows DSL  
 **Minimalny projektanta WinForm** DSL szablon służy do tworzenia minimalne DSL, który można dostosować do własnych własnych wymagań.  

#### <a name="to-create-a-minimal-winforms-dsl"></a>Aby utworzyć minimalny DSL WinForms  

1. Utwórz DSL z **minimalny projektanta WinForm** szablonu.  

    W tym przewodniku przyjęto są następujące nazwy:  

   |                       |                 |
   |-----------------------|-----------------|
   | Nazwa rozwiązania i DSL |     FarmApp     |
   |       Przestrzeń nazw       | Company.FarmApp |

2. Poeksperymentuj z początkowej przykładu, który zawiera szablon:  

   1.  Transformuj wszystkie szablony.  

   2.  Tworzenie i uruchamianie aplikacji przykładowej (**kombinację klawiszy CTRL + F5**).  

   3.  W doświadczalnym wystąpieniu programu Visual Studio, otwórz `Sample` plik debugowania projektu.  

        Należy zauważyć, że jest wyświetlany w kontrolce Windows Forms.  

        Widać również elementy modelu są wyświetlane w Eksploratorze.  

        Dodaj niektóre elementy w formularzu lub programu Explorer i zwróć uwagę, że pojawiają się na innym ekranie.  

   W głównym wystąpieniu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], zwróć uwagę na następujące kwestie dotyczące rozwiązania DSL:  

-   `DslDefinition.dsl` nie zawiera żadnych elementów diagramu. Jest to spowodowane DSL diagramów nie będzie używać do wyświetlania wystąpienia modele tego języka DSL. Zamiast tego formularza Windows będzie powiązać modelu i elementów w formularzu będą wyświetlane w modelu.  

-   Oprócz `Dsl` i `DslPackage` projektów, rozwiązanie zawiera projekt trzeci o nazwie `UI.` **interfejsu użytkownika** projekt zawiera definicję formantu Windows Forms. `DslPackage` zależy od `UI`, i `UI` zależy od `Dsl`.  

-   W `DslPackage` projektu, `UI\DocView.cs` zawiera kod, który wyświetla formantu Windows Forms, która jest zdefiniowana w `UI` projektu.  

-   `UI` Projekt zawiera przykładowe pracy kontrolki formularza, powiązany z język DSL. Jednak nie będzie ona działać po zostały zmienione w definicji DSL. `UI` Projekt zawiera:  

    -   Klasy Windows Forms o nazwie `ModelViewControl`.  

    -   Plik o nazwie `DataBinding.cs` zawierający dodatkowe częściową definicję `ModelViewControl`. Aby wyświetlić jego zawartość w **Eksploratora rozwiązań**, otwórz menu skrótów dla pliku i wybierz polecenie **Wyświetl kod**.  

### <a name="about-the-ui-project"></a>Temat projektu interfejsu użytkownika  
 Po zaktualizowaniu pliku definicji DSL, aby określić własne DSL, trzeba będzie zaktualizować kontrolki na `UI` projektu DSL. W odróżnieniu od `Dsl` i `DslPackage` projektami, na przykład `UI` projektu nie jest generowany na podstawie `DslDefinitionl.dsl`. Możesz dodać .TT — pliki do generowania kodu, jeśli chcesz, mimo że nie jest objęty w tym przewodniku.  

## <a name="updating-the-dsl-definition"></a>Aktualizowanie definicji DSL  
 Następujące definicji DSL jest używana w tym przewodniku.  

 ![DSL&#45;Wpf&#45;1](../modeling/media/dsl-wpf-1.png "DSL-Wpf-1")  

#### <a name="to-update-the-dsl-definition"></a>Aby zaktualizować definicję DSL  

1.  Otwórz DslDefinition.dsl w projektanta DSL.  

2.  Usuń **ExampleElement**  

3.  Zmień nazwę **ExampleModel** klasy domeny `Farm`.  

     Wypróbuj dodatkowe właściwości o nazwie `Size` typu **Int32**, i `IsOrganic` typu **logiczna**.  

    > [!NOTE]
    >  Jeśli usuniesz klasy domeny katalogu głównego, a następnie utwórz nowy katalog główny, trzeba będzie zresetować właściwość klasy głównej edytora. W **Eksplorator DSL**, wybierz opcję **edytora**. Następnie w oknie właściwości ustaw **klasę główną** do `Farm`.  

4.  Użyj **klasy domeny o nazwie** narzędzia do tworzenia następujących klas domeny:  

    -   `Field` — Podać to właściwość dodatkowe domeny o nazwie `Size`.  

    -   `Animal` W oknie właściwości ustaw **modyfikator dziedziczenia** do **abstrakcyjne**.  

5.  Użyj **klasy domeny** narzędzia do tworzenia następujących klas:  

    -   `Sheep`  

    -   `Goat`  

6.  Użyj **dziedziczenia** narzędzie `Goat` i `Sheep` dziedziczyć `Animal`.  

7.  Użyj **osadzania** narzędzie do osadzania `Field` i `Animal` w obszarze `Farm`.  

8.  Warto uporządkować dane na diagramie. Aby zmniejszyć liczbę zduplikowanych elementów, należy użyć **Przenieś tutaj poddrzewo** polecenia przejdź do menu skrótów w elementów typu liść.  

9. **Transformuj wszystkie szablony** na pasku narzędzi Eksploratora rozwiązań.  

10. Tworzenie **Dsl** projektu.  

    > [!NOTE]
    >  Na tym etapie inne projekty nie zostanie skompilowany bez błędów. Jednakże chcemy kompilacji projektu Dsl, tak aby jej zestaw jest dostępne w Kreatorze źródła danych.  

## <a name="updating-the-ui-project"></a>Aktualizowanie projektu interfejsu użytkownika  
 Teraz można utworzyć nowej kontrolki użytkownika, który spowoduje wyświetlenie informacji, która jest przechowywana w modelu DSL. Najprostszym sposobem łączenia kontrolki użytkownika w modelu jest za pomocą powiązania danych. Typ adaptera o nazwie powiązania danych **ModelingBindingSource** specjalnie do łączenia z językami DSL VMSDK innych interfejsów.  

#### <a name="to-define-your-dsl-model-as-a-data-source"></a>Aby zdefiniować modelu DSL jako źródło danych  

1.  Na **danych** menu, wybierz **Pokaż źródła danych**.  

     **Źródeł danych** zostanie otwarte okno.  

     Wybierz **Dodaj nowe źródło danych**. **Kreatora konfiguracji źródła danych** zostanie otwarty.  

2.  Wybierz **obiektu**, **dalej**.  

     Rozwiń **Dsl**, **Company.FarmApp**i wybierz **farmy**, która jest klasą głównego modelu. Wybierz **Zakończ**.  

     W oknie Eksploratora rozwiązań **interfejsu użytkownika** projektu zawiera teraz **Properties\DataSources\Farm.datasource**  

     Właściwości i relacje klasy modelu są wyświetlane w oknie źródeł danych.  

     ![DslWpf&#45;3](../modeling/media/dslwpf-3.png "DslWpf-3")  

#### <a name="to-connect-your-model-to-a-form"></a>Aby połączyć swój model do formularza  

1. W **interfejsu użytkownika** projektu, Usuń wszystkie istniejące pliki CS.  

2. Dodaj nową **kontrolki użytkownika** plik o nazwie `FarmControl` do **interfejsu użytkownika** projektu.  

3. W **źródeł danych** okna w menu rozwijanego **farmy**, wybierz **szczegóły**.  

    Pozostaw ustawienia domyślne dla innych właściwości.  

4. Otwórz FarmControl.cs w widoku Projekt.  

    Przeciągnij **farmy** z okna źródeł danych na FarmControl.  

    Zestaw formantów zostanie wyświetlona, jeden dla każdej właściwości. Właściwości relacji nie generują kontrolki.  

5. Usuń **farmBindingNavigator**. To jest automatycznie generowany w `FarmControl` projektanta, ale nie jest przydatne w przypadku tej aplikacji.  

6. Korzystanie z przybornika, Utwórz dwa wystąpienia **DataGridView**i nazwij je `AnimalGridView` i `FieldGridView`.  

   > [!NOTE]
   >  Etap alternatywne jest przeciągnij zwierząt i pól elementów z okna źródeł danych w formancie. Ta akcja tworzy automatycznie siatek danych i powiązania między widokiem siatki i źródła danych. Jednak tego powiązania nie działa prawidłowo dla języków DSL. W związku z tym zaleca się tworzenie siatek danych i powiązania ręcznie.  

7. Jeśli przybornik nie zawiera **ModelingBindingSource** narzędzia, dodaj ją. W menu skrótów **danych** kartę, wybrać **wybierz elementy**. W **wybierz elementy przybornika** okno dialogowe, wybierz opcję **ModelingBindingSource** z **.NET Framework kartę**.  

8. Korzystanie z przybornika, Utwórz dwa wystąpienia **ModelingBindingSource**i nazwij je `AnimalBinding` i `FieldBinding`.  

9. Ustaw **DataSource** właściwości każdego **ModelingBindingSource** do **farmBindingSource**.  

     Ustaw **DataMember** właściwości **zwierząt** lub **pola**.  

10. Ustaw **DataSource** właściwości `AnimalGridView` do `AnimalBinding`i `FieldGridView` do `FieldBinding`.  

11. Dostosowywanie układu formantu farmy, aby Twoje smak.  

    **ModelingBindingSource** to karta, która wykonuje kilka zadań, które są specyficzne dla języków DSL:  

- W ramach transakcji Store VMSDK opakowuje aktualizacji.  

   Na przykład gdy użytkownik usuwa wiersz z widoku siatki danych, regularne powiązania mogłyby spowodować wyjątek transakcji.  

- Zapewnia, że gdy użytkownik wybierze wiersz, w oknie właściwości wyświetla właściwości odpowiedniego elementu modelu, a nie wiersz siatki danych.  

  ![DslWpf4](../modeling/media/dslwpf4.png "DslWpf4")  
  Schemat łącza między źródłami danych i widoków.  

#### <a name="to-complete-the-bindings-to-the-dsl"></a>Aby ukończyć powiązania z język DSL  

1.  Dodaj następujący kod w osobnym pliku kodu w **interfejsu użytkownika** projektu:  

    ```csharp  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Modeling;  
    using Microsoft.VisualStudio.Modeling.Design;  

    namespace Company.FarmApp  
    {  
      partial class FarmControl  
      {  
        public IContainer Components { get { return components; } }  

        /// <summary>Binds the WinForms data source to the DSL model.  
        /// </summary>  
        /// <param name="nodelRoot">The root element of the model.</param>  
        public void DataBind(ModelElement modelRoot)  
        {  
          WinFormsDataBindingHelper.PreInitializeDataSources(this);  
          this.farmBindingSource.DataSource = modelRoot;  
          WinFormsDataBindingHelper.InitializeDataSources(this);  
        }  
      }  
    }  
    ```  

2.  W **DslPackage** projekt, Edytuj **DslPackage\DocView.tt** można zaktualizować następujących definicji zmiennej:  

    ```csharp  
    string viewControlTypeName = "FarmControl";  
    ```  

## <a name="testing-the-dsl"></a>Testowanie język DSL  
 Rozwiązanie DSL teraz skompilować i uruchomić, chociaż możesz zechcieć dodać kolejne ulepszenia później.  

#### <a name="to-test-the-dsl"></a>Aby przetestować język DSL  

1.  Skompiluj i uruchom rozwiązanie.  

2.  W doświadczalnym wystąpieniu programu Visual Studio, otwórz **przykładowe** pliku.  

3.  W **FarmApp Explorer**, otwórz menu skrótów na **farmy** węzła głównego, a następnie wybierz **Dodaj nowe koza**.  

     `Goat1` pojawia się w **zwierząt** widoku.  

    > [!WARNING]
    >  Musisz użyć menu skrótów na **farmy** węzła nie **zwierząt** węzła.  

4.  Wybierz **farmy** węzła głównego i wyświetlić jego właściwości.  

     W widoku formularza, zmień **nazwa** lub **rozmiar** farmy.  

     Po wyjściu z każdego pola w formularzu odpowiednie zmiany właściwości w oknie dialogowym właściwości.  

## <a name="enhancing-the-dsl"></a>Udoskonalanie język DSL  

#### <a name="to-make-the-properties-update-immediately"></a>Zapewnienie właściwości wykonać natychmiastową aktualizację  

1.  W widoku Projekt FarmControl.cs zaznacz pole proste, takie jak nazwa, rozmiar lub IsOrganic.  

2.  W oknie właściwości rozwiń **powiązania danych** , a następnie otwórz **(zaawansowane)**.  

     W **formatowanie i powiązywanie zaawansowane** okna dialogowego, w obszarze **tryb aktualizacji źródła danych**, wybierz **onpropertychanged —**.  

3.  Skompiluj i uruchom rozwiązanie.  

     Upewnij się, że po zmianie zawartości tego pola do odpowiedniej właściwości natychmiast zmiany modelu farmy.  

#### <a name="to-provide-add-buttons"></a>Aby zapewnić Dodaj przyciski  

1. W widoku Projekt FarmControl.cs Użyj przybornika, aby utworzyć przycisk w formularzu.  

    Edytuj nazwę i tekstu przycisku na przykład, aby `New Sheep`.  

2. Otwórz kod związany z przycisku (np. przez dwukrotne kliknięcie).  

    Edytuj w następujący sposób:  

   ```csharp  
   private void NewSheepButton_Click(object sender, EventArgs e)  
   {  
     using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))  
     {  
       elementOperations.MergeElementGroup(farm,  
         new ElementGroup(new Sheep(farm.Partition)));  
       t.Commit();  
     }  
   }  

   // The following code is shared with other add buttons:  
   private ElementOperations operationsCache = null;  
   private ElementOperations elementOperations  
   {  
     get  
     {  
       if (operationsCache == null)  
       {  
         operationsCache = new ElementOperations(farm.Store, farm.Partition);  
       }  
       return operationsCache;  
     }  
   }  
   private Farm farm  
   {  
     get { return this.farmBindingSource.DataSource as Farm; }  
   }  

   ```  

    Należy również Wstaw następujące dyrektywy:  

   ```csharp  

   using Microsoft.VisualStudio.Modeling;  

   ```  

3. Dodaj przyciski podobne do kóz i pól.  

4. Skompiluj i uruchom rozwiązanie.  

5. Upewnij się, że nowy przycisk dodaje element. Nowy element powinien pojawić się w Eksploratorze FarmApp i w widoku siatki danych.  

    Powinien móc edytować nazwę tego elementu w widoku siatki danych. Można również usunąć z tego miejsca.  

   ![DSL&#45;Wpf&#45;2](../modeling/media/dsl-wpf-2.png "DSL-Wpf-2")  

### <a name="about-the-code-to-add-an-element"></a>Kod, aby dodać element — informacje  
 Nowy element przycisków poniższy kod alternatywne jest nieco prostsze.  

```csharp  
private void NewSheepButton_Click(object sender, EventArgs e)  
{  
  using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))  
  {  
    farm.Animals.Add(new Sheep(farm.Partition)); ;  
    t.Commit();  
  }  
}  

```  

 Ten kod nie ustawiać, domyślna nazwa dla nowego elementu. Nie działa on dostosowany scalania, który został zdefiniowany w **dyrektywy scalania elementów** elementu DSL, a nie działa on żadnych niestandardowych scalać kod, który może być zdefiniowany.  

 W związku z tym firma Microsoft zaleca użycie <xref:Microsoft.VisualStudio.Modeling.ElementOperations> do tworzenia nowych elementów. Aby uzyskać więcej informacji, zobacz [Dostosowywanie tworzenia i przesuwania elementu](../modeling/customizing-element-creation-and-movement.md).  

## <a name="see-also"></a>Zobacz też  
 [Jak zdefiniować języka specyficznego dla domeny](../modeling/how-to-define-a-domain-specific-language.md)   
 [Pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [Modelowanie SDK dla Visual Studio — języki specyficzne dla domeny](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)
