---
title: Dodawanie polecenia do paska narzędzi Eksploratora rozwiązań | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding buttons
- buttons [Visual Studio], adding to Solution Explorer
- Solution Explorer, adding buttons
ms.assetid: f6411557-2f4b-4e9f-b02e-fce12a6ac7e9
caps.latest.revision: 40
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ac07a2c6becd46a2536e6a9b3340d075d5f078f2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63403242"
---
# <a name="adding-a-command-to-the-solution-explorer-toolbar"></a>Dodawanie polecenia do paska narzędzi Eksploratora rozwiązań
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu pokazano, jak dodać przycisk, aby **Eksploratora rozwiązań** paska narzędzi.  
  
 Dowolnego polecenia na pasku narzędzi lub menu nosi nazwę przycisku w programie Visual Studio. Po kliknięciu przycisku, jest wykonywany kod w program obsługi poleceń. Zazwyczaj powiązane polecenia są grupowane razem tworzą jedną grupę. Menu i paski narzędzi działają jak kontenery dla grupy. Priorytet określa kolejność wyświetlania pojedynczych poleceń w grupie w menu lub na pasku narzędzi. Aby uniemożliwić przycisku są wyświetlane na pasku narzędzi lub menu poprzez kontrolowanie jego widoczność. Polecenia, który znajduje się w `<VisibilityConstraints>` części pliku vsct pojawia się tylko w skojarzonego kontekstu. Widoczność nie może być stosowany do grup.  
  
 Aby uzyskać więcej informacji na temat menu, poleceń paska narzędzi i plików vsct zobacz [polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md).  
  
> [!NOTE]
> Pliki tabeli poleceń XML (vsct) zamiast pliki konfiguracji (.ctc) tabeli poleceń mogą być używane do definiowania sposobu wyświetlania menu i poleceń w swojej pakietów VSPackage. Aby uzyskać więcej informacji, zobacz [tabeli poleceń w usłudze Visual Studio (. Pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-an-extension-with-a-menu-command"></a>Tworzenie rozszerzenia za pomocą polecenia menu  
 Utwórz projekt VSIX, o nazwie `SolutionToolbar`. Dodaj szablon elementu polecenia menu o nazwie **ToolbarButton**. Aby dowiedzieć się, jak to zrobić, zobacz [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="adding-a-button-to-the-solution-explorer-toolbar"></a>Dodawanie przycisku do paska narzędzi Eksploratora rozwiązań  
 Tej części instruktażu pokazano, jak dodać przycisk, aby **Eksploratora rozwiązań** paska narzędzi. Po kliknięciu przycisku uruchamiania kodu w metodzie wywołania zwrotnego.  
  
1. W pliku ToolbarButtonPackage.vsct, przejdź do `<Symbols>` sekcji. `<GuidSymbol>` Węzeł zawiera grupy menu i poleceń, który został wygenerowany przez szablon pakietu. Dodaj `<IDSymbol>` elementu do tego węzła do deklarowania grupy, w którym będą przechowywane do swojej dyspozycji.  
  
    ```xml  
    <IDSymbol name="SolutionToolbarGroup" value="0x0190"/>  
    ```  
  
2. W `<Groups>` sekcji po istniejący wpis grupy zdefiniować nową grupę, zadeklarowanej w poprzednim kroku.  
  
    ```xml  
    <Group guid="guidToolbarButtonPackageCmdSet"  
           id="SolutionToolbarGroup" priority="0xF000">  
            <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>  
          </Group>  
    ```  
  
     Ustawienie nadrzędnego pary GUID:ID `guidSHLMainMenu` i `IDM_VS_TOOL_PROJWIN` umieszcza tę grupę na **Eksploratora rozwiązań** narzędzi i ustawienie wartości o wysokim priorytecie umieszcza go od innych grup poleceń.  
  
3. W `<Buttons>` sekcji, zmień identyfikator elementu nadrzędnego w wygenerowanym `<Button>` wpis w celu uwzględnienia grupy, które są zdefiniowane w poprzednim kroku. Zmodyfikowanego `<Button>` element powinien wyglądać następująco:  
  
    ```xml  
    <Button guid="guidToolbarButtonPackageCmdSet" id="ToolbarButtonId" priority="0x0100" type="Button">  
        <Parent guid="guidToolbarButtonPackageCmdSet" id="SolutionToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPicStrikethrough" />  
        <Strings>  
            <ButtonText>Invoke ToolbarButton</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
4. Skompiluj projekt, a następnie rozpocząć debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne.  
  
     **Eksploratora rozwiązań** na prawo od istniejących przycisków paska narzędzi powinien być wyświetlany nowy przycisk polecenia. Ikona przycisku jest przekreślenie.  
  
5. Kliknij przycisk Nowy.  
  
     Okno dialogowe z komunikatu **ToolbarButtonPackage wewnątrz SolutionToolbar.ToolbarButton.MenuItemCallback()** powinien być wyświetlany.  
  
## <a name="controlling-the-visibility-of-a-button"></a>Kontrolowanie widoczności przycisku  
 Tej części instruktażu pokazano, jak kontrolować widoczność przycisku paska narzędzi. Ustawiając jeden lub więcej projektów w kontekście `<VisibilityConstraints>` sekcji pliku SolutionToolbar.vsct ograniczyć przycisku, aby są wyświetlane tylko kiedy projekt lub projekty są otwarte.  
  
#### <a name="to-display-a-button-when-one-or-more-projects-are-open"></a>Aby wyświetlić przycisk, gdy jeden lub więcej projektów są otwarte  
  
1. W `<Buttons>` sekcji ToolbarButtonPackage.vsct, Dodaj dwie flagi polecenia do istniejących `<Button>` elementu, między `<Strings>` i `<Icons>` tagów.  
  
   ```xml  
   <CommandFlag>DefaultInvisible</CommandFlag>  
   <CommandFlag>DynamicVisibility</CommandFlag>  
   ```  
  
    `DefaultInvisible` i `DynamicVisibility` flagi musi być ustawiona tak że wpisy w `<VisibilityConstraints>` sekcji zostały wprowadzone.  
  
2. Tworzenie `<VisibilityConstraints>` sekcja, która ma dwa `<VisibilityItem>` wpisów. Umieść nową sekcję zaraz po zamykającym `</Commands>` tagu.  
  
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
  
    Każdy element widoczność reprezentuje warunek, pod którym jest wyświetlana określonego przycisku. Aby zastosować wiele warunków, należy utworzyć wiele pozycji dla tego samego przycisku.  
  
3. Skompiluj projekt, a następnie rozpocząć debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne.  
  
    **Eksploratora rozwiązań** paska narzędzi nie zawiera przycisk przekreślenie.  
  
4. Otwórz dowolnego rozwiązania zawierającego projekt.  
  
    Przycisk będzie już przekreślanych pojawia się na pasku narzędzi po prawej stronie istniejące przyciski.  
  
5. Na **pliku** menu, kliknij przycisk **Zamknij rozwiązanie**. Przycisk zniknie z paska narzędzi.  
  
   Widoczność przycisku jest kontrolowana przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] do momentu załadowania pakietu VSPackage. Po załadowaniu pakietu VSPackage widoczność przycisku jest kontrolowana przez pakietu VSPackage.  Aby uzyskać więcej informacji, zobacz [MenuCommands programu Vs. OleMenuCommands](../misc/menucommands-vs-olemenucommands.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)
