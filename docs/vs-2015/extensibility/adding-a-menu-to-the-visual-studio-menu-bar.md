---
title: Dodawanie menu do paska menu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
caps.latest.revision: 52
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 64ab627d785e8b00b5159969a01dc1102df30359
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184925"
---
# <a name="adding-a-menu-to-the-visual-studio-menu-bar"></a>Dodawanie menu do paska menu programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu pokazano, jak dodać menu do paska menu zintegrowanego środowiska programistycznego (IDE) programu Visual Studio. Pasek menu IDE zawiera kategorie menu, takie jak **plik**, **Edycja**, **Widok**, **okno**i **Pomoc**.

 Przed dodaniem nowego menu do paska menu programu Visual Studio należy rozważyć, czy polecenia powinny być umieszczane w istniejącym menu. Aby uzyskać więcej informacji na temat umieszczania poleceń, zobacz [menu i polecenia dla programu Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).

 Menu są zadeklarowane w pliku. vsct projektu. Aby uzyskać więcej informacji na temat menu i plików. vsct, zobacz [polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md).

 Wykonując ten Instruktaż, można utworzyć menu o nazwie **TestMenu** , które zawiera jedno polecenie.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="creating-a-vsix-project-that-has-a-custom-command-item-template"></a>Tworzenie projektu VSIX, który ma szablon elementu niestandardowego polecenia

1. Utwórz projekt VSIX o nazwie `TopLevelMenu` . Szablon projektu VSIX można znaleźć w oknie dialogowym **Nowy projekt** w obszarze **Visual C#**  /  **rozszerzalność**Visual C#.  Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Po otwarciu projektu Dodaj niestandardowy szablon elementu polecenia o nazwie **TestCommand**. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj/nowy element**. W oknie dialogowym **Dodaj nowy element** przejdź do pozycji **Visual C#/rozszerzalność** i wybierz **polecenie niestandardowe**. W polu **Nazwa** w dolnej części okna Zmień nazwę pliku polecenia na **TestCommand.cs**.

## <a name="creating-a-menu-on-the-ide-menu-bar"></a>Tworzenie menu na pasku menu IDE

#### <a name="to-create-a-menu"></a>Aby utworzyć menu

1. W **Eksplorator rozwiązań**otwórz TestCommandPackage. vsct.

     Na końcu pliku znajduje się \<Symbols> węzeł, który zawiera kilka \<GuidSymbol> węzłów. W węźle o nazwie guidTestCommandPackageCmdSet Dodaj nowy symbol w następujący sposób:

    ```xml
    <IDSymbol name="TopLevelMenu" value="0x1021"/>
    ```

2. Utwórz pusty \<Menus> węzeł w \<Commands> węźle tuż przed \<Groups> . W \<Menus> węźle Dodaj \<Menu> węzeł w następujący sposób:

    ```xml
    <Menus>
          <Menu guid="guidTestCommandPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
            <Parent guid="guidSHLMainMenu"
                    id="IDG_VS_MM_TOOLSADDINS" />
            <Strings>
              <ButtonText>TestMenu</ButtonText>
              <CommandName>TestMenu</CommandName>
            </Strings>
        </Menu>
    </Menus>
    ```

     `guid`Wartości i `id` menu określają zestaw poleceń i określone menu w zestawie poleceń.

     `guid`Wartości i `id` pozycji elementu nadrzędnego menu w sekcji na pasku menu programu Visual Studio, które zawierają menu Narzędzia i dodatki.

     Wartość `CommandName` ciągu określa, że tekst powinien pojawić się w elemencie menu.

3. W \<Groups> sekcji Znajdź \<Group> i Zmień \<Parent> element, aby wskazywał menu, które właśnie dodałeś:

    ```csharp
    <Groups>
          <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
            <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
          </Group>
        </Groups>
    ```

     Powoduje to, że grupa jest częścią nowego menu.

4. Znajdź `Buttons` sekcję. Zwróć uwagę, że [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] szablon pakietu spowodował wygenerowanie `Button` elementu, który ma jego element nadrzędny ustawiony na `MyMenuGroup` . W efekcie to polecenie pojawi się w menu.

## <a name="building-and-testing-the-extension"></a>Kompilowanie i testowanie rozszerzenia

1. Skompiluj projekt i Rozpocznij debugowanie. Powinno zostać wyświetlone wystąpienie eksperymentalnego wystąpienia.

2. Pasek menu w eksperymentalnym wystąpieniu powinien zawierać menu **TestMenu** .

3. W menu **TestMenu** kliknij polecenie **Invoke test**.

     Powinien pojawić się okno komunikatu z komunikatem "pakiet TestCommand wewnątrz TopLevelMenu. TestCommand. MenuItemCallback ()". Oznacza to, że nowe polecenie działa.

## <a name="see-also"></a>Zobacz też
 [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)
