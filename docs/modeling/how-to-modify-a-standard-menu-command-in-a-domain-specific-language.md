---
title: 'Porady: modyfikowanie standardowego polecenia menu w języku specyficznym dla domeny'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsct files, adding commands to a domain-specific language
- Domain-Specific Language, adding custom commands
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 6aa827781cb8ea78aa5df79f8cb839a6f3548e11
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "50967054"
---
# <a name="how-to-modify-a-standard-menu-command-in-a-domain-specific-language"></a>Porady: modyfikowanie standardowego polecenia menu w języku specyficznym dla domeny

Można zmodyfikować zachowanie niektóre standardowe polecenia, które są automatycznie definiowane w DSL. Na przykład, można zmodyfikować **Wytnij** tak, aby nie obejmuje on poufne informacje. Aby to zrobić, można zastąpić metody w klasie zestawu poleceń. Te klasy są zdefiniowane w pliku CommandSet.cs w projekcie DslPackage i są uzyskiwane z <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>.

> [!NOTE]
> Jeśli chcesz utworzyć własne polecenia menu, zobacz [porady: Dodawanie polecenia do Menu skrótów](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

## <a name="what-commands-can-you-modify"></a>Jakie polecenia mogą zmodyfikować?

### <a name="to-discover-what-commands-you-can-modify"></a>Aby dowiedzieć się, co polecenia, należy zmodyfikować

1.  W `DslPackage` otwarty projekt `GeneratedCode\CommandSet.cs`. Ten plik C# można znaleźć w Eksploratorze rozwiązań jako podmiot zależny firmy `CommandSet.tt`.

2.  Znajdź klas w tym pliku, których nazwy kończą się za pomocą "`CommandSet`", na przykład `Language1CommandSet` i `Language1ClipboardCommandSet`.

3.  W każdej klasie zestaw poleceń, wpisz "`override`" następuje spacja. Funkcja IntelliSense wyświetli listę metod, które można przesłonić. Każde polecenie parą metod, których nazwy zaczynają się "`ProcessOnStatus`"i"`ProcessOnMenu`".

4.  Zwróć uwagę, które polecenia Ustaw klasy zawiera polecenia, które chcesz zmodyfikować.

5.  Zamknij plik bez zapisywania zmian.

    > [!NOTE]
    > Zazwyczaj nie należy edytować pliki, które zostały wygenerowane. Wszelkie zmiany zostaną utracone pliki są generowane przy następnym uruchomieniu.

## <a name="extend-the-appropriate-command-set-class"></a>Rozszerzenie klasy zestawu odpowiednie polecenie

Utwórz nowy plik, który zawiera deklarację częściowe klasy zestawu poleceń.

### <a name="to-extend-the-command-set-class"></a>Aby rozszerzyć polecenia Set — klasa

1.  W Eksploratorze rozwiązań w projekcie DslPackage Otwórz GeneratedCode folder, a następnie sprawdź w obszarze CommandSet.tt i otwieranie jego pliku wygenerowanego CommandSet.cs. Należy pamiętać, że przestrzeń nazw i nazwę pierwszej klasy, która jest zdefiniowany w niej. Na przykład może zostać wyświetlony:

     `namespace Company.Language1`

     `{ ...  internal partial class Language1CommandSet : ...`

2.  W **DslPackage**, Utwórz folder o nazwie **kod niestandardowy**. W tym folderze utwórz nowy plik klasy o nazwie `CommandSet.cs`.

3.  W nowym pliku zapisu częściowa deklaracja, która ma tę samą nazwę jak wygenerowanej częściowej klasy i przestrzeni nazw. Na przykład:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Design;
    namespace Company.Language1 /* Make sure this is correct */
    { internal partial class Language1CommandSet { ...
    ```

     **Uwaga** Jeżeli szablon pliku klasy został użyty do utworzenia nowego pliku, należy usunąć przestrzeni nazw i nazwę klasy.

## <a name="override-the-command-methods"></a>Przesłaniaj metody polecenia

Większość poleceń ma dwie metody skojarzone: metody o nazwie, takich jak `ProcessOnStatus`... określa, czy polecenie powinno być widoczne i włączone. Jest wywoływane, gdy użytkownik kliknie prawym przyciskiem myszy diagram i powinna wykonać szybkie i nie wprowadzaj żadnych zmian. `ProcessOnMenu`... jest wywoływana, gdy użytkownik kliknie polecenie i należy wykonać funkcję polecenia. Można zastąpić jedną lub obie te metody.

### <a name="to-change-when-the-command-appears-on-a-menu"></a>Aby zmienić, gdy polecenie jest wyświetlane w menu

Zastąp ProcessOnStatus... metody. Ta metoda powinna być ustawiona widoczne i włączone właściwości tego parametru MenuCommand. Zazwyczaj polecenia wygląda na to. CurrentSelection, aby określić, czy polecenie ma zastosowanie do wybranych elementów i mogą również przeglądać ich właściwości, aby określić, czy polecenia mogą być stosowane w jego bieżącym stanie.

Jako ogólnej wskazówki należy określić właściwość Visible przez elementy są zaznaczone. Właściwość włączone, która określa, czy polecenie pojawia się czarny lub szary w menu, powinna zależeć od bieżącego stanu zaznaczenia.

Poniższy przykład wyłącza usuwanie elementu menu, po użytkownik wybrał więcej niż jeden kształt.

> [!NOTE]
> Ta metoda nie wpływa na czy polecenie jest dostępne poprzez naciśnięcie klawisza. Na przykład wyłączenie usuwanie elementu menu nie uniemożliwia polecenia są wywoływane za pośrednictwem klawisz Delete.

```csharp
/// <summary>
/// Called when user right-clicks on the diagram or clicks the Edit menu.
/// </summary>
/// <param name="command">Set Visible and Enabled properties.</param>
protected override void ProcessOnStatusDeleteCommand (MenuCommand command)
{
  // Default settings from the base method.
  base.ProcessOnStatusDeleteCommand(command);
  if (this.CurrentSelection.Count > 1)
  {
    // If user has selected more than one item, Delete is greyed out.
    command.Enabled = false;
  }
}
```

Jest dobrą praktyką, najpierw wywołać metodę bazową, aby poradzić sobie ze wszystkimi przypadków i ustawienia, z którymi nie jest niezbędne.

Metoda ProcessOnStatus nie powinien Utwórz, usuń lub zaktualizuj elementy Store.

### <a name="to-change-the-behavior-of-the-command"></a>Aby zmienić zachowanie polecenia

Zastąp ProcessOnMenu... metody. Poniższy przykład uniemożliwia użytkownikowi usunięcie więcej niż jeden element w czasie, nawet przy użyciu klawisza Delete.

```csharp
/// <summary>
/// Called when user presses Delete key
/// or clicks the Delete command on a menu.
/// </summary>
protected override void ProcessOnMenuDeleteCommand()
{
  // Allow users to delete only one thing at a time.
  if (this.CurrentSelection.Count <= 1)
  {
    base.ProcessOnMenuDeleteCommand();
  }
}
```

Jeśli Twój kod zmienia Store, takie jak tworzenie, usuwanie lub aktualizowania elementów lub łącza, należy to zrobić w transakcji. Aby uzyskać więcej informacji, zobacz [jak tworzenie i aktualizowanie elementów modelu](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

### <a name="write-the-code-of-the-methods"></a>Pisanie kodu metody

Następujące fragmenty są często przydatne w przypadku tych metod:

-   `this.CurrentSelection`. Kształt, który kliknięto prawym przyciskiem myszy użytkownika, zawsze znajduje się na tej liście kształtów i łączników. Gdy użytkownik kliknie pustą część diagramu, Diagram jest jedynym członkiem listy.

-   `this.IsDiagramSelected()` - `true` Jeśli użytkownik kliknął pustą część diagramu.

-   `this.IsCurrentDiagramEmpty()`

-   `this.IsSingleSelection()` — użytkownik nie został wybrany wiele kształtów

-   `this.SingleSelection` -kształt lub diagram, który kliknięto prawym przyciskiem myszy użytkownika

-   `shape.ModelElement as MyLanguageElement` — element modelu, reprezentowane przez kształty.

Aby uzyskać więcej informacji na temat sposobu nawigowania element po elemencie oraz o sposobie tworzenia obiektów i łączy, zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.ComponentModel.Design.MenuCommand>
- [Pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Instrukcje: Dodawanie polecenia do menu skrótów](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)
- [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Odwołanie do schematu XML VSCT](../extensibility/vsct-xml-schema-reference.md)
- [VMSDK — przykładowe wykresy obwodu. Dostosowywanie rozbudowane DSL](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
