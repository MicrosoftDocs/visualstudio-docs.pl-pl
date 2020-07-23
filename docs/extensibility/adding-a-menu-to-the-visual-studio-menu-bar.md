---
title: Dodawanie menu do paska menu programu Visual Studio | Microsoft Docs
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 61321555a6896fad926d2ee38c5d73d50801d6b9
ms.sourcegitcommit: cb0c6e55ae560960a493df9ab56e3e9d9bc50100
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "86972351"
---
# <a name="add-a-menu-to-the-visual-studio-menu-bar"></a>Dodawanie menu do paska menu programu Visual Studio

W tym instruktażu pokazano, jak dodać menu do paska menu zintegrowanego środowiska programistycznego (IDE) programu Visual Studio. Pasek menu IDE zawiera kategorie menu, takie jak **plik**, **Edycja**, **Widok**, **okno**i **Pomoc**.

Przed dodaniem nowego menu do paska menu programu Visual Studio należy rozważyć, czy polecenia powinny być umieszczane w istniejącym menu. Aby uzyskać więcej informacji na temat umieszczania poleceń, zobacz [menu i polecenia dla programu Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).

Menu są zadeklarowane w pliku *. vsct* projektu. Aby uzyskać więcej informacji na temat menu i plików *. vsct* , zobacz [polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md).

Wykonując ten Instruktaż, można utworzyć menu o nazwie **menu testowego** , które zawiera jedno polecenie.

:::moniker range=">=vs-2019"
> [!NOTE]
> Począwszy od programu Visual Studio 2019, menu najwyższego poziomu udostępniane przez rozszerzenia są umieszczane w menu **rozszerzenia** .
:::moniker-end

## <a name="prerequisites"></a>Wymagania wstępne

Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-vsix-project-that-has-a-custom-command-item-template"></a>Utwórz projekt VSIX, który ma szablon elementu niestandardowego polecenia

1. Utwórz projekt VSIX o nazwie `TopLevelMenu` . Szablon projektu VSIX można znaleźć w oknie dialogowym **Nowy projekt** , wyszukując frazę "VSIX".  Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

::: moniker range="vs-2017"

2. Po otwarciu projektu Dodaj niestandardowy szablon elementu polecenia o nazwie **TestCommand**. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj**  >   **nowy element**. W oknie dialogowym **Dodaj nowy element** przejdź do pozycji **Visual C#/rozszerzalność** i wybierz **polecenie niestandardowe**. W polu **Nazwa** w dolnej części okna Zmień nazwę pliku polecenia na *TestCommand.cs*.

::: moniker-end

::: moniker range=">=vs-2019"

2. Po otwarciu projektu Dodaj niestandardowy szablon elementu polecenia o nazwie **TestCommand**. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj**  >   **nowy element**. W oknie dialogowym **Dodaj nowy element** przejdź do pozycji **Visual C#/rozszerzalność** i wybierz **polecenie**. W polu **Nazwa** w dolnej części okna Zmień nazwę pliku polecenia na *TestCommand.cs*.

::: moniker-end

## <a name="create-a-menu-on-the-ide-menu-bar"></a>Tworzenie menu na pasku menu IDE

::: moniker range="vs-2017"

1. W **Eksplorator rozwiązań**Otwórz *TestCommandPackage. vsct*.

    Na końcu pliku znajduje się `<Symbols>` węzeł, który zawiera kilka `<GuidSymbol>` węzłów. W węźle o nazwie `guidTestCommandPackageCmdSet` Dodaj nowy symbol w następujący sposób:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Utwórz pusty `<Menus>` węzeł w `<Commands>` węźle tuż przed `<Groups>` . W `<Menus>` węźle Dodaj `<Menu>` węzeł w następujący sposób:

   ```xml
   <Menus>
         <Menu guid="guidTestCommandPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
           <Parent guid="guidSHLMainMenu"
                   id="IDG_VS_MM_TOOLSADDINS" />
           <Strings>
             <ButtonText>Test Menu</ButtonText>
           </Strings>
       </Menu>
   </Menus>
   ```

    `guid`Wartości i `id` menu określają zestaw poleceń i określone menu w zestawie poleceń.

    `guid`Wartości i `id` pozycji elementu nadrzędnego menu w sekcji na pasku menu programu Visual Studio, które zawierają menu Narzędzia i dodatki.

    `<ButtonText>`Element określa, że tekst powinien pojawić się w elemencie menu.

3. W `<Groups>` sekcji Znajdź `<Group>` i Zmień `<Parent>` element, aby wskazywał menu, które właśnie dodałeś:

   ```xml
   <Groups>
       <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
       </Group>
   </Groups>
   ```

    Powoduje to, że grupa jest częścią nowego menu.

::: moniker-end

::: moniker range=">=vs-2019"

1. W **Eksplorator rozwiązań**Otwórz *TopLevelMenuPackage. vsct*.

    Na końcu pliku znajduje się `<Symbols>` węzeł, który zawiera kilka `<GuidSymbol>` węzłów. W węźle o nazwie `guidTopLevelMenuPackageCmdSet` Dodaj nowy symbol w następujący sposób:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Utwórz pusty `<Menus>` węzeł w `<Commands>` węźle tuż przed `<Groups>` . W `<Menus>` węźle Dodaj `<Menu>` węzeł w następujący sposób:

   ```xml
   <Menus>
         <Menu guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
           <Parent guid="guidSHLMainMenu"
                   id="IDG_VS_MM_TOOLSADDINS" />
           <Strings>
             <ButtonText>Test Menu</ButtonText>
           </Strings>
       </Menu>
   </Menus>
   ```

    `guid`Wartości i `id` menu określają zestaw poleceń i określone menu w zestawie poleceń.

    `guid`Wartości i `id` pozycji elementu nadrzędnego menu w sekcji na pasku menu programu Visual Studio, które zawierają menu Narzędzia i dodatki.

    `<ButtonText>`Element określa, że tekst powinien pojawić się w elemencie menu.

3. W `<Groups>` sekcji Znajdź `<Group>` i Zmień `<Parent>` element, aby wskazywał menu, które właśnie dodałeś:

   ```xml
   <Groups>
       <Group guid="guidTopLevelMenuPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu"/>
       </Group>
   </Groups>
   ```

    Powoduje to, że grupa jest częścią nowego menu.

::: moniker-end

4. `<Buttons>`Znajdź węzeł w sekcji `<Button>` . Następnie w `<Strings>` węźle Zmień `<ButtonText>` element na `Test Command` .

    Zwróć uwagę, że [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] szablon pakietu spowodował wygenerowanie `Button` elementu, który ma jego element nadrzędny ustawiony na `MyMenuGroup` . W związku z tym to polecenie pojawia się w menu.

## <a name="build-and-test-the-extension"></a>Kompiluj i Testuj rozszerzenie

1. Skompiluj projekt i Rozpocznij debugowanie. Powinno zostać wyświetlone wystąpienie eksperymentalnego wystąpienia.

::: moniker range="vs-2017"

2. Pasek menu w eksperymentalnym wystąpieniu powinien zawierać menu **menu testowego** .

::: moniker-end

::: moniker range=">=vs-2019"

2. Menu **rozszerzenia** w eksperymentalnym wystąpieniu powinno zawierać menu **menu testowego** .

::: moniker-end

3. W menu **test menu** , kliknij **polecenie Testuj**.

    Powinien pojawić się okno komunikatu z komunikatem "TestCommand wewnątrz TopLevelMenu. TestCommand. MenuItemCallback ()".

## <a name="see-also"></a>Zobacz także

- [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)
