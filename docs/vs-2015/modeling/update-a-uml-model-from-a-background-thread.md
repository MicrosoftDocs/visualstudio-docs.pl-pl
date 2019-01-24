---
title: Aktualizowanie modelu UML z wątku w tle | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 42c06b0b-b681-4e19-b5f3-6116dd2a4072
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cd0707ec7838ffb2dcebc8a176c79810f2614133
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54796462"
---
# <a name="update-a-uml-model-from-a-background-thread"></a>Aktualizowanie modelu UML z wątku w tle
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Czasami może być przydatny do wprowadzania zmian do modelu w wątku w tle. Na przykład przypadku ładowania informacji z powolnego zewnętrznego zasobu, można użyć wątku tła do nadzorowania aktualizacji. Dzięki temu użytkownikowi oglądać każdą aktualizację, tak szybko, jak zdarza się.  
  
 Jednak należy pamiętać, że magazyn UML nie jest bezpieczny dla wątków. Ważne są następujące środki ostrożności:  
  
-   Każda aktualizacji modelu lub diagramu musi nastąpić w wątku interfejsu użytkownika. Wątek tła musi użyć <xref:System.Windows.Forms.Control.Invoke%2A> lub `Dispatcher.` <xref:System.Windows.Threading.Dispatcher.Invoke%2A> mieć wątku interfejsu użytkownika wykona bieżące aktualizacje.  
  
-   Jeśli grupujesz serie zmian w pojedynczą transakcję, zaleca się, że można uniemożliwić użytkownikowi edytowanie modelu gdy transakcja jest w toku. W przeciwnym razie zmiany wprowadzone przez użytkownika staną się częścią tej samej transakcji. Aby uniemożliwić użytkownikowi dokonywanie zmian poprzez wyświetlenie modalnego okna dialogowego. Jeśli chcesz, możesz dostarczyć przycisk Anuluj w oknie dialogowym. Użytkownik może wyświetlić zmiany po ich wprowadzeniu.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto wątku w tle, aby wprowadzić wiele zmian do modelu. Okno dialogowe służy do wykluczenia użytkownika, gdy wątek jest uruchomiony. W tym prostym przykładzie Brak przycisku Anuluj znajduje się w oknie dialogowym. Jednakże może być łatwo dodać tę funkcję.  
  
#### <a name="to-run-the-example"></a>Aby uruchomić przykład  
  
1. Utwórz procedurę obsługi poleceń w projekcie języka C#, zgodnie z opisem w [Definiowanie polecenia menu na diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
2. Upewnij się, że projekt zawiera odwołania do tych zestawów:  
  
   -   Microsoft.VisualStudio.ArchitectureTools.Extensibility  
  
   -   Microsoft.VisualStudio.Modeling.Sdk.[version]  
  
   -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]  
  
   -   Microsoft.VisualStudio.Uml.Interfaces  
  
   -   System.ComponentModel.Composition  
  
   -   System.Windows.Forms  
  
3. Dodaj do projektu formularz Windows o nazwie **ProgressForm**. Powinna zostać wyświetlona komunikat informujący o tym, że aktualizacje są w toku. Nie ma mieć żadnych innych formantów.  
  
4. Dodaj plik języka C#, który zawiera kod, który jest wyświetlany po kroku 7.  
  
5. Skompiluj i uruchom projekt.  
  
    Nowe wystąpienie klasy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozpocznie się w trybie doświadczalnym.  
  
6. Utwórz lub Otwórz diagram klas UML w doświadczalnym wystąpieniu programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
7. Kliknij prawym przyciskiem myszy w dowolnym miejscu na diagramie klas UML, a następnie kliknij przycisk **Dodaj kilka klas UML**.  
  
   Kilka nowych pól klasy pojawi się na diagramie, po kolei w odstępach co pół sekundy.  
  
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
  
#### <a name="to-allow-the-user-to-cancel-the-thread-in-the-example"></a>Aby zezwolić użytkownikowi anulowanie wątku w przykładzie  
  
1.  Dodaj przycisk Anuluj do okna dialogowego postępu.  
  
2.  Dodaj następujący kod do okna dialogowego postępu:  
  
     `public event MethodInvoker Cancel;`  
  
     `private void CancelButton_Click(object sender, EventArgs e)`  
  
     `{`  
  
     `Cancel();`  
  
     `}`  
  
3.  W metodzie Execute() Wstaw ten wiersz po zbudowaniu formularza:  
  
     `form.Cancel += delegate() { worker.CancelAsync(); };`  
  
### <a name="other-methods-of-accessing-the-ui-thread"></a>Inne metody dostępu do wątku interfejsu użytkownika  
 Jeśli chcesz utworzyć okno dialogowe, możesz uzyskać dostęp formant, który wyświetla diagram:  
  
 `DiagramView uiThreadHolder = context.CurrentDiagram.GetObject<Diagram>().ActiveDiagramView;`  
  
 Możesz użyć `uiThreadHolder.Invoke()` do wykonywania operacji w wątku interfejsu użytkownika.  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie polecenia menu na diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [Definiowanie procedury obsługi gestów na diagramie modelowania](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)
