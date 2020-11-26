---
title: Projekt. Pliki vsct | Microsoft Docs
description: Dowiedz się, jak tworzyć pliki. vsct, które dodają elementy menu, paski narzędzi i inne elementy interfejsu użytkownika do zintegrowanego środowiska programistycznego (IDE) programu Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: e0aeb601449ffcc47b7f7786825ee222b8b6ac5b
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2020
ms.locfileid: "96190086"
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

2. Dodaj wymagane przestrzenie nazw do `CommandTable` elementu, jak pokazano w następującym przykładzie:

    ```xml
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"
        xmlns:xs="http://www.w3.org/2001/XMLSchema">

    ```

3. W `CommandTable` elemencie Dodaj `Commands` element, aby hostować wszystkie niestandardowe menu, paski narzędzi, grupy poleceń i polecenia. Aby można było załadować niestandardowe elementy interfejsu użytkownika, `Commands` element musi mieć `Package` ustawiony atrybut na nazwę pakietu.

     Po `Commands` elemencie Dodaj `Symbols` element, aby zdefiniować identyfikatory GUID pakietu oraz nazwy i identyfikatory poleceń dla elementów interfejsu użytkownika.

### <a name="include-visual-studio-resources"></a>Uwzględnij zasoby programu Visual Studio
 Użyj elementu [extern](../../extensibility/extern-element.md) , aby uzyskać dostęp do plików, które definiują polecenia programu Visual Studio i menu, które są wymagane do umieszczenia elementów interfejsu użytkownika w IDE. Jeśli będziesz używać poleceń zdefiniowanych poza pakietem, użyj elementu [UsedCommands](../../extensibility/usedcommands-element.md) , aby poinformować program Visual Studio.

#### <a name="to-include-visual-studio-resources"></a>Aby uwzględnić zasoby programu Visual Studio

1. W górnej części `CommandTable` elementu Dodaj jeden `Extern` element dla każdego pliku zewnętrznego, który ma zostać przywoływany, a następnie ustaw `href` atrybut na nazwę pliku. Aby uzyskać dostęp do zasobów programu Visual Studio, można odwoływać się do następujących plików nagłówkowych:

   - *Stdidcmd. h*: definiuje identyfikatory wszystkich poleceń udostępnianych przez program Visual Studio.

   - *Vsshlids. h*: zawiera identyfikatory poleceń dla menu programu Visual Studio.

2. Jeśli pakiet wywołuje wszystkie polecenia, które są zdefiniowane przez program Visual Studio lub przez inne pakiety, Dodaj `UsedCommands` element po `Commands` elemencie. Wypełnij ten element elementem [UsedCommand](../../extensibility/usedcommand-element.md) dla każdego wywoływanego polecenia, które nie jest częścią pakietu. Ustaw `guid` atrybuty i `id` `UsedCommand` elementów na identyfikator GUID oraz wartości identyfikatorów poleceń, które mają być wywoływane.

   Aby uzyskać więcej informacji na temat wyszukiwania identyfikatorów GUID i identyfikatorów poleceń programu Visual Studio, zobacz identyfikatory [GUID i identyfikatory poleceń programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Aby wywołać polecenia z innych pakietów, użyj identyfikatora GUID i identyfikatora polecenia, zgodnie z definicją w pliku *. vsct* dla tych pakietów.

### <a name="declare-ui-elements"></a>Zadeklaruj elementy interfejsu użytkownika
 Zadeklaruj wszystkie nowe elementy interfejsu użytkownika w `Symbols` sekcji pliku *. vsct* .

#### <a name="to-declare-ui-elements"></a>Aby zadeklarować elementy interfejsu użytkownika

1. W `Symbols` elemencie Dodaj trzy elementy [GuidSymbol](../../extensibility/guidsymbol-element.md) . Każdy `GuidSymbol` element ma `name` atrybut i `value` atrybut. Ustaw `name` atrybut tak, aby odzwierciedlał cel elementu. `value`Atrybut przyjmuje identyfikator GUID. (Aby wygenerować identyfikator GUID, w menu **Narzędzia** wybierz polecenie **Utwórz identyfikator GUID**, a następnie wybierz pozycję **Format rejestru**).

     Pierwszy `GuidSymbol` element reprezentuje pakiet i zwykle nie ma elementów podrzędnych. Drugi `GuidSymbol` element reprezentuje zestaw poleceń i będzie zawierać wszystkie symbole, które definiują menu, grupy i polecenia. Trzeci `GuidSymbol` element reprezentuje magazyn obrazów i zawiera symbole dla wszystkich ikon poleceń. Jeśli nie masz poleceń, które używają ikon, możesz pominąć trzeci `GuidSymbol` element.

2. W `GuidSymbol` elemencie, który reprezentuje zestaw poleceń, Dodaj co najmniej jeden element [IDSymbol](../../extensibility/idsymbol-element.md) . Każdy z nich reprezentuje menu, pasek narzędzi, grupę lub polecenie dodawane do interfejsu użytkownika.

     Dla każdego `IDSymbol` elementu Ustaw `name` atrybut na nazwę, która będzie używana do odwoływania się do odpowiadającego menu, grupy lub polecenia, a następnie ustaw `value` element na liczbę szesnastkową, która będzie reprezentować identyfikator polecenia. Żadne dwa `IDSymbol` elementy, które mają ten sam element nadrzędny, nie mogą mieć tej samej wartości.

3. Jeśli którykolwiek z elementów interfejsu użytkownika wymaga ikon, Dodaj `IDSymbol` element dla każdej ikony do `GuidSymbol` elementu, który reprezentuje swój magazyn obrazu.

### <a name="put-ui-elements-in-the-ide"></a>Umieszczanie elementów interfejsu użytkownika w IDE
 Elementy [menu](../../extensibility/menus-element.md), [grupy](../../extensibility/groups-element.md)i [przyciski](../../extensibility/buttons-element.md) zawierają definicje wszystkich menu, grup i poleceń, które są zdefiniowane w pakiecie. Te menu, grupy i polecenia należy umieścić w IDE przy użyciu elementu [nadrzędnego](../../extensibility/parent-element.md) , który jest częścią definicji elementu interfejsu użytkownika lub za pomocą elementu [CommandPlacement](../../extensibility/commandplacement-element.md) , który jest zdefiniowany w innym miejscu.

 Każdy `Menu` `Group` element,, i `Button` ma `guid` atrybut i `id` atrybut. Zawsze ustawiaj `guid` atrybut na zgodny z nazwą elementu, `GuidSymbol` który reprezentuje zestaw poleceń, i ustaw `id` atrybut na nazwę `IDSymbol` elementu, który reprezentuje menu, grupę lub polecenie w `Symbols` sekcji.

#### <a name="to-define-ui-elements"></a>Aby zdefiniować elementy interfejsu użytkownika

1. Jeśli definiujesz nowe menu, podmenu, menu skrótów lub paski narzędzi, Dodaj `Menus` element do `Commands` elementu. Następnie dla każdego menu, które ma zostać utworzone, Dodaj element [menu](../../extensibility/menu-element.md) do `Menus` elementu.

    Ustaw `guid` atrybuty i `id` `Menu` elementu, a następnie ustaw `type` atrybut na typ tworzonego menu. Możesz również ustawić atrybut, `priority` Aby określić względne położenie menu w grupie nadrzędnej.

   > [!NOTE]
   > Ten `priority` atrybut nie ma zastosowania do pasków narzędzi i menu kontekstowych.

2. Wszystkie polecenia w środowisku IDE programu Visual Studio muszą być hostowane przez grupy poleceń, które są bezpośrednimi elementami podrzędnymi menu i pasków narzędzi. Jeśli dodajesz nowe menu lub paski narzędzi do IDE, muszą one zawierać nowe grupy poleceń. Możesz również dodawać grupy poleceń do istniejących menu i pasków narzędzi, aby można było wizualnie grupować polecenia.

    Po dodaniu nowych grup poleceń należy najpierw utworzyć `Groups` element, a następnie dodać do niego element [grupy](../../extensibility/group-element.md) dla każdej grupy poleceń.

    Ustaw `guid` atrybuty i `id` każdego `Group` elementu, a następnie ustaw `priority` atrybut, aby określić względne położenie grupy w menu nadrzędnym. Aby uzyskać więcej informacji, zobacz [Tworzenie grup przycisków do wielokrotnego użytku](../../extensibility/creating-reusable-groups-of-buttons.md).

3. Jeśli dodajesz nowe polecenia do IDE, Dodaj `Buttons` element do `Commands` elementu. Następnie dla każdego polecenia Dodaj element [Button](../../extensibility/button-element.md) do `Buttons` elementu.

   1. Ustaw `guid` atrybuty i `id` dla każdego `Button` elementu, a następnie ustaw `type` atrybut na żądany typ przycisku. Możesz również ustawić atrybut, `priority` Aby określić względne położenie polecenia w grupie nadrzędnej.

       > [!NOTE]
       > Użyj `type="button"` dla standardowych poleceń menu i przycisków na paskach narzędzi.

   2. W `Button` elemencie Dodaj element [Strings](../../extensibility/strings-element.md) , który zawiera element [ButtonText](../../extensibility/buttontext-element.md) i element [CommandName](../../extensibility/commandname-element.md) . `ButtonText`Element zawiera etykietę tekstową dla elementu menu lub etykietki narzędzia dla przycisku paska narzędzi. `CommandName`Element zawiera nazwę polecenia, które ma być używane w poleceniu.

   3. Jeśli polecenie będzie miało ikonę, Utwórz element [ikony](../../extensibility/icon-element.md) w `Button` elemencie i ustaw jego `guid` `id` atrybuty i na `Bitmap` element ikony.

       > [!NOTE]
       > Przyciski paska narzędzi muszą mieć ikony.

   Aby uzyskać więcej informacji, zobacz [MenuCommands vs. OleMenuCommands](/previous-versions/visualstudio/visual-studio-2015/misc/menucommands-vs-olemenucommands?preserve-view=true&view=vs-2015).

4. Jeśli którekolwiek z poleceń wymagają ikon, Dodaj element [bitmaps](../../extensibility/bitmaps-element.md) do `Commands` elementu. Następnie dla każdej ikony Dodaj element [bitmapy](../../extensibility/bitmap-element.md) do `Bitmaps` elementu. Jest to miejsce, w którym można określić lokalizację zasobu mapy bitowej. Aby uzyskać więcej informacji, zobacz [Dodawanie ikon do poleceń menu](../../extensibility/adding-icons-to-menu-commands.md).

   Można polegać na strukturze nadrzędnej w celu poprawnego umieszczania większości menu, grup i poleceń. W przypadku bardzo dużych poleceń lub gdy menu, grupy lub polecenia muszą występować w wielu miejscach, zalecamy określenie położenia poleceń.

#### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>Aby polegać na nadrzędnym umieszczeniu elementów interfejsu użytkownika w IDE

1. W przypadku typowych elementów nadrzędnych Utwórz `Parent` element w każdym `Menu` , `Group` , i `Command` element, który jest zdefiniowany w pakiecie.

    Obiektem docelowym `Parent` elementu jest menu lub Grupa, która będzie zawierać menu, grupę lub polecenie.

   1. Ustaw `guid` atrybut na nazwę `GuidSymbol` elementu, który definiuje zestaw poleceń. Jeśli element docelowy nie jest częścią pakietu, użyj identyfikatora GUID dla tego zestawu poleceń, zgodnie z definicją w odpowiednim pliku *vsct* .

   2. Ustaw `id` atrybut pasujący do `id` atrybutu menu lub grupy docelowej. Aby zapoznać się z listą menu i grup, które są udostępniane przez program Visual Studio, zobacz identyfikatory [GUID i identyfikator menu programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) lub [identyfikatory GUID i identyfikator pasków narzędzi programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).

   Jeśli masz dużą liczbę elementów interfejsu użytkownika do umieszczenia w środowisku IDE lub jeśli masz elementy, które powinny się znajdować w wielu miejscach, zdefiniuj ich umieszczenie w elemencie [CommandPlacements](../../extensibility/commandplacements-element.md) , jak pokazano w poniższych krokach.

#### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>Aby umieścić elementy interfejsu użytkownika w IDE przy użyciu polecenia umieszczania

1. Po elemencie `Commands` dodaj element `CommandPlacements`.

2. W `CommandPlacements` elemencie Dodaj `CommandPlacement` element dla każdego menu, grupy lub polecenia do miejsca.

    Każdy `CommandPlacement` element lub `Parent` element umieszcza jedno menu, grupę lub polecenie w jednej lokalizacji IDE. Element interfejsu użytkownika może mieć tylko jeden element nadrzędny, ale może mieć wiele miejsc poleceń. Aby umieścić element interfejsu użytkownika w wielu lokalizacjach, Dodaj `CommandPlacement` element dla każdej lokalizacji.

3. Ustaw `guid` atrybuty i `id` każdego `CommandPlacement` elementu na menu hostingu lub grupę, tak jak dla `Parent` elementu. Można również ustawić atrybut, `priority` Aby określić względne położenie elementu interfejsu użytkownika.

   Można mieszać umieszczanie za pomocą elementu nadrzędnego i umieszczania poleceń. Jednak dla bardzo dużych zestawów poleceń zalecamy używanie tylko umieszczania poleceń.

### <a name="add-specialized-behaviors"></a>Dodawanie zachowań wyspecjalizowanych
 Można użyć elementu [CommandFlag](../../extensibility/command-flag-element.md) , aby zmodyfikować zachowanie menu i poleceń, na przykład w celu zmiany ich wyglądu i widoczności. Możesz również mieć wpływ na to, kiedy polecenie jest widoczne przy użyciu elementu [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) , lub Dodaj skróty klawiaturowe za pomocą elementu [powiązań](../../extensibility/keybindings-element.md) klawiszy. Niektóre rodzaje menu i poleceń mają już wbudowane zachowania specjalne.

#### <a name="to-add-specialized-behaviors"></a>Aby dodać zachowania specjalne

1. Aby element interfejsu użytkownika był widoczny tylko w niektórych kontekstach interfejsu użytkownika, na przykład w przypadku załadowania rozwiązania, należy użyć ograniczeń widoczności.

   1. Po elemencie `Commands` dodaj element `VisibilityConstraints`.

   2. Dla każdego elementu interfejsu użytkownika, aby ograniczyć, Dodaj element [VisibilityItem](../../extensibility/visibilityitem-element.md) .

   3. Dla każdego `VisibilityItem` elementu Ustaw `guid` `id` atrybuty i na menu, grupę lub polecenie, a następnie ustaw `context` atrybut na kontekst interfejsu użytkownika, zgodnie z definicją w <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> klasie.

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

5. Aby dołączyć skrót klawiaturowy zależny od menu do menu lub elementu w menu, Dodaj znak handlowego "i" (&) w `ButtonText` elemencie menu lub elementu menu. Znak, który następuje po znaku handlowego ", jest aktywnym skrótem klawiaturowym, gdy menu nadrzędne jest otwarte.

6. Aby dołączyć niezależny do menu skrót klawiaturowy do polecenia, użyj elementu [powiązania](../../extensibility/keybindings-element.md) klawiszy. Aby uzyskać więcej informacji, zobacz element [powiązanie klawiszy](../../extensibility/keybinding-element.md) .

7. Aby zlokalizować tekst menu, użyj `LocCanonicalName` elementu. Aby uzyskać więcej informacji, zobacz element [Strings](../../extensibility/strings-element.md) .

   Niektóre typy menu i przycisków zawierają wyspecjalizowane zachowania. Na poniższej liście opisano niektóre wyspecjalizowane typy menu i przycisków. W przypadku innych typów zobacz `types` opisy atrybutów w [menu](../../extensibility/menu-element.md), [przycisk](../../extensibility/button-element.md)i elementy [kombi](../../extensibility/combo-element.md) .

   - Pole kombi: pole kombi jest listą rozwijaną, która może być używana na pasku narzędzi. Aby dodać pola kombi do interfejsu użytkownika, Utwórz element [kombi](../../extensibility/combos-element.md) w `Commands` elemencie. Następnie Dodaj do `Combos` elementu element `Combo` dla każdego pola kombi do dodania. `Combo` elementy mają te same atrybuty i elementy podrzędne jako `Button` elementy, a `DefaultWidth` także `idCommandList` atrybuty i. `DefaultWidth`Atrybut ustawia szerokość w pikselach, a `idCommandList` ATRYBUT wskazuje identyfikator polecenia, który jest używany do wypełniania pola kombi.

   - Kontroler menu: kontroler menu jest przyciskiem, który ma strzałkę obok niej. Kliknięcie strzałki spowoduje otwarcie listy. Aby dodać kontroler menu do interfejsu użytkownika, Utwórz `Menu` element i ustaw jego `type` atrybut na lub, w zależności od żądanego `MenuController` `MenuControllerLatched` zachowania. Aby wypełnić kontroler menu, ustaw go jako element nadrzędny `Group` elementu. Kontroler menu będzie wyświetlał wszystkie elementy podrzędne tej grupy na liście rozwijanej.

## <a name="see-also"></a>Zobacz też
- [Poszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md)
- [Pliki tabeli poleceń programu Visual Studio (. vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Dokumentacja schematu XML VSCT](../../extensibility/vsct-xml-schema-reference.md)