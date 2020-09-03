---
title: 'Instrukcje: Dodawanie polecenia do menu skrótów | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
ms.assetid: cd550399-05fc-4dbf-be4c-f5094bb752ce
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2d5ddea477aa7295c41097177265b43483b7aa45
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850418"
---
# <a name="how-to-add-a-command-to-the-shortcut-menu"></a>Porady: dodawanie polecenia do menu skrótów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Polecenia menu można dodać do języka specyficznego dla domeny (DSL), aby użytkownicy mogli wykonywać zadania specyficzne dla DSL. Polecenia pojawiają się w menu kontekstowym (skrót), gdy użytkownik kliknie prawym przyciskiem myszy na diagramie. Można zdefiniować polecenie, aby było wyświetlane tylko w menu w określonych okolicznościach. Można na przykład wykonać polecenie widoczne tylko wtedy, gdy użytkownik kliknie określone typy elementu lub elementy w określonych stanach.

 Podsumowując, kroki są wykonywane w projekcie DslPackage w następujący sposób:

1. [Zadeklaruj polecenie w poleceniach. vsct](#VSCT)

2. [Zaktualizuj numer wersji pakietu w Package.tt](#version). Należy to zrobić za każdym razem, gdy zmienisz polecenie. vsct

3. [Metody zapisu w klasie element CommandSet](#CommandSet) , aby wyświetlić polecenie i zdefiniować, co ma być wykonywane w poleceniu.

   Aby zapoznać się z przykładami, zobacz [witrynę internetową zestawu SDK wizualizacji i modelowania](https://www.visualstudio.com/).

> [!NOTE]
> Możesz również zmodyfikować zachowanie niektórych istniejących poleceń, takich jak Wytnij, wklej, zaznacz wszystko i Drukuj przez zastępowanie metod w CommandSet.cs. Aby uzyskać więcej informacji, zobacz [How to: Modify a standardowe polecenie menu](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

## <a name="defining-a-command-using-mef"></a>Definiowanie polecenia przy użyciu MEF
 Managed Extension Framework (MEF) oferuje alternatywną metodę definiowania poleceń menu w menu Diagram. Jej podstawowym celem jest umożliwienie przedłużonia przez użytkownika lub innych stron poziomu DSL. Użytkownicy mogą zdecydować się na zainstalowanie tylko DSL lub zainstalować zarówno DSL, jak i rozszerzenia. Jednak MEF zmniejsza również nakład pracy definiowania poleceń menu skrótów po początkowej pracy, aby włączyć MEF na DSL.

 Użyj metody w tym temacie, jeśli:

1. Chcesz definiować polecenia menu w menu innym niż menu skrótów kliknij prawym przyciskiem myszy.

2. Chcesz zdefiniować określone grupowania poleceń w menu.

3. Nie chcesz zezwolić innym osobom na rozciągnięcie DSL z własnymi poleceniami.

4. Należy zdefiniować tylko jedno polecenie.

   W przeciwnym razie Rozważ użycie metody MEF w celu zdefiniowania poleceń. Aby uzyskać więcej informacji, zobacz sekcję "Rozpoznaj [swój DSL" przy użyciu MEF](../modeling/extend-your-dsl-by-using-mef.md).

## <a name="declare-the-command-in-commandsvsct"></a><a name="VSCT"></a> Zadeklaruj polecenie w poleceniach. vsct
 Polecenia menu są zadeklarowane w DslPackage\Commands.vsct. Te definicje określają etykiety elementów menu i miejsca, w których są wyświetlane w menu.

 Plik, który edytujesz, Commands. vsct, Importuje definicje z kilku plików. h, które znajdują się w katalogu *Visual Studio SDK ścieżka instalacji*\VisualStudioIntegration\Common\Inc. Zawiera również GeneratedVsct. vsct, który jest generowany na podstawie definicji DSL.

 Aby uzyskać więcej informacji na temat plików. vsct, zobacz [Visual Studio Command Table (. Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

#### <a name="to-add-the-command"></a>Aby dodać polecenie

1. W **Eksplorator rozwiązań**w projekcie **DslPackage** Otwórz polecenie Commands. vsct.

2. W `Commands` elemencie Zdefiniuj jeden lub więcej przycisków i grupę. *Przycisk* jest elementem menu. *Grupa* jest sekcją w menu. Aby zdefiniować te elementy, Dodaj następujące elementy:

    ```
    <!-- Define a group - a section in the menu -->
    <Groups>
      <Group guid="guidCustomMenuCmdSet" id="grpidMyMenuGroup" priority="0x0100">
        <!-- These symbols are defined in GeneratedVSCT.vsct -->
        <Parent guid="guidCmdSet" id="menuidContext" />
      </Group>
    </Groups>
    <!-- Define a button - a menu item - inside the Group -->
    <Buttons>
      <Button guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"
        priority="0x0100" type="Button">
        <Parent guid="guidCustomMenuCmdSet" id="grpidMyMenuGroup"/>
        <!-- If you do not want to place the command in your own Group,
             use Parent guid="guidCmdSet" id="grpidContextMain".
             These symbols are defined in GeneratedVSCT.vsct -->
        <CommandFlag>DynamicVisibility</CommandFlag>
        <Strings>
          <ButtonText>My Context Menu Command</ButtonText>
        </Strings>
      </Button>
    </Buttons>
    ```

    > [!NOTE]
    > Każdy przycisk lub grupa są identyfikowane za pomocą identyfikatora GUID i identyfikatora w postaci liczby całkowitej. Można utworzyć kilka grup i przycisków z tym samym identyfikatorem GUID. Jednak muszą mieć różne identyfikatory. Nazwy i nazwy identyfikatorów GUID są tłumaczone na rzeczywiste identyfikatory GUID i identyfikatory liczbowe w `<Symbols>` węźle.

3. Dodaj ograniczenie widoczności dla polecenia, aby było ładowane tylko w kontekście języka specyficznego dla domeny. Aby uzyskać więcej informacji, zobacz [VisibilityConstraints Element](../extensibility/visibilityconstraints-element.md).

     Aby to zrobić, Dodaj następujące elementy w `CommandTable` elemencie po `Commands` elemencie.

    ```
    <VisibilityConstraints>
      <!-- Ensures the command is only loaded for this DSL -->
      <VisibilityItem guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"
        context="guidEditor"/>
    </VisibilityConstraints>
    ```

4. Zdefiniuj nazwy używane dla identyfikatorów GUID i identyfikator. Aby to zrobić, Dodaj `Symbols` element do `CommandTable` elementu po `Commands` elemencie.

    ```
    <Symbols>
      <!-- Substitute a unique GUID for the placeholder: -->
      <GuidSymbol name="guidCustomMenuCmdSet"
        value="{00000000-0000-0000-0000-000000000000}" >
        <IDSymbol name="grpidMyMenuGroup" value="0x01001"/>
        <IDSymbol name="cmdidMyContextMenuCommand" value="0x00001"/>
      </GuidSymbol>
    </Symbols>
    ```

5. Zamień na `{000...000}` Identyfikator GUID, który identyfikuje grupy i elementy menu. Aby uzyskać nowy identyfikator GUID, użyj narzędzia **Tworzenie identyfikatora GUID** w menu **Narzędzia** .

    > [!NOTE]
    > Jeśli dodasz więcej grup lub elementów menu, możesz użyć tego samego identyfikatora GUID. Należy jednak użyć nowych wartości dla `IDSymbols` .

6. W kodzie skopiowanym z tej procedury Zastąp każde wystąpienie następujących ciągów własnymi ciągami:

    - `grpidMyMenuGroup`

    - `cmdidMyContextMenuCommand`

    - `guidCustomMenuCmdSet`

    - `My Context Menu Command`

## <a name="update-the-package-version-in-packagett"></a><a name="version"></a> Aktualizowanie wersji pakietu w programie Package.tt
 Za każdym razem, gdy dodasz lub zmienisz polecenie, zaktualizuj `version` parametr, <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> który jest stosowany do klasy pakietu przed wydaniem nowej wersji języka specyficznego dla domeny.

 Ponieważ Klasa pakietu jest zdefiniowana w wygenerowanym pliku, zaktualizuj atrybut w pliku szablonu tekstu, który generuje plik Package.cs.

#### <a name="to-update-the-packagett-file"></a>Aby zaktualizować plik Package.tt

1. W **Eksplorator rozwiązań**w projekcie **DslPackage** w folderze **GeneratedCode** Otwórz plik Package.tt.

2. Znajdź `ProvideMenuResource` atrybut.

3. Zwiększ `version` parametr atrybutu, który jest drugim parametrem. Jeśli chcesz, możesz jawnie napisać nazwę parametru, aby przypominać o swoim przeznaczeniu. Na przykład:

     `[VSShell::ProvideMenuResource("1000.ctmenu", version: 2 )]`

## <a name="define-the-behavior-of-the-command"></a><a name="CommandSet"></a> Zdefiniuj zachowanie polecenia
 Twoje DSL ma już kilka poleceń, które są zaimplementowane w klasie częściowej zadeklarowanej w DslPackage\GeneratedCode\CommandSet.cs. Aby dodać nowe polecenia, należy ją rozwinąć, tworząc nowy plik, który zawiera częściową deklarację tej samej klasy. Nazwa klasy jest zwykle *\<YourDslName>* `CommandSet` . Warto zacząć od zweryfikowania nazwy klasy i sprawdzenia jej zawartości.

 Klasa zestawu poleceń pochodzi od <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> .

#### <a name="to-extend-the-commandset-class"></a>Aby zwiększyć klasę element CommandSet

1. W Eksplorator rozwiązań w projekcie DslPackage Otwórz folder GeneratedCode, a następnie poszukaj w obszarze CommandSet.tt i otwórz jego wygenerowany plik CommandSet.cs. Zanotuj przestrzeń nazw i nazwę pierwszej klasy, która jest tam zdefiniowana. Na przykład można zobaczyć:

     `namespace Company.Language1`

     `{ ...  internal partial class Language1CommandSet : ...`

2. W **DslPackage**Utwórz folder o nazwie **kod niestandardowy**. W tym folderze Utwórz nowy plik klasy o nazwie `CommandSet.cs` .

3. W nowym pliku Napisz deklarację częściową, która ma taką samą przestrzeń nazw i nazwę jak wygenerowana Klasa częściowa. Na przykład:

     `namespace Company.Language1 /* Make sure this is correct */`

     `{ internal partial class Language1CommandSet { ...`

     **Uwaga** Jeśli do utworzenia nowego pliku użyto szablonu klasy, należy poprawić zarówno przestrzeń nazw, jak i nazwę klasy.

### <a name="extend-the-command-set-class"></a>Rozwiń klasę zestawu poleceń
 Kod zestawu poleceń zazwyczaj będzie wymagał importu następujących przestrzeni nazw:

```
using System;
using System.Collections.Generic;
using System.ComponentModel.Design;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Shell;
```

 Dostosuj przestrzeń nazw i nazwę klasy, aby były zgodne z wygenerowanymi CommandSet.cs:

```
namespace Company.Language1 /* Make sure this is correct */
{
  // Same class as the generated class.
  internal partial class Language1CommandSet
  {
```

 Musisz zdefiniować dwie metody, jeden, aby określić, kiedy polecenie będzie widoczne w menu kontekstowym, a drugie, aby wykonać polecenie. Te metody nie są zastępują zastąpień; Zamiast tego rejestruje się je na liście poleceń.

### <a name="define-when-the-command-will-be-visible"></a>Zdefiniuj, kiedy polecenie będzie widoczne
 Dla każdego polecenia Zdefiniuj metodę, `OnStatus...` która określa, czy polecenie pojawi się w menu, oraz czy zostanie włączone lub wyszarzone. Ustaw `Visible` właściwości i `Enabled` `MenuCommand` , jak pokazano w poniższym przykładzie. Ta metoda jest wywoływana w celu skonstruowania menu skrótów za każdym razem, gdy użytkownik kliknie prawym przyciskiem myszy diagram, dzięki czemu musi on szybko rozpocząć pracę.

 W tym przykładzie polecenie jest widoczne tylko wtedy, gdy użytkownik wybrał określony typ kształtu i jest włączone tylko wtedy, gdy co najmniej jeden z wybranych elementów jest w określonym stanie. Przykład jest oparty na szablonie diagramu DSL, a ClassShape i ModelClass są typami, które są zdefiniowane w DSL:

```
private void OnStatusMyContextMenuCommand(object sender, EventArgs e)
{
  MenuCommand command = sender as MenuCommand;
  command.Visible = command.Enabled = false;
  foreach (object selectedObject in this.CurrentSelection)
  {
    ClassShape shape = selectedObject as ClassShape;
    if (shape != null)
    {
      // Visibility depends on what is selected.
      command.Visible = true;
      ModelClass element = shape.ModelElement as ModelClass;
      // Enabled depends on state of selection.
      if (element != null && element.Comments.Count == 0)
      {
        command.Enabled = true;
        return; // seen enough
} } } }
```

 Następujące fragmenty są często przydatne w metodach OnStatus:

- `this.CurrentSelection`. Kształt, który kliknięto prawym przyciskiem myszy, jest zawsze uwzględniony na tej liście. Jeśli użytkownik kliknie pustą część diagramu, diagram jest jedyną składową listy.

- `this.IsDiagramSelected()` - `true` Jeśli użytkownik kliknął pustą część diagramu.

- `this.IsCurrentDiagramEmpty()`

- `this.IsSingleSelection()` -Użytkownik nie wybrał wielu obiektów

- `this.SingleSelection` -kształt lub diagram, który kliknął użytkownik prawym przyciskiem myszy.

- `shape.ModelElement as MyLanguageElement` — element modelu reprezentowany przez kształt.

  Ogólnie rzecz biorąc, ustaw `Visible` Właściwość zależnie od tego, co jest zaznaczone, i ustaw `Enabled` Właściwość zależnie od stanu wybranych elementów.

  Metoda OnStatus nie powinna zmieniać stanu magazynu.

### <a name="define-what-the-command-does"></a>Zdefiniuj działanie polecenia
 Dla każdego polecenia Zdefiniuj `OnMenu...` metodę, która wykonuje wymaganą akcję, gdy użytkownik kliknie polecenie menu.

 W przypadku wprowadzania zmian do elementów modelu należy to zrobić wewnątrz transakcji. Aby uzyskać więcej informacji, zobacz [How to: Modify a standardowe polecenie menu](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

 W tym przykładzie, `ClassShape` , `ModelClass` i `Comment` są typami, które są zdefiniowane w DSL, które są uzyskiwane z szablonu klasy diagramu DSL.

```
private void OnMenuMyContextMenuCommand(object sender, EventArgs e)
{
  MenuCommand command = sender as MenuCommand;
  Store store = this.CurrentDocData.Store;
  // Changes to elements and shapes must be performed in a Transaction.
  using (Transaction transaction =
       store.TransactionManager.BeginTransaction("My command"))
  {
    foreach (object selectedObject in this.CurrentSelection)
    {
      // ClassShape is defined in my DSL.
      ClassShape shape = selectedObject as ClassShape;
      if (shape != null)
      {
        // ModelClass is defined in my DSL.
        ModelClass element = shape.ModelElement as ModelClass;
        if (element != null)
        {
          // Do required action here - for example:

          // Create a new element. Comment is defined in my DSL.
          Comment newComment = new Comment(element.Partition);
          // Every element must be the target of an embedding link.
          element.ModelRoot.Comments.Add(newComment);
          // Set properties of new element.
          newComment.Text = "This is a comment";
          // Create a reference link to existing object.
          element.Comments.Add(newComment);
        }
      }
    }
    transaction.Commit(); // Don't forget this!
  }
}
```

 Aby uzyskać więcej informacji na temat sposobu nawigowania z obiektu do obiektu w modelu i informacje o sposobie tworzenia obiektów i linków, zobacz [How to: Modify a standardowe polecenie menu](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

### <a name="register-the-command"></a>Zarejestruj polecenie
 Powtarzaj w języku C# deklaracje identyfikatora GUID i wartości identyfikatora, które zostały wprowadzone w sekcji symboli w element CommandSet. vsct:

```
private Guid guidCustomMenuCmdSet =
    new Guid("00000000-0000-0000-0000-000000000000");
private const int grpidMyMenuGroup = 0x01001;
private const int cmdidMyContextMenuCommand = 1;
```

 Użyj tej samej wartości identyfikatora GUID, która została wstawiona w **Commands. vsct**.

> [!NOTE]
> Jeśli zmienisz sekcję symboli pliku VSCT, musisz również zmienić te deklaracje tak, aby były zgodne. Należy również zwiększyć numer wersji w Package.tt

 Zarejestruj polecenia menu w ramach tego zestawu poleceń. `GetMenuCommands()` jest wywoływana jednokrotnie po zainicjowaniu diagramu:

```
protected override IList<MenuCommand> GetMenuCommands()
{
  // Get the list of generated commands.
  IList<MenuCommand> commands = base.GetMenuCommands();
  // Add a custom command:
  DynamicStatusMenuCommand myContextMenuCommand =
    new DynamicStatusMenuCommand(
      new EventHandler(OnStatusMyContextMenuCommand),
      new EventHandler(OnMenuMyContextMenuCommand),
      new CommandID(guidCustomMenuCmdSet, cmdidMyContextMenuCommand));
  commands.Add(myContextMenuCommand);
  // Add more commands here.
  return commands;
}
```

## <a name="test-the-command"></a>Przetestuj polecenie
 Kompiluj i uruchamiaj DSL w eksperymentalnym wystąpieniu programu Visual Studio. Polecenie powinno pojawić się w menu skrótów w określonych sytuacjach.

#### <a name="to-exercise-the-command"></a>Aby wykonać polecenie

1. Na pasku narzędzi **Eksplorator rozwiązań** kliknij pozycję **Przekształć wszystkie szablony**.

2. Naciśnij klawisz **F5** , aby skompilować ponownie rozwiązanie i rozpocząć debugowanie języka specyficznego dla domeny w kompilacji eksperymentalnej.

3. W przypadku kompilacji eksperymentalnej Otwórz przykładowy diagram.

4. Kliknij prawym przyciskiem myszy różne elementy na diagramie, aby sprawdzić, czy polecenie jest prawidłowo włączone lub wyłączone, i odpowiednio wyświetlane lub ukryte, w zależności od wybranego elementu.

## <a name="troubleshooting"></a>Rozwiązywanie problemów
 **Polecenie nie jest wyświetlane w menu:**

- Polecenie będzie wyświetlane tylko w przypadku debugowania wystąpień programu Visual Studio, dopóki nie zostanie zainstalowany pakiet DSL. Aby uzyskać więcej informacji, zobacz [wdrażanie rozwiązań językowych właściwych dla domeny](../modeling/deploying-domain-specific-language-solutions.md).

- Upewnij się, że próbka eksperymentalna ma poprawne rozszerzenie nazwy pliku dla tego języka DSL. Aby sprawdzić rozszerzenie nazwy pliku, Otwórz DslDefinition. DSL w głównym wystąpieniu programu Visual Studio. Następnie w Eksploratorze DSL kliknij prawym przyciskiem myszy węzeł Edytor, a następnie kliknij polecenie Właściwości. W okno Właściwości, zapoznaj się z właściwością FileExtension.

- Czy [numer wersji pakietu został zwiększony](#version)?

- Ustaw punkt przerwania na początku metody OnStatus. Po kliknięciu prawym przyciskiem myszy dowolnej części diagramu powinna zostać przerwana.

   **Metoda OnStatus nie jest wywoływana**:

  - Upewnij się, że identyfikatory GUID i identyfikator w kodzie element CommandSet pasują do nazw w sekcji symboli poleceń. vsct.

  - W polecenie Commands. vsct upewnij się, że identyfikatory GUID i ID w każdym węźle nadrzędnym identyfikują poprawną grupę nadrzędną.

  - W wierszu polecenia programu Visual Studio wpisz devenv/rootsuffix Exp/Setup. Następnie uruchom ponownie wystąpienie debugowania programu Visual Studio.

- Przejdź przez metodę OnStatus, aby sprawdzić, czy polecenie. Visible i polecenie. Wartość Enabled jest ustawiona na true.

  **Pojawia się nieprawidłowy tekst menu lub polecenie pojawia się w niewłaściwym miejscu**:

- Upewnij się, że kombinacja identyfikatorów GUID i ID jest unikatowa dla tego polecenia.

- Upewnij się, że zostały odinstalowane wcześniejsze wersje pakietu.

## <a name="see-also"></a>Zobacz też
 [Pisanie kodu w celu dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md) [: modyfikowanie standardowego polecenia menu](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md) [wdrażanie rozwiązań językowych właściwych dla domeny](../modeling/deploying-domain-specific-language-solutions.md)
