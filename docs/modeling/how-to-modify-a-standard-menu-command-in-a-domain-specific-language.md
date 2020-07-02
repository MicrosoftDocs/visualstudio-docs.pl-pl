---
title: Modyfikowanie standardowego polecenia menu w DSL
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- .vsct files, adding commands to a domain-specific language
- Domain-Specific Language, adding custom commands
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a7236c074bda17023c989c744042db2de4046558
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85532499"
---
# <a name="how-to-modify-a-standard-menu-command-in-a-domain-specific-language"></a>Porady: modyfikowanie standardowego polecenia menu w języku specyficznym dla domeny

Można zmodyfikować zachowanie niektórych standardowych poleceń, które są zdefiniowane automatycznie w DSL. Na przykład można zmodyfikować **wycinanie** , aby wykluczyć informacje poufne. W tym celu należy zastąpić metody w klasie zestawu poleceń. Te klasy są zdefiniowane w pliku CommandSet.cs, w projekcie DslPackage i są wyprowadzane z <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> .

> [!NOTE]
> Jeśli chcesz utworzyć własne polecenia menu, zobacz [jak: Dodawanie polecenia do menu skrótów](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

## <a name="what-commands-can-you-modify"></a>Jakie polecenia można modyfikować?

### <a name="to-discover-what-commands-you-can-modify"></a>Aby poznać, jakie polecenia można modyfikować

1. W projekcie `DslPackage` otwórz plik `GeneratedCode\CommandSet.cs`. Ten plik w języku C# można znaleźć w Eksplorator rozwiązań jako jednostka zależna `CommandSet.tt` .

2. Znajdź klasy w tym pliku, których nazwy kończą się znakiem " `CommandSet` ", na przykład `Language1CommandSet` i `Language1ClipboardCommandSet` .

3. W każdej klasie zestawu poleceń wpisz " `override` ", a po niej spację. Funkcja IntelliSense wyświetli listę metod, które można przesłonić. Każde polecenie ma parę metod, których nazwy zaczynają się od " `ProcessOnStatus` " do " `ProcessOnMenu` ".

4. Należy pamiętać, że klasy zestawu poleceń zawierają polecenie, które chcesz zmodyfikować.

5. Zamknij plik bez zapisywania zmian.

    > [!NOTE]
    > Zwykle nie należy edytować plików, które zostały wygenerowane. Wszelkie zmiany zostaną utracone przy następnym wygenerowanym pliku.

## <a name="extend-the-appropriate-command-set-class"></a>Poszerzenie odpowiedniej klasy zestawu poleceń

Utwórz nowy plik zawierający częściową deklarację klasy zestawu poleceń.

### <a name="to-extend-the-command-set-class"></a>Aby rozwinąć klasę zestawu poleceń

1. W Eksplorator rozwiązań w projekcie DslPackage Otwórz folder GeneratedCode, a następnie poszukaj w obszarze CommandSet.tt i otwórz jego wygenerowany plik CommandSet.cs. Zanotuj przestrzeń nazw i nazwę pierwszej klasy, która jest tam zdefiniowana. Na przykład można zobaczyć:

     `namespace Company.Language1`

     `{ ...  internal partial class Language1CommandSet : ...`

2. W **DslPackage**Utwórz folder o nazwie **kod niestandardowy**. W tym folderze Utwórz nowy plik klasy o nazwie `CommandSet.cs` .

3. W nowym pliku Napisz deklarację częściową, która ma taką samą przestrzeń nazw i nazwę jak wygenerowana Klasa częściowa. Przykład:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Design;
    namespace Company.Language1 /* Make sure this is correct */
    { internal partial class Language1CommandSet { ...
    ```

    > [!NOTE]
    > Jeśli do utworzenia nowego pliku użyto szablonu pliku klasy, należy poprawić zarówno przestrzeń nazw, jak i nazwę klasy.

## <a name="override-the-command-methods"></a>Zastąp metody polecenia

Większość poleceń ma dwie skojarzone metody: metodę o nazwie takiej jak `ProcessOnStatus` ... Określa, czy polecenie powinno być widoczne i włączone. Jest wywoływana za każdym razem, gdy użytkownik kliknie prawym przyciskiem myszy diagram i powinien być wykonywany szybko i nie wprowadzać żadnych zmian. `ProcessOnMenu`... jest wywoływana, gdy użytkownik kliknie polecenie i powinien wykonać funkcję polecenia. Możesz chcieć przesłonić jedną lub obie te metody.

### <a name="to-change-when-the-command-appears-on-a-menu"></a>Aby zmienić, gdy polecenie pojawia się w menu

Zastąp ProcessOnStatus... Method. Ta metoda powinna ustawiać właściwości Visible i Enabled parametru MenuCommand. Zwykle jest to polecenie. CurrentSelection, aby określić, czy polecenie ma zastosowanie do wybranych elementów, i może również sprawdzić ich właściwości, aby określić, czy polecenie można zastosować w bieżącym stanie.

Ogólnie rzecz biorąc, właściwość Visible powinna być określona przez elementy, które są zaznaczone. Właściwość Enabled, która określa, czy polecenie pojawia się jako czarno lub szaro w menu, powinno zależeć od bieżącego stanu zaznaczenia.

Poniższy przykład wyłącza element menu Usuń, gdy użytkownik wybierze więcej niż jeden kształt.

> [!NOTE]
> Ta metoda nie ma wpływu na to, czy polecenie jest dostępne przez naciśnięcie klawisza. Na przykład wyłączenie elementu menu Usuń nie uniemożliwia wywołania polecenia za pomocą klucza usuwania.

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

Dobrym sposobem jest Wywołaj metodę bazową w pierwszej kolejności, aby zająć się wszystkimi przypadkami i ustawieniami, których nie dotyczy.

Metoda ProcessOnStatus nie powinna tworzyć, usuwać ani aktualizować elementów w sklepie.

### <a name="to-change-the-behavior-of-the-command"></a>Aby zmienić zachowanie polecenia

Zastąp ProcessOnMenu... Method. Poniższy przykład uniemożliwia użytkownikowi usunięcie więcej niż jednego elementu jednocześnie, nawet przy użyciu klucza Delete.

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

Jeśli kod wprowadza zmiany do magazynu, takie jak tworzenie, usuwanie lub aktualizowanie elementów lub łączy, należy to zrobić w ramach transakcji. Aby uzyskać więcej informacji, zobacz [jak tworzyć i aktualizować elementy modelu](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

### <a name="write-the-code-of-the-methods"></a>Napisz kod metod

Następujące fragmenty są często przydatne w następujących metodach:

- `this.CurrentSelection`. Kształt kliknięty prawym przyciskiem myszy jest zawsze uwzględniony na liście kształtów i łączników. Jeśli użytkownik kliknie pustą część diagramu, diagram jest jedyną składową listy.

- `this.IsDiagramSelected()` - `true`Jeśli użytkownik kliknął pustą część diagramu.

- `this.IsCurrentDiagramEmpty()`

- `this.IsSingleSelection()`-Użytkownik nie wybrał wielu kształtów

- `this.SingleSelection`-kształt lub diagram, który kliknął użytkownik prawym przyciskiem myszy.

- `shape.ModelElement as MyLanguageElement`— element modelu reprezentowany przez kształt.

Aby uzyskać więcej informacji na temat nawigowania z elementu do elementu i sposobu tworzenia obiektów i linków, zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.ComponentModel.Design.MenuCommand>
- [Pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Porady: dodawanie polecenia do menu skrótów](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)
- [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Odwołanie do schematu XML VSCT](../extensibility/vsct-xml-schema-reference.md)
- [Przykładowe diagramy obwodów VMSDK. Szerokie dostosowanie DSL](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
