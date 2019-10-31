---
title: Dodawanie polecenia do Eksplorator rozwiązań pasku narzędzi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 99a21a4dd4c39a4cefdf6be30171c503fc2ce005
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187108"
---
# <a name="add-a-command-to-the-solution-explorer-toolbar"></a>Dodaj polecenie do paska narzędzi Eksplorator rozwiązań
W tym instruktażu pokazano, jak dodać przycisk do paska narzędzi **Eksplorator rozwiązań** .

 Każde polecenie na pasku narzędzi lub menu nosi nazwę przycisku w programie Visual Studio. Gdy przycisk zostanie kliknięty, kod w programie obsługi poleceń jest wykonywany. Zazwyczaj powiązane polecenia są pogrupowane w celu utworzenia jednej grupy. Menu lub paski narzędzi działają jako kontenery dla grup. Priorytet określa kolejność, w jakiej poszczególne polecenia w grupie pojawiają się w menu lub na pasku narzędzi. Można zapobiec wyświetlaniu przycisku na pasku narzędzi lub w menu poprzez kontrolowanie jego widoczności. Polecenie, które jest wymienione w sekcji `<VisibilityConstraints>` pliku *. vsct* , pojawia się tylko w skojarzonym kontekście. Nie można zastosować widoczności do grup.

 Aby uzyskać więcej informacji na temat menu, poleceń paska narzędzi i plików *. vsct* , zobacz [polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md).

> [!NOTE]
> Użyj plików tabeli poleceń XML ( *. vsct*) zamiast plików konfiguracji tabeli poleceń ( *. CTC*), aby zdefiniować sposób wyświetlania menu i poleceń w pakietów VSPackage. Aby uzyskać więcej informacji, zobacz [tabela poleceń programu Visual Studio (. Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-menu-command"></a>Tworzenie rozszerzenia za pomocą polecenia menu
 Utwórz projekt VSIX o nazwie `SolutionToolbar`. Dodaj szablon elementu polecenia menu o nazwie **ToolbarButton**. Aby uzyskać informacje o tym, jak to zrobić, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="add-a-button-to-the-solution-explorer-toolbar"></a>Dodaj przycisk do Eksplorator rozwiązań pasku narzędzi
 W tej części przewodnika pokazano, jak dodać przycisk do paska narzędzi **Eksplorator rozwiązań** . Gdy przycisk zostanie kliknięty, kod w metodzie wywołania zwrotnego jest uruchamiany.

1. W pliku *ToolbarButtonPackage. vsct* przejdź do sekcji `<Symbols>`. Węzeł `<GuidSymbol>` zawiera grupę menu i polecenie, które zostały wygenerowane przez szablon pakietu. Dodaj element `<IDSymbol>` do tego węzła, aby zadeklarować grupę, w której będzie przechowywane Polecenie.

    ```xml
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>
    ```

2. W sekcji `<Groups>` po istniejącym wpisie grupy Zdefiniuj nową grupę zadeklarowaną w poprzednim kroku.

    ```xml
    <Group guid="guidToolbarButtonPackageCmdSet"
           id="SolutionToolbarGroup" priority="0xF000">
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
          </Group>
    ```

     Ustawienie pary nadrzędny identyfikator GUID: ID na `guidSHLMainMenu` i `IDM_VS_TOOL_PROJWIN` umieszcza tę grupę na pasku narzędzi **Eksplorator rozwiązań** i ustawienie wartości o wysokim priorytecie spowoduje jej umieszczenie po innych grupach poleceń.

3. W sekcji `<Buttons>` Zmień identyfikator elementu nadrzędnego wygenerowanego `<Button>`, aby odzwierciedlał grupę zdefiniowaną w poprzednim kroku. Zmodyfikowany element `<Button>` powinien wyglądać następująco:

    ```xml
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />
        <Icon guid="guidImages" id="bmpPicStrikethrough" />
        <Strings>
            <ButtonText>Invoke ToolbarButton</ButtonText>
        </Strings>
    </Button>
    ```

4. Skompiluj projekt i Rozpocznij debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne.

     Na pasku narzędzi **Eksplorator rozwiązań** powinien zostać wyświetlony nowy przycisk polecenia z prawej strony istniejących przycisków. Ikona przycisku jest przekreśleniem.

5. Kliknij przycisk Nowy.

     Powinno zostać wyświetlone okno dialogowe z komunikatem **ToolbarButtonPackage wewnątrz elementu SolutionToolbar. ToolbarButton. MenuItemCallback ()** .

## <a name="control-the-visibility-of-a-button"></a>Kontrolowanie widoczności przycisku
 W tej części przewodnika pokazano, jak kontrolować widoczność przycisku na pasku narzędzi. Ustawiając kontekst do co najmniej jednego projektu w `<VisibilityConstraints>` sekcji pliku *SolutionToolbar. vsct* , można ograniczyć przycisk tak, aby był wyświetlany tylko wtedy, gdy projekt lub projekty są otwarte.

### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>Aby wyświetlić przycisk, gdy jeden lub więcej projektów jest otwartych

1. W sekcji `<Buttons>` *ToolbarButtonPackage. vsct*Dodaj dwa flagi poleceń do istniejącego elementu `<Button>`, między tagami `<Strings>` i `<Icons>`.

   ```xml
   <CommandFlag>DefaultInvisible</CommandFlag>
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

    Flagi `DefaultInvisible` i `DynamicVisibility` muszą być ustawione tak, aby wpisy w sekcji `<VisibilityConstraints>` mogły wejść w życie.

2. Utwórz sekcję `<VisibilityConstraints>`, która zawiera dwa `<VisibilityItem>` wpisy. Umieść nową sekcję tuż po tagu zamykającym `</Commands>`.

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidToolbarButtonPackageCmdSet"
             id="ToolbarButtonId"
             context="UICONTEXT_SolutionHasSingleProject" />
       <VisibilityItem guid="guidToolbarButtonPackageCmdSet"
             id="ToolbarButtonId"
             context="UICONTEXT_SolutionHasMultipleProjects" />
   </VisibilityConstraints>
   ```

    Każdy element widoczności reprezentuje warunek, pod którym zostanie wyświetlony określony przycisk. Aby zastosować wiele warunków, należy utworzyć wiele wpisów dla tego samego przycisku.

3. Skompiluj projekt i Rozpocznij debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne.

    Pasek narzędzi **Eksplorator rozwiązań** nie zawiera przycisku przekreślone.

4. Otwórz dowolne rozwiązanie, które zawiera projekt.

    Przycisk przekreślony pojawia się na pasku narzędzi z prawej strony istniejących przycisków.

5. W menu **plik** kliknij polecenie **Zamknij rozwiązanie**. Przycisk znika z paska narzędzi.

   Widoczność przycisku jest kontrolowana przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] do momentu załadowania pakietu VSPackage. Po załadowaniu pakietu VSPackage widoczność przycisku jest kontrolowana przez pakietu VSPackage.  Aby uzyskać więcej informacji, zobacz [MenuCommands vs. OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015).

## <a name="see-also"></a>Zobacz także
- [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)