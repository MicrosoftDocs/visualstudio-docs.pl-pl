---
title: Tworzenie języka specyficznego dla domeny opartego na modelu Windows Forms
description: Zawiera informacje na temat sposobu używania Windows Forms do wyświetlania stanu modelu języka specyficznego dla domeny.
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 9a77a22b7ed888b28f12154974d735213952899c
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389543"
---
# <a name="create-a-windows-forms-based-domain-specific-language"></a>Tworzenie języka Windows Forms opartego na Domain-Specific języku

Możesz użyć Windows Forms do wyświetlania stanu modelu języka specyficznego dla domeny (DSL), zamiast korzystać z diagramu DSL. W tym temacie otworzymy proces tworzenia powiązania formularza systemu Windows z DSL przy użyciu zestawu SDK Visual Studio wizualizacji i modelowania.

Na poniższej ilustracji przedstawiono interfejs użytkownika formularzy systemu Windows i eksploratora modeli dla wystąpienia DSL:

![Wystąpienie DSL w Visual Studio](../modeling/media/dsl-wpf-2.png)

## <a name="create-a-windows-forms-dsl"></a>Tworzenie Windows Forms DSL

Szablon **DSL minimalnej winForm Projektant** tworzy minimalne DSL, które można zmodyfikować do własnych wymagań.

1. Utwórz DSL na podstawie **szablonu Minimal WinForm Designer.**

    W tym przewodniku przyjęto następujące nazwy:

    - Nazwa rozwiązania i DSL: `FarmApp`
    - Przestrzeń nazw: `Company.FarmApp`

2. Poeksperymentuj z początkowym przykładem, który zawiera szablon:

   1. Przekształć wszystkie szablony.

   2. Skompilowanie i uruchomienie przykładu **(Ctrl** + **F5).**

   3. W eksperymentalnym wystąpieniu Visual Studio otwórz `Sample` plik w projekcie debugowania.

        Zwróć uwagę, że jest on wyświetlany w Windows Forms kontrolki.

        Elementy modelu są również wyświetlane w Eksploratorze.

        Dodaj niektóre elementy w formularzu lub Eksploratorze i zwróć uwagę, że są one wyświetlane na drugim ekranie.

   W głównym wystąpieniu Visual Studio zwróć uwagę na następujące kwestie dotyczące rozwiązania DSL:

- `DslDefinition.dsl` Nie zawiera żadnych elementów diagramu. Wynika to z tego, że nie będziesz używać diagramów DSL do wyświetlania modeli wystąpień tego DSL. Zamiast tego powiąż formularz systemu Windows z modelem, a elementy w formularzu będą wyświetlać model.

- Oprócz projektów i rozwiązanie zawiera trzeci projekt o nazwie projekt interfejsu użytkownika zawierający definicję Windows Forms `Dsl` `DslPackage` `UI.`  interfejsu użytkownika. `DslPackage` zależy od `UI` , i zależy od `UI` `Dsl` .

- W `DslPackage` projekcie `UI\DocView.cs` zawiera kod, który wyświetla Windows Forms zdefiniowaną w `UI` projekcie.

- Projekt `UI` zawiera roboczy przykład kontrolki formularza powiązanej z DSL. Jednak nie będzie działać po zmianie definicji DSL. Projekt `UI` zawiera:

  - Klasa Windows Forms o nazwie `ModelViewControl` .

  - Plik o `DataBinding.cs` nazwie zawierający dodatkową częściową definicję `ModelViewControl` . Aby wyświetlić jego zawartość, w **Eksplorator rozwiązań** otwórz menu skrótów dla pliku i wybierz **pozycję Wyświetl kod.**

### <a name="about-the-ui-project"></a>Informacje o projekcie interfejsu użytkownika

Po zaktualizowaniu pliku definicji DSL w celu zdefiniowania własnego DSL należy zaktualizować kontrolkę w projekcie, aby `UI` wyświetlić DSL. W przeciwieństwie `Dsl` do projektów i `DslPackage` `UI` przykładowy projekt nie jest generowany na podstawie . `DslDefinitionl.dsl` Jeśli chcesz, możesz dodać pliki tt, aby wygenerować kod, chociaż nie o tym w tym przewodniku.

## <a name="update-the-dsl-definition"></a>Aktualizowanie definicji DSL

Na poniższej ilustracji przedstawiono definicję DSL używaną w tym przewodniku.

![Definicja DSL](../modeling/media/dsl-wpf-1.png)

1. Otwórz dslDefinition.dsl w projektancie DSL.

2. Usuwanie **elementu ExampleElement**

3. Zmień nazwę **klasy domeny ExampleModel** na `Farm` .

     Nadaj mu dodatkowe właściwości domeny `Size` o nazwie **typu Int32** i `IsOrganic` typu Wartość **logiczna**.

    > [!NOTE]
    > Jeśli usuniesz klasę domeny głównej, a następnie utworzysz nowy katalog główny, musisz zresetować właściwość Klasa główna edytora. W **Eksploratorze DSL** wybierz pozycję **Edytor**. Następnie w okno Właściwości klasy głównej **ustaw** wartość `Farm` .

4. Użyj narzędzia **Nazwana klasa domeny,** aby utworzyć następujące klasy domen:

    - `Field` — Nadaj jej dodatkową właściwość domeny o nazwie `Size` .

    - `Animal` — W okno Właściwości ustaw **modyfikator dziedziczenia** na **wartość Abstrakt**.

5. Użyj narzędzia **Klasy domeny,** aby utworzyć następujące klasy:

    - `Sheep`

    - `Goat`

6. Użyj narzędzia **dziedziczenia,** aby wykonać i `Goat` `Sheep` dziedziczyć z `Animal` .

7. Użyj narzędzia **osadzania,** aby osadzić elementy `Field` i w obszarze `Animal` `Farm` .

8. Warto uporządkować diagram. Aby zmniejszyć liczbę zduplikowanych elementów, użyj polecenia **Bring Subtree Here** w menu skrótów elementów liścia.

9. **Przekształć wszystkie** szablony na pasku narzędzi Eksplorator rozwiązań.

10. Skompilowanie **projektu Dsl.**

    > [!NOTE]
    > Na tym etapie inne projekty nie będą kompilowane bez błędów. Chcemy jednak skompilować projekt Dsl, aby jego zestaw był dostępny dla Kreatora źródła danych.

## <a name="update-the-ui-project"></a>Aktualizowanie projektu interfejsu użytkownika

Teraz możesz utworzyć nową kontrolkę użytkownika, która będzie wyświetlać informacje przechowywane w modelu DSL. Najprostszym sposobem połączenia kontrolki użytkownika z modelem są powiązania danych. Typ adaptera powiązania danych o nazwie **ModelingBindingSource** został specjalnie zaprojektowany w celu połączenia plików DSL z interfejsami spoza vmsdk.

### <a name="define-your-dsl-model-as-a-data-source"></a>Definiowanie modelu DSL jako źródła danych

1. W menu **Dane** wybierz pozycję **Pokaż źródła danych.**

     Zostanie **otwarte okno Źródła** danych.

     Wybierz **pozycję Dodaj nowe źródło danych.** Zostanie **otwarty Kreator konfiguracji źródła** danych.

2. Wybierz **pozycję Obiekt**, **Dalej**.

     Rozwiń **pozycję Dsl,** **Company.FarmApp** i **wybierz pozycję Farma**, która jest klasą główną modelu. Wybierz **pozycję Zakończ.**

     W Eksplorator rozwiązań **interfejsu** użytkownika projekt zawiera teraz **element Properties\DataSources\Farm.datasource**

     Właściwości i relacje klasy modelu są wyświetlane w oknie Źródła danych.

     ![Okno Źródeł danych](../modeling/media/dslwpf-3.png)

### <a name="connect-your-model-to-a-form"></a>Łączenie modelu z formularzem

1. W **projekcie interfejsu** użytkownika usuń wszystkie istniejące pliki cs.

2. Dodaj nowy plik **kontroli użytkownika** o nazwie do `FarmControl` projektu **interfejsu** użytkownika.

3. W **oknie Źródła** danych z menu rozwijanego farmy wybierz pozycję **Szczegóły.**

    Pozostaw ustawienia domyślne dla innych właściwości.

4. Otwórz farmcontrol.cs w widoku projektu.

    Przeciągnij **farmę** z okna Źródła danych do pola FarmControl.

    Zostanie wyświetlony zestaw kontrolek, po jednym dla każdej właściwości. Właściwości relacji nie generują kontrolek.

5. Usuń **farmBindingNavigator**. Jest ona również generowana automatycznie w `FarmControl` projektancie, ale nie jest przydatna w przypadku tej aplikacji.

6. Przy użyciu przybornika utwórz dwa wystąpienia obiektu **DataGridView** i nadaj im `AnimalGridView` nazwy oraz `FieldGridView` .

   > [!NOTE]
   > Alternatywnym krokiem jest przeciągnięcie elementów Zwierzęta i Pola z okna Źródła danych do kontrolki. Ta akcja powoduje automatyczne utworzenie siatek danych i powiązań między widokiem siatki a źródłem danych. Jednak to powiązanie nie działa poprawnie w przypadku plików DSL. W związku z tym lepiej jest ręcznie utworzyć siatki danych i powiązania.

7. Jeśli przybornik nie zawiera narzędzia **ModelingBindingSource,** dodaj go. W menu skrótów na **karcie Dane** wybierz pozycję **Wybierz elementy.** W **oknie dialogowym Wybieranie elementów przybornika** wybierz pozycję **ModelingBindingSource** na **karcie .NET Framework** narzędzi.

8. Przy użyciu przybornika utwórz dwa wystąpienia klasy **ModelingBindingSource** i nadaj im `AnimalBinding` nazwy oraz `FieldBinding` .

9. Ustaw właściwość **DataSource** każdego **obiektu ModelingBindingSource** na **wartość farmBindingSource.**

     Ustaw właściwość **DataMember na** **wartość Zwierzęta** lub **Pola**.

10. Ustaw właściwości **źródła danych** na wartość , a dla właściwości na `AnimalGridView` wartość `AnimalBinding`  `FieldGridView` `FieldBinding` .

11. Dostosuj układ kontrolki Farm do swoich potrzeb.

    **ModelingBindingSource** to karta, która wykonuje kilka funkcji specyficznych dla plików DSL:

- Opakowywuje aktualizacje w transakcji magazynu VMSDK.

   Na przykład gdy użytkownik usunie wiersz z siatki widoku danych, zwykłe powiązanie spowoduje wyjątek transakcji.

- Dzięki temu, gdy użytkownik wybierze wiersz, okno Właściwości wyświetla właściwości odpowiedniego elementu modelu, a nie wiersza siatki danych.

  ![Schemat powiązania DSL](../modeling/media/dslwpf4.png)
  
  Schemat połączeń między źródłami danych i widokami.

### <a name="complete-the-bindings-to-the-dsl"></a>Ukończenie powiązań z DSL

1. Dodaj następujący kod w oddzielnym pliku kodu w **projekcie interfejsu** użytkownika:

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

2. W **projekcie DslPackage** edytuj folder **DslPackage\DocView.tt,** aby zaktualizować następującą definicję zmiennej:

    ```csharp
    string viewControlTypeName = "FarmControl";
    ```

## <a name="test-the-dsl"></a>Testowanie DSL

Rozwiązanie DSL może teraz kompilować i uruchamiać, chociaż możesz dodać kolejne ulepszenia później.

1. Skompiluj i uruchom rozwiązanie.

2. W eksperymentalnym wystąpieniu Visual Studio otwórz **przykładowy** plik.

3. W **Eksploratorze farmy aplikacji** otwórz  menu skrótów w węźle głównym farmy, a następnie wybierz pozycję **Dodaj nową kłaź.**

     `Goat1`w widoku **Zwierzęta.**

    > [!WARNING]
    > Należy użyć menu skrótów w węźle **Farma,** a nie **w węźle Zwierzęta.**

4. Wybierz węzeł **główny farmy** i wyświetl jego właściwości.

     W widoku formularza zmień nazwę **lub** **rozmiar** farmy.

     Gdy odchodzisz od każdego pola w formularzu, odpowiednia właściwość zmienia się w okno Właściwości.

## <a name="enhance-the-dsl"></a>Ulepszanie DSL

### <a name="make-the-properties-update-immediately"></a>Natychmiastowe aktualizowanie właściwości

1. W widoku projektu FarmControl.cs wybierz proste pole, takie jak Nazwa, Rozmiar lub IsOrganic.

2. W okno Właściwości rozwiń **okno DataBindings i** otwórz **(Zaawansowane).**

     W **oknie dialogowym Formatowanie** i powiązanie zaawansowane w **obszarze Tryb aktualizacji źródła danych** wybierz pozycję **OnPropertyChanged.**

3. Skompiluj i uruchom rozwiązanie.

     Sprawdź, czy po zmianie zawartości pola odpowiednia właściwość modelu farmy natychmiast się zmienia.

### <a name="provide-add-buttons"></a>Zapewnianie przycisków Dodaj

1. W widoku projektu farmcontrol.cs użyj przybornika, aby utworzyć przycisk w formularzu.

    Edytuj nazwę i tekst przycisku, na przykład `New Sheep` na .

2. Otwórz kod znajdujący się za przyciskiem (na przykład klikając go dwukrotnie).

    Edytuj go w następujący sposób:

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

    Należy również wstawić następującą dyrektywę:

   ```csharp

   using Microsoft.VisualStudio.Modeling;
   ```

3. Dodaj podobne przyciski dla pól i kłazy.

4. Skompiluj i uruchom rozwiązanie.

5. Sprawdź, czy nowy przycisk dodaje element. Nowy element powinien pojawić się zarówno w Eksploratorze farmy aplikacji, jak i w odpowiednim widoku siatki danych.

    Powinno być możliwe edytowanie nazwy elementu w widoku siatki danych. Możesz go również usunąć z tego miejscu.

   ![Przykładowy widok siatki danych](../modeling/media/dsl-wpf-2.png)

### <a name="about-the-code-to-add-an-element"></a>Informacje o kodzie dodawania elementu

W przypadku przycisków nowego elementu poniższy kod alternatywny jest nieco prostszy.

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

Jednak ten kod nie ustawia domyślnej nazwy dla nowego elementu. Nie uruchamia żadnych dostosowanych scalania, które  mogły być zdefiniowane w dyrektywach scalania elementów DSL i nie uruchamia żadnego niestandardowego kodu scalania, który mógł zostać zdefiniowany.

W związku z tym zalecamy używanie <xref:Microsoft.VisualStudio.Modeling.ElementOperations> polecenia do tworzenia nowych elementów. Aby uzyskać więcej informacji, zobacz [Dostosowywanie tworzenia i przemieszczania elementów.](../modeling/customizing-element-creation-and-movement.md)

## <a name="see-also"></a>Zobacz też

- [Jak zdefiniować język Domain-Specific język](../modeling/how-to-define-a-domain-specific-language.md)
- [Pisanie kodu w celu dostosowania Domain-Specific języku](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Modelowanie SDK dla Visual Studio — języki specyficzne dla domeny](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)
