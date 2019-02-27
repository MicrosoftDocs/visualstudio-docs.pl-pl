---
title: Tworzenie. Pliki Vsct | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, manual authoring
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bf3d9acd493cd10a8d014b4479684a0107cb8740
ms.sourcegitcommit: cea6187005f8a0cdf44e866a1534a4cf5356208c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2019
ms.locfileid: "56954030"
---
# <a name="authoring-vsct-files"></a>Tworzenie. Pliki Vsct
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W tym dokumencie przedstawiono sposób tworzenie pliku vsct, aby dodać elementy menu, paski narzędzi i inne elementy interfejsu użytkownika do programu Visual Studio zintegrowane środowisko programistyczne (IDE). Po dodaniu elementów interfejsu użytkownika do pakiet rozszerzeń Visual Studio (pakietu VSPackage), nie ma jeszcze pliku vsct, wykonaj następujące kroki.  
  
 Dla nowych projektów zaleca się użyć szablonu pakiet rozszerzeń Visual Studio, ponieważ generuje on pliku vsct, który w zależności od ustawień, ma już elementy wymagane dla polecenia menu, okna narzędzi lub niestandardowy Edytor. Można zmodyfikować tego pliku vsct do wymagań Twojego pakietu VSPackage. Aby uzyskać więcej informacji na temat sposobu modyfikowania pliku vsct Zobacz przykłady w [rozszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md).  
  
## <a name="authoring-the-file"></a>Tworzenie pliku  
 Tworzenie pliku vsct w tych etapów: Tworzenie struktury plików i zasobów, Zadeklaruj elementy interfejsu użytkownika, umieść elementy interfejsu użytkownika w środowisku IDE i Dodaj wszelkie specjalne zachowania.  
  
### <a name="file-structure"></a>Struktura plików  
 Podstawowa struktura pliku vsct jest [CommandTable](../../extensibility/commandtable-element.md) element główny, który zawiera [polecenia](../../extensibility/commands-element.md) elementu i [symbole](../../extensibility/symbols-element.md) elementu.  
  
##### <a name="to-create-the-file-structure"></a>Tworzenie struktury pliku  
  
1.  Dodawanie pliku vsct do projektu, wykonując kroki opisane w [jak: Tworzenie. Pliku Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md).  
  
2.  Dodaj wymagane przestrzenie nazw do `CommandTable` elementu, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"   
        xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
    ```  
  
3.  W `CommandTable` elementu Dodawanie `Commands` element do obsługi wszystkich niestandardowych menu, paski narzędzi, grup poleceń i polecenia. Tak, aby załadować niestandardowe elementy interfejsu użytkownika, `Commands` element musi mieć jej `Package` atrybut ustawiony na nazwę pakietu.  
  
     Po `Commands` elementu Dodawanie `Symbols` element, aby zdefiniować identyfikatorów GUID dla pakietu i nazwy i identyfikatory poleceń Twoje elementów interfejsu użytkownika.  
  
### <a name="including-visual-studio-resources"></a>W tym zasobów w programie Visual Studio  
 Użyj [Extern](../../extensibility/extern-element.md) elementu, aby uzyskać dostęp do plików, które definiują poleceń programu Visual Studio i menu, które są wymagane do umieszczenia elementów interfejsu użytkownika w środowisku IDE. Jeśli użyjesz polecenia zdefiniowane poza pakietu, należy użyć [UsedCommands](../../extensibility/usedcommands-element.md) elementu, aby poinformować program Visual Studio.  
  
##### <a name="to-include-visual-studio-resources"></a>Aby dołączyć zasoby programu Visual Studio  
  
1.  W górnej części `CommandTable` elementu, dodaj je `Extern` elementu dla każdego pliku zewnętrznego, odwołania i ustawiania `href` atrybut nazwy pliku. Możesz odwołać się następujące pliki nagłówków, aby uzyskać dostęp do zasobów programu Visual Studio:  
  
    -   Stdidcmd.h, definiuje identyfikatorów dla wszystkich poleceń udostępnianych przez program Visual Studio.  
  
    -   Vsshlids.h, zawiera identyfikatory poleceń menu programu Visual Studio.  
  
2.  Jeśli pakiet wymaga dowolne polecenia, które zostały zdefiniowane przez program Visual Studio lub innych pakietów, należy dodać `UsedCommands` elementu po `Commands` elementu. Wypełnij ten element z [UsedCommand](../../extensibility/usedcommand-element.md) elementu dla każdego polecenia, oznacza to wywołanie nie jest częścią pakietu. Ustaw `guid` i `id` atrybuty `UsedCommand` elementy do wartości Identyfikator GUID i identyfikator polecenia do wywołania. Aby uzyskać więcej informacji o tym, jak znaleźć polecenia identyfikatory GUID i identyfikatory programu Visual Studio, zobacz [identyfikatory GUID i identyfikatory programu Visual Studio — polecenia](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Aby wywołać poleceń z innych pakietów, należy użyć identyfikator GUID i identyfikator polecenia zgodnie z definicją w pliku vsct tych pakietów.  
  
### <a name="declaring-ui-elements"></a>Zadeklarowanie elementów interfejsu użytkownika  
 Zadeklaruj nowych elementów interfejsu użytkownika w `Symbols` części pliku vsct.  
  
##### <a name="to-declare-ui-elements"></a>Aby zadeklarować elementy interfejsu użytkownika  
  
1.  W `Symbols` elementu, Dodaj trzy [GuidSymbol](../../extensibility/guidsymbol-element.md) elementów. Każdy `GuidSymbol` element ma `name` atrybutu i `value` atrybutu. Ustaw `name` atrybutu, aby odzwierciedlały celem elementu. `value` Atrybut przyjmuje postać identyfikatora GUID. (Można wygenerować identyfikatora GUID na **narzędzia** menu, kliknij przycisk **Utwórz GUID**, a następnie wybierz pozycję **Format rejestru**.)  
  
     Pierwszy `GuidSymbol` element, który reprezentuje pakiet, a zwykle nie ma elementów podrzędnych. Drugi `GuidSymbol` element reprezentuje polecenie Ustaw i będzie zawierać wszystkie symbole, które definiują menu, grup i poleceń. Trzeci `GuidSymbol` element reprezentuje swoje magazynu obrazów i zawiera symbole dla wszystkich ikony dla poleceń. Jeśli nie masz żadnych poleceń korzystających z ikon, można pominąć trzeci `GuidSymbol` elementu.  
  
2.  W `GuidSymbol` elementu, który reprezentuje zestaw poleceń, Dodaj jeden lub kilka [IDSymbol](../../extensibility/idsymbol-element.md) elementów. Każdy z nich reprezentuje menu, pasek narzędzi, grupy lub polecenia, które dodajesz do Interfejsu użytkownika.  
  
     Dla każdego `IDSymbol` elementu, ustaw `name` atrybutu nazwa będzie używana do odwoływania się do odpowiedniego menu, grupy lub polecenia, a następnie ustaw `value` elementu liczbę szesnastkową, która będzie reprezentowała identyfikatora polecenia. Nie dwóch `IDSymbol` elementy, które mają ten sam nadrzędny element może mieć taką samą wartość.  
  
3.  Jeśli dowolne elementy interfejsu użytkownika wymaga ikony, należy dodać `IDSymbol` elementu dla każdego ikonę, aby `GuidSymbol` elementu, który reprezentuje magazynu w obrazie.  
  
### <a name="putting-ui-elements-in-the-ide"></a>Umieszczenie elementów interfejsu użytkownika w środowisku IDE  
 [Menu](../../extensibility/menus-element.md) elementu [grup](../../extensibility/groups-element.md) elementu, a [przyciski](../../extensibility/buttons-element.md) element zawiera definicje dla wszystkich menu, grup i poleceń, które są zdefiniowane w pakiecie. Umieść następujące menu, grupy i polecenia w środowisku IDE, za pomocą [nadrzędnego](../../extensibility/parent-element.md) elementu, który jest częścią definicji elementu interfejsu użytkownika lub za pomocą [CommandPlacement](../../extensibility/commandplacement-element.md) element, który jest zdefiniowany w innym miejscu.  
  
 Każdy `Menu`, `Group`, i `Button` element ma `guid` atrybutu i `id` atrybutu. Zawsze wartość `guid` atrybutu do dopasowania nazwy `GuidSymbol` elementu, który reprezentuje polecenie ustawić i `id` atrybutu nazwy `IDSymbol` elementu, który reprezentuje użytkownika menu, grupę lub polecenie `Symbols`sekcji.  
  
##### <a name="to-define-ui-elements"></a>Aby zdefiniować elementy interfejsu użytkownika  
  
1. Jeśli definiujesz nowe menu, podmenu, menu skrótów i paski narzędzi, należy dodać `Menus` elementu `Commands` elementu. Następnie dla każdego menu, który ma zostać utworzony, Dodaj [Menu](../../extensibility/menu-element.md) elementu `Menus` elementu.  
  
    Ustaw `guid` i `id` atrybuty `Menu` elementu, a następnie ustaw `type` atrybutu rodzaj elementu menu, które chcesz. Możesz też ustawić opcję `priority` atrybutu, aby ustanowić względne położenie menu w grupie nadrzędnej.  
  
   > [!NOTE]
   >  `priority` Atrybut nie ma zastosowania do pasków narzędzi i menu kontekstowego.  
  
2. Wszystkie polecenia w środowisku IDE programu Visual Studio musi być hostowany przez polecenie grup, które są bezpośrednimi elementami podrzędnymi menu i paski narzędzi. Jeśli dodajesz nowe menu i paski narzędzi do środowiska IDE programu zawierają one nowe grupy polecenia. Może również dodać grup poleceń do istniejącego menu i paski narzędzi, dzięki czemu można pogrupować poleceń.  
  
    Po dodaniu nowych grup poleceń, należy najpierw utworzyć `Groups` elementu, a następnie dodać do niego [grupy](../../extensibility/group-element.md) elementu dla każdej grupy polecenia.  
  
    Ustaw `guid` i `id` atrybuty każdego `Group` elementu, a następnie ustaw `priority` atrybutu, aby ustanowić względne położenie grupy menu nadrzędnego. Aby uzyskać więcej informacji, zobacz [tworzenia wielokrotnego użytku, do grup przycisków](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
3. Jeśli dodajesz nowe polecenia do IDE, Dodaj `Buttons` elementu `Commands` elementu. Następnie dla każdego polecenia, należy dodać [przycisk](../../extensibility/button-element.md) elementu `Buttons` elementu.  
  
   1. Ustaw `guid` i `id` atrybuty każdego `Button` elementu, a następnie ustaw `type` atrybutu z rodzajem przycisku. Możesz też ustawić opcję `priority` atrybutu, aby ustanowić względne położenie polecenia w grupie nadrzędnej.  
  
      > [!NOTE]
      >  Użyj `type="button"` polecenia standardowe menu i przycisków na paskach narzędzi.  
  
   2. W `Button` elementu Dodawanie [ciągi](../../extensibility/strings-element.md) element, który zawiera [ButtonText](../../extensibility/buttontext-element.md) elementu i [CommandName](../../extensibility/commandname-element.md) elementu. `ButtonText` Element udostępnia etykietę tekstową dla elementu menu lub etykietkę narzędzia dla przycisku paska narzędzi. `CommandName` Element zawiera nazwę polecenia można również użyć w poleceniu.  
  
   3. Jeśli polecenie będzie miał ikony, należy utworzyć [ikonę](../../extensibility/icon-element.md) elementu w `Button` elementu, a następnie ustaw jego `guid` i `id` atrybuty do `Bitmap` element ikony.  
  
      > [!NOTE]
      >  Przyciski paska narzędzi muszą mieć ikon.  
  
      Aby uzyskać więcej informacji, zobacz [MenuCommands programu Vs. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md).  
  
4. Jeśli dowolny poleceń wymagają ikony, należy dodać [mapy bitowe](../../extensibility/bitmaps-element.md) elementu `Commands` elementu. Następnie dla każdej ikony, należy dodać [mapy bitowej](../../extensibility/bitmap-element.md) elementu `Bitmaps` elementu. Jest to, gdzie możesz określić lokalizację zasób mapy bitowej. Aby uzyskać więcej informacji, zobacz [dodawanie ikon do poleceń Menu](../../extensibility/adding-icons-to-menu-commands.md).  
  
   Możesz polegać na strukturze element nadrzędny poprawnie umieścić Większość menu, grupy i polecenia. Dla polecenia bardzo dużych zestawów lub gdy menu, grupy lub polecenia musi znajdować się w wielu miejscach, firma Microsoft zaleca, aby określić położenie polecenia.  
  
##### <a name="to-rely-on-parenting-to-place-ui-elements-in-the-ide"></a>Opierać się na element nadrzędny, aby umieścić elementy interfejsu użytkownika w środowisku IDE  
  
1. W przypadku typowej element nadrzędny, utworzyć `Parent` elementu w każdym `Menu`, `Group`, i `Command` element, który jest zdefiniowany w pakiecie.  
  
    Celem `Parent` element jest menu lub grupy, która będzie zawierać menu, grupy lub polecenia.  
  
   1.  Ustaw `guid` atrybutu nazwy `GuidSymbol` element, który definiuje zestaw poleceń. Jeśli element docelowy nie jest częścią pakietu, należy użyć identyfikatora guid dla tego zestawu poleceń, zgodnie z definicją w odpowiedniego pliku vsct.  
  
   2.  Ustaw `id` atrybutu do dopasowania `id` atrybut menu docelowego lub grupy. Aby uzyskać listę menu i grup, które są dostępne w programie Visual Studio, zobacz [identyfikatory GUID i identyfikatory Visual Studio menu](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) lub [identyfikatory GUID i identyfikatory programu Visual Studio pasków narzędzi](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).  
  
   Jeśli masz dużą liczbę elementów interfejsu użytkownika można umieścić w IDE lub w przypadku elementów, które powinny się wyświetlać w wielu miejscach, zdefiniuj ich rozmieszczenia w [CommandPlacements](../../extensibility/commandplacements-element.md) elementu, jak pokazano w poniższych krokach.  
  
##### <a name="to-use-command-placement-to-place-ui-elements-in-the-ide"></a>Aby użyć położenie polecenia można umieścić elementy interfejsu użytkownika w środowisku IDE  
  
1. Po `Commands` elementu Dodawanie `CommandPlacements` elementu.  
  
2. W `CommandPlacements` elementu Dodawanie `CommandPlacement` elementu dla każdego menu, grupy lub polecenie, aby umieścić.  
  
    Każdy `CommandPlacement` element lub `Parent` element umieszcza jeden menu, grupy lub polecenia w jednym miejscu środowiska IDE. Element interfejsu użytkownika może mieć tylko jedną jednostkę nadrzędną, ale może mieć wiele angażowania polecenia. Aby umieścić element interfejsu użytkownika w wielu lokalizacjach, należy dodać `CommandPlacement` elementu dla każdej lokalizacji.  
  
3. Ustaw `guid` i `id` atrybuty każdego `CommandPlacement` elementu do hostingu menu lub grupy, podobnie jak w przypadku `Parent` elementu. Można również ustawić `priority` atrybutu, aby ustanowić względne położenie elementu interfejsu użytkownika.  
  
   Możesz mieszać umieszczania przez element nadrzędny i położenie polecenia. Dla polecenia bardzo dużych zestawów, zalecamy użycie tylko położenie polecenia.  
  
### <a name="adding-specialized-behaviors"></a>Dodawanie zachowania specjalne  
 Możesz użyć [CommandFlag](../../extensibility/command-flag-element.md) elementów, aby zmodyfikować zachowanie, menu i poleceń, na przykład, aby zmienić ich wyglądu i widoczność. Użytkownik może również wpływać na gdy polecenie jest widoczna przy użyciu [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md), lub dodawać skróty klawiaturowe przy użyciu [powiązania klawiszy](../../extensibility/keybindings-element.md). Niektóre rodzaje menu i poleceń już mieć wyspecjalizowane wbudowanych zachowań.  
  
##### <a name="to-add-specialized-behaviors"></a>Aby dodać zachowania specjalne  
  
1. Aby element interfejsu użytkownika było widoczne tylko w określonych kontekstach interfejsu użytkownika, na przykład po załadowaniu rozwiązania, użyj ograniczeń widoczność.  
  
   1.  Po `Commands` elementu Dodawanie `VisibilityConstraints` elementu.  
  
   2.  Dla każdego elementu interfejsu użytkownika w celu ograniczenia Dodaj [VisibilityItem](../../extensibility/visibilityitem-element.md) elementu.  
  
   3.  Dla każdego `VisibilityItem` elementu, ustaw `guid` i `id` atrybutów, które mają menu, grupy lub polecenia, a następnie ustaw `context` atrybutu kontekstu interfejsu użytkownika, należy zgodnie z definicją w <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> klasy. Aby uzyskać więcej informacji, zobacz [VisibilityItem, Element](../../extensibility/visibilityitem-element.md).  
  
2. Aby ustawić widoczność i dostępność elementów interfejsu użytkownika w kodzie, należy użyć co najmniej jeden z następujących flag poleceń:  
  
   - DefaultDisabled  
  
   - DefaultInvisible  
  
   - DynamicItemStart  
  
   - DynamicVisibility  
  
   - NoShowOnMenuController  
  
   - NotInTBList  
  
     Aby uzyskać więcej informacji, zobacz [Command Flag, Element](../../extensibility/command-flag-element.md).  
  
3. Aby zmienić sposób element jest wyświetlany lub dynamicznie zmieniać jego wygląd, należy użyć co najmniej jeden z następujących flag poleceń:  
  
   - AlwaysCreate  
  
   - CommandWellOnly  
  
   - DefaultDocked  
  
   - DontCache  
  
   - DynamicItemStart  
  
   - FixMenuController  
  
   - IconAndText  
  
   - PICT  
  
   - StretchHorizontally  
  
   - TextMenuUseButton  
  
   - TextChanges  
  
   - TextOnly  
  
     Aby uzyskać więcej informacji, zobacz [Command Flag, Element](../../extensibility/command-flag-element.md).  
  
4. Aby zmienić, jak element reaguje, gdy otrzyma poleceń, należy użyć co najmniej jeden z następujących flag poleceń:  
  
   - AllowParams  
  
   - CaseSensitive  
  
   - CommandWellOnly  
  
   - FilterKeys  
  
   - NoAutoComplete  
  
   - NoButtonCustomize  
  
   - NoKeyCustomize  
  
   - NoToolbarClose  
  
   - PostExec  
  
   - RouteToDocs  
  
   - TextIsAnchorCommand  
  
     Aby uzyskać więcej informacji, zobacz [Command Flag, Element](../../extensibility/command-flag-element.md).  
  
5. Aby dołączyć skrót klawiaturowy zależnych od menu do menu lub elementu menu, Dodaj znak handlowe "i" ("&") w `ButtonText` elementu menu lub elementu menu. Znak, który następuje handlowe "i" skrót klawiaturowy aktywne po otwarciu menu nadrzędnego.  
  
6. Aby dołączyć skrót klawiaturowy niezależne od menu do polecenia, użyj [powiązania klawiszy](../../extensibility/keybindings-element.md). Aby uzyskać więcej informacji, zobacz [KeyBinding, Element](../../extensibility/keybinding-element.md).  
  
7. Aby zlokalizować tekst menu, użyj `LocCanonicalName` elementu. Aby uzyskać więcej informacji, zobacz [Strings, Element](../../extensibility/strings-element.md).  
  
   Niektóre typy menu i przycisk to specjalne zachowania. W poniższej tabeli opisano niektóre menu wyspecjalizowanych i typach przycisków. Dla innych typów, zobacz `types` atrybutu opisy w [Menu Element](../../extensibility/menu-element.md), [Button Element](../../extensibility/button-element.md), i [Combo, Element](../../extensibility/combo-element.md).  
  
   Pole kombi  
   Pole kombi jest listy rozwijanej, która może być używany na pasku narzędzi. Aby dodać pola kombi w interfejsie użytkownika, Utwórz [Combos](../../extensibility/combos-element.md) element `Commands` elementu. Następnie dodaj do `Combos` element `Combo` elementu dla każdego pola kombi dodać. `Combo` elementy mają te same atrybuty i elementy podrzędne, jak `Button` elementy oraz mają także `DefaultWidth` i `idCommandList` atrybutów. `DefaultWidth` Atrybut Ustawia szerokość w pikselach i `idCommandList` atrybutu punktów do Identyfikatora polecenia, który jest używany do wypełnienia pola kombi. Aby uzyskać więcej informacji, zobacz `Combo` dokumentację elementu.  
  
   MenuController  
   Kontroler menu jest przycisk, który zawiera strzałkę obok niej. Kliknięcie strzałki powoduje otwarcie listy. Aby dodać kontroler menu w interfejsie użytkownika, Utwórz `Menu` element i ustaw jego `type` atrybutu **MenuController** lub **MenuControllerLatched**, w zależności od żądane zachowanie. Aby wypełnić kontroler menu, należy ustawić go jako element nadrzędny `Group` elementu. Kontroler menu spowoduje wyświetlenie wszystkich elementów podrzędnych tej grupy na liście rozwijanej.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md)   
 [Tabeli poleceń programu Visual Studio (. Pliki Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Odwołanie do schematu XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
