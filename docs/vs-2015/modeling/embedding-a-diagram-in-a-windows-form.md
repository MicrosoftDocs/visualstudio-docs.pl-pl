---
title: Osadzanie diagramu w formularzu Windows | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: fa6cd040-7c88-4329-b9c3-2a80b312610f
caps.latest.revision: 3
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 440b60697d4ab1e88f535b6c5ef824bc74e19c48
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60068694"
---
# <a name="embedding-a-diagram-in-a-windows-form"></a>Osadzanie diagramu w formularzu systemu Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DSL diagram można osadzić w kontrolce Windows, która jest wyświetlana w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] okna.  
  
## <a name="embedding-a-diagram"></a>Osadzanie diagramu  
  
#### <a name="to-embed-a-dsl-diagram-in-a-windows-control"></a>Aby osadzić DSL diagram w kontrolce Windows  
  
1. Dodaj nową **kontrolki użytkownika** pliku do projektu DslPackage.  
  
2. Dodaj kontrolkę panelu do kontrolki użytkownika. Ten panel będzie zawierać DSL Diagram.  
  
     Dodaj inne kontrolki, których potrzebujesz.  
  
     Ustaw właściwości zakotwiczenia formantów.  
  
3. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy plik kontrolki użytkownika, a następnie kliknij przycisk **Wyświetl kod**. Dodaj ten konstruktor i zmiennej w kodzie:  
  
    ```csharp  
  
    internal UserControl1(MyDSLDocView docView, Control content)  
      : this()  
    {  
      panel1.Controls.Add(content);  
      this.docView = docView;  
    }  
    private MyDSLDSLDocView docView;  
  
    ```  
  
4. Dodaj nowy plik do projektu DslPackage, o następującej zawartości:  
  
    ```  
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
  
5. Aby przetestować język DSL, naciśnij klawisz F5, a następnie otworzyć przykładowy plik modelu. Diagram pojawia się wewnątrz formantu. Przybornik i inne funkcje działają normalnie.  
  
#### <a name="updating-the-form-using-store-events"></a>Aktualizowanie formularza przy użyciu zdarzenia Store  
  
1. W Projektancie formularza należy dodać **ListBox** o nazwie `listBox1`. Spowoduje to wyświetlenie listy elementów w modelu. Zostaną zachowane w synchronism przy użyciu modelu *przechowywania zdarzeń*. Aby uzyskać więcej informacji, zobacz [obsługi propagowanie zmian poza Model zdarzeń](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
2. W pliku kodu niestandardowego zastąpić dalsze metody do klasy DocView:  
  
    ```  
  
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
  
3. W kodzie kontrolki użytkownika należy wstawić metody do nasłuchiwania pod kątem elementów dodawane lub usuwane:  
  
    ```  
  
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
  
4. Aby przetestować język DSL, naciśnij klawisz F5, a w doświadczalnym wystąpieniu programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], otworzyć przykładowy plik modelu.  
  
     Należy zauważyć, że pole listy to lista elementów w modelu, i że jest on poprawny po albo i po Cofnij i ponów.  
  
## <a name="see-also"></a>Zobacz też  
 [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)
