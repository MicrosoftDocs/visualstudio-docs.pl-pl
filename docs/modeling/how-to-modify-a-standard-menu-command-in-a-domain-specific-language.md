---
title: Modyfikowanie standardowego polecenia menu w DSL
description: Dowiedz się, jak można modyfikować zachowanie niektórych standardowych poleceń, które są definiowane automatycznie w DSL.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- .vsct files, adding commands to a domain-specific language
- Domain-Specific Language, adding custom commands
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ccbc82801c3570c74e96010d5f9fc0e0e7940937
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387102"
---
# <a name="how-to-modify-a-standard-menu-command-in-a-domain-specific-language"></a>Porady: modyfikowanie standardowego polecenia menu w języku specyficznym dla domeny

Można zmodyfikować zachowanie niektórych standardowych poleceń, które są definiowane automatycznie w DSL. Na przykład można zmodyfikować **wytnij** tak, aby wykluczał poufne informacje. W tym celu należy przesłonić metody w klasie zestawu poleceń. Te klasy są zdefiniowane w pliku CommandSet.cs w projekcie DslPackage i pochodzą z <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet> klasy .

> [!NOTE]
> Jeśli chcesz utworzyć własne polecenia menu, zobacz Jak dodać polecenie do [menu skrótów](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

## <a name="what-commands-can-you-modify"></a>Jakie polecenia można modyfikować?

### <a name="to-discover-what-commands-you-can-modify"></a>Aby dowiedzieć się, jakie polecenia można modyfikować

1. W projekcie `DslPackage` otwórz plik `GeneratedCode\CommandSet.cs`. Ten plik języka C# można znaleźć w Eksplorator rozwiązań jako podmiot zależny od `CommandSet.tt` programu .

2. Znajdź klasy w tym pliku, których nazwy kończą się na " `CommandSet` ", na przykład `Language1CommandSet` i `Language1ClipboardCommandSet` .

3. W każdej klasie zestawu poleceń wpisz " `override` ", po którym następuje spacja. Funkcja IntelliSense wyświetla listę metod, które można przesłonić. Każde polecenie ma parę metod, których nazwy rozpoczynają się od " `ProcessOnStatus` " i " `ProcessOnMenu` ".

4. Zwróć uwagę, która z klas zestawu poleceń zawiera polecenie, które chcesz zmodyfikować.

5. Zamknij plik bez zapisywania zmian.

    > [!NOTE]
    > Zazwyczaj nie należy edytować wygenerowanych plików. Wszelkie zmiany zostaną utracone przy następnym wygenerowaniu plików.

## <a name="extend-the-appropriate-command-set-class"></a>Rozszerzanie odpowiedniej klasy zestawu poleceń

Utwórz nowy plik zawierający częściową deklarację klasy zestawu poleceń.

### <a name="to-extend-the-command-set-class"></a>Aby rozszerzyć klasę Zestaw poleceń

1. W Eksplorator rozwiązań projektu DslPackage otwórz folder GeneratedCode, a następnie w obszarze CommandSet.tt otwórz wygenerowany plik CommandSet.cs. Zanotuj przestrzeń nazw i nazwę pierwszej klasy, która jest tam zdefiniowana. Możesz na przykład zobaczyć:

     `namespace Company.Language1`

     `{ ...  internal partial class Language1CommandSet : ...`

2. W **pliku DslPackage** utwórz folder o nazwie **Custom Code**. W tym folderze utwórz nowy plik klasy o nazwie `CommandSet.cs` .

3. W nowym pliku napisz częściową deklarację, która ma taką samą przestrzeń nazw i nazwę jak wygenerowana klasa częściowa. Na przykład:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Design;
    namespace Company.Language1 /* Make sure this is correct */
    { internal partial class Language1CommandSet { ...
    ```

    > [!NOTE]
    > Jeśli do utworzenia nowego pliku został użyty szablon pliku klasy, należy poprawić zarówno przestrzeń nazw, jak i nazwę klasy.

## <a name="override-the-command-methods"></a>Zastępowanie metod poleceń

Większość poleceń ma dwie skojarzone metody: metodę o nazwie podobnej do `ProcessOnStatus` ... Określa, czy polecenie powinno być widoczne i włączone. Jest on wywoływany za każdym razem, gdy użytkownik kliknie diagram prawym przyciskiem myszy i powinien zostać wykonany szybko i nie wprowadzać żadnych zmian. `ProcessOnMenu`... Jest wywoływana, gdy użytkownik kliknie polecenie i powinien wykonać funkcję polecenia . Możesz zastąpić jedną lub obie te metody.

### <a name="to-change-when-the-command-appears-on-a-menu"></a>Aby zmienić, gdy polecenie pojawi się w menu

Zastąp processOnStatus... Metoda. Ta metoda powinna ustawić właściwości Visible i Enabled parametru MenuCommand. Zwykle polecenie to przejmuje. CurrentSelection, aby określić, czy polecenie ma zastosowanie do wybranych elementów, a także może sprawdzić ich właściwości, aby określić, czy polecenie może być stosowane w ich bieżącym stanie.

Ogólnie rzecz biorąc, właściwość Visible powinna być określana na podstawie wybranych elementów. Właściwość Enabled, która określa, czy polecenie jest wyświetlane w menu jako czarne, czy szare, powinno zależeć od bieżącego stanu zaznaczenia.

Poniższy przykład wyłącza element menu Usuń, gdy użytkownik wybrał więcej niż jeden kształt.

> [!NOTE]
> Ta metoda nie ma wpływu na to, czy polecenie jest dostępne za pośrednictwem naciśnięcia klawisza. Na przykład wyłączenie elementu menu Usuń nie uniemożliwia wywoływania polecenia za pomocą klawisza Delete.

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

Dobrym rozwiązaniem jest wywołanie metody podstawowej w pierwszej kolejności, aby zająć się wszystkimi przypadkami i ustawieniami, których nie dotyczy.

Metoda ProcessOnStatus nie powinna tworzyć, usuwać ani aktualizować elementów w magazynie.

### <a name="to-change-the-behavior-of-the-command"></a>Aby zmienić zachowanie polecenia

Zastąp processOnMenu... Metoda. Poniższy przykład uniemożliwia użytkownikowi usunięcie więcej niż jednego elementu na raz, nawet przy użyciu usuń klucz.

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

Jeśli kod wprowadza zmiany w magazynie, takie jak tworzenie, usuwanie lub aktualizowanie elementów lub linków, należy to zrobić w ramach transakcji. Aby uzyskać więcej informacji, zobacz How to Create and Update model elements (Jak [tworzyć i aktualizować elementy modelu).](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)

### <a name="write-the-code-of-the-methods"></a>Pisanie kodu metod

Następujące fragmenty są często przydatne w ramach tych metod:

- `this.CurrentSelection`. Kształt, który użytkownik kliknął prawym przyciskiem myszy, jest zawsze uwzględniony na tej liście kształtów i łączników. Jeśli użytkownik kliknie pustą część diagramu, diagram jest jedynym elementem członkowskim listy.

- `this.IsDiagramSelected()` - `true` jeśli użytkownik kliknął pustą część diagramu.

- `this.IsCurrentDiagramEmpty()`

- `this.IsSingleSelection()` — użytkownik nie zaznaczył wielu kształtów

- `this.SingleSelection` — kształt lub diagram, który użytkownik kliknął prawym przyciskiem myszy

- `shape.ModelElement as MyLanguageElement` — element modelu reprezentowany przez kształt.

Aby uzyskać więcej informacji na temat przechodzenia z elementu do elementu oraz sposobu tworzenia obiektów i linków, zobacz [Navigateing and Updating a Model in Program Code](../modeling/navigating-and-updating-a-model-in-program-code.md)(Nawigowanie i aktualizowanie modelu w kodzie programu).

## <a name="see-also"></a>Zobacz też

- <xref:System.ComponentModel.Design.MenuCommand>
- [Pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [Porady: dodawanie polecenia do menu skrótów](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)
- [Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Odwołanie do schematu XML VSCT](../extensibility/vsct-xml-schema-reference.md)
- [VMSDK — przykład diagramów obwodu. Rozbudowane dostosowywanie DSL](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
