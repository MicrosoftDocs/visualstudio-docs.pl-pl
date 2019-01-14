---
title: 'Instrukcje: Dodawanie polecenia do menu skrótów'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: a415657c86f6f4a6f54ce4273e49ad6302ae77b4
ms.sourcegitcommit: 38db86369af19e174b0aba59ba1918a5c4fe4a61
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2019
ms.locfileid: "54270038"
---
# <a name="how-to-add-a-command-to-the-shortcut-menu"></a>Instrukcje: Dodawanie polecenia do menu skrótów

Polecenia menu można dodać do języka specyficznego dla domeny (DSL), dzięki czemu użytkownicy mogą wykonywać zadania, które są specyficzne dla DSL. Polecenia są wyświetlane w menu kontekstowym (skrót), po kliknięciu prawym przyciskiem myszy na diagramie. Polecenie może zdefiniować i pojawia się tylko w menu w określonych okolicznościach. Na przykład możesz można uwidocznić polecenia tylko wtedy, gdy użytkownik kliknie określonych typów elementu lub elementów w określone stany.

Podsumowując czynności są wykonywane w projekcie DslPackage w następujący sposób:

1. [Zadeklaruj polecenie w Commands.vsct](#VSCT)

2. [Zaktualizuj numer wersji pakietu w Package.tt](#version). Trzeba to zrobić, po każdym wprowadzeniu zmiany Commands.vsct

3. [Pisanie metod w klasie element CommandSet](#CommandSet) aby uwidocznić polecenia i aby zdefiniować, co chcesz wykonać polecenie.

   Aby uzyskać przykłady, zobacz [wizualizacji i modelowania SDK witryny sieci Web](http://go.microsoft.com/fwlink/?LinkID=185579).

> [!NOTE]
> Można również zmodyfikować zachowanie niektórych istniejących poleceń, takich jak Wytnij, Wklej, zaznacz wszystko i drukowania, poprzez zastąpienie metody CommandSet.cs. Aby uzyskać więcej informacji, zobacz [jak: Modyfikowanie standardowego polecenia Menu](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

## <a name="define-a-command-using-mef"></a>Definiowanie polecenia za pomocą MEF

Zarządzane rozszerzenia Framework (MEF) zapewnia alternatywny sposób definiowania polecenia menu w menu diagramu. Ich głównym celem jest umożliwiające DSL być rozszerzony przez Ciebie lub innych stron. Użytkowników można wybrać opcję zainstalowania tylko DSL lub zainstalować DSL i rozszerzeń. MEF zmniejsza również pracy Definiowanie polecenia menu skrótów, po początkowej pracy, aby umożliwić MEF na język DSL.

Użyj metody w tym temacie:

1. Chcesz zdefiniować polecenia menu w menu niż menu skrótów kliknij prawym przyciskiem myszy.

2. Chcesz zdefiniować określone grupy poleceń w menu.

3. Czy chcesz umożliwić innym rozszerzanie DSL za pomocą ich własnych poleceń.

4. Chcesz zdefiniować jednego polecenia.

   W przeciwnym razie należy wziąć pod uwagę przy użyciu metody MEF do definiowania polecenia. Aby uzyskać więcej informacji, zobacz [rozszerzanie DSL za pomocą MEF](../modeling/extend-your-dsl-by-using-mef.md).

##  <a name="VSCT"></a> Zadeklaruj polecenie w Commands.Vsct
 Polecenia menu są deklarowane w DslPackage\Commands.vsct. Te definicje Określ etykiety elementów menu i gdzie są wyświetlane na pasku menu.

 Plik, który można edytować Commands.vsct, importuje definicje z kilku pliki .h, które znajdują się w katalogu *ścieżka instalacji programu Visual Studio SDK*\VisualStudioIntegration\Common\Inc. Zawiera on również GeneratedVsct.vsct, która jest generowana z definicji DSL.

 Aby uzyskać więcej informacji na temat plików vsct zobacz [tabeli poleceń w usłudze Visual Studio (. Pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

### <a name="to-add-the-command"></a>Aby dodać polecenie

1.  W **Eksploratora rozwiązań**w obszarze **DslPackage** projektu, otwórz Commands.vsct.

2.  W `Commands` elementu, zdefiniuj jeden lub więcej przycisków i grup. A *przycisk* element menu. A *grupy* to sekcja w menu. Aby zdefiniować te elementy, Dodaj następujące elementy:

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
    > Każdy przycisk lub grupa jest identyfikowana przez identyfikator GUID i liczby całkowitej. Można utworzyć kilka grup i przyciski, za pomocą tego samego identyfikatora GUID. Jednak musi mieć różne identyfikatory. Do nazw identyfikator GUID i identyfikator są tłumaczone na rzeczywistych identyfikatorów GUID i identyfikatory numeryczne w `<Symbols>` węzła.

3.  Dodaj ograniczenie widoczności dla polecenia, więc, że jest załadowany tylko w kontekście języka specyficznego dla domeny. Aby uzyskać więcej informacji, zobacz [VisibilityConstraints, Element](../extensibility/visibilityconstraints-element.md).

     Aby to zrobić, Dodaj następujące elementy w `CommandTable` elementu po `Commands` elementu.

    ```xml
    <VisibilityConstraints>
      <!-- Ensures the command is only loaded for this DSL -->
      <VisibilityItem guid="guidCustomMenuCmdSet" id="cmdidMyContextMenuCommand"
        context="guidEditor"/>
    </VisibilityConstraints>
    ```

4.  Definiowanie nazw, które były używane identyfikatory GUID i identyfikatory. Aby to zrobić, Dodaj `Symbols` element `CommandTable` elementu po `Commands` elementu.

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

5.  Zastąp `{000...000}` o identyfikatorze GUID, który identyfikuje elementy menu i grupy. Aby uzyskać nowy identyfikator GUID, użyj **Utwórz GUID** narzędzie **narzędzia** menu.

    > [!NOTE]
    >  Jeśli dodasz więcej grup lub elementy menu, można użyć tego samego identyfikatora GUID. Jednakże, należy użyć nowych wartości dla `IDSymbols`.

6.  W kodzie skopiowanych z tej procedury Zastąp każde wystąpienie następujących ciągów własne ciągi:

    -   `grpidMyMenuGroup`

    -   `cmdidMyContextMenuCommand`

    -   `guidCustomMenuCmdSet`

    -   `My Context Menu Command`

##  <a name="version"></a> Zaktualizuj wersję pakietu w Package.tt
 Przy dodawaniu lub zmienić polecenie aktualizacji `version` parametru <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> mający zastosowanie do klasy pakietu przed publikacją nową wersję języka specyficznego dla domeny.

 Ponieważ klasa pakietu jest zdefiniowana w wygenerowanym pliku, należy zaktualizować atrybutu w pliku szablonu tekstu, który generuje Package.cs plik.

### <a name="to-update-the-packagett-file"></a>Aby zaktualizować plik Package.tt

1.  W **Eksploratora rozwiązań**w **DslPackage** projektu w **GeneratedCode** folder, otwórz plik Package.tt.

2.  Znajdź `ProvideMenuResource` atrybutu.

3.  Inkrementacja `version` parametr atrybut, który jest drugi parametr. Jeśli chcesz, możesz napisać nazwę parametru jawnie, aby pamiętać o jego przeznaczenia. Na przykład:

     `[VSShell::ProvideMenuResource("1000.ctmenu", version: 2 )]`

##  <a name="CommandSet"></a> Zdefiniuj zachowanie polecenia

DSL ma już niektóre polecenia, które są implementowane w częściową klasą, która jest zadeklarowana w DslPackage\GeneratedCode\CommandSet.cs. Aby dodać nowe polecenia, można rozszerzyć tę klasę, tworząc nowy plik, który zawiera częściowa deklaracja tego samego rodzaju. Nazwa klasy jest zazwyczaj  *\<YourDslName >*`CommandSet`. Jest to przydatne rozpocząć przez weryfikowanie nazwę klasy i zapoznanie się jego zawartość.

Polecenie klasę zestawu jest tworzony na podstawie <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>.

### <a name="extend-the-commandset-class"></a>Rozszerzenie klasy element CommandSet

1.  W Eksploratorze rozwiązań w projekcie DslPackage Otwórz GeneratedCode folder, a następnie sprawdź w obszarze CommandSet.tt i otwieranie jego pliku wygenerowanego CommandSet.cs. Należy pamiętać, że przestrzeń nazw i nazwę pierwszej klasy, która jest zdefiniowany w niej. Na przykład może zostać wyświetlony:

     `namespace Company.Language1`

     `{ ...  internal partial class Language1CommandSet : ...`

2.  W **DslPackage**, Utwórz folder o nazwie **kod niestandardowy**. W tym folderze utwórz plik nowej klasy, który nosi nazwę `CommandSet.cs`.

3.  W nowym pliku zapisu częściowa deklaracja, która ma tę samą nazwę jak wygenerowanej częściowej klasy i przestrzeni nazw. Na przykład:

     `namespace Company.Language1 /* Make sure this is correct */`

     `{ internal partial class Language1CommandSet { ...`

     **Uwaga** Jeśli szablon klasy jest używany do utworzenia nowego pliku, należy poprawić przestrzeni nazw i nazwę klasy.

Kod zestawu poleceń zazwyczaj konieczne zaimportuj następujące przestrzenie nazw:

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel.Design;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Shell;
```

Ustawienia przestrzeni nazw i nazwę klasy, aby odpowiadały tym w wygenerowanym CommandSet.cs:

```csharp
namespace Company.Language1 /* Make sure this is correct */
{
  // Same class as the generated class.
  internal partial class Language1CommandSet
  {
```

Należy zdefiniować dwie metody, do określenia, kiedy polecenie będzie widoczny w menu kliknij prawym przyciskiem myszy (kontekstu), a druga do wykonania polecenia. Te metody nie są zastąpienia; Zamiast tego należy zarejestrować je w listy poleceń.

### <a name="define-when-the-command-will-be-visible"></a>Zdefiniuj, gdy polecenie będzie widoczne
 Dla każdego polecenia, należy zdefiniować `OnStatus...` metodę, która określa, czy polecenia pojawi się w menu i czy będzie włączona, czy nieaktywna. Ustaw `Visible` i `Enabled` właściwości `MenuCommand`, jak pokazano w poniższym przykładzie. Ta metoda jest wywoływana w celu utworzenia menu skrótów, ilekroć dany użytkownik kliknie prawym przyciskiem myszy diagram, więc musi działać szybko.

 W tym przykładzie polecenie jest widoczny tylko wtedy, gdy użytkownik wybrał określonego typu kształt i jest włączona tylko wtedy, gdy co najmniej jeden z wybranych elementów w określonym stanie. Przykład jest oparty na szablonie DSL diagramu klasy i typy, które są zdefiniowane w język DSL to ClassShape i ModelClass:

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

- `this.CurrentSelection`. Kształt, który kliknięto prawym przyciskiem myszy użytkownika, zawsze znajduje się na tej liście. Gdy użytkownik kliknie pustą część diagramu, Diagram jest jedynym członkiem listy.

- `this.IsDiagramSelected()` - `true` Jeśli użytkownik kliknął pustą część diagramu.

- `this.IsCurrentDiagramEmpty()`

- `this.IsSingleSelection()` — użytkownik nie został wybrany wiele obiektów

- `this.SingleSelection` -kształt lub diagram, który kliknięto prawym przyciskiem myszy użytkownika

- `shape.ModelElement as MyLanguageElement` — element modelu, reprezentowane przez kształty.

Ogólną wytyczną wprowadzić `Visible` są zależne od wybranej właściwości i upewnij `Enabled` właściwości zależą od stanu wybranych elementów.

Metoda OnStatus nie należy zmieniać stan Store.

### <a name="define-what-the-command-does"></a>Zdefiniuj polecenie powoduje
 Dla każdego polecenia, należy zdefiniować `OnMenu...` metodę, która wykonuje wymaganych akcji, gdy użytkownik kliknie polecenie menu.

 W przypadku wprowadzenia zmian do elementów modelu, należy to zrobić w transakcji. Aby uzyskać więcej informacji, zobacz [jak: Modyfikowanie standardowego polecenia Menu](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

 W tym przykładzie `ClassShape`, `ModelClass`, i `Comment` typów, które są zdefiniowane w DSL, który jest tworzony na podstawie szablonu klasy Diagram DSL.

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

 Aby uzyskać więcej informacji o tym, jak można przejść do innego obiektu w modelu oraz o sposobie tworzenia obiektów i łączy, zobacz [jak: Modyfikowanie standardowego polecenia Menu](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

### <a name="register-the-command"></a>Zarejestruj się polecenia
 Powtórz w języku C# deklaracje identyfikator GUID i identyfikator wartości, które zostały wprowadzone w sekcji symbole CommandSet.vsct:

```csharp
private Guid guidCustomMenuCmdSet =
    new Guid("00000000-0000-0000-0000-000000000000");
private const int grpidMyMenuGroup = 0x01001;
private const int cmdidMyContextMenuCommand = 1;
```

 Użyj tej samej wartości identyfikatora GUID jako wstawione w **Commands.vsct**.

> [!NOTE]
>  Jeśli zmienisz symbole części pliku VSCT, należy także zmienić te deklaracje do dopasowania. Należy również zwiększenie numeru wersji Package.tt

 Zarejestruj poleceń menu jako część tego zestawu poleceń. `GetMenuCommands()` jest wywoływana, gdy po zainicjowaniu diagramu:

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
 Twórz i uruchamiaj język DSL w eksperymentalnym wystąpieniu programu Visual Studio. Polecenie powinno pojawić się w menu skrótów w sytuacjach, które zostały określone.

### <a name="to-exercise-the-command"></a>Wykonywanie polecenia

1.  Na **Eksploratora rozwiązań** narzędzi, kliknij przycisk **Przekształć wszystkie szablony**.

2.  Naciśnij klawisz **F5** ponownie skompiluj rozwiązanie i rozpocząć debugowanie języka specyficznego dla domeny w eksperymentalnym kompilacji.

3.  W eksperymentalnym kompilacji Otwórz diagram przykładowej.

4.  Kliknij prawym przyciskiem myszy różne elementy na diagramie, aby sprawdzić, czy polecenie jest prawidłowo włączone lub wyłączone i odpowiednio wyświetlane lub ukryte, w zależności od wybranego elementu.

## <a name="troubleshoot"></a>Rozwiązywanie problemów

**W menu nie ma polecenia:**

- Polecenie pojawi się tylko w przypadku debugowania wystąpienia programu Visual Studio, dopóki nie zostanie zainstalowany pakiet języka DSL. Aby uzyskać więcej informacji, zobacz [wdrażania rozwiązań języka dotyczącego określonej domeny](../modeling/deploying-domain-specific-language-solutions.md).

- Upewnij się, że eksperymentalne przykładu ma poprawne rozszerzenie nazwy pliku dla tego języka DSL. Aby sprawdzić rozszerzenie nazwy pliku, otwórz DslDefinition.dsl w głównym wystąpieniu programu Visual Studio. Następnie w Eksplorator DSL, kliknij prawym przyciskiem myszy węzeł edytora, a następnie kliknij polecenie Właściwości. W oknie dialogowym właściwości zbadać właściwości FileExtension.

- Czy [zwiększ numer wersji pakietu](#version)?

- Ustaw punkt przerwania na początku wybrać metodę OnStatus. Należy go przerwać po kliknięciu prawym przyciskiem myszy nad dowolnym część diagramu.

**Nie jest wywoływana metoda OnStatus**:

-   Upewnij się, że identyfikatory GUID i identyfikatory w kodzie element CommandSet odpowiadają polom w sekcji symbole Commands.vsct.

-   Commands.vsct upewnij się, że identyfikator GUID i identyfikator w każdym węźle nadrzędnym zidentyfikować poprawne nadrzędnej grupy.

-   W wierszu polecenia programu Visual Studio wpisz devenv/Setup z exp /rootsuffix. Następnie uruchom ponownie wystąpienie debugowania programu Visual Studio.

- Przejść przez metodę OnStatus, aby sprawdzić tego polecenia. Widoczne i polecenia. Włączone są ustawione na wartość true.

**Pojawia się tekst menu problem lub polecenie pojawia się w niewłaściwym miejscu**:

- Upewnij się, że kombinacja identyfikator GUID i identyfikator jest unikatowy dla tego polecenia.

- Upewnij się, odinstalowano wcześniejszą wersję pakietu.

## <a name="see-also"></a>Zobacz także

- [Pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Instrukcje: Modyfikowanie standardowego polecenia Menu](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)
- [Wdrażanie rozwiązań dla języka specyficznego dla domeny](../modeling/deploying-domain-specific-language-solutions.md)
- [Przykładowy kod: Diagramy obwodu](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]