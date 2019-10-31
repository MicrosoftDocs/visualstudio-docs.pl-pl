---
title: Projekt. Pliki vsct | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 82960de02c43a7c4002e189d573a914bb2a73f20
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186652"
---
# <a name="author-vsct-files"></a>Author. vsct — pliki
W tym dokumencie przedstawiono sposób tworzenia pliku *. vsct* w celu dodania elementów menu, pasków narzędzi i innych elementów interfejsu użytkownika do zintegrowanego środowiska programistycznego (IDE) programu Visual Studio. Poniższe kroki umożliwiają dodanie elementów interfejsu użytkownika do pakietu programu Visual Studio (pakietu VSPackage), który nie ma jeszcze pliku *. vsct* .

 W przypadku nowych projektów zaleca się użycie szablonu pakietu programu Visual Studio, ponieważ generuje on plik *. vsct* , który w zależności od wybranych opcji ma już wymagane elementy dla polecenia menu, okna narzędzi lub niestandardowego edytora. Możesz zmodyfikować ten plik *. vsct* , aby spełniał wymagania pakietu VSPackage. Więcej informacji o sposobach modyfikowania pliku *. vsct* można znaleźć w przykładach w sekcji [rozszerzone menu i polecenia](../../extensibility/extending-menus-and-commands.md).

## <a name="author-the-file"></a>Tworzenie pliku
 Twórz plik *. vsct* w następujących fazach: Utwórz strukturę dla plików i zasobów, zadeklaruj elementy interfejsu użytkownika, umieść elementy interfejsu użytkownika w IDE, a następnie Dodaj wszelkie wyspecjalizowane zachowania.

### <a name="file-structure"></a>Struktura plików
 Podstawowa struktura pliku *. vsct* jest [elementem głównym poleceń](../../extensibility/commandtable-element.md) , który zawiera element [Commands](../../extensibility/commands-element.md) i element [Symbols](../../extensibility/symbols-element.md) .

#### <a name="to-create-the-file-structure"></a>Aby utworzyć strukturę plików

1. Dodaj plik *. vsct* do projektu, wykonując czynności opisane w temacie [How to: Create a. vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md).

2. Dodaj wymagane przestrzenie nazw do elementu `CommandTable`, jak pokazano w następującym przykładzie:

    ```xml
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"
        xmlns:xs="http://www.w3.org/2001/XMLSchema">

    ```

3. W `CommandTable` elementu Dodaj element `Commands`, aby hostować wszystkie niestandardowe menu, paski narzędzi, grupy poleceń i polecenia. Aby można było załadować niestandardowe elementy interfejsu użytkownika, element `Commands` musi mieć atrybut `Package` ustawiony na nazwę pakietu.

     Po elemencie `Commands` Dodaj element `Symbols`, aby zdefiniować identyfikatory GUID pakietu oraz nazwy i identyfikatory poleceń dla elementów interfejsu użytkownika.

### <a name="include-visual-studio-resources"></a>Uwzględnij zasoby programu Visual Studio
 Użyj elementu [extern](../../extensibility/extern-element.md) , aby uzyskać dostęp do plików, które definiują polecenia programu Visual Studio i menu, które są wymagane do umieszczenia elementów interfejsu użytkownika w IDE. Jeśli będziesz używać poleceń zdefiniowanych poza pakietem, użyj elementu [UsedCommands](../../extensibility/usedcommands-element.md) , aby poinformować program Visual Studio.

#### <a name="to-include-visual-studio-resources"></a>Aby uwzględnić zasoby programu Visual Studio

1. W górnej części elementu `CommandTable` należy dodać jeden element `Extern` dla każdego pliku zewnętrznego, który ma być przywoływany, i ustawić atrybut `href` na nazwę pliku. Aby uzyskać dostęp do zasobów programu Visual Studio, można odwoływać się do następujących plików nagłówkowych:

   - *Stdidcmd. h*: definiuje identyfikatory wszystkich poleceń udostępnianych przez program Visual Studio.

   - *Vsshlids. h*: zawiera identyfikatory poleceń dla menu programu Visual Studio.

2. Jeśli pakiet wywołuje wszystkie polecenia, które są zdefiniowane przez program Visual Studio lub przez inne pakiety, Dodaj `UsedCommands` element po elemencie `Commands`. Wypełnij ten element elementem [UsedCommand](../../extensibility/usedcommand-element.md) dla każdego wywoływanego polecenia, które nie jest częścią pakietu. Ustaw atrybuty `guid` i `id` elementów `UsedCommand` na wartości identyfikatora GUID i identyfikatora poleceń, które mają być wywoływane.

   Aby uzyskać więcej informacji na temat wyszukiwania identyfikatorów GUID i identyfikatorów poleceń programu Visual Studio, zobacz identyfikatory [GUID i identyfikatory poleceń programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Aby wywołać polecenia z innych pakietów, użyj identyfikatora GUID i identyfikatora polecenia, zgodnie z definicją w pliku *. vsct* dla tych pakietów.

### <a name="declare-ui-elements"></a>Zadeklaruj elementy interfejsu użytkownika
 Zadeklaruj wszystkie nowe elementy interfejsu użytkownika w `Symbols` sekcji pliku *. vsct* .

#### <a name="to-declare-ui-elements"></a>Aby zadeklarować elementy interfejsu użytkownika

1. W `Symbols` elementu Dodaj trzy elementy [GuidSymbol](../../extensibility/guidsymbol-element.md) . Każdy element `GuidSymbol` ma atrybut `name` i atrybut `value`. Ustaw atrybut `name` tak, aby odzwierciedlał cel elementu. Atrybut `value` przyjmuje identyfikator GUID. (Aby wygenerować identyfikator GUID, w menu **Narzędzia** wybierz polecenie **Utwórz identyfikator GUID**, a następnie wybierz pozycję **Format rejestru**).

     Pierwszy element `GuidSymbol` reprezentuje pakiet i zwykle nie ma elementów podrzędnych. Drugi `GuidSymbol` element reprezentuje zestaw poleceń i będzie zawierać wszystkie symbole, które definiują menu, grupy i polecenia. Trzeci element `GuidSymbol` reprezentuje swój magazyn obrazów i zawiera symbole dla wszystkich ikon poleceń. Jeśli nie masz poleceń, które używają ikon, możesz pominąć trzeci `GuidSymbol` elementu.

2. W `GuidSymbol` element, który reprezentuje zestaw poleceń, Dodaj co najmniej jeden element [IDSymbol](../../extensibility/idsymbol-element.md) . Każdy z nich reprezentuje menu, pasek narzędzi, grupę lub polecenie dodawane do interfejsu użytkownika.

     Dla każdego elementu `IDSymbol` ustaw atrybut `name` na nazwę, która będzie używana do odwoływania się do odpowiadającego menu, grupy lub polecenia, a następnie ustaw element `value` na liczbę szesnastkową, która będzie reprezentować identyfikator polecenia. Żadne dwa elementy `IDSymbol`, które mają ten sam element nadrzędny, nie mogą mieć tej samej wartości.

3. Jeśli którykolwiek z elementów interfejsu użytkownika wymaga ikon, Dodaj element `IDSymbol` dla każdej ikony do elementu `GuidSymbol`, który reprezentuje swój magazyn obrazu.

### <a name="put-ui-elements-in-the-ide"></a>Umieszczanie elementów interfejsu użytkownika w IDE
 Elementy [menu](../../extensibility/menus-element.md), [grupy](../../extensibility/groups-element.md)i [przyciski](../../extensibility/buttons-element.md) zawierają definicje wszystkich menu, grup i poleceń, które są zdefiniowane w pakiecie. Te menu, grupy i polecenia należy umieścić w IDE przy użyciu elementu [nadrzędnego](../../extensibility/parent-element.md) , który jest częścią definicji elementu interfejsu użytkownika lub za pomocą elementu [CommandPlacement](../../extensibility/commandplacement-element.md) , który jest zdefiniowany w innym miejscu.

 Każdy `Menu`, `Group`i `Button` elementu ma atrybut `guid` i `id`. Należy zawsze ustawić atrybut `guid` tak, aby pasował do nazwy elementu `GuidSymbol`, który reprezentuje zestaw poleceń, i ustawić atrybut `id` na nazwę elementu `IDSymbol`, który reprezentuje menu, grupę lub polecenie w sekcji `Symbols`.

#### <a name="to-define-ui-elements"></a>Aby zdefiniować elementy interfejsu użytkownika

1. Jeśli definiujesz nowe menu, podmenu, menu skrótów lub paski narzędzi, Dodaj element `Menus` do elementu `Commands`. Następnie dla każdego menu, które ma zostać utworzone, Dodaj element [menu](../../extensibility/menu-element.md) do elementu `Menus`.

    Ustaw atrybuty `guid` i `id` elementu `Menu`, a następnie ustaw atrybut `type` na żądany rodzaj menu. Możesz również ustawić atrybut `priority`, aby określić względne położenie menu w grupie nadrzędnej.

   > [!NOTE]
   > Atrybut `priority` nie ma zastosowania do pasków narzędzi i menu kontekstowych.

2. Wszystkie polecenia w środowisku IDE programu Visual Studio muszą być hostowane przez grupy poleceń, które są bezpośrednimi elementami podrzędnymi menu i pasków narzędzi. Jeśli dodajesz nowe menu lub paski narzędzi do IDE, muszą one zawierać nowe grupy poleceń. Możesz również dodawać grupy poleceń do istniejących menu i pasków narzędzi, aby można było wizualnie grupować polecenia.

    Po dodaniu nowych grup poleceń należy najpierw utworzyć element `Groups`, a następnie dodać do niego element [grupy](../../extensibility/group-element.md) dla każdej grupy poleceń.

    Ustaw atrybuty `guid` i `id` każdego elementu `Group`, a następnie ustaw atrybut `priority`, aby określić względne położenie grupy w menu nadrzędnym. Aby uzyskać więcej informacji, zobacz [Tworzenie grup przycisków do wielokrotnego użytku](../../extensibility/creating-reusable-groups-of-buttons.md).

3. Jeśli dodajesz nowe polecenia do IDE, Dodaj element `Buttons` do elementu `Commands`. Następnie dla każdego polecenia Dodaj element [Button](../../extensibility/button-element.md) do elementu `Buttons`.

   1. Ustaw atrybuty `guid` i `id` każdego elementu `Button`, a następnie ustaw atrybut `type` na żądany typ przycisku. Możesz również ustawić atrybut `priority`, aby określić względne położenie polecenia w grupie nadrzędnej.

       > [!NOTE]
       > Użyj `type="button"` dla standardowych poleceń menu i przycisków na paskach narzędzi.

   2. W `Button` elementu Dodaj element [Strings](../../extensibility/strings-element.md) , który zawiera element [ButtonText](../../extensibility/buttontext-element.md) i element [CommandName](../../extensibility/commandname-element.md) . Element `ButtonText` zawiera etykietę tekstową dla elementu menu lub etykietkę narzędzia dla przycisku paska narzędzi. Element `CommandName` zawiera nazwę polecenia, które ma być używane w poleceniu.

   3. Jeśli polecenie będzie miało ikonę, Utwórz element [Icon](../../extensibility/icon-element.md) w elemencie `Button` i ustaw jego atrybuty `guid` i `id` na element `Bitmap` dla ikony.

       > [!NOTE]
       > Przyciski paska narzędzi muszą mieć ikony.

   Aby uzyskać więcej informacji, zobacz [MenuCommands vs. OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015).

4. Jeśli dowolne z poleceń wymaga ikon, Dodaj element [mapy bitowe](../../extensibility/bitmaps-element.md) do elementu `Commands`. Następnie dla każdej ikony Dodaj element [bitmapy](../../extensibility/bitmap-element.md) do elementu `Bitmaps`. Jest to miejsce, w którym można określić lokalizację zasobu mapy bitowej. Aby uzyskać więcej informacji, zobacz [Dodawanie ikon do poleceń menu](../../extensibility/adding-icons-to-menu-commands.md).

   Można polegać na strukturze nadrzędnej w celu poprawnego umieszczania większości menu, grup i poleceń. W przypadku bardzo dużych poleceń lub gdy menu, grupy lub polecenia muszą występować w wielu miejscach, zalecamy określenie położenia poleceń.

#### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>Aby polegać na nadrzędnym umieszczeniu elementów interfejsu użytkownika w IDE

1. W przypadku typowych elementów nadrzędnych Utwórz `Parent` element w każdym `Menu`, `Group`i element `Command`, który jest zdefiniowany w pakiecie.

    Obiektem docelowym elementu `Parent` jest menu lub Grupa, która będzie zawierać menu, grupę lub polecenie.

   1. Ustaw atrybut `guid` na nazwę elementu `GuidSymbol`, który definiuje zestaw poleceń. Jeśli element docelowy nie jest częścią pakietu, użyj identyfikatora GUID dla tego zestawu poleceń, zgodnie z definicją w odpowiednim pliku *vsct* .

   2. Ustaw atrybut `id` tak, aby pasował do atrybutu `id` menu lub grupy docelowej. Aby zapoznać się z listą menu i grup, które są udostępniane przez program Visual Studio, zobacz identyfikatory [GUID i identyfikator menu programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) lub [identyfikatory GUID i identyfikator pasków narzędzi programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).

   Jeśli masz dużą liczbę elementów interfejsu użytkownika do umieszczenia w środowisku IDE lub jeśli masz elementy, które powinny się znajdować w wielu miejscach, zdefiniuj ich umieszczenie w elemencie [CommandPlacements](../../extensibility/commandplacements-element.md) , jak pokazano w poniższych krokach.

#### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>Aby umieścić elementy interfejsu użytkownika w IDE przy użyciu polecenia umieszczania

1. Po elemencie `Commands` Dodaj element `CommandPlacements`.

2. W `CommandPlacements` elementu Dodaj element `CommandPlacement` dla każdego menu, grupy lub polecenia do umieszczenia.

    Każdy element `CommandPlacement` lub element `Parent` umieszcza jedno menu, grupę lub polecenie w jednej lokalizacji IDE. Element interfejsu użytkownika może mieć tylko jeden element nadrzędny, ale może mieć wiele miejsc poleceń. Aby umieścić element interfejsu użytkownika w wielu lokalizacjach, Dodaj element `CommandPlacement` dla każdej lokalizacji.

3. Ustaw atrybuty `guid` i `id` każdego elementu `CommandPlacement` do menu lub grupy hostingu, tak jak w przypadku elementu `Parent`. Można również ustawić atrybut `priority`, aby określić względne położenie elementu interfejsu użytkownika.

   Można mieszać umieszczanie za pomocą elementu nadrzędnego i umieszczania poleceń. Jednak dla bardzo dużych zestawów poleceń zalecamy używanie tylko umieszczania poleceń.

### <a name="add-specialized-behaviors"></a>Dodawanie zachowań wyspecjalizowanych
 Można użyć elementu [CommandFlag](../../extensibility/command-flag-element.md) , aby zmodyfikować zachowanie menu i poleceń, na przykład w celu zmiany ich wyglądu i widoczności. Możesz również mieć wpływ na to, kiedy polecenie jest widoczne przy użyciu elementu [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) , lub Dodaj skróty klawiaturowe za pomocą elementu [powiązań](../../extensibility/keybindings-element.md) klawiszy. Niektóre rodzaje menu i poleceń mają już wbudowane zachowania specjalne.

#### <a name="to-add-specialized-behaviors"></a>Aby dodać zachowania specjalne

1. Aby element interfejsu użytkownika był widoczny tylko w niektórych kontekstach interfejsu użytkownika, na przykład w przypadku załadowania rozwiązania, należy użyć ograniczeń widoczności.

   1. Po elemencie `Commands` Dodaj element `VisibilityConstraints`.

   2. Dla każdego elementu interfejsu użytkownika, aby ograniczyć, Dodaj element [VisibilityItem](../../extensibility/visibilityitem-element.md) .

   3. Dla każdego elementu `VisibilityItem` ustaw atrybuty `guid` i `id` do menu, grupy lub polecenia, a następnie ustaw atrybut `context` na żądany kontekst interfejsu użytkownika, zgodnie z definicją w klasie <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>.

2. Aby ustawić widoczność lub dostępność elementu interfejsu użytkownika w kodzie, Użyj co najmniej jednej z następujących flag polecenia:

   - `DefaultDisabled`

   - `DefaultInvisible`

   - `DynamicItemStart`

   - `DynamicVisibility`

   - `NoShowOnMenuController`

   - `NotInTBList`

   Aby uzyskać więcej informacji, zobacz element [CommandFlag](../../extensibility/command-flag-element.md) .

3. Aby zmienić sposób wyświetlania elementu lub zmienić jego wygląd dynamicznie, Użyj co najmniej jednej z następujących flag poleceń:

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

   Aby uzyskać więcej informacji, zobacz element [CommandFlag](../../extensibility/command-flag-element.md) .

4. Aby zmienić sposób, w jaki element reaguje po odebraniu poleceń, Użyj co najmniej jednej z następujących flag poleceń:

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

   Aby uzyskać więcej informacji, zobacz element [CommandFlag](../../extensibility/command-flag-element.md) .

5. Aby dołączyć skrót klawiaturowy zależny od menu do menu lub elementu w menu, Dodaj znak handlowego "i" (&) w elemencie `ButtonText` dla elementu menu lub menu. Znak, który następuje po znaku handlowego ", jest aktywnym skrótem klawiaturowym, gdy menu nadrzędne jest otwarte.

6. Aby dołączyć niezależny do menu skrót klawiaturowy do polecenia, użyj elementu [powiązania](../../extensibility/keybindings-element.md) klawiszy. Aby uzyskać więcej informacji, zobacz element [powiązanie klawiszy](../../extensibility/keybinding-element.md) .

7. Aby zlokalizować tekst menu, użyj elementu `LocCanonicalName`. Aby uzyskać więcej informacji, zobacz element [Strings](../../extensibility/strings-element.md) .

   Niektóre typy menu i przycisków zawierają wyspecjalizowane zachowania. Na poniższej liście opisano niektóre wyspecjalizowane typy menu i przycisków. W przypadku innych typów Zobacz opisy atrybutów `types` w [menu](../../extensibility/menu-element.md), [przycisk](../../extensibility/button-element.md)i elementy [kombi](../../extensibility/combo-element.md) .

   - Pole kombi: pole kombi jest listą rozwijaną, która może być używana na pasku narzędzi. Aby dodać pola kombi do interfejsu użytkownika, Utwórz element [combo](../../extensibility/combos-element.md) w `Commands` elemencie. Następnie Dodaj do elementu `Combos` elementu `Combo` dla każdego pola kombi do dodania. elementy `Combo` mają takie same atrybuty i elementy podrzędne jak elementy `Button`, a także mają atrybuty `DefaultWidth` i `idCommandList`. Atrybut `DefaultWidth` ustawia szerokość w pikselach, a atrybut `idCommandList` wskazuje identyfikator polecenia, który jest używany do wypełniania pola kombi.

   - Kontroler menu: kontroler menu jest przyciskiem, który ma strzałkę obok niej. Kliknięcie strzałki spowoduje otwarcie listy. Aby dodać kontroler menu do interfejsu użytkownika, Utwórz element `Menu` i ustaw jego atrybut `type` na `MenuController` lub `MenuControllerLatched`, w zależności od żądanego zachowania. Aby wypełnić kontroler menu, ustaw go jako element nadrzędny elementu `Group`. Kontroler menu będzie wyświetlał wszystkie elementy podrzędne tej grupy na liście rozwijanej.

## <a name="see-also"></a>Zobacz także
- [Poszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md)
- [Pliki tabeli poleceń programu Visual Studio (. vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Dokumentacja schematu XML VSCT](../../extensibility/vsct-xml-schema-reference.md)