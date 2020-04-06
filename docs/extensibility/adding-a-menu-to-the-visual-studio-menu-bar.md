---
title: Dodawanie menu do paska menu programu Visual Studio | Dokumenty firmy Microsoft
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 91e5a6e1714dbb87abc67fbf722c3bbd1a194a5b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740310"
---
# <a name="add-a-menu-to-the-visual-studio-menu-bar"></a>Dodawanie menu do paska menu programu Visual Studio

W tym przewodniku pokazano, jak dodać menu do paska menu zintegrowanego środowiska programistycznego programu Visual Studio (IDE). Pasek menu IDE zawiera kategorie menu, takie jak **Plik,** **Edycja,** **Widok,** **Okno**i **Pomoc**.

Przed dodaniem nowego menu do paska menu programu Visual Studio należy rozważyć, czy polecenia powinny być umieszczane w istniejącym menu. Aby uzyskać więcej informacji na temat umieszczania poleceń, zobacz [Menu i polecenia programu Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).

Menu są zadeklarowane w pliku *vsct* projektu. Aby uzyskać więcej informacji o menu i plikach *vsct,* zobacz [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md).

Wypełniając ten instruktaż, można utworzyć menu o nazwie **TestMenu,** które zawiera jedno polecenie.

> [!NOTE]
> W programie VS 2019 menu najwyższego poziomu, które są dodane przez rozszerzenia, są umieszczane w menu **Rozszerzenia.**

## <a name="prerequisites"></a>Wymagania wstępne

Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-vsix-project-that-has-a-custom-command-item-template"></a>Tworzenie projektu VSIX z szablonem niestandardowego elementu polecenia

1. Utwórz projekt VSIX o nazwie `TopLevelMenu`. Szablon projektu VSIX można znaleźć w oknie dialogowym **Nowy projekt,** wyszukując "vsix".  Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Po otwarciu projektu dodaj niestandardowy szablon elementu polecenia o nazwie **TestCommand**. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj** >  **nowy element**. W oknie dialogowym **Dodawanie nowego elementu** przejdź do pozycji Visual **C# / Extensibility** i wybierz polecenie **Niestandardowe**. W polu **Nazwa** u dołu okna zmień nazwę pliku polecenia na *TestCommand.cs*.

## <a name="create-a-menu-on-the-ide-menu-bar"></a>Tworzenie menu na pasku menu IDE

::: moniker range="vs-2017"

1. W **Eksploratorze rozwiązań**otwórz *plik TestCommandPackage.vsct*.

    Na końcu pliku znajduje \<się węzeł symboli>, który \<zawiera kilka węzłów> GuidSymbol. W węźle o nazwie guidTestCommandPackageCmdSet dodaj nowy symbol w następujący sposób:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Utwórz \<pusty węzeł menu> \<w węźle> polecenia, \<tuż przed> grup. W \<węźle Menu> dodaj \<następujący węzeł Menu>:

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

    Wartości `guid` `id` menu określają zestaw poleceń i konkretne menu w zestawie poleceń.

    I `guid` `id` wartości nadrzędnego pozycjonowania menu w sekcji paska menu programu Visual Studio, który zawiera narzędzia i dodatki menu.

    Wartość `CommandName` ciągu określa, że tekst powinien pojawić się w elemencie menu.

3. W \<sekcji Grupy> znajdź \<> grupy i zmień \<element> nadrzędny, aby wskazywał menu, które właśnie dodaliśmy:

   ```csharp
   <Groups>
         <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
         </Group>
       </Groups>
   ```

    Dzięki temu grupa jest częścią nowego menu.

::: moniker-end

::: moniker range=">=vs-2019"

1. W **Eksploratorze rozwiązań**otwórz *plik TopLevelMenuPackage.vsct*.

    Na końcu pliku znajduje \<się węzeł symboli>, który \<zawiera kilka węzłów> GuidSymbol. W węźle o nazwie guidTopLevelMenuPackageCmdSet dodaj nowy symbol w następujący sposób:

   ```xml
   <IDSymbol name="TopLevelMenu" value="0x1021"/>
   ```

2. Utwórz \<pusty węzeł menu> \<w węźle> polecenia, \<tuż przed> grup. W \<węźle Menu> dodaj \<następujący węzeł Menu>:

   ```xml
   <Menus>
         <Menu guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu" priority="0x700" type="Menu">
           <Parent guid="guidSHLMainMenu"
                   id="IDG_VS_MM_TOOLSADDINS" />
           <Strings>
             <ButtonText>TestMenu</ButtonText>
             <CommandName>TestMenu</CommandName>
           </Strings>
       </Menu>
   </Menus>
   ```

    Wartości `guid` `id` menu określają zestaw poleceń i konkretne menu w zestawie poleceń.

    I `guid` `id` wartości nadrzędnego pozycjonowania menu w sekcji paska menu programu Visual Studio, który zawiera narzędzia i dodatki menu.

    Wartość `CommandName` ciągu określa, że tekst powinien pojawić się w elemencie menu.

3. W \<sekcji Grupy> znajdź \<> grupy i zmień \<element> nadrzędny, aby wskazywał menu, które właśnie dodaliśmy:

   ```csharp
   <Groups>
         <Group guid="guidTopLevelMenuPackageCmdSet" id="MyMenuGroup" priority="0x0600">
           <Parent guid="guidTopLevelMenuPackageCmdSet" id="TopLevelMenu"/>
         </Group>
       </Groups>
   ```

    Dzięki temu grupa jest częścią nowego menu.

::: moniker-end

4. Znajdź `Buttons` sekcję. Należy zauważyć, że [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] szablon `Button` Pakiet wygenerował element, `MyMenuGroup`który ma ustawioną wartość nadrzędną . W rezultacie to polecenie pojawi się w menu.

## <a name="build-and-test-the-extension"></a>Tworzenie i testowanie rozszerzenia

1. Skompiluj projekt i rozpocznij debugowanie. Powinno pojawić się wystąpienie eksperymentalne.

::: moniker range="vs-2017"

2. Pasek menu w wystąpieniu eksperymentalnym powinien zawierać menu **TestMenu.**

::: moniker-end

::: moniker range=">=vs-2019"

2. **Rozszerzenia** menu w wystąpieniu eksperymentalnym powinny zawierać **menu TestMenu.**

::: moniker-end

3. W menu **TestMenu** kliknij polecenie **Wywołaj polecenie testu**.

     Powinno pojawić się okno komunikatu i wyświetlić komunikat "TestCommand Package Inside TopLevelMenu.TestCommand.MenuItemCallback()".

## <a name="see-also"></a>Zobacz też

- [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)
