---
title: Tworzenie. Pliki Vsct | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 27624f4b5336d91b30410303c9fd3823cc00fb88
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56620918"
---
# <a name="author-vsct-files"></a>Tworzenie plików vsct
W tym dokumencie pokazano, jak tworzyć *vsct* plik, aby dodać elementy menu, paski narzędzi i inne elementy interfejsu użytkownika do programu Visual Studio zintegrowane środowisko programistyczne (IDE). Wykonaj następujące czynności, po dodaniu elementów interfejsu użytkownika do pakietu Visual Studio (pakietu VSPackage), który nie ma jeszcze *vsct* pliku.

 Dla nowych projektów, zalecane jest użycie szablonu pakietu programu Visual Studio, ponieważ generuje on *vsct* pliku, który w zależności od ustawień, jest już wymagane elementy dla polecenia menu, okna narzędzi lub edytora niestandardowego . Można to modyfikować *vsct* pliku do wymagań Twojego pakietu VSPackage. Aby uzyskać więcej informacji na temat sposobu modyfikowania *vsct* plików, zobacz przykłady w [rozszerzenia menu i poleceń](../../extensibility/extending-menus-and-commands.md).

## <a name="author-the-file"></a>Tworzenie pliku
 Autor *vsct* pliku w tych etapów: Tworzenie struktury plików i zasobów, Zadeklaruj elementy interfejsu użytkownika, umieść elementy interfejsu użytkownika w środowisku IDE i Dodaj wszelkie specjalne zachowania.

### <a name="file-structure"></a>Struktura plików
 Podstawowa struktura *vsct* plik jest [CommandTable](../../extensibility/commandtable-element.md) element główny, który zawiera [polecenia](../../extensibility/commands-element.md) elementu i [symbole](../../extensibility/symbols-element.md) elementu.

#### <a name="to-create-the-file-structure"></a>Tworzenie struktury pliku

1.  Dodaj *vsct* plik do projektu, wykonując kroki opisane w [jak: Tworzenie pliku vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md).

2. Dodaj wymagane przestrzenie nazw do `CommandTable` elementu, jak pokazano w poniższym przykładzie:

    ```xml
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"
        xmlns:xs="http://www.w3.org/2001/XMLSchema">

    ```

3.  W `CommandTable` elementu Dodawanie `Commands` element do obsługi wszystkich niestandardowych menu, paski narzędzi, grup poleceń i polecenia. Tak, aby załadować niestandardowe elementy interfejsu użytkownika, `Commands` element musi mieć jej `Package` atrybut ustawiony na nazwę pakietu.

     Po `Commands` elementu Dodawanie `Symbols` element, aby zdefiniować identyfikatorów GUID dla pakietu i nazwy i identyfikatory poleceń Twoje elementów interfejsu użytkownika.

### <a name="include-visual-studio-resources"></a>Dołączanie zasobów w programie Visual Studio
 Użyj [Extern](../../extensibility/extern-element.md) elementu, aby uzyskać dostęp do plików, które definiują poleceń programu Visual Studio i menu, które są wymagane do umieszczenia elementów interfejsu użytkownika w środowisku IDE. Jeśli użyjesz polecenia zdefiniowane poza pakietu, należy użyć [UsedCommands](../../extensibility/usedcommands-element.md) elementu, aby poinformować program Visual Studio.

#### <a name="to-include-visual-studio-resources"></a>Aby dołączyć zasoby programu Visual Studio

1. W górnej części `CommandTable` elementu, dodaj je `Extern` elementu dla każdego pliku zewnętrznego, odwołania i ustawiania `href` atrybut nazwy pliku. Możesz odwołać się następujące pliki nagłówków, aby uzyskać dostęp do zasobów programu Visual Studio:

   -   *Stdidcmd.h*: Definiuje identyfikatorów dla wszystkich poleceń udostępnianych przez program Visual Studio.

   -   *Vsshlids.h*: Zawiera identyfikatory poleceń menu programu Visual Studio.

2. Jeśli pakiet wymaga dowolne polecenia, które zostały zdefiniowane przez program Visual Studio lub innych pakietów, należy dodać `UsedCommands` elementu po `Commands` elementu. Wypełnij ten element z [UsedCommand](../../extensibility/usedcommand-element.md) elementu dla każdego polecenia, oznacza to wywołanie nie jest częścią pakietu. Ustaw `guid` i `id` atrybuty `UsedCommand` elementy do wartości Identyfikator GUID i identyfikator polecenia do wywołania.

   Aby uzyskać więcej informacji o tym, jak znaleźć polecenia identyfikatory GUID i identyfikatory programu Visual Studio, zobacz [poleceń identyfikatory GUID i identyfikatory programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Aby wywołać poleceń z innych pakietów, należy użyć identyfikatora GUID i identyfikator polecenia zgodnie z definicją w *vsct* tych pakietów w pliku.

### <a name="declare-ui-elements"></a>Zadeklaruj elementy interfejsu użytkownika
 Zadeklaruj nowych elementów interfejsu użytkownika w `Symbols` części *vsct* pliku.

#### <a name="to-declare-ui-elements"></a>Aby zadeklarować elementy interfejsu użytkownika

1.  W `Symbols` elementu, Dodaj trzy [GuidSymbol](../../extensibility/guidsymbol-element.md) elementów. Każdy `GuidSymbol` element ma `name` atrybutu i `value` atrybutu. Ustaw `name` atrybutu, aby odzwierciedlały celem elementu. `value` Atrybut przyjmuje postać identyfikatora GUID. (Można wygenerować identyfikatora GUID na **narzędzia** menu, wybierz opcję **Utwórz GUID**, a następnie wybierz pozycję **Format rejestru**.)

     Pierwszy `GuidSymbol` element, który reprezentuje pakiet, a zwykle nie ma elementów podrzędnych. Drugi `GuidSymbol` element reprezentuje polecenie Ustaw i będzie zawierać wszystkie symbole, które definiują menu, grup i poleceń. Trzeci `GuidSymbol` element reprezentuje swoje magazynu obrazów i zawiera symbole dla wszystkich ikony dla poleceń. Jeśli nie masz żadnych poleceń korzystających z ikon, można pominąć trzeci `GuidSymbol` elementu.

2.  W `GuidSymbol` elementu, który reprezentuje zestaw poleceń, Dodaj jeden lub kilka [IDSymbol](../../extensibility/idsymbol-element.md) elementów. Każdy z nich reprezentuje menu, pasek narzędzi, grupy lub polecenia, które dodajesz do Interfejsu użytkownika.

     Dla każdego `IDSymbol` elementu, ustaw `name` atrybutu nazwa będzie używana do odwoływania się do odpowiedniego menu, grupy lub polecenia, a następnie ustaw `value` elementu liczbę szesnastkową, która będzie reprezentowała jego identyfikator polecenia. Nie dwóch `IDSymbol` elementy, które mają ten sam nadrzędny element może mieć taką samą wartość.

3.  Jeśli dowolne elementy interfejsu użytkownika wymaga ikony, należy dodać `IDSymbol` elementu dla każdego ikonę, aby `GuidSymbol` elementu, który reprezentuje magazynu w obrazie.

### <a name="put-ui-elements-in-the-ide"></a>Umieść elementy interfejsu użytkownika w środowisku IDE
 [Menu](../../extensibility/menus-element.md), [grup](../../extensibility/groups-element.md), i [przyciski](../../extensibility/buttons-element.md) elementy zawierają definicje dla wszystkich menu, grup i poleceń, które są zdefiniowane w pakiecie. Umieść następujące menu, grupy i polecenia w środowisku IDE, za pomocą [nadrzędnego](../../extensibility/parent-element.md) elementu, który jest częścią definicji elementu interfejsu użytkownika lub za pomocą [CommandPlacement](../../extensibility/commandplacement-element.md) element, który jest zdefiniowany w innym miejscu.

 Każdy `Menu`, `Group`, i `Button` element ma `guid` atrybutu i `id` atrybutu. Zawsze wartość `guid` atrybutu do dopasowania nazwy `GuidSymbol` elementu, który reprezentuje polecenie ustawić i `id` atrybutu nazwy `IDSymbol` elementu, który reprezentuje użytkownika menu, grupę lub polecenie `Symbols`sekcji.

#### <a name="to-define-ui-elements"></a>Aby zdefiniować elementy interfejsu użytkownika

1. Jeśli definiujesz nowe menu, podmenu, menu skrótów i paski narzędzi, należy dodać `Menus` elementu `Commands` elementu. Następnie dla każdego menu, który ma zostać utworzony, Dodaj [Menu](../../extensibility/menu-element.md) elementu `Menus` elementu.

    Ustaw `guid` i `id` atrybuty `Menu` elementu, a następnie ustaw `type` atrybutu rodzaj elementu menu, które chcesz. Możesz też ustawić opcję `priority` atrybutu, aby ustanowić względne położenie menu w grupie nadrzędnej.

   > [!NOTE]
   >  `priority` Atrybut nie ma zastosowania do pasków narzędzi i menu kontekstowego.

2. Wszystkie polecenia w środowisku IDE programu Visual Studio musi być hostowany przez polecenie grup, które są bezpośrednimi elementami podrzędnymi menu i paski narzędzi. Jeśli dodajesz nowe menu i paski narzędzi do środowiska IDE programu zawierają one nowe grupy polecenia. Może również dodać grup poleceń do istniejącego menu i paski narzędzi, dzięki czemu można pogrupować poleceń.

    Po dodaniu nowych grup poleceń, należy najpierw utworzyć `Groups` elementu, a następnie dodać do niego [grupy](../../extensibility/group-element.md) elementu dla każdej grupy polecenia.

    Ustaw `guid` i `id` atrybuty każdego `Group` elementu, a następnie ustaw `priority` atrybutu, aby ustanowić względne położenie grupy menu nadrzędnego. Aby uzyskać więcej informacji, zobacz [tworzenie wielokrotnego użytku grup przycisków](../../extensibility/creating-reusable-groups-of-buttons.md).

3. Jeśli dodajesz nowe polecenia do IDE, Dodaj `Buttons` elementu `Commands` elementu. Następnie dla każdego polecenia, należy dodać [przycisk](../../extensibility/button-element.md) elementu `Buttons` elementu.

   1.  Ustaw `guid` i `id` atrybuty każdego `Button` elementu, a następnie ustaw `type` atrybutu z rodzajem przycisku. Możesz też ustawić opcję `priority` atrybutu, aby ustanowić względne położenie polecenia w grupie nadrzędnej.

       > [!NOTE]
       >  Użyj `type="button"` polecenia standardowe menu i przycisków na paskach narzędzi.

   2.  W `Button` elementu Dodawanie [ciągi](../../extensibility/strings-element.md) element, który zawiera [ButtonText](../../extensibility/buttontext-element.md) elementu i [CommandName](../../extensibility/commandname-element.md) elementu. `ButtonText` Element udostępnia etykietę tekstową dla elementu menu lub etykietkę narzędzia dla przycisku paska narzędzi. `CommandName` Element zawiera nazwę polecenia można również użyć w poleceniu.

   3.  Jeśli polecenie będzie miał ikony, należy utworzyć [ikonę](../../extensibility/icon-element.md) elementu w `Button` elementu, a następnie ustaw jego `guid` i `id` atrybuty do `Bitmap` element ikony.

       > [!NOTE]
       >  Przyciski paska narzędzi muszą mieć ikon.

   Aby uzyskać więcej informacji, zobacz [MenuCommands programu vs. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md).

4. Jeśli dowolny poleceń wymagają ikony, należy dodać [mapy bitowe](../../extensibility/bitmaps-element.md) elementu `Commands` elementu. Następnie dla każdej ikony, należy dodać [mapy bitowej](../../extensibility/bitmap-element.md) elementu `Bitmaps` elementu. Jest to, gdzie możesz określić lokalizację zasób mapy bitowej. Aby uzyskać więcej informacji, zobacz [dodawanie ikon do poleceń menu](../../extensibility/adding-icons-to-menu-commands.md).

   Możesz polegać na strukturze element nadrzędny poprawnie umieścić Większość menu, grupy i polecenia. Dla polecenia bardzo dużych zestawów lub gdy menu, grupy lub polecenia musi znajdować się w wielu miejscach, firma Microsoft zaleca, aby określić położenie polecenia.

#### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>Opierać się na element nadrzędny, aby umieścić elementy interfejsu użytkownika w środowisku IDE

1. W przypadku typowej element nadrzędny, utworzyć `Parent` elementu w każdym `Menu`, `Group`, i `Command` element, który jest zdefiniowany w pakiecie.

    Celem `Parent` element jest menu lub grupy, która będzie zawierać menu, grupy lub polecenia.

   1.  Ustaw `guid` atrybutu nazwy `GuidSymbol` element, który definiuje zestaw poleceń. Jeśli element docelowy nie jest częścią pakietu, użyj identyfikatora guid dla tego zestawu poleceń zgodnie z definicją w odpowiednich *vsct* pliku.

   2.  Ustaw `id` atrybutu do dopasowania `id` atrybut menu docelowego lub grupy. Aby uzyskać listę menu i grup, które są dostępne w programie Visual Studio, zobacz [menu identyfikatory GUID i identyfikatory programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) lub [pasków narzędzi identyfikatory GUID i identyfikatory programu Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).

   Jeśli masz dużą liczbę elementów interfejsu użytkownika można umieścić w IDE lub w przypadku elementów, które powinny się wyświetlać w wielu miejscach, zdefiniuj ich rozmieszczenia w [CommandPlacements](../../extensibility/commandplacements-element.md) elementu, jak pokazano w poniższych krokach.

#### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>Aby użyć położenie polecenia można umieścić elementy interfejsu użytkownika w środowisku IDE

1. Po `Commands` elementu Dodawanie `CommandPlacements` elementu.

2. W `CommandPlacements` elementu Dodawanie `CommandPlacement` elementu dla każdego menu, grupy lub polecenie, aby umieścić.

    Każdy `CommandPlacement` element lub `Parent` element umieszcza jeden menu, grupy lub polecenia w jednym miejscu środowiska IDE. Element interfejsu użytkownika może mieć tylko jedną jednostkę nadrzędną, ale może mieć wiele angażowania polecenia. Aby umieścić element interfejsu użytkownika w wielu lokalizacjach, należy dodać `CommandPlacement` elementu dla każdej lokalizacji.

3. Ustaw `guid` i `id` atrybuty każdego `CommandPlacement` elementu do hostingu menu lub grupy, podobnie jak w przypadku `Parent` elementu. Można również ustawić `priority` atrybutu, aby ustanowić względne położenie elementu interfejsu użytkownika.

   Możesz mieszać umieszczania przez element nadrzędny i położenie polecenia. Dla polecenia bardzo dużych zestawów, zalecamy użycie tylko położenie polecenia.

### <a name="add-specialized-behaviors"></a>Dodaj specjalne zachowania
 Możesz użyć [CommandFlag](../../extensibility/command-flag-element.md) element, aby zmodyfikować zachowanie, menu i poleceń, na przykład, aby zmienić ich wyglądu i widoczność. Użytkownik może również wpływać na gdy polecenie jest widoczna przy użyciu [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) elementu, lub dodawać skróty klawiaturowe przy użyciu [powiązania klawiszy](../../extensibility/keybindings-element.md) elementu. Niektóre rodzaje menu i poleceń już mieć wyspecjalizowane wbudowanych zachowań.

#### <a name="to-add-specialized-behaviors"></a>Aby dodać zachowania specjalne

1. Aby element interfejsu użytkownika było widoczne tylko w określonych kontekstach interfejsu użytkownika, na przykład po załadowaniu rozwiązania, użyj ograniczeń widoczność.

   1.  Po `Commands` elementu Dodawanie `VisibilityConstraints` elementu.

   2.  Dla każdego elementu interfejsu użytkownika w celu ograniczenia Dodaj [VisibilityItem](../../extensibility/visibilityitem-element.md) elementu.

   3.  Dla każdego `VisibilityItem` elementu, ustaw `guid` i `id` atrybutów, które mają menu, grupy lub polecenia, a następnie ustaw `context` atrybutu kontekstu interfejsu użytkownika, należy zgodnie z definicją w <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> klasy.

2. Aby ustawić widoczność i dostępność elementów interfejsu użytkownika w kodzie, należy użyć co najmniej jeden z następujących flag poleceń:

   -   `DefaultDisabled`

   -   `DefaultInvisible`

   -   `DynamicItemStart`

   -   `DynamicVisibility`

   -   `NoShowOnMenuController`

   -   `NotInTBList`

   Aby uzyskać więcej informacji, zobacz [CommandFlag](../../extensibility/command-flag-element.md) elementu.

3. Aby zmienić sposób element jest wyświetlany lub dynamicznie zmieniać jego wygląd, należy użyć co najmniej jeden z następujących flag poleceń:

   -   `AlwaysCreate`

   -   `CommandWellOnly`

   -   `DefaultDocked`

   -   `DontCache`

   -   `DynamicItemStart`

   -   `FixMenuController`

   -   `IconAndText`

   -   `Pict`

   -   `StretchHorizontally`

   -   `TextMenuUseButton`

   -   `TextChanges`

   -   `TextOnly`

   Aby uzyskać więcej informacji, zobacz [CommandFlag](../../extensibility/command-flag-element.md) elementu.

4. Aby zmienić, jak element reaguje, gdy otrzyma poleceń, należy użyć co najmniej jeden z następujących flag poleceń:

   -   `AllowParams`

   -   `CaseSensitive`

   -   `CommandWellOnly`

   -   `FilterKeys`

   -   `NoAutoComplete`

   -   `NoButtonCustomize`

   -   `NoKeyCustomize`

   -   `NoToolbarClose`

   -   `PostExec`

   -   `RouteToDocs`

   -   `TextIsAnchorCommand`

   Aby uzyskać więcej informacji, zobacz [CommandFlag](../../extensibility/command-flag-element.md) elementu.

5. Aby dołączyć skrót klawiaturowy zależnych od menu do menu lub elementu menu, Dodaj znak handlowe "i" (&) w `ButtonText` elementu menu lub elementu menu. Znak, który następuje handlowe "i" skrót klawiaturowy aktywne po otwarciu menu nadrzędnego.

6. Aby dołączyć skrót klawiaturowy niezależne od menu do polecenia, użyj [powiązania klawiszy](../../extensibility/keybindings-element.md) elementu. Aby uzyskać więcej informacji, zobacz [powiązanie klawiszy](../../extensibility/keybinding-element.md) elementu.

7. Aby zlokalizować tekst menu, użyj `LocCanonicalName` elementu. Aby uzyskać więcej informacji, zobacz [ciągi](../../extensibility/strings-element.md) elementu.

   Niektóre typy menu i przycisk to specjalne zachowania. Na poniższej liście opisano niektóre menu wyspecjalizowanych i typach przycisków. Dla innych typów, zobacz `types` atrybutu opisy w [Menu](../../extensibility/menu-element.md), [przycisk](../../extensibility/button-element.md), i [kombi](../../extensibility/combo-element.md) elementów.

   - Pole kombi: Pole kombi jest listy rozwijanej, która może być używany na pasku narzędzi. Aby dodać pola kombi w interfejsie użytkownika, Utwórz [Combos](../../extensibility/combos-element.md) element `Commands` elementu. Następnie dodaj do `Combos` element `Combo` elementu dla każdego pola kombi dodać. `Combo` elementy mają te same atrybuty i elementy podrzędne, jak `Button` elementy oraz mają także `DefaultWidth` i `idCommandList` atrybutów. `DefaultWidth` Atrybut Ustawia szerokość w pikselach i `idCommandList` atrybutu punktów do Identyfikatora polecenia, który jest używany do wypełnienia pola kombi.

   - Kontroler menu: Kontroler menu jest przycisk, który zawiera strzałkę obok niej. Kliknięcie strzałki powoduje otwarcie listy. Aby dodać kontroler menu w interfejsie użytkownika, Utwórz `Menu` element i ustaw jego `type` atrybutu `MenuController` lub `MenuControllerLatched`, w zależności od żądane zachowanie. Aby wypełnić kontroler menu, należy ustawić go jako element nadrzędny `Group` elementu. Kontroler menu spowoduje wyświetlenie wszystkich elementów podrzędnych tej grupy na liście rozwijanej.

## <a name="see-also"></a>Zobacz także
- [Rozszerzenie menu i poleceń](../../extensibility/extending-menus-and-commands.md)
- [Pliki tabeli (vsct) polecenia programu Visual Studio](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Odwołanie do schematu VSCT XML](../../extensibility/vsct-xml-schema-reference.md)