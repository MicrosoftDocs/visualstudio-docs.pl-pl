---
title: Dodawanie polecenia do paska narzędzi Eksploratora rozwiązań | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44a14d87fbb5754d7af35d3add9e438351877a49
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740331"
---
# <a name="add-a-command-to-the-solution-explorer-toolbar"></a>Dodawanie polecenia do paska narzędzi Eksploratora rozwiązań
W tym przewodniku pokazano, jak dodać przycisk do paska narzędzi **Eksploratora rozwiązań.**

 Każde polecenie na pasku narzędzi lub menu jest nazywane przyciskiem w programie Visual Studio. Po kliknięciu przycisku, kod w programie obsługi poleceń jest wykonywany. Zazwyczaj powiązane polecenia są grupowane w celu utworzenia jednej grupy. Menu lub paski narzędzi działają jako kontenery dla grup. Priorytet określa kolejność, w jakiej poszczególne polecenia w grupie są wyświetlane w menu lub na pasku narzędzi. Można zapobiec wyświetlaniu przycisku na pasku narzędzi lub w menu, kontrolując jego widoczność. Polecenie wymienione w `<VisibilityConstraints>` sekcji pliku *vsct* jest wyświetlane tylko w skojarzonym kontekście. Widoczności nie można zastosować do grup.

 Aby uzyskać więcej informacji o menu, poleceniach paska narzędzi i plikach *vsct,* zobacz [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md).

> [!NOTE]
> Użyj plików XML Command Table (*.vsct*) zamiast plików konfiguracji tabeli poleceń (*ctc*), aby zdefiniować sposób, w jaki menu i polecenia są wyświetlane w pakietach VSPackages. Aby uzyskać więcej informacji, zobacz [Visual Studio Command Table (. vsct) plików](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-menu-command"></a>Tworzenie rozszerzenia za pomocą polecenia menu
 Utwórz projekt VSIX o nazwie `SolutionToolbar`. Dodaj szablon elementu polecenia menu o nazwie **ToolbarButton**. Aby uzyskać informacje na temat tego, jak to zrobić, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="add-a-button-to-the-solution-explorer-toolbar"></a>Dodawanie przycisku do paska narzędzi Eksploratora rozwiązań
 W tej sekcji przewodnika pokazano, jak dodać przycisk do paska narzędzi **Eksploratora rozwiązań.** Po kliknięciu przycisku kod w metodzie wywołania zwrotnego jest uruchamiany.

1. W pliku *ToolbarButtonPackage.vsct* przejdź `<Symbols>` do sekcji. Węzeł `<GuidSymbol>` zawiera grupę menu i polecenie, które zostało wygenerowane przez szablon pakietu. Dodaj `<IDSymbol>` element do tego węzła, aby zadeklarować grupę, która będzie zawierać polecenie.

    ```xml
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>
    ```

2. W `<Groups>` sekcji po istniejącym wpisie grupy zdefiniuj nową grupę zadeklarowanej w poprzednim kroku.

    ```xml
    <Group guid="guidToolbarButtonPackageCmdSet"
           id="SolutionToolbarGroup" priority="0xF000">
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
          </Group>
    ```

     Ustawienie nadrzędnej pary GUID:ID `guidSHLMainMenu` i `IDM_VS_TOOL_PROJWIN` umieszcza tę grupę na pasku narzędzi **Eksploratora rozwiązań,** a ustawienie wartości o wysokim priorytecie umieszcza ją po innych grupach poleceń.

3. W `<Buttons>` sekcji zmień identyfikator nadrzędny wygenerowanego wpisu, aby odzwierciedlić `<Button>` grupę zdefiniowaną w poprzednim kroku. Zmodyfikowany `<Button>` element powinien wyglądać następująco:

    ```xml
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />
        <Icon guid="guidImages" id="bmpPicStrikethrough" />
        <Strings>
            <ButtonText>Invoke ToolbarButton</ButtonText>
        </Strings>
    </Button>
    ```

4. Skompiluj projekt i rozpocznij debugowanie. Pojawi się eksperymentalne wystąpienie.

     Pasek narzędzi **Eksploratora rozwiązań** powinien wyświetlać nowy przycisk polecenia po prawej stronie istniejących przycisków. Ikona przycisku jest przekreśleniem.

5. Kliknij nowy przycisk.

     Okno dialogowe z komunikatem **ToolbarButtonPackage Inside SolutionToolbar.ToolbarButton.MenuItemCallback()** powinno być wyświetlane.

## <a name="control-the-visibility-of-a-button"></a>Sterowanie widocznością przycisku
 W tej sekcji przewodnika pokazano, jak kontrolować widoczność przycisku na pasku narzędzi. Ustawiając kontekst na jeden lub `<VisibilityConstraints>` więcej projektów w sekcji *pliku SolutionToolbar.vsct,* można ograniczyć przycisk do wyświetlenia tylko wtedy, gdy projekt lub projekty są otwarte.

### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>Aby wyświetlić przycisk, gdy jeden lub więcej projektów jest otwartych

1. W `<Buttons>` sekcji *ToolbarButtonPackage.vsct*, dodaj dwie flagi `<Button>` poleceń `<Strings>` do `<Icons>` istniejącego elementu, między tagami.

   ```xml
   <CommandFlag>DefaultInvisible</CommandFlag>
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

    Flagi `DefaultInvisible` `DynamicVisibility` i muszą być ustawione tak, `<VisibilityConstraints>` aby wpisy w sekcji mogą zostać zastosowane.

2. Utwórz `<VisibilityConstraints>` sekcję `<VisibilityItem>` zawierającą dwa wpisy. Umieść nową sekcję tuż `</Commands>` za tagiem zamykającym.

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

    Każdy element widoczności reprezentuje warunek, pod którym wyświetlany jest określony przycisk. Aby zastosować wiele warunków, należy utworzyć wiele wpisów dla tego samego przycisku.

3. Skompiluj projekt i rozpocznij debugowanie. Pojawi się eksperymentalne wystąpienie.

    Pasek narzędzi **Eksploratora rozwiązań** nie zawiera przycisku przekreślenia.

4. Otwórz dowolne rozwiązanie zawierające projekt.

    Przycisk przekreślenia pojawi się na pasku narzędzi po prawej stronie istniejących przycisków.

5. W menu **Plik** kliknij polecenie **Zamknij rozwiązanie**. Przycisk zniknie z paska narzędzi.

   Widoczność przycisku jest [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kontrolowana przez dopóki vspackage jest ładowany. Po załadowaniu VSPackage widoczność przycisku jest kontrolowana przez VSPackage.  Aby uzyskać więcej informacji, zobacz [MenuCommands vs. OleMenuCommands](/visualstudio/extensibility/menucommands-vs-olemenucommands?view=vs-2015).

## <a name="see-also"></a>Zobacz też
- [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)
