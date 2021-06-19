---
title: 'Szybki start: dodawanie polecenia do menu skrótów'
description: Dowiedz się, jak dodać polecenia menu do języka specyficznego dla domeny (DSL), aby użytkownicy mogą wykonywać zadania specyficzne dla dsl.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4b578c949b3b5121eb90b2c034766ea15ae6d096
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386569"
---
# <a name="how-to-add-a-command-to-the-shortcut-menu"></a>Szybki start: dodawanie polecenia do menu skrótów

Można dodać polecenia menu do języka specyficznego dla domeny (DSL), aby użytkownicy mogą wykonywać zadania, które są specyficzne dla DSL. Polecenia są wyświetlane w menu kontekstowym (skrótowym), gdy użytkownicy klikną diagram prawym przyciskiem myszy. Polecenie można zdefiniować tak, aby było wyświetlane tylko w menu w określonych okolicznościach. Na przykład polecenie można ustawić jako widoczne tylko wtedy, gdy użytkownik kliknie określone typy elementów lub elementy w określonych stanach.

Podsumowując, kroki są wykonywane w projekcie DslPackage w następujący sposób:

1. [Zadeklaruj polecenie w programie Commands.vsct](#VSCT)

2. [Zaktualizuj numer wersji pakietu w Package.tt](#version). Należy to zrobić za każdym razem, gdy zmieniasz polecenie Commands.vsct

3. [Napisz metody w klasie CommandSet,](#CommandSet) aby polecenie było widoczne i aby zdefiniować, co ma robić polecenie.

> [!NOTE]
> Możesz również zmodyfikować zachowanie niektórych istniejących poleceń, takich jak Wytnij, Wklej, Zaznacz wszystko i Drukuj, przesłaniając metody w pliku CommandSet.cs. Aby uzyskać więcej informacji, zobacz How to: Modify a Standard Menu Command ( 2. [3. 3. Aby](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)uzyskać więcej informacji, zobacz Temat How to: Modify a Standard Menu Command ).

## <a name="define-a-command-using-mef"></a>Definiowanie polecenia przy użyciu mef

Managed Extension Framework (MEF) to alternatywna metoda definiowania poleceń menu w menu diagramu. Jej głównym celem jest umożliwienie DSL być rozszerzone przez Ciebie lub przez inne strony. Użytkownicy mogą zainstalować tylko DSL lub zainstalować zarówno DSL, jak i rozszerzenia. Jednak MEF zmniejsza również pracy definiowania poleceń menu skrótów, po początkowej pracy, aby włączyć MEF na DSL.

Użyj metody w tym temacie, jeśli:

1. Chcesz zdefiniować polecenia menu w menu innym niż menu skrótów po kliknięciu prawym przyciskiem myszy.

2. Chcesz zdefiniować określone grupy poleceń w menu.

3. Nie chcesz, aby inne osoby rozszerzały DSL za pomocą własnych poleceń.

4. Chcesz zdefiniować tylko jedno polecenie.

   W przeciwnym razie rozważ użycie metody MEF do definiowania poleceń. Aby uzyskać więcej informacji, zobacz [Rozszerzanie DSL przy użyciu MEF](../modeling/extend-your-dsl-by-using-mef.md).

## <a name="declare-the-command-in-commandsvsct"></a><a name="VSCT"></a> Deklarowanie polecenia w poleceniu Commands.Vsct
 Polecenia menu są deklarowane w dslPackage\Commands.vsct. Definicje te określają etykiety elementów menu i miejsce ich pojawiania się w menu.

 Edytowany plik Commands.vsct importuje definicje z kilku plików h, które znajdują się w katalogu *Visual Studio SDK* ścieżka instalacji \VisualStudioIntegration\Common\Inc. Zawiera również generatedVsct.vsct, który jest generowany na podstawie definicji DSL.

 Aby uzyskać więcej informacji na temat plików vsct, [zobacz Visual Studio Command Table (. Vsct) Pliki](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

### <a name="to-add-the-command"></a>Aby dodać polecenie

1. W **Eksplorator rozwiązań** w **projekcie DslPackage** otwórz program Commands.vsct.

2. W `Commands` elemencie zdefiniuj co najmniej jeden przycisk i grupę. Przycisk *jest* elementem w menu. Grupa *to* sekcja w menu. Aby zdefiniować te elementy, dodaj następujące elementy:

    ```xml
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
    > Każdy przycisk lub grupa jest identyfikowany za pomocą identyfikatora GUID i identyfikatora liczby całkowitej. Można utworzyć kilka grup i przycisków o tym samym identyfikatorze GUID. Muszą jednak mieć różne identyfikatory. Nazwy identyfikatorów GUID i ID są tłumaczone na rzeczywiste identyfikatory GUID i numeryczne identyfikatory w `<Symbols>` węźle.

3. Dodaj ograniczenie widoczności dla polecenia, aby było ładowane tylko w kontekście języka specyficznego dla domeny. Aby uzyskać więcej informacji, zobacz [VisibilityConstraints, element](../extensibility/visibilityconstraints-element.md).

     Aby to zrobić, dodaj następujące elementy w `CommandTable` elemencie po `Commands` elemencie .

    ```xml
    <VisibilityConstraints>
      <!-- Ensures the command is only loaded for this DSL -->
      <VisibilityItem guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"
        context="guidEditor"/>
    </VisibilityConstraints>
    ```

4. Zdefiniuj nazwy identyfikatorów GUID i IDENTYFIKATORów, które zostały użyte. Aby to zrobić, dodaj `Symbols` element w `CommandTable` elemencie po `Commands` elemencie .

    ```xml
    <Symbols>
      <!-- Substitute a unique GUID for the placeholder: -->
      <GuidSymbol name="guidCustomMenuCmdSet"
        value="{00000000-0000-0000-0000-000000000000}" >
        <IDSymbol name="grpidMyMenuGroup" value="0x01001"/>
        <IDSymbol name="cmdidMyContextMenuCommand" value="0x00001"/>
      </GuidSymbol>
    </Symbols>
    ```

5. Zastąp `{000...000}` element identyfikatorem GUID, który identyfikuje grupy i elementy menu. Aby uzyskać nowy identyfikator GUID, użyj narzędzia Create GUID (Utwórz **identyfikator GUID)** w menu **Tools (Narzędzia).**

    > [!NOTE]
    > Jeśli dodasz więcej grup lub elementów menu, możesz użyć tego samego identyfikatora GUID. Należy jednak użyć nowych wartości dla `IDSymbols` .

6. W kodzie skopiowanym z tej procedury zastąp każde wystąpienie następujących ciągów własnymi ciągami:

    - `grpidMyMenuGroup`

    - `cmdidMyContextMenuCommand`

    - `guidCustomMenuCmdSet`

    - `My Context Menu Command`

## <a name="update-the-package-version-in-packagett"></a><a name="version"></a> Aktualizowanie wersji pakietu w programie Package.tt
 Za każdym razem, gdy dodajesz lub zmieniasz polecenie, aktualizuj parametr klasy , który jest stosowany do klasy pakietu, przed wydaniem nowej wersji języka `version` <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> specyficznego dla domeny.

 Ponieważ klasa pakietu jest zdefiniowana w wygenerowanym pliku, zaktualizuj atrybut w pliku szablonu tekstowego, który generuje plik Package.cs.

### <a name="to-update-the-packagett-file"></a>Aby zaktualizować Package.tt plik

1. W **Eksplorator rozwiązań** pliku w **projekcie DslPackage** otwórz plik Package.tt **GeneratedCode.**

2. Znajdź `ProvideMenuResource` atrybut .

3. Zwiększa `version` parametr atrybutu, który jest drugim parametrem. Jeśli chcesz, możesz jawnie zapisać nazwę parametru, aby przypominać o jego przeznacie. Na przykład:

     `[VSShell::ProvideMenuResource("1000.ctmenu", version: 2 )]`

## <a name="define-the-behavior-of-the-command"></a><a name="CommandSet"></a> Definiowanie zachowania polecenia

Dsl ma już kilka poleceń, które są implementowane w klasie częściowej, która jest zadeklarowana w DslPackage\GeneratedCode\CommandSet.cs. Aby dodać nowe polecenia, należy rozszerzyć tę klasę, tworząc nowy plik zawierający częściową deklarację tej samej klasy. Nazwa klasy to zwykle *\<YourDslName>* `CommandSet` . Warto rozpocząć od zweryfikowania nazwy klasy i sprawdzenia jej zawartości.

Klasa zestawu poleceń pochodzi z <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> klasy .

### <a name="extend-the-commandset-class"></a>Rozszerzanie klasy CommandSet

1. W Eksplorator rozwiązań projektu DslPackage otwórz folder GeneratedCode, a następnie w obszarze CommandSet.tt otwórz wygenerowany plik CommandSet.cs. Zanotuj przestrzeń nazw i nazwę pierwszej klasy, która jest tam zdefiniowana. Możesz na przykład zobaczyć:

     `namespace Company.Language1`

     `{ ...  internal partial class Language1CommandSet : ...`

2. W **pliku DslPackage** utwórz folder o nazwie **Kod niestandardowy**. W tym folderze utwórz nowy plik klasy o nazwie `CommandSet.cs` .

3. W nowym pliku napisz deklarację częściową, która ma taką samą przestrzeń nazw i nazwę jak wygenerowana klasa częściowa. Na przykład:

     `namespace Company.Language1 /* Make sure this is correct */`

     `{ internal partial class Language1CommandSet { ...`

     > [!NOTE]
     > Jeśli do utworzenia nowego pliku został użyty szablon klasy, należy poprawić zarówno przestrzeń nazw, jak i nazwę klasy.

Kod zestawu poleceń zazwyczaj wymaga zaimportowania następujących przestrzeni nazw:

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel.Design;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Shell;
```

Dostosuj przestrzeń nazw i nazwę klasy tak, aby były zgodne z nazwami w wygenerowanym pliku CommandSet.cs:

```csharp
namespace Company.Language1 /* Make sure this is correct */
{
  // Same class as the generated class.
  internal partial class Language1CommandSet
  {
```

Należy zdefiniować dwie metody— jedną, aby określić, kiedy polecenie będzie widoczne w menu kontekstowym (kontekstowym) prawym przyciskiem myszy, a drugą w celu wykonania polecenia. Te metody nie są przesłonięciami; Zamiast tego należy zarejestrować je na liście poleceń.

### <a name="define-when-the-command-will-be-visible"></a>Definiowanie, kiedy polecenie będzie widoczne
 Dla każdego polecenia zdefiniuj metodę, która określa, czy polecenie będzie wyświetlane w menu oraz czy będzie włączone, `OnStatus...` czy wyszazone. Ustaw właściwości `Visible` i obiektu , jak `Enabled` `MenuCommand` pokazano w poniższym przykładzie. Ta metoda jest wywoływana w celu skonstruowania menu skrótów za każdym razem, gdy użytkownik kliknie diagram prawym przyciskiem myszy, więc musi działać szybko.

 W tym przykładzie polecenie jest widoczne tylko wtedy, gdy użytkownik wybrał określony typ kształtu i jest włączone tylko wtedy, gdy co najmniej jeden z wybranych elementów jest w określonym stanie. Przykład jest oparty na szablonie DSL diagramu klas, a ClassShape i ModelClass są typami, które są zdefiniowane w DSL:

```csharp
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

- `this.CurrentSelection`. Kształt, który użytkownik kliknął prawym przyciskiem myszy, jest zawsze uwzględniony na tej liście. Jeśli użytkownik kliknie pustą część diagramu, diagram jest jedynym elementem członkowskim listy.

- `this.IsDiagramSelected()` - `true` jeśli użytkownik kliknął pustą część diagramu.

- `this.IsCurrentDiagramEmpty()`

- `this.IsSingleSelection()` — użytkownik nie zaznaczył wielu obiektów

- `this.SingleSelection` — kształt lub diagram klikony prawym przyciskiem myszy przez użytkownika

- `shape.ModelElement as MyLanguageElement` — element modelu reprezentowany przez kształt.

Zgodnie z ogólną wyątką należy sprawić, że właściwość będzie zależeć od tego, co jest zaznaczone, i sprawić, że właściwość będzie zależeć `Visible` `Enabled` od stanu wybranych elementów.

Metoda OnStatus nie powinna zmieniać stanu magazynu.

### <a name="define-what-the-command-does"></a>Definiowanie, do czego służy polecenie
 Dla każdego polecenia zdefiniuj `OnMenu...` metodę, która wykonuje wymaganą akcję, gdy użytkownik kliknie polecenie menu.

 Jeśli wprowadzasz zmiany w elementach modelu, należy to zrobić w ramach transakcji. Aby uzyskać więcej informacji, zobacz How to: Modify a Standard Menu Command ( 2. [3. 3. Aby](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)uzyskać więcej informacji, zobacz Temat How to: Modify a Standard Menu Command ).

 W tym przykładzie , i są typy, które są zdefiniowane w DSL, który pochodzi od szablonu `ClassShape` `ModelClass` DSL `Comment` diagramu klasy.

```csharp
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

 Aby uzyskać więcej informacji na temat nawigowania z obiektu do obiektu w modelu oraz o tworzeniu obiektów i linków, zobacz How [to: Modify a Standard Menu Command](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

### <a name="register-the-command"></a>Rejestrowanie polecenia
 Powtórz w języku C# deklaracje wartości identyfikatora GUID i ID, które zostały wprowadzone w sekcji Symbole w commandSet.vsct:

```csharp
private Guid guidCustomMenuCmdSet =
    new Guid("00000000-0000-0000-0000-000000000000");
private const int grpidMyMenuGroup = 0x01001;
private const int cmdidMyContextMenuCommand = 1;
```

 Użyj tej samej wartości identyfikatora GUID, która zostanie wstawiona w **stosunku do polecenia Commands.vsct.**

> [!NOTE]
> Jeśli zmienisz sekcję Symbole w pliku VSCT, musisz również zmienić te deklaracje, aby były zgodne. Należy również zwiększyć numer wersji w Package.tt

 Zarejestruj polecenia menu w ramach tego zestawu poleceń. `GetMenuCommands()` Jest wywoływana raz podczas inicjowania diagramu:

```csharp
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

## <a name="test-the-command"></a>Testowanie polecenia
 Kompilowanie i uruchamianie DSL w eksperymentalnym wystąpieniu Visual Studio. Polecenie powinno pojawić się w menu skrótów w określonych sytuacjach.

### <a name="to-exercise-the-command"></a>Aby skorzystać z polecenia

1. Na pasku **Eksplorator rozwiązań** kliknij pozycję **Przekształć wszystkie szablony.**

2. Naciśnij **klawisz F5,** aby ponownie skompilować rozwiązanie, i rozpocznij debugowanie języka specyficznego dla domeny w eksperymentalnej kompilacji.

3. W kompilacji eksperymentalnej otwórz przykładowy diagram.

4. Kliknij prawym przyciskiem myszy różne elementy na diagramie, aby sprawdzić, czy polecenie jest poprawnie włączone lub wyłączone oraz odpowiednio wyświetlane lub ukryte w zależności od wybranego elementu.

## <a name="troubleshoot"></a>Rozwiązywanie problemów

**Polecenie nie jest wyświetlane w menu:**

- Polecenie będzie wyświetlane tylko w wystąpieniach debugowania Visual Studio, dopóki nie zainstalujesz pakietu DSL. Aby uzyskać więcej informacji, zobacz [Deploying Domain-Specific Language Solutions](msi-and-vsix-deployment-of-a-dsl.md).

- Upewnij się, że przykład eksperymentalny ma poprawne rozszerzenie nazwy pliku dla tego DSL. Aby sprawdzić rozszerzenie nazwy pliku, otwórz plik DslDefinition.dsl w głównym wystąpieniu Visual Studio. Następnie w Eksploratorze DSL kliknij prawym przyciskiem myszy węzeł Edytor, a następnie kliknij pozycję Właściwości. W okno Właściwości sprawdź właściwość FileExtension.

- Czy numer [wersji pakietu został zwiększany?](#version)

- Ustaw punkt przerwania na początku metody OnStatus. Po kliknięciu prawym przyciskiem myszy dowolnej części diagramu powinno się to przerwać.

**Metoda OnStatus nie jest nazywana**:

- Upewnij się, że identyfikatory GUID i IDENTYFIKATORY w kodzie CommandSet są zgodne z identyfikatorami w sekcji Symbole w stosunku do polecenia Commands.vsct.

- W programie Commands.vsct upewnij się, że identyfikator GUID i identyfikator w każdym węźle nadrzędnym identyfikują prawidłową grupę nadrzędną.

- W wierszu Visual Studio wpisz devenv /rootsuffix exp /setup. Następnie uruchom ponownie wystąpienie debugowania Visual Studio.

- Aby zweryfikować to polecenie, należy przejść przez metodę OnStatus. Widoczne i polecenia. Dla opcji Włączone ustawiono wartość true.

Zostanie wyświetlony nieprawidłowy tekst menu lub **polecenie zostanie wyświetlone w niewłaściwym miejscu:**

- Upewnij się, że kombinacja identyfikatora GUID i identyfikatora jest unikatowa dla tego polecenia.

- Upewnij się, że zostały odinstalowane wcześniejsze wersje pakietu.

## <a name="see-also"></a>Zobacz też

- [Pisanie kodu w celu dostosowania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [2. Modyfikowanie standardowego polecenia menu](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)
- [Wdrażanie rozwiązań językowych specyficznych dla domeny](msi-and-vsix-deployment-of-a-dsl.md)
- [Przykładowy kod: Diagramy obwodów](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
