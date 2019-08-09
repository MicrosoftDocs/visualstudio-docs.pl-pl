---
title: Zdefiniuj obsługę linku elementu pracy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: d52e0bbf-0166-4bb4-a2e3-cefed6188875
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 240f143015f22435deb4f1347f74bebcc8b334c3
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68871900"
---
# <a name="define-a-work-item-link-handler"></a>Definiowanie procedury obsługi łącza elementu roboczego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można utworzyć rozszerzenie integracji programu Visual Studio, które reaguje, gdy użytkownik tworzy lub usuwa łącze między elementem modelu UML a elementem roboczym. Na przykład, gdy użytkownik zdecyduje się połączyć nowy element roboczy do elementu modelu, kod może zainicjować pola elementu pracy z wartości w modelu.

## <a name="set-up-a-uml-extension-solution"></a>Skonfiguruj rozwiązanie rozszerzenia UML
 Pozwoli to na programowanie programów obsługi, a następnie ich dystrybucję do innych użytkowników. Należy skonfigurować dwa projekty programu Visual Studio:

- Projekt biblioteki klas zawierający kod obsługi łącza.

- Projekt VSIX, który działa jako kontener służący do instalowania polecenia. Jeśli chcesz, możesz dołączyć inne składniki do tego samego VSIX.

#### <a name="to-set-up-the-visual-studio-solution"></a>Aby skonfigurować rozwiązanie Visual Studio

1. Utwórz projekt biblioteki klas, dodając go do istniejącego rozwiązania VSIX lub tworząc nowe rozwiązanie.

    1. W menu **plik** wybierz polecenie **Nowy**, **projekt**.

    2. W obszarze **zainstalowane szablony**rozwiń **pozycję C# Wizualizacja** lub **Visual Basic**, a następnie w środkowej kolumnie kliknij pozycję **Biblioteka klas**.

    3. Ustaw **rozwiązanie** , aby wskazać, czy chcesz utworzyć nowe rozwiązanie, czy dodać składnik do rozwiązania VSIX, które zostało już otwarte.

    4. Ustaw nazwę i lokalizację projektu, a następnie kliknij przycisk OK.

2. Chyba że rozwiązanie zawiera już jeden, Utwórz projekt VSIX.

    1. W **Eksplorator rozwiązań**, w menu skrótów rozwiązania, wybierz **Dodaj**, **Nowy projekt**.

    2. W obszarze **zainstalowane szablony**rozwiń **pozycję C# Wizualizacja** lub **Visual Basic**, a następnie wybierz pozycję **rozszerzalność**. W środkowej kolumnie Wybierz pozycję **Projekt VSIX**.

3. Ustaw projekt VSIX jako projekt startowy rozwiązania.

    - W Eksplorator rozwiązań, w menu skrótów projektu VSIX, wybierz **Ustaw jako projekt startowy**.

4. W obszarze **source. Extension. vsixmanifest**w obszarze **zawartość**Dodaj projekt biblioteki klas jako składnik MEF.

    1. Na karcie **metadane** Ustaw nazwę VSIX.

    2. Na karcie **Instalowanie obiektów docelowych** Ustaw wersje programu Visual Studio jako elementy docelowe.

    3. Na karcie **zasoby** wybierz pozycję **Nowy**, a następnie w oknie dialogowym Ustaw wartość:

         Wpisz = **składnik MEF**

         Źródło = **projektu w bieżącym rozwiązaniu**

         Projekt = *biblioteki klas*

## <a name="defining-the-work-item-link-handler"></a>Definiowanie procedury obsługi łącza elementu pracy
 Wykonaj wszystkie poniższe zadania w projekcie biblioteki klas.

### <a name="project-references"></a>Informacje o projekcie
 Dodaj następujące [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] zestawy do odwołań projektu:

 `Microsoft.TeamFoundation.WorkItemTracking.Client.dll`

 `Microsoft.VisualStudio.TeamFoundation.WorkItemTracking.dll Microsoft.VisualStudio.Modeling.Sdk.[version]`

 `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml`

 `Microsoft.VisualStudio.Uml.Interfaces`

 `System.ComponentModel.Composition`

 `System.Drawing`-używane przez przykładowy kod

 Jeśli nie możesz znaleźć jednego z tych odwołań na karcie **.NET** okna dialogowego **Dodaj odwołanie** , Użyj karty Przeglądaj, aby go znaleźć w folderze \Program Files\Microsoft Visual Studio [Version] \Common7\IDE\PrivateAssemblies\\.

### <a name="import-the-work-item-namespace"></a>Importowanie przestrzeni nazw elementów roboczych
 W odniesieniu do projektuDodajodwołaniadonastępujących[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zestawów:

- Microsoft.TeamFoundation.WorkItemTracking.Client.dll

- Microsoft.VisualStudio.TeamFoundation.WorkItemTracking.dll

  W kodzie programu Zaimportuj następujące przestrzenie nazw:

```
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.Uml.Classes;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.TeamFoundation.WorkItemTracking;
using System.Linq;
```

### <a name="define-the-linked-work-item-event-handler"></a>Zdefiniuj procedurę obsługi zdarzeń połączonego elementu pracy
 Dodaj plik klasy do projektu biblioteki klas i ustaw jego zawartość w następujący sposób. Zmień nazwy przestrzeni nazw i klas na dowolne preferowane.

```
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.Uml.Classes;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.TeamFoundation.WorkItemTracking;
using System.Linq;

namespace WorkItems
{
  [Export(typeof(ILinkedWorkItemExtension))]
  public class MyWorkItemExtension : ILinkedWorkItemExtension
  {
    // Called before a new work item is edited by the user.
    // Use this to initialize work item fields from the model element.
    public void OnWorkItemCreated(System.Collections.Generic.IEnumerable<IElement> elementsToBeLinked, IWorkItemDocument workItemDocument)
    {
      INamedElement namedElement =
            elementsToBeLinked.First() as INamedElement;
      if (namedElement != null)
        workItemDocument.Item.Title = namedElement.Name;

    }

    // Called when any work item is linked to a model element.
    public void OnWorkItemLinked(System.Collections.Generic.IEnumerable<IElement> elements, string serverUri, int workItemId)
    {
      foreach (IElement element in elements)
        foreach (IShape shape in element.Shapes())
          shape.Color = System.Drawing.Color.Red;
    }

    // Called when a work item is unlinked from a model element.
    public void OnWorkItemRemoved(IElement element, string serverUri, int workItemId)
    {
      foreach (IShape shape in element.Shapes())
        shape.Color = System.Drawing.Color.White;
    }
  }
}
```

## <a name="testing-the-link-handler"></a>Testowanie obsługi łącza
 Dla celów testowych wykonaj procedurę obsługi linków w trybie debugowania.

> [!WARNING]
> Aby utworzyć element roboczy lub połączyć się z nim, musisz mieć już połączenie z kontrolą kodu źródłowego (SCC) programu TFS. Jeśli spróbujesz otworzyć połączenie z innym TFS SCC, program Visual Studio automatycznie zamknie bieżące rozwiązanie. Upewnij się, że masz już połączenie z odpowiednim SCC, przed podjęciem próby utworzenia lub połączenia z elementem roboczym. W nowszych wersjach programu Visual Studio polecenia menu nie są dostępne, jeśli nie masz połączenia z SCC.

#### <a name="to-test-the-link-handler"></a>Aby przetestować obsługę łącza

1. Naciśnij klawisz **F5**lub w menu **Debuguj** wybierz polecenie **Rozpocznij debugowanie**.

     Doświadczalne wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uruchomienia.

     **Rozwiązywanie problemów**: Jeśli nowe [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nie zostanie uruchomione, upewnij się, że projekt VSIX jest ustawiony jako projekt startowy rozwiązania.

2. W eksperymentalnym [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], Otwórz lub Utwórz projekt modelowania, a następnie otwórz lub Utwórz diagram modelowania.

3. Utwórz element modelu, taki jak Klasa UML, i ustaw jego nazwę.

4. Kliknij prawym przyciskiem myszy element, a następnie kliknij pozycję **Utwórz element roboczy**.

    - Jeśli podmenu zawiera pozycję **otwórz Team Foundation Server połączenie**, należy zamknąć projekt, nawiązać połączenie z odpowiednim TFS i ponownie uruchomić tę procedurę.

    - Jeśli podmenu zawiera listę typów elementów roboczych, kliknij jeden.

         Zostanie otwarty nowy formularz elementu pracy.

5. Sprawdź, czy tytuł elementu pracy jest taki sam jak element modelu, jeśli użyto przykładowego kodu w poprzedniej sekcji. Ta ilustracja `OnWorkItemCreated()` zadziałała.

6. Wypełnij formularz, Zapisz i Zamknij element roboczy.

7. Sprawdź, czy element roboczy ma teraz kolor czerwony. Pokazano `OnWorkItemLinked()` to w przykładowym kodzie.

     **Rozwiązywanie problemów**: Jeśli nie uruchomiono metod obsługi, sprawdź, czy:

    - Projekt biblioteki klas jest wymieniony jako składnik MEF na liście **zawartości** w pliku **source. Extensions. manifest** w projekcie VSIX.

    - Poprawna `Export` wartość atrybutu jest dołączona do klasy obsługi i implementuje `ILinkedWorkItemExtension`klasy.

    - Parametry wszystkich `Import` i `Export` atrybuty są prawidłowe.

## <a name="about-the-work-item-handler-code"></a>Informacje o kodzie procedury obsługi elementu pracy

### <a name="listening-for-new-work-items"></a>Nasłuchiwanie nowych elementów roboczych
 `OnWorkItemCreated`jest wywoływana, gdy użytkownik zdecyduje się na utworzenie nowego elementu pracy, który ma być połączony z elementami modelu. Kod może inicjować pola elementu pracy. Element roboczy jest następnie prezentowany użytkownikowi, który może zaktualizować pola i zapisać element roboczy. Łącze do elementu modelu nie zostanie utworzone, dopóki element roboczy nie zostanie pomyślnie zapisany.

```
public void OnWorkItemCreated(
    IEnumerable<IElement> elementsToBeLinked,
    IWorkItemDocument workItem)
{
  INamedElement namedElement =
         elementsToBeLinked.First() as INamedElement;
  if (namedElement != null)
      workItem.Item.Title = namedElement.Name;
}
```

### <a name="listening-for-link-creation"></a>Nasłuchiwanie tworzenia linku
 `OnWorkItemLinked`jest wywoływana zaraz po utworzeniu linku. Jest on wywoływany niezależnie od tego, czy łącze jest nowym elementem roboczym czy istniejącym elementem. Jest wywoływana jednokrotnie dla każdego elementu pracy.

```
public void OnWorkItemLinked
        (IEnumerable<IElement> elements,
         string serverUri, // TFS server
         int workItemId)
{
  foreach (IElement element in elements)
    foreach (IShape shape in element.Shapes())
         shape.Color = System.Drawing.Color.Red;
}
```

> [!NOTE]
> Aby ten przykład działał, należy dodać odwołanie do projektu do `System.Drawing.dll`i zaimportować przestrzeń nazw. `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation` Jednak te dodatki nie są wymagane dla innych implementacji programu `OnWorkItemLinked`.

### <a name="listening-for-link-removal"></a>Nasłuchiwanie usunięcia linku
 `OnWorkItemRemoved`jest wywoływana raz tuż przed każdym usuniętym łączem elementu pracy. W przypadku usunięcia elementu modelu wszystkie jego linki zostaną usunięte.

```
public void OnWorkItemRemoved
         (IElement element, string serverUri, int workItemId)
{...}
```

## <a name="updating-a-work-item"></a>Aktualizowanie elementu pracy
 Za pomocą przestrzeni nazw Team Foundation można manipulować elementem roboczym.

 Aby użyć poniższego przykładu, należy dodać te zestawy .NET do odwołań projektu:

- Microsoft.TeamFoundation.Client.dll

- Microsoft.TeamFoundation.WorkItemTracking.Client.dll

```

using Microsoft.TeamFoundation.Client;
using Microsoft.TeamFoundation.WorkItemTracking.Client;
...
public void OnWorkItemLinked
        (IEnumerable<IElement> elements,
         string serverUri, // TFS server
         int workItemId)
{
  TfsTeamProjectCollection tfs =
        TfsTeamProjectCollectionFactory
            .GetTeamProjectCollection(new Uri(serverUri));
  WorkItemStore workItemStore = new WorkItemStore(tfs);
  WorkItem item = workItemStore.GetWorkItem(workItemId);
  item.Open();
  item.Title = "something";
  item.Save();
} 
```

## <a name="accessing-the-work-item-reference-links"></a>Uzyskiwanie dostępu do linków odwołań do elementów roboczych
 Dostęp do linków można uzyskać w następujący sposób:

```
//Get:
string linkString = element.GetReference(ReferenceConstants.WorkItem);
// Set:
element.AddReference(ReferenceConstants.WorkItem, linkString, true);

```

 Format `linkString` jest:

 `string.Format(@"%{0}\{1}#{1}${2}", tfServer, projectCollection, RepositoryGuid, workItem.Id);`

 gdzie:

- Identyfikator URI serwera:

   `http://tfServer:8080/tfs/projectCollection`

   Wielkość liter jest ważna `projectCollection`w temacie.

- `RepositoryGuid`można uzyskać z połączenia TFS:

  ```csharp
  TfsTeamProjectCollection tpc = TfsTeamProjectCollectionFactory...;
  RepositoryGuid= tpc.InstanceId;

  ```

  Aby uzyskać więcej informacji na temat odwołań, zobacz Dołączanie [ciągów odwołania do elementów modelu UML](../modeling/attach-reference-strings-to-uml-model-elements.md).

## <a name="see-also"></a>Zobacz także

- [Microsoft. TeamFoundation. WorkItemTracking. Client. WorkItemStore](/previous-versions/visualstudio/visual-studio-2013/bb179850(v=vs.120))
- [Łączenie elementów modeli i elementów roboczych](../modeling/link-model-elements-and-work-items.md)
- [Dołączanie ciągów odwołania do elementów modelu UML](../modeling/attach-reference-strings-to-uml-model-elements.md)
- [Definiowanie i instalowanie rozszerzenia modelowania](../modeling/define-and-install-a-modeling-extension.md)
- [Programowanie za pomocą interfejsu API UML](../modeling/programming-with-the-uml-api.md)
