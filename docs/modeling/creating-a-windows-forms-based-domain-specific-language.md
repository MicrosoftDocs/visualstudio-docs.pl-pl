---
title: Tworzenie języka specyficznego dla domeny opartego na modelu Windows Forms
description: Zawiera informacje dotyczące sposobu używania Windows Forms do wyświetlania stanu modelu języka specyficznego dla domeny.
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 41c3ba299df1e6f9ce0e2848f7ffad59e5b3fbea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945412"
---
# <a name="create-a-windows-forms-based-domain-specific-language"></a>Tworzenie języka Domain-Specific opartego na Windows Formsach

Za pomocą Windows Forms można wyświetlić stan modelu języka specyficznego dla domeny (DSL), zamiast korzystać z diagramu DSL. Ten temat przeprowadzi Cię przez powiązanie formularza systemu Windows z DSL przy użyciu wizualizacji i modelowania SDK programu Visual Studio.

Na poniższej ilustracji przedstawiono interfejs użytkownika formularza systemu Windows i Eksplorator modelu dla wystąpienia DSL:

![Wystąpienie DSL w programie Visual Studio](../modeling/media/dsl-wpf-2.png)

## <a name="create-a-windows-forms-dsl"></a>Tworzenie Windows Forms DSL

Szablon DSL **projektanta w minimalnym** stopniu pozwala utworzyć minimalny DSL, który można zmodyfikować zgodnie z własnymi wymaganiami.

1. Utwórz DSL przy użyciu szablonu **minimalnego projektanta** .

    W tym instruktażu założono następujące nazwy:

    - Nazwa rozwiązania i DSL: `FarmApp`
    - Przestrzeń nazw: `Company.FarmApp`

2. Eksperymentuj z początkowym przykładem udostępnianym przez szablon:

   1. Przekształć wszystkie szablony.

   2. Kompiluj i uruchamiaj przykład (**Ctrl** + **F5**).

   3. W eksperymentalnym wystąpieniu programu Visual Studio Otwórz `Sample` plik w projekcie debugowania.

        Zauważ, że jest on wyświetlany w kontrolce Windows Forms.

        Widoczne są również elementy modelu wyświetlanego w Eksploratorze.

        Dodaj niektóre elementy w formularzu lub w Eksploratorze i Zauważ, że pojawiają się one w drugim ekranie.

   W głównym wystąpieniu programu Visual Studio Zwróć uwagę na następujące kwestie dotyczące rozwiązania DSL:

- `DslDefinition.dsl` nie zawiera elementów diagramu. Dzieje się tak dlatego, że nie będziesz używać diagramów DSL do wyświetlania modeli wystąpień tego języka DSL. Zamiast tego utworzysz powiązanie formularza systemu Windows z modelem, a elementy w formularzu będą wyświetlały model.

- Oprócz `Dsl` `DslPackage` projektów i, rozwiązanie zawiera trzeci projekt o nazwie `UI.` projekt **interfejsu użytkownika** zawiera definicję kontrolki Windows Forms. `DslPackage` zależy od `UI` , i `UI` zależy od `Dsl` .

- W `DslPackage` projekcie, `UI\DocView.cs` zawiera kod, który wyświetla formant Windows Forms, który jest zdefiniowany w `UI` projekcie.

- `UI`Projekt zawiera roboczą próbkę kontrolki formularza powiązaną z DSL. Nie będzie jednak działała po zmianie definicji DSL. `UI`Projekt zawiera:

  - Klasa Windows Forms o nazwie `ModelViewControl` .

  - Plik o nazwie `DataBinding.cs` , który zawiera dodatkową definicję częściową `ModelViewControl` . Aby wyświetlić jego zawartość, w **Eksplorator rozwiązań** Otwórz menu skrótów dla pliku i wybierz polecenie **Wyświetl kod**.

### <a name="about-the-ui-project"></a>Projekt interfejsu użytkownika — informacje

Po zaktualizowaniu pliku definicji DSL w celu zdefiniowania własnego modemu DSL należy zaktualizować kontrolkę w `UI` projekcie, aby wyświetlić dane DSL. W przeciwieństwie `Dsl` do `DslPackage` projektów i, przykładowy `UI` projekt nie jest generowany z `DslDefinitionl.dsl` . Możesz dodać pliki. TT, aby wygenerować kod w razie potrzeby, chociaż nie został on uwzględniony w tym instruktażu.

## <a name="update-the-dsl-definition"></a>Aktualizowanie definicji DSL

Poniższy obraz to Definicja DSL użyta w tym instruktażu.

![Definicja DSL](../modeling/media/dsl-wpf-1.png)

1. Otwórz DslDefinition. DSL w projektancie DSL.

2. Usuń **przykładElement**

3. Zmień nazwę klasy domeny **ExampleModel** na `Farm` .

     Nadaj mu dodatkowe właściwości domeny o nazwie `Size` typu **Int32** i `IsOrganic` typie **Boolean**.

    > [!NOTE]
    > W przypadku usunięcia klasy domeny głównej, a następnie utworzenia nowego katalogu głównego należy zresetować właściwość klasy głównej edytora. W **Eksploratorze DSL** wybierz pozycję **Edytor**. Następnie w okno Właściwości ustaw **klasę root** na `Farm` .

4. Użyj narzędzia **klasy nazwanej domeny** do utworzenia następujących klas domeny:

    - `Field` -Nadaj tej domenie dodatkową właściwość o nazwie `Size` .

    - `Animal` -W okno Właściwości ustaw **modyfikator dziedziczenia** na **abstrakcyjny**.

5. Użyj narzędzia **klasy domeny** do utworzenia następujących klas:

    - `Sheep`

    - `Goat`

6. Użyj narzędzia **dziedziczenie** , aby utworzyć `Goat` i `Sheep` odziedziczyć z `Animal` .

7. Za pomocą narzędzia **osadzania** Osadź `Field` i `Animal` w obszarze `Farm` .

8. Możesz chcieć uporządkowanego diagram. Aby zmniejszyć liczbę zduplikowanych elementów, użyj polecenia **Przenieś poddrzewo tutaj** w menu skrótów elementów liścia.

9. **Przekształć wszystkie szablony** na pasku narzędzi Eksplorator rozwiązań.

10. Kompiluj projekt **DSL** .

    > [!NOTE]
    > Na tym etapie inne projekty nie zostaną skompilowane bez błędów. Jednak chcemy skompilować projekt DSL, aby jego zestaw był dostępny dla Kreatora źródła danych.

## <a name="update-the-ui-project"></a>Aktualizowanie projektu interfejsu użytkownika

Teraz można utworzyć nową kontrolkę użytkownika, która będzie wyświetlać informacje przechowywane w modelu DSL. Najprostszym sposobem łączenia kontrolki użytkownika z modelem jest użycie powiązań danych. Typ łączenia powiązania danych o nazwie **ModelingBindingSource** jest przeznaczony specjalnie do połączenia językami DSL z interfejsami nieVMSDK.

### <a name="define-your-dsl-model-as-a-data-source"></a>Definiowanie modelu DSL jako źródła danych

1. W menu **dane** wybierz polecenie **Pokaż źródła danych**.

     Zostanie otwarte okno **źródła danych** .

     Wybierz pozycję **Dodaj nowe źródło danych**. Zostanie otwarty **Kreator konfiguracji źródła danych** .

2. Wybierz **obiekt**, **dalej**.

     Rozwiń węzeł **DSL**, **Company. FarmApp** i wybierz opcję **Farma**, która jest klasą główną modelu. Wybierz pozycję **Zakończ**.

     W Eksplorator rozwiązań projekt **interfejsu użytkownika** zawiera teraz **Properties\DataSources\Farm.DataSource**

     Właściwości i relacje klasy modelu są wyświetlane w oknie źródła danych.

     ![Okno źródeł danych](../modeling/media/dslwpf-3.png)

### <a name="connect-your-model-to-a-form"></a>Łączenie modelu z formularzem

1. W projekcie **interfejsu użytkownika** Usuń wszystkie istniejące pliki. cs.

2. Dodaj nowy plik **kontrolki użytkownika** o nazwie `FarmControl` do projektu **interfejsu użytkownika** .

3. W oknie **źródła danych** , w menu rozwijanym w **farmie**, wybierz pozycję **szczegóły**.

    Pozostaw ustawienia domyślne dla innych właściwości.

4. Otwórz FarmControl.cs w widoku projektu.

    Przeciągnij **farmę** z okna źródła danych na FarmControl.

    Zostanie wyświetlony zestaw kontrolek, po jednym dla każdej właściwości. Właściwości relacji nie generują formantów.

5. Usuń **farmBindingNavigator**. Jest to również generowane automatycznie w `FarmControl` projektancie, ale nie jest to przydatne w przypadku tej aplikacji.

6. Za pomocą przybornika Utwórz dwa wystąpienia **formantu DataGridView** i nadaj im nazwę `AnimalGridView` i `FieldGridView` .

   > [!NOTE]
   > Alternatywnym krokiem jest przeciągnięcie elementów zwierzęta i pola z okna źródła danych na kontrolkę. Ta akcja powoduje automatyczne utworzenie sieci i powiązań danych między widokiem siatki a źródłem danych. Jednak to powiązanie nie działa prawidłowo dla językami DSL. W związku z tym lepiej jest tworzyć siatki danych i powiązania ręcznie.

7. Jeśli Przybornik nie zawiera narzędzia **ModelingBindingSource** , Dodaj go. W menu skrótów na karcie **dane** wybierz pozycję **Wybierz elementy**. W oknie dialogowym **Wybierz elementy przybornika** wybierz pozycję **ModelingBindingSource** z karty **.NET Framework** .

8. Za pomocą przybornika Utwórz dwa wystąpienia **ModelingBindingSource** i nadaj im nazwę `AnimalBinding` i `FieldBinding` .

9. Ustaw właściwość **DataSource** każdego **ModelingBindingSource** na **farmBindingSource**.

     Ustaw właściwość **DataMember** na **zwierzęta** lub **pola**.

10. Ustaw właściwości **źródła danych** `AnimalGridView` na `AnimalBinding` , i z  `FieldGridView` na `FieldBinding` .

11. Dostosuj układ kontrolki farmy do swojego smaku.

    **ModelingBindingSource** to karta, która wykonuje kilka funkcji, które są specyficzne dla językami DSL:

- Spowoduje to otoczenie aktualizacji w transakcji magazynu VMSDK.

   Na przykład, gdy użytkownik usuwa wiersz z siatki widoku danych, regularne powiązanie spowoduje wyjątek transakcji.

- Gwarantuje to, że gdy użytkownik wybierze wiersz, okno Właściwości wyświetla właściwości odpowiedniego elementu modelu, a nie wiersz siatki danych.

  ![Schemat powiązania DSL](../modeling/media/dslwpf4.png)
  
  Schemat linków między źródłami danych i widokami.

### <a name="complete-the-bindings-to-the-dsl"></a>Ukończ powiązania z DSL

1. Dodaj następujący kod w osobnym pliku kodu w projekcie **interfejsu użytkownika** :

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

2. W projekcie **DslPackage** Edytuj **DslPackage\DocView.tt** , aby zaktualizować następującą definicję zmiennej:

    ```csharp
    string viewControlTypeName = "FarmControl";
    ```

## <a name="test-the-dsl"></a>Testowanie DSL

Rozwiązanie DSL może teraz kompilować i uruchamiać, chociaż warto później dodać dalsze ulepszenia.

1. Skompiluj i uruchom rozwiązanie.

2. W eksperymentalnym wystąpieniu programu Visual Studio Otwórz plik **przykładowy** .

3. W **Eksploratorze FarmApp** Otwórz menu skrótów w węźle głównym **farmy** i wybierz polecenie **Dodaj nowe kozy**.

     `Goat1` pojawia się w widoku **zwierzęta** .

    > [!WARNING]
    > Musisz użyć menu skrótów w węźle **farmy** , a nie w węźle **zwierzęta** .

4. Wybierz węzeł główny **farmy** i Wyświetl jego właściwości.

     W widoku Formularz Zmień **nazwę** lub **rozmiar** farmy.

     W przypadku opuszczenia każdego pola w formularzu odpowiednia właściwość zmienia się w okno Właściwości.

## <a name="enhance-the-dsl"></a>Ulepszanie DSL

### <a name="make-the-properties-update-immediately"></a>Natychmiastowe aktualizowanie właściwości

1. W widoku Projekt FarmControl.cs wybierz proste pole, takie jak Name, size lub isorganiczny.

2. W okno Właściwości rozwiń węzeł **DataBindings** i Otwórz **(Zaawansowane)**.

     W oknie dialogowym **Formatowanie i zaawansowane powiązanie** w obszarze **Tryb aktualizacji źródła danych** wybierz pozycję **OnPropertyChanged**.

3. Skompiluj i uruchom rozwiązanie.

     Sprawdź, czy po zmianie zawartości pola odpowiednia właściwość modelu farmy zostanie natychmiast zmieniona.

### <a name="provide-add-buttons"></a>Podaj przyciski dodawania

1. W widoku Projekt FarmControl.cs, Użyj przybornika, aby utworzyć przycisk w formularzu.

    Edytuj nazwę i tekst przycisku, na przykład `New Sheep` .

2. Otwórz kod za przyciskiem (na przykład przez dwukrotne kliknięcie).

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

    Należy również wprowadzić następującą dyrektywę:

   ```csharp

   using Microsoft.VisualStudio.Modeling;
   ```

3. Dodaj podobne przyciski dla kóz i pól.

4. Skompiluj i uruchom rozwiązanie.

5. Sprawdź, czy nowy przycisk dodaje element. Nowy element powinien pojawić się zarówno w Eksploratorze FarmApp, jak i w odpowiednim widoku siatki danych.

    Powinno być możliwe edytowanie nazwy elementu w widoku siatki danych. Możesz również z niej usunąć.

   ![Widok siatki przykładowych danych](../modeling/media/dsl-wpf-2.png)

### <a name="about-the-code-to-add-an-element"></a>Informacje o kodzie umożliwiającym dodanie elementu

W przypadku przycisków nowego elementu Poniższy kod alternatywny jest nieco łatwiejszy.

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

Jednak ten kod nie ustawia domyślnej nazwy dla nowego elementu. Nie jest wykonywane żadne niestandardowe scalanie, które mogło zostać zdefiniowane w **dyrektywach scalania elementów** DSL, i nie uruchamia żadnego niestandardowego kodu scalania, który mógł zostać zdefiniowany.

Dlatego zalecamy użycie <xref:Microsoft.VisualStudio.Modeling.ElementOperations> programu w celu utworzenia nowych elementów. Aby uzyskać więcej informacji, zobacz [Dostosowywanie tworzenia i przenoszenia elementów](../modeling/customizing-element-creation-and-movement.md).

## <a name="see-also"></a>Zobacz też

- [Jak zdefiniować język Domain-Specific](../modeling/how-to-define-a-domain-specific-language.md)
- [Napisz kod, aby dostosować język Domain-Specific](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Modelowanie SDK dla Visual Studio — języki specyficzne dla domeny](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)
