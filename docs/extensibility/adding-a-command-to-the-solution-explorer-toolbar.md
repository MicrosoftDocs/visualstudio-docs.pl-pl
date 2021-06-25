---
title: Dodawanie polecenia do Eksplorator rozwiązań paska narzędzi | Microsoft Docs
description: Dowiedz się, jak dodać przycisk, który wykonuje polecenie na pasku Eksplorator rozwiązań narzędzi Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0aa75bd1a229be147e3462845a61266a650e072e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900242"
---
# <a name="add-a-command-to-the-solution-explorer-toolbar"></a>Dodawanie polecenia do paska Eksplorator rozwiązań narzędzi
W tym przewodniku pokazano, jak dodać przycisk do **Eksplorator rozwiązań** narzędzi.

 Każde polecenie na pasku narzędzi lub w menu jest nazywane przyciskiem w Visual Studio. Po kliknięciu przycisku wykonywany jest kod w programie obsługi poleceń. Zazwyczaj powiązane polecenia są grupowane razem, tworząc jedną grupę. Menu lub paski narzędzi działają jako kontenery dla grup. Priorytet określa kolejność, w jakiej poszczególne polecenia w grupie są wyświetlane w menu lub na pasku narzędzi. Możesz zapobiec wyświetlaniu przycisku na pasku narzędzi lub w menu, kontrolując jego widoczność. Polecenie wymienione w sekcji pliku `<VisibilityConstraints>` *vsct* pojawia się tylko w skojarzonym kontekście. Widoczności nie można zastosować do grup.

 Aby uzyskać więcej informacji na temat menu, poleceń paska narzędzi i *plików vsct,* zobacz [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md).

> [!NOTE]
> Użyj plików tabeli poleceń XML *(vsct*) zamiast plików konfiguracji tabeli poleceń *(ctc),* aby zdefiniować sposób, w jaki menu i polecenia są wyświetlane w pakietach VSPackage. Aby uzyskać więcej informacji, [zobacz Visual Studio Command Table (. Vsct) plików](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od Visual Studio 2015 r., zestaw SDK usługi Visual Studio nie jest instalowany z Centrum pobierania. Jest ona dołączona jako opcjonalna funkcja w Visual Studio konfiguracji. Zestaw VS SDK można również zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-an-extension-with-a-menu-command"></a>Tworzenie rozszerzenia za pomocą polecenia menu
 Utwórz projekt VSIX o nazwie `SolutionToolbar` . Dodaj szablon elementu polecenia menu o nazwie **ToolbarButton**. Aby uzyskać informacje o tym, jak to zrobić, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="add-a-button-to-the-solution-explorer-toolbar"></a>Dodawanie przycisku do paska Eksplorator rozwiązań narzędzi
 W tej sekcji przewodnika pokazano, jak dodać przycisk do Eksplorator rozwiązań **narzędzi.** Po kliknięciu przycisku zostanie uruchomiony kod w metodzie wywołania zwrotnego.

1. W pliku *ToolbarButtonPackage.vsct* przejdź do  `<Symbols>` sekcji . Węzeł `<GuidSymbol>`  zawiera grupę menu i polecenie wygenerowane przez szablon pakietu. Dodaj element `<IDSymbol>` do tego węzła, aby zadeklarować grupę, która będzie przechowywać polecenie.

    ```xml
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>
    ```

2. W `<Groups>` sekcji po istniejącym wpisie grupy zdefiniuj nową grupę zadeklarowaną w poprzednim kroku.

    ```xml
    <Group guid="guidToolbarButtonPackageCmdSet"
           id="SolutionToolbarGroup" priority="0xF000">
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
          </Group>
    ```

     Ustawienie nadrzędnej pary GUID:ID na i umieszcza tę grupę na pasku narzędzi Eksplorator rozwiązań, a ustawienie wartości o wysokim priorytecie umieszcza ją po innych `guidSHLMainMenu` `IDM_VS_TOOL_PROJWIN` grupach poleceń. 

3. W sekcji zmień identyfikator elementu nadrzędnego wygenerowanego wpisu, aby odzwierciedlić grupę `<Buttons>` `<Button>` zdefiniowaną w poprzednim kroku. Zmodyfikowany `<Button>` element powinien wyglądać tak:

    ```xml
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />
        <Icon guid="guidImages" id="bmpPicStrikethrough" />
        <Strings>
            <ButtonText>Invoke ToolbarButton</ButtonText>
        </Strings>
    </Button>
    ```

4. Skompilowanie projektu i rozpoczęcie debugowania. Zostanie wyświetlone wystąpienie eksperymentalne.

     Na **Eksplorator rozwiązań** pasku narzędzi powinien zostać wyświetlany nowy przycisk polecenia po prawej stronie istniejących przycisków. Ikona przycisku to przekreślenie.

5. Kliknij nowy przycisk.

     Powinno zostać wyświetlone okno dialogowe z komunikatem **ToolbarButtonPackage Inside SolutionToolbar.ToolbarButton.MenuItemCallback().**

## <a name="control-the-visibility-of-a-button"></a>Kontrolowanie widoczności przycisku
 W tej sekcji przewodnika pokazano, jak kontrolować widoczność przycisku na pasku narzędzi. Ustawiając kontekst na co najmniej jeden projekt w sekcji pliku `<VisibilityConstraints>` *SolutionToolbar.vsct,* można ograniczyć przycisk wyświetlany tylko wtedy, gdy projekt lub projekty są otwarte.

### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>Aby wyświetlić przycisk, gdy co najmniej jeden projekt jest otwarty

1. W sekcji `<Buttons>` *ToolbarButtonPackage.vsct* dodaj dwie flagi poleceń do istniejącego `<Button>` elementu między `<Strings>` tagami i `<Icons>` .

   ```xml
   <CommandFlag>DefaultInvisible</CommandFlag>
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

    Flagi `DefaultInvisible` `DynamicVisibility` i muszą być ustawione, aby wpisy w `<VisibilityConstraints>` sekcji obowiązywały.

2. Utwórz `<VisibilityConstraints>` sekcję, która ma dwa `<VisibilityItem>` wpisy. Umieść nową sekcję tuż po tagu `</Commands>` zamykającym.

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

    Każdy element widoczności reprezentuje warunek, w którym jest wyświetlany określony przycisk. Aby zastosować wiele warunków, należy utworzyć wiele wpisów dla tego samego przycisku.

3. Skompilowanie projektu i rozpoczęcie debugowania. Zostanie wyświetlone wystąpienie eksperymentalne.

    Pasek **Eksplorator rozwiązań** narzędzi nie zawiera przycisku przekreślenia.

4. Otwórz dowolne rozwiązanie, które zawiera projekt.

    Przycisk przekreślenia pojawi się na pasku narzędzi po prawej stronie istniejących przycisków.

5. W menu **Plik** kliknij polecenie **Zamknij rozwiązanie.** Przycisk zniknie z paska narzędzi.

   Widoczność przycisku jest kontrolowana przez do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] momentu załadowania pakietów VSPackage. Po załadowaniu pakietów VSPackage widoczność przycisku jest kontrolowana przez pakiet VSPackage.  Aby uzyskać więcej informacji, zobacz [MenuCommands vs. OleMenuCommands](/previous-versions/visualstudio/visual-studio-2015/misc/menucommands-vs-olemenucommands?preserve-view=true&view=vs-2015).

## <a name="see-also"></a>Zobacz też
- [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)