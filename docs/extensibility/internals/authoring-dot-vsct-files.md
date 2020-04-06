---
title: Tworzenia. Pliki Vsct | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dfa276d04e2d312d7ff00b1e9bc0015beb1e254e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709999"
---
# <a name="author-vsct-files"></a>Autor plików vsct
W tym dokumencie pokazano, jak tworzyć plik *vsct,* aby dodać elementy menu, paski narzędzi i inne elementy interfejsu użytkownika (UI) do zintegrowanego środowiska programistycznego programu Visual Studio (IDE). Wykonaj następujące kroki podczas dodawania elementów interfejsu użytkownika do pakietu programu Visual Studio (VSPackage), który nie ma jeszcze pliku *vsct.*

 W przypadku nowych projektów zaleca się użycie szablonu pakietu programu Visual Studio, ponieważ generuje on plik *vsct,* który w zależności od wybranych opcji ma już wymagane elementy dla polecenia menu, okna narzędzia lub edytora niestandardowego. Można zmodyfikować ten plik *vsct,* aby spełnić wymagania vsPackage. Aby uzyskać więcej informacji na temat modyfikowania pliku *vsct,* zobacz przykłady w [menu rozszerzania i polecenia .](../../extensibility/extending-menus-and-commands.md)

## <a name="author-the-file"></a>Tworzenie pliku
 Autor pliku *.vsct* w tych fazach: Tworzenie struktury dla plików i zasobów, zadeklarować elementy interfejsu użytkownika, umieścić elementy interfejsu użytkownika w IDE i dodać wszelkie zachowania specjalistyczne.

### <a name="file-structure"></a>Struktura plików
 Podstawowa struktura pliku *.vsct* jest elementem głównym [CommandTable,](../../extensibility/commandtable-element.md) który zawiera element [Commands](../../extensibility/commands-element.md) i element [Symbols.](../../extensibility/symbols-element.md)

#### <a name="to-create-the-file-structure"></a>Aby utworzyć strukturę plików

1. Dodaj plik *vsct* do projektu, wykonując czynności opisane w [instrukcjach dotyczących tworzenia pliku vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md).

2. Dodaj wymagane przestrzenie nazw `CommandTable` do elementu, jak pokazano w poniższym przykładzie:

    ```xml
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"
        xmlns:xs="http://www.w3.org/2001/XMLSchema">

    ```

3. W `CommandTable` elemencie `Commands` dodaj element, aby hostować wszystkie niestandardowe menu, paski narzędzi, grupy poleceń i polecenia. Aby można było załadować niestandardowe `Commands` elementy interfejsu `Package` użytkownika, element musi mieć ustawiony atrybut na nazwę pakietu.

     Po `Commands` elemencie `Symbols` dodaj element, aby zdefiniować identyfikatory GUID dla pakietu oraz nazwy i identyfikatory poleceń dla elementów interfejsu użytkownika.

### <a name="include-visual-studio-resources"></a>Uwzględnij zasoby programu Visual Studio
 Użyj [Extern](../../extensibility/extern-element.md) element, aby uzyskać dostęp do plików, które definiują polecenia programu Visual Studio i menu, które są wymagane do umieszczenia elementów interfejsu użytkownika w IDE. Jeśli użyjesz poleceń zdefiniowanych poza pakietem, użyj [UsedCommands](../../extensibility/usedcommands-element.md) element do informowania programu Visual Studio.

#### <a name="to-include-visual-studio-resources"></a>Aby uwzględnić zasoby programu Visual Studio

1. W górnej części `CommandTable` elementu dodaj `Extern` jeden element dla każdego pliku zewnętrznego, `href` do którego ma się odwoływać, i ustaw atrybut na nazwę pliku. Aby uzyskać dostęp do zasobów programu Visual Studio, można odwoływać się do następujących plików nagłówkowych:

   - *Stdidcmd.h*: Definiuje identyfikatory dla wszystkich poleceń udostępniane przez program Visual Studio.

   - *Vsshlids.h*: Zawiera identyfikatory poleceń dla menu programu Visual Studio.

2. Jeśli pakiet wywołuje wszystkie polecenia, które są zdefiniowane przez `UsedCommands` program Visual `Commands` Studio lub przez inne pakiety, dodaj element po elemencie. Wypełnij ten element z [UsedCommand](../../extensibility/usedcommand-element.md) element dla każdego polecenia, które można wywołać, który nie jest częścią pakietu. Ustaw `guid` i `id` atrybuty `UsedCommand` elementów do wartości GUID i ID poleceń do wywołania.

   Aby uzyskać więcej informacji na temat znajdowania identyfikatorów GUID i identyfikatorów poleceń programu Visual Studio, zobacz [identyfikatory GUID i identyfikatory poleceń programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Aby wywołać polecenia z innych pakietów, użyj identyfikatora GUID i identyfikatora polecenia zdefiniowanego w pliku *vsct* dla tych pakietów.

### <a name="declare-ui-elements"></a>Deklarowanie elementów interfejsu użytkownika
 Zadeklarować wszystkie nowe elementy `Symbols` interfejsu użytkownika w sekcji pliku *.vsct.*

#### <a name="to-declare-ui-elements"></a>Aby zadeklarować elementy interfejsu użytkownika

1. W `Symbols` elemencie dodaj trzy [guidSymbol](../../extensibility/guidsymbol-element.md) elementów. Każdy `GuidSymbol` element `name` ma atrybut `value` i atrybut. Ustaw `name` atrybut tak, aby odzwierciedlał cel elementu. Atrybut `value` przyjmuje identyfikator GUID. (Aby wygenerować identyfikator GUID, w menu **Narzędzia** wybierz polecenie **Utwórz identyfikator GUID**, a następnie wybierz pozycję **Format rejestru).**

     Pierwszy `GuidSymbol` element reprezentuje pakiet i zazwyczaj nie ma elementów podrzędnych. Drugi `GuidSymbol` element reprezentuje zestaw poleceń i będzie zawierać wszystkie symbole definiujące menu, grupy i polecenia. Trzeci `GuidSymbol` element reprezentuje magazyn obrazów i zawiera symbole dla wszystkich ikon dla poleceń. Jeśli nie masz żadnych poleceń, które używają ikon, można pominąć trzeci `GuidSymbol` element.

2. W `GuidSymbol` elemencie reprezentującym zestaw poleceń dodaj jeden lub więcej elementów [IDSymbol.](../../extensibility/idsymbol-element.md) Każdy z nich reprezentuje menu, pasek narzędzi, grupę lub polecenie dodane do interfejsu użytkownika.

     Dla `IDSymbol` każdego elementu `name` ustaw atrybut na nazwę, która będzie używana do odwoływania się do `value` odpowiedniego menu, grupy lub polecenia, a następnie ustaw element na liczbę szesnastkową, która będzie reprezentować jego identyfikator polecenia. Żadne `IDSymbol` dwa elementy, które mają ten sam element nadrzędny może mieć taką samą wartość.

3. Jeśli którykolwiek z elementów interfejsu użytkownika `IDSymbol` wymaga ikon, `GuidSymbol` dodaj element dla każdej ikony do elementu, który reprezentuje magazyn obrazów.

### <a name="put-ui-elements-in-the-ide"></a>Umieszczanie elementów interfejsu użytkownika w idei
 [Menu,](../../extensibility/menus-element.md) [Grupy](../../extensibility/groups-element.md)i [Przyciski](../../extensibility/buttons-element.md) elementy zawierają definicje wszystkich menu, grup i poleceń zdefiniowanych w pakiecie. Umieść te menu, grupy i polecenia w IDE za pomocą [Elementu Nadrzędnego,](../../extensibility/parent-element.md) który jest częścią definicji elementu interfejsu użytkownika lub za pomocą elementu [CommandPlacement,](../../extensibility/commandplacement-element.md) który jest zdefiniowany w innym miejscu.

 Każdy `Menu` `Group`, `Button` i element `guid` ma atrybut `id` i atrybut. Zawsze ustaw `guid` atrybut tak, aby `GuidSymbol` odpowiadał nazwie elementu reprezentującego `id` zestaw poleceń i `IDSymbol` ustaw atrybut na nazwę elementu reprezentującego `Symbols` menu, grupę lub polecenie w sekcji.

#### <a name="to-define-ui-elements"></a>Aby zdefiniować elementy interfejsu użytkownika

1. W przypadku definiowania nowych menu, podmenu, menu skrótów lub pasków narzędzi dodaj `Menus` element do `Commands` elementu. Następnie dla każdego menu, które [Menu](../../extensibility/menu-element.md) ma zostać `Menus` utworzone, dodaj element Menu do elementu.

    Ustaw `guid` atrybuty `id` `Menu` elementu, a następnie `type` ustaw atrybut do odpowiedniego rodzaju menu. Można również ustawić `priority` atrybut, aby ustalić względne położenie menu w grupie nadrzędnej.

   > [!NOTE]
   > Atrybut `priority` nie ma zastosowania do pasków narzędzi i menu kontekstowych.

2. Wszystkie polecenia w programie Visual Studio IDE muszą być hostowane przez grupy poleceń, które są bezpośrednimi elementami podrzędnymi menu i pasków narzędzi. Jeśli dodajesz nowe menu lub paski narzędzi do IDE, muszą one zawierać nowe grupy poleceń. Grupy poleceń można również dodawać do istniejących menu i pasków narzędzi, aby można było wizualnie grupować polecenia.

    Podczas dodawania nowych grup poleceń `Groups` należy najpierw utworzyć element, a następnie dodać do niego element [Grupy](../../extensibility/group-element.md) dla każdej grupy poleceń.

    Ustaw `guid` atrybuty `id` każdego `Group` elementu, a `priority` następnie ustaw atrybut, aby ustalić względne położenie grupy w menu nadrzędnym. Aby uzyskać więcej informacji, zobacz [Tworzenie grup przycisków wielokrotnego użytku](../../extensibility/creating-reusable-groups-of-buttons.md).

3. Jeśli dodajesz nowe polecenia do IDE, `Buttons` dodaj `Commands` element do elementu. Następnie dla każdego polecenia dodaj [Button](../../extensibility/button-element.md) `Buttons` element do elementu.

   1. Ustaw `guid` atrybuty `id` każdego `Button` elementu, a `type` następnie ustaw atrybut na odpowiedni rodzaj przycisku. Można również ustawić `priority` atrybut, aby ustalić względną pozycję polecenia w grupie nadrzędnej.

       > [!NOTE]
       > Służy `type="button"` do standardowych poleceń menu i przycisków na paskach narzędzi.

   2. W `Button` elemencie dodaj [Strings](../../extensibility/strings-element.md) element, który zawiera [ButtonText](../../extensibility/buttontext-element.md) element i [CommandName](../../extensibility/commandname-element.md) element. Element `ButtonText` zawiera etykietę tekstową elementu menu lub etykietę narzędzia dla przycisku paska narzędzi. Element `CommandName` zawiera nazwę polecenia do użycia w poleceniu dobrze.

   3. Jeśli twoje polecenie będzie miało [Icon](../../extensibility/icon-element.md) ikonę, `Button` utwórz element `guid` Icon `id` w `Bitmap` elemencie i ustaw jego i atrybuty elementu ikony.

       > [!NOTE]
       > Przyciski paska narzędzi muszą zawierać ikony.

   Aby uzyskać więcej informacji, zobacz [MenuCommands vs. OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015).

4. Jeśli którekolwiek z poleceń wymaga ikon, dodaj element `Commands` [Bitmaps](../../extensibility/bitmaps-element.md) do elementu. Następnie dla każdej ikony dodaj element `Bitmaps` [bitmapy](../../extensibility/bitmap-element.md) do elementu. W tym miejscu można określić lokalizację zasobu mapy bitowej. Aby uzyskać więcej informacji, zobacz [Dodawanie ikon do poleceń menu](../../extensibility/adding-icons-to-menu-commands.md).

   Można polegać na strukturze nadrzędnej, aby poprawnie umieścić większość menu, grup i poleceń. W przypadku bardzo dużych zestawów poleceń lub gdy menu, grupa lub polecenie musi być wyświetlane w wielu miejscach, zaleca się określenie rozmieszczenia poleceń.

#### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>Aby polegać na rodzicielstwie, aby umieścić elementy interfejsu użytkownika w IDE

1. Dla typowego rodzicielstwa `Parent` należy `Menu`utworzyć `Group`element `Command` w każdym , i element, który jest zdefiniowany w pakiecie.

    Celem `Parent` elementu jest menu lub grupa, która będzie zawierać menu, grupy lub polecenia.

   1. Ustaw `guid` atrybut na nazwę `GuidSymbol` elementu, który definiuje zestaw poleceń. Jeśli element docelowy nie jest częścią pakietu, użyj identyfikatora guid dla tego zestawu poleceń, zgodnie z definicją w odpowiednim pliku *vsct.*

   2. Ustaw `id` atrybut tak, `id` aby odpowiadał atrybutowi docelowego menu lub grupy. Aby uzyskać listę menu i grup, które są udostępniane przez program Visual Studio, zobacz [identyfikatory GUID i identyfikatory menu programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) lub [identyfikatory GUID i identyfikatory pasków narzędzi programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).

   Jeśli masz dużą liczbę elementów interfejsu użytkownika do umieszczenia w IDE lub jeśli masz elementy, które powinny pojawić się w wielu miejscach, zdefiniuj ich miejsca docelowe w [CommandPlacements](../../extensibility/commandplacements-element.md) element, jak pokazano w poniższych krokach.

#### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>Aby użyć rozmieszczenia poleceń do umieszczenia elementów interfejsu użytkownika w ide

1. Po elemencie `Commands` dodaj element `CommandPlacements`.

2. W `CommandPlacements` elemencie `CommandPlacement` dodaj element dla każdego menu, grupy lub polecenia do umieszczenia.

    Każdy `CommandPlacement` element `Parent` lub element umieszcza jedno menu, grupę lub polecenie w jednej lokalizacji IDE. Element interfejsu użytkownika może mieć tylko jeden element nadrzędny, ale może mieć wiele miejsc docelowych poleceń. Aby umieścić element interfejsu użytkownika w `CommandPlacement` wielu lokalizacjach, dodaj element dla każdej lokalizacji.

3. Ustaw `guid` atrybuty `id` i `CommandPlacement` każdy element do menu hostingu lub `Parent` grupy, tak jak w przypadku elementu. Można również ustawić `priority` atrybut, aby ustalić względną pozycję elementu interfejsu użytkownika.

   Umieszczenie można mieszać według rodzicielstwa i umieszczania poleceń. Jednak w przypadku bardzo dużych zestawów poleceń zaleca się użycie tylko rozmieszczenia poleceń.

### <a name="add-specialized-behaviors"></a>Dodawanie zachowań specjalistycznych
 Za pomocą [CommandFlag](../../extensibility/command-flag-element.md) element zmodyfikować zachowanie menu i poleceń, na przykład, aby zmienić ich wygląd i widoczność. Można również wpłynąć na to, czy polecenie jest widoczne za pomocą elementu [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) lub dodać skróty klawiaturowe za pomocą elementu [KeyBindings.](../../extensibility/keybindings-element.md) Niektóre rodzaje menu i polecenia mają już wbudowane wyspecjalizowane zachowania.

#### <a name="to-add-specialized-behaviors"></a>Aby dodać zachowania specjalistyczne

1. Aby element interfejsu użytkownika był widoczny tylko w niektórych kontekstach interfejsu użytkownika, na przykład podczas ładowania rozwiązania należy użyć ograniczeń widoczności.

   1. Po elemencie `Commands` dodaj element `VisibilityConstraints`.

   2. Dla każdego elementu interfejsu użytkownika, aby ograniczyć, dodaj [Element VisibilityItem.](../../extensibility/visibilityitem-element.md)

   3. Dla `VisibilityItem` każdego elementu `guid` ustaw `id` i atrybuty do menu, grupy lub `context` polecenia, a następnie ustaw atrybut do <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> kontekstu interfejsu użytkownika, który chcesz, zgodnie z definicją w klasie.

2. Aby ustawić widoczność lub dostępność elementu interfejsu użytkownika w kodzie, użyj co najmniej jednej z następujących flag poleceń:

   - `DefaultDisabled`

   - `DefaultInvisible`

   - `DynamicItemStart`

   - `DynamicVisibility`

   - `NoShowOnMenuController`

   - `NotInTBList`

   Aby uzyskać więcej informacji, zobacz [CommandFlag](../../extensibility/command-flag-element.md) element.

3. Aby zmienić sposób pojawiania się elementu lub dynamicznie zmieniać jego wygląd, użyj co najmniej jednej z następujących flag poleceń:

   - `AlwaysCreate`

   - `CommandWellOnly`

   - `DefaultDocked`

   - `DontCache`

   - `DynamicItemStart`

   - `FixMenuController`

   - `IconAndText`

   - `Pict`

   - `StretchHorizontally`

   - `TextMenuUseButton`

   - `TextChanges`

   - `TextOnly`

   Aby uzyskać więcej informacji, zobacz [CommandFlag](../../extensibility/command-flag-element.md) element.

4. Aby zmienić sposób reakcji elementu po odebraniu poleceń, użyj co najmniej jednej z następujących flag poleceń:

   - `AllowParams`

   - `CaseSensitive`

   - `CommandWellOnly`

   - `FilterKeys`

   - `NoAutoComplete`

   - `NoButtonCustomize`

   - `NoKeyCustomize`

   - `NoToolbarClose`

   - `PostExec`

   - `RouteToDocs`

   - `TextIsAnchorCommand`

   Aby uzyskać więcej informacji, zobacz [CommandFlag](../../extensibility/command-flag-element.md) element.

5. Aby dołączyć skrót klawiaturowy zależny od menu do menu lub elementu w menu, dodaj znak `ButtonText` ampersand (&) w elemencie menu lub pozycji menu. Znak, który następuje po znaku ampersand jest aktywnym skrótem klawiaturowym, gdy menu nadrzędne jest otwarte.

6. Aby dołączyć skrót klawiaturowy niezależny od menu do polecenia, użyj elementu [KeyBindings.](../../extensibility/keybindings-element.md) Aby uzyskać więcej informacji, zobacz [KeyBinding](../../extensibility/keybinding-element.md) element.

7. Aby zlokalizować tekst menu, użyj `LocCanonicalName` elementu. Aby uzyskać więcej informacji, zobacz [Strings](../../extensibility/strings-element.md) element.

   Niektóre typy menu i przycisków obejmują zachowania specjalistyczne. Na poniższej liście opisano niektóre wyspecjalizowane typy menu i przycisków. W przypadku innych `types` typów zobacz opisy atrybutów w [menu](../../extensibility/menu-element.md), [przycisku](../../extensibility/button-element.md)i elementów [kombi.](../../extensibility/combo-element.md)

   - Pole kombi: pole kombi to lista rozwijana, która może być używana na pasku narzędzi. Aby dodać pola kombi do interfejsu użytkownika, należy `Commands` utworzyć element [Combos](../../extensibility/combos-element.md) w elemencie. Następnie dodaj `Combos` do `Combo` elementu element dla każdego pola kombi, aby dodać. `Combo`elementy mają takie same `Button` atrybuty i `DefaultWidth` `idCommandList` elementy podrzędne jak elementy, a także mają i atrybuty. Atrybut `DefaultWidth` ustawia szerokość w pikselach, `idCommandList` a atrybut wskazuje identyfikator polecenia, który jest używany do wypełniania pola kombi.

   - Kontroler menu: Kontroler menu to przycisk, który ma obok strzałkę. Kliknięcie strzałki powoduje otwarcie listy. Aby dodać kontroler menu do interfejsu `Menu` użytkownika, utwórz element `MenuController` `MenuControllerLatched`i ustaw jego `type` atrybut na lub , w zależności od żądanego zachowania. Aby wypełnić kontroler menu, ustaw go jako `Group` element nadrzędny elementu. Kontroler menu wyświetli wszystkie elementy podrzędne tej grupy na liście rozwijanej.

## <a name="see-also"></a>Zobacz też
- [Rozszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md)
- [Pliki tabeli poleceń programu Visual Studio (vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Odwołanie do schematu XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
