---
title: Dodawanie Menu do paska Menu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- menus, creating top level
- top-level menus
ms.assetid: 58fc1a31-2aeb-441c-8e48-c7d5cbcfe501
caps.latest.revision: 52
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 440bd2c8c7e1505b8d729274a06440d596690773
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53065887"
---
# <a name="adding-a-menu-to-the-visual-studio-menu-bar"></a>Dodawanie menu do paska menu programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu przedstawiono sposób dodawania menu na pasku menu programu Visual Studio zintegrowane środowisko programistyczne (IDE). Pasek menu IDE zawiera menu Kategorie, takie jak **pliku**, **Edytuj**, **widoku**, **okna**, i **pomocy** .

 Przed dodaniem nowego menu na pasku menu programu Visual Studio, należy rozważyć, czy poleceń powinny zostać umieszczone w ramach istniejącego menu. Aby uzyskać więcej informacji na temat położenie polecenia zobacz [menu i poleceń dla programu Visual Studio](../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md).

 Menu są deklarowane w pliku vsct projektu. Aby uzyskać więcej informacji na temat menu i plików vsct zobacz [polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md).

 Przez ukończenie tego instruktażu, można utworzyć menu o nazwie **TestMenu** zawierający jednego polecenia.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="creating-a-vsix-project-that-has-a-custom-command-item-template"></a>Tworzenie projektu VSIX, zawierający szablon elementu niestandardowego polecenia

1.  Utwórz projekt VSIX, o nazwie `TopLevelMenu`. Można znaleźć szablonu projektu VSIX w **nowy projekt** , okno dialogowe **Visual C#** / **rozszerzalności**.  Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2.  Po otwarciu projektu, Dodaj polecenie niestandardowe szablon elementu o nazwie **TestCommand**. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Add / nowy element**. W **Dodaj nowy element** okno dialogowe, przejdź do **Visual C# / rozszerzalności** i wybierz **polecenia niestandardowego**. W **nazwa** u dołu okna, Zmień nazwę pliku polecenia, aby **TestCommand.cs**.

## <a name="creating-a-menu-on-the-ide-menu-bar"></a>Tworzenie Menu na pasku Menu środowiska IDE

#### <a name="to-create-a-menu"></a>Aby utworzyć menu

1.  W **Eksploratora rozwiązań**, otwórz TestCommandPackage.vsct.

     Na końcu pliku istnieje \<symbole > węzeł, który zawiera kilka \<GuidSymbol > węzłów. W węźle, nazwane guidTestCommandPackageCmdSet Dodaj nowy symbol w następujący sposób:

    ```xml
    <IDSymbol name="TopLevelMenu" value="0x1021"/>
    ```

2.  Utwórz pustą \<menu > w węźle \<polecenia > węzła, tuż przed \<grupy >. W \<menu > węzła, Dodaj \<Menu > węzła, w następujący sposób:

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

     `guid` i `id` wartości menu określić zestaw poleceń i menu określonych w zestaw poleceń.

     `guid` i `id` wartości elementu nadrzędnego pozycji menu w sekcji pasek menu programu Visual Studio, który zawiera menu Narzędzia i Add-ins.

     Wartość `CommandName` ciąg Określa, że tekst powinien pojawić się w elemencie menu.

3.  W \<grupy > sekcji, Znajdź \<grupy > i zmień \<nadrzędnego > elementu, aby wskazać polecenie menu, który właśnie został dodany:

    ```csharp
    <Groups>
          <Group guid="guidTestCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
            <Parent guid="guidTestCommandPackageCmdSet" id="TopLevelMenu"/>
          </Group>
        </Groups>
    ```

     Dzięki temu grupy część nowego menu.

4.  Znajdź `Buttons` sekcji. Należy zauważyć, że [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] został wygenerowany szablon pakietu `Button` element, który ma nadrzędnego równa `MyMenuGroup`. W wyniku tego polecenia pojawi się w menu.

## <a name="building-and-testing-the-extension"></a>Tworzenie i testowanie rozszerzenia

1.  Skompiluj projekt, a następnie rozpocząć debugowanie. Wystąpienie doświadczalne wystąpienie powinna zostać wyświetlona.

2.  Na pasku menu w eksperymentalnym wystąpieniu powinien zawierać **TestMenu** menu.

3.  Na **TestMenu** menu, kliknij przycisk **Wywołaj polecenie Test**.

     Okno komunikatu powinno pojawiają się i wyświetli komunikat "TestCommand pakietu wewnątrz TopLevelMenu.TestCommand.MenuItemCallback()". Oznacza to, że nowe polecenie działa.

## <a name="see-also"></a>Zobacz też
 [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)
