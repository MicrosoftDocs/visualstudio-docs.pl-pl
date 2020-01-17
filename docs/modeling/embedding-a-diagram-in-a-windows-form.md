---
title: Osadzanie diagramu w formularzu systemu Windows
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94425c9f3bc586847f43589f7abdcef2295cf1b9
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114624"
---
# <a name="embed-a-diagram-in-a-windows-form"></a>Osadzanie diagramu w formularzu systemu Windows

Diagram DSL można osadzić w kontrolce systemu Windows, która jest wyświetlana w oknie programu Visual Studio.

## <a name="embed-a-dsl-diagram-in-a-windows-control"></a>Osadzanie diagramu DSL w kontrolce systemu Windows

1. Dodaj nowy plik **kontrolki użytkownika** do projektu DslPackage.

2. Dodaj kontrolkę panel do kontrolki użytkownika. Ten panel będzie zawierać diagram DSL.

     Dodaj inne wymagane kontrolki.

     Ustaw właściwości zakotwiczenia kontrolek.

3. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy plik kontrolki użytkownika, a następnie kliknij polecenie **Wyświetl kod**. Dodaj ten Konstruktor i zmienną do kodu:

    ```csharp
    internal UserControl1(MyDSLDocView docView, Control content)
      : this()
    {
      panel1.Controls.Add(content);
      this.docView = docView;
    }
    private MyDSLDocView docView;
    ```

4. Dodaj nowy plik do projektu DslPackage z następującą zawartością:

    ```csharp
    using System.Windows.Forms;
    namespace Company.MyDSL
    {
      partial class MyDSLDocView
      {
        private UserControl1 container;
        public override IWin32Window Window
        {
          get
          {
            if (container == null)
            {
              // Put our own form inside the DSL window:
              container = new UserControl1(this,
                (Control)base.Window);
            }
            return container;
    } } } }
    ```

5. Aby przetestować DSL, naciśnij klawisz **F5** , a następnie otwórz przykładowy plik modelu. Diagram zostanie wyświetlony wewnątrz kontrolki. Przybornik i inne funkcje działają normalnie.

## <a name="update-the-form-using-store-events"></a>Aktualizowanie formularza przy użyciu zdarzeń ze sklepu

1. W projektancie formularzy Dodaj **pole listy** o nazwie `listBox1`. Spowoduje to wyświetlenie listy elementów w modelu. Jest on synchronizowany z modelem przy użyciu *zdarzeń ze sklepu*. Aby uzyskać więcej informacji, zobacz [programy obsługi zdarzeń propagują zmiany poza modelem](../modeling/event-handlers-propagate-changes-outside-the-model.md).

2. W pliku kodu niestandardowego Zastąp dalsze metody do klasy DocView:

    ```csharp
    partial class MyDSLDocView
    {
     /// <summary>
     /// Register store event listeners.
     /// This method is called when the model and diagram
     /// have completed loading.
     /// </summary>
     protected override bool LoadView()
      {
        bool result = base.LoadView();
        Store store = this.DocData.Store;
        EventManagerDirectory emd = store.EventManagerDirectory;
        DomainClassInfo componentClass = store.DomainDataDirectory.FindDomainClass(typeof(ExampleElement));
        emd.ElementAdded.Add(componentClass, new EventHandler<ElementAddedEventArgs>(AddElement));
        emd.ElementDeleted.Add(componentClass, new EventHandler<ElementDeletedEventArgs>(RemoveElement));

        // Do the initial parts list:
        container.SetUpFormFromModel();
        return result;
      }
     /// <summary>
     /// Listener method called on creation of each instance of
     /// the ExampleElement class or its subclasses.
     /// </summary>
     private void AddElement(object sender, ElementAddedEventArgs e)
     {
       container.Add(e.ModelElement as ExampleElement);
     }
     /// <summary>
     /// Listener method called after deletion of each instance of
     /// the ExampleElement class or its subclasses.
     /// </summary>
     private void RemoveElement(object sender, ElementDeletedEventArgs e)
     {
       container.Remove(e.ModelElement as ExampleElement);
     }
    ```

3. W kodzie związanym z kontrolką użytkownika Wstaw metody do nasłuchiwania dla elementów dodanych i usuniętych:

    ```csharp
    public partial class UserControl1 : UserControl { ...

    private ExampleModel modelRoot;

    internal void Add(ExampleElement e) { UpdatePartsList(); }
    internal void Remove(ExampleElement e) { UpdatePartsList(); }

    internal void SetUpFormFromModel()
    {
      modelRoot = this.docView.CurrentDiagram.ModelElement as ExampleModel;
      UpdatePartsList();
    }

    private void UpdatePartsList()
    {
      StringBuilder builder = new StringBuilder();
      listBox1.Items.Clear();
      foreach (ExampleElement c in modelRoot.Elements)
      {
        listBox1.Items.Add(c.Name);
      }
    }
    ```

4. Aby przetestować DSL, naciśnij klawisz **F5** i w eksperymentalnym wystąpieniu programu Visual Studio Otwórz przykładowy plik modelu.

     Zwróć uwagę, że pole listy zawiera listę elementów w modelu i że jest poprawna po dodaniu lub usunięciu, a następnie Cofnij i wykonaj ponownie.

## <a name="see-also"></a>Zobacz także

- [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)
