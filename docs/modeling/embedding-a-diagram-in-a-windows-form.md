---
title: Osadzanie diagramu w formularzu systemu Windows
description: Dowiedz się, jak osadzić diagram DSL w kontrolce systemu Windows, która jest wyświetlana Visual Studio oknie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4db60267b835882a69a08c990af644b902697bad
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388987"
---
# <a name="embed-a-diagram-in-a-windows-form"></a>Osadzanie diagramu w formularzu systemu Windows

Diagram DSL można osadzić w kontrolce systemu Windows, która jest wyświetlana Visual Studio okna.

## <a name="embed-a-dsl-diagram-in-a-windows-control"></a>Osadzanie diagramu DSL w kontrolce systemu Windows

1. Dodaj nowy plik **kontroli użytkownika** do projektu DslPackage.

2. Dodaj kontrolkę Panel do kontrolki użytkownika. Ten panel będzie zawierać diagram DSL.

     Dodaj inne wymagane kontrolki.

     Ustaw właściwości kotwicy kontrolek.

3. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy plik kontroli użytkownika, a następnie kliknij polecenie **Wyświetl kod.** Dodaj ten konstruktor i zmienną do kodu:

    ```csharp
    internal UserControl1(MyDSLDocView docView, Control content)
      : this()
    {
      panel1.Controls.Add(content);
      this.docView = docView;
    }
    private MyDSLDocView docView;
    ```

4. Dodaj nowy plik do projektu DslPackage o następującej zawartości:

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

5. Aby przetestować DSL, naciśnij **klawisz F5** i otwórz przykładowy plik modelu. Diagram zostanie wyświetlony wewnątrz kontrolki. Przybornik i inne funkcje działają normalnie.

## <a name="update-the-form-using-store-events"></a>Aktualizowanie formularza przy użyciu zdarzeń magazynu

1. W projektancie formularzy dodaj pole **ListBox** o nazwie `listBox1` . Spowoduje to wyświetlenie listy elementów w modelu. Jest on synchronizowany z modelem przy użyciu *zdarzeń magazynu*. Aby uzyskać więcej informacji, zobacz [Programy obsługi zdarzeń propagują zmiany poza modelem](../modeling/event-handlers-propagate-changes-outside-the-model.md).

2. W niestandardowym pliku kodu zastąp dalsze metody klasą DocView:

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

3. W kodzie, za kontrolą użytkownika, wstaw metody, aby nasłuchiwać elementów dodanych i usuniętych:

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

4. Aby przetestować DSL, naciśnij **klawisz F5** i w eksperymentalnym wystąpieniu Visual Studio otwórz przykładowy plik modelu.

     Zwróć uwagę, że pole listy zawiera listę elementów w modelu i że jest prawidłowa po każdym dodatku lub usunięciu oraz po cofnięcie i ponowne jego usunięcie.

## <a name="see-also"></a>Zobacz też

- [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)
