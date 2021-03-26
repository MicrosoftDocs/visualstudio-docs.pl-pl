---
title: Tworzenie grup przycisków do wielokrotnego użytku | Microsoft Docs
description: Dowiedz się, jak utworzyć grupę poleceń, która jest kolekcją poleceń, które pojawiają się razem w menu lub pasku narzędzi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- button groups, creating in VSPackages
- VSPackages, creating reusable button groups
- buttons, creating reusable groups
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6b9c0bd759083a0d0d053133cc9f2d4d03a52389
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055742"
---
# <a name="create-reusable-groups-of-buttons"></a>Tworzenie grup przycisków do wielokrotnego użytku
Grupa poleceń to kolekcja poleceń, które zawsze pojawiają się w menu lub pasku narzędzi. Każdą grupę poleceń można ponownie użyć, przypisując ją do różnych menu nadrzędnych w sekcji CommandPlacements pliku *. vsct* .

 Grupy poleceń zazwyczaj zawierają przyciski, ale mogą również zawierać inne menu lub pola kombi.

## <a name="to-create-a-reusable-group-of-buttons"></a>Aby utworzyć grupę przycisków wielokrotnego użytku

1. Utwórz projekt VSIX o nazwie `ReusableButtons` . Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Po otwarciu projektu Dodaj niestandardowy szablon elementu polecenia o nazwie **ReusableCommand**. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj**  >  **nowy element**. W oknie dialogowym **Dodaj nowy element** przejdź do rozszerzalności **Visual C#**  >   i wybierz **polecenie niestandardowe**. W polu **Nazwa** w dolnej części okna Zmień nazwę pliku polecenia na *ReusableCommand. cs*.

3. W pliku *. vsct* przejdź do sekcji symbole i Znajdź element GuidSymbol, który zawiera grupy i polecenia dla projektu. Powinien być nazwany guidReusableCommandPackageCmdSet.

4. Dodaj IDSymbol dla każdego przycisku, który zostanie dodany do grupy, jak w poniższym przykładzie.

    ```xml
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">
        <IDSymbol name="MyMenuGroup" value="0x1020" />
        <IDSymbol name="ReusableCommandId" value="0x0100" />
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />
    </GuidSymbol>
    ```

     Domyślnie szablon elementu polecenia tworzy grupę o nazwie **webmenu** i przycisk o podanej nazwie, a także wpis IDSymbol dla każdego z nich.

5. W sekcji grupy Utwórz element grupy, który ma te same atrybuty GUID i identyfikator, co podane w sekcji symbole. Możesz również użyć istniejącej grupy lub użyć wpisu dostarczonego przez szablon polecenia, jak w poniższym przykładzie. Ta grupa pojawia się w menu **Narzędzia**

    ```xml
    <Groups>
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>
        </Group>
    </Groups>
    ```

## <a name="to-create-a-group-of-buttons-for-reuse"></a>Aby utworzyć grupę przycisków do ponownego użycia

1. Możesz umieścić polecenie lub menu w grupie za pomocą grupy jako elementu nadrzędnego w definicji polecenia lub menu lub przez umieszczenie polecenia lub menu w grupie przy użyciu sekcji CommandPlacements.

     W sekcji przyciski Zdefiniuj przycisk, który ma swoją grupę jako element nadrzędny, lub użyj przycisku dostarczonego przez szablon pakietu, jak pokazano w poniższym przykładzie.

    ```xml
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ReusableCommand</ButtonText>
        </Strings>
    </Button>
    ```

2. Jeśli przycisk musi znajdować się w więcej niż jednej grupie, Utwórz dla niego wpis w sekcji CommandPlacements, który musi być umieszczony po sekcji Commands. Ustaw identyfikatory GUID i identyfikator elementu CommandPlacement, aby pasowały do przycisków, które chcesz umieścić w pozycji, a następnie ustaw identyfikator GUID i identyfikator jego elementu nadrzędnego dla grupy docelowej, jak pokazano w poniższym przykładzie.

    ```xml
    <CommandPlacements>
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        </CommandPlacement>
    </CommandPlacements>
    ```

    > [!NOTE]
    > Wartość pola priorytet określa pozycję polecenia w nowej grupie poleceń. Priorytety ustawione w elemencie CommandPlacement przesłaniają te ustawienia w definicji elementu. Polecenia o niższych wartościach priorytetów są wyświetlane przed poleceniami, które mają wyższe wartości priorytetów. Wartości zduplikowanych priorytetów są dozwolone, ale względne położenie poleceń o tej samej wartości priorytetu nie może być gwarantowane, ponieważ kolejność, w której polecenie **devenv/setup** tworzy końcowy interfejs z rejestru, może być niespójna.

## <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>Aby umieścić w menu grupę przycisków do wielokrotnego użytku

1. Utwórz wpis w `CommandPlacements` sekcji. Ustaw identyfikator GUID i identyfikator `CommandPlacement` elementu dla grupy, a następnie ustaw nadrzędny identyfikator GUID i identyfikator dla lokalizacji docelowej.

    Sekcja CommandPlacements powinna zostać umieszczona bezpośrednio po sekcji Commands:

   ```xml
   <CommandTable>
   ...
     <Commands>... </Commands>
     <CommandPlacements>... </CommandPlacements>
   ...
   </CommandTable>
   ```

    Grupa poleceń może być uwzględniona w więcej niż jednym menu. Menu nadrzędne może być jedną z utworzonych przez siebie, która jest dostarczana przez program [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (zgodnie z opisem w *ShellCmdDef. vsct* lub *SharedCmdDef. vsct*) lub jeden, który jest zdefiniowany w innym pakietu VSPackage. Liczba warstw nadrzędnych jest nieograniczona, o ile menu nadrzędne jest ostatecznie połączone z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] lub do menu skrótów, które jest wyświetlane przez pakietu VSPackage.

    Poniższy przykład umieszcza grupę na pasku narzędzi **Eksplorator rozwiązań** po prawej stronie innych przycisków.

   ```xml
   <CommandPlacements>
       <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0xF00">
         <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>
       </CommandPlacement>
   </CommandPlacements>
   ```

   ```xml
   <CommandPlacements>
     <CommandPlacement guid="guidButtonGroupCmdSet" id="MyMenuGroup"
         priority="0x605">
       <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS" />
     </CommandPlacement>
   </CommandPlacements>

   ```
