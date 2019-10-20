---
title: Aktualizowanie modelu UML z wątku w tle | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 42c06b0b-b681-4e19-b5f3-6116dd2a4072
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9e6626faa09f1e38506c2d205d13caa9a3707fc0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659463"
---
# <a name="update-a-uml-model-from-a-background-thread"></a>Aktualizowanie modelu UML z wątku w tle
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Czasami może być przydatne wprowadzanie zmian do modelu w wątku w tle. Na przykład, Jeśli ładujesz informacje z powolnego zasobu zewnętrznego, można użyć wątku w tle do nadzorowania aktualizacji. Dzięki temu użytkownik może zobaczyć każdą aktualizację tak szybko, jak to się dzieje.

 Należy jednak pamiętać, że sklep UML nie jest bezpieczny wątkowo. Ważne są następujące środki ostrożności:

- Każda Aktualizacja modelu lub diagramu musi zostać wykonana w wątku interfejsu użytkownika. Wątek w tle musi używać <xref:System.Windows.Forms.Control.Invoke%2A> lub `Dispatcher.` <xref:System.Windows.Threading.Dispatcher.Invoke%2A>, aby wątek interfejsu użytkownika wykonywał rzeczywiste aktualizacje.

- Jeśli grupujesz serię zmian w pojedynczą transakcję, zalecamy uniemożliwienie użytkownikowi edytowania modelu, gdy transakcja jest w toku. W przeciwnym razie wszelkie zmiany wprowadzone przez użytkownika staną się częścią tej samej transakcji. Można uniemożliwić użytkownikowi wprowadzanie zmian, wyświetlając modalne okno dialogowe. Jeśli chcesz, możesz podać przycisk Anuluj w oknie dialogowym. Użytkownik może zobaczyć zmiany w miarę ich występowania.

## <a name="example"></a>Przykład
 W tym przykładzie używa wątku w tle w celu wprowadzenia kilku zmian w modelu. Okno dialogowe służy do wykluczenia użytkownika, gdy wątek jest uruchomiony. W tym prostym przykładzie w oknie dialogowym nie jest dostępny przycisk Anuluj. Można jednak łatwo dodać tę funkcję.

#### <a name="to-run-the-example"></a>Aby uruchomić przykład

1. Utwórz procedurę obsługi poleceń w C# projekcie, zgodnie z opisem w temacie [Definiowanie polecenia menu na diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

2. Upewnij się, że projekt zawiera odwołania do tych zestawów:

   - Microsoft. VisualStudio. ArchitectureTools. rozszerzalność

   - Microsoft. VisualStudio. Modeling. Sdk. nowszym

   - Microsoft. VisualStudio. Modeling. Sdk. diagramy. nowszym

   - Microsoft. VisualStudio. UML. Interfaces

   - System. ComponentModel. kompozycji

   - System. Windows. Forms

3. Dodaj do projektu formularz systemu Windows o nazwie **ProgressForm**. Powinien zostać wyświetlony komunikat informujący o tym, że aktualizacje są w toku. Nie musi mieć żadnych innych kontrolek.

4. Dodaj C# plik zawierający kod, który jest wyświetlany po kroku 7.

5. Skompiluj i Uruchom projekt.

    Nowe wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozpocznie się w trybie eksperymentalnym.

6. Utwórz lub Otwórz diagram klas UML w eksperymentalnym wystąpieniu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

7. Kliknij prawym przyciskiem myszy w dowolnym miejscu diagramu klas UML, a następnie kliknij polecenie **Dodaj kilka klas UML**.

   Kilka nowych pól klas zostanie wyświetlonych na diagramie, jeden po drugim w odstępach czasu pół sekundy.

```csharp
using System;
using System.ComponentModel;
using System.ComponentModel.Composition;
using System.Threading;
using System.Windows.Forms;

using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using Microsoft.VisualStudio.Uml.Classes;

namespace BackgroundThreadProgressUI // CHANGE TO YOUR NAMESPACE
{
  [Export(typeof(ICommandExtension))]
  [ClassDesignerExtension]
  class UmlClassAdderCommand : ICommandExtension
  {

    [Import]
    IDiagramContext context { get; set; }

    [Import]
    ILinkedUndoContext linkedUndoContext { get; set; }

    // Called when the user runs the command.
    public void Execute(IMenuCommand command)
    {
      // The form that will exclude the user.
      ProgressForm form = new ProgressForm();

      // System.ComponentModel.BackgroundWorker is a
      // convenient way to run a background thread.
      BackgroundWorker worker = new BackgroundWorker();
      worker.WorkerSupportsCancellation = true;

      worker.DoWork += delegate(object sender, DoWorkEventArgs args)
      {
        // This block will be executed in a background thread.

        IClassDiagram diagram = context.CurrentDiagram as IClassDiagram;
        IModelStore store = diagram.ModelStore;
        const int CLASSES_TO_CREATE = 15;

        // Group all the changes together.
        using (ILinkedUndoTransaction transaction = linkedUndoContext.BeginTransaction("Background Updates"))
        {
          for (int i = 1; i < CLASSES_TO_CREATE; i++)
          {
            if (worker.CancellationPending)
               return; // No commit - undo all.

            // Create model elements using the UI thread by using
            // the Invoke method on the progress form. Always
            // modify the model and diagrams from a UI thread.
            form.Invoke((MethodInvoker)(delegate
            {
              IClass newClass = store.Root.CreateClass();
              newClass.Name = string.Format("NewClass{0}", i);
              diagram.Display(newClass);
            }));

            // Sleep briefly so that we can watch the updates.
            Thread.Sleep(500);
          }

          // Commit the transaction or it will be rolled back.
          transaction.Commit();
        }
      };

      // Close the form when the thread completes.
      worker.RunWorkerCompleted += delegate(object sender, RunWorkerCompletedEventArgs args)
      {
        form.Close();
      };

      // Start the thread before showing the modal progress dialog.
      worker.RunWorkerAsync();

      // Show the form modally, parented on VS.
      // Prevents the user from making changes while in progress.
      form.ShowDialog();
    }

    public void QueryStatus(IMenuCommand command)
    {
      command.Enabled = command.Visible = true;
    }

    public string Text
    {
      get { return "Add several classes"; }
    }
  }
}
```

#### <a name="to-allow-the-user-to-cancel-the-thread-in-the-example"></a>Aby zezwolić użytkownikowi na anulowanie wątku w przykładzie

1. Dodaj przycisk Anuluj do okna dialogowego postępu.

2. Dodaj następujący kod do okna dialogowego postęp:

     `public event MethodInvoker Cancel;`

     `private void CancelButton_Click(object sender, EventArgs e)`

     `{`

     `Cancel();`

     `}`

3. W metodzie Execute () Wstaw ten wiersz po konstrukcji formularza:

     `form.Cancel += delegate() { worker.CancelAsync(); };`

### <a name="other-methods-of-accessing-the-ui-thread"></a>Inne metody uzyskiwania dostępu do wątku interfejsu użytkownika
 Jeśli nie chcesz tworzyć okna dialogowego, możesz uzyskać dostęp do formantu, który wyświetla Diagram:

 `DiagramView uiThreadHolder = context.CurrentDiagram.GetObject<Diagram>().ActiveDiagramView;`

 Za pomocą `uiThreadHolder.Invoke()` do wykonywania operacji w wątku interfejsu użytkownika.

## <a name="see-also"></a>Zobacz też
 [Definiowanie polecenia menu na diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [Definiowanie obsługi gestów na diagramie modelowania](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)
