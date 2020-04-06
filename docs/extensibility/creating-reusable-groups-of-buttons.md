---
title: Tworzenie grup przycisków wielokrotnego pożyciem | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- button groups, creating in VSPackages
- VSPackages, creating reusable button groups
- buttons, creating reusable groups
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ddfba6701890f73ce6438ddc03a338912841a37d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739465"
---
# <a name="create-reusable-groups-of-buttons"></a>Tworzenie grup przycisków wielokrotnego pożyciem
Grupa poleceń to zbiór poleceń, które zawsze pojawiają się razem na menu lub pasku narzędzi. Dowolną grupę poleceń można ponownie użyć, przypisując ją do różnych menu nadrzędnych w sekcji CommandPlacements pliku *vsct.*

 Grupy poleceń zazwyczaj zawierają przyciski, ale mogą również zawierać inne menu lub pola kombi.

## <a name="to-create-a-reusable-group-of-buttons"></a>Aby utworzyć grupę przycisków wielokrotnego pożycie

1. Utwórz projekt VSIX o nazwie `ReusableButtons`. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Po otwarciu projektu dodaj niestandardowy szablon elementu polecenia o nazwie **ReusableCommand**. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj** > **nowy element**. W oknie dialogowym **Dodawanie nowego elementu** przejdź do pozycji**Rozszerzalność** **programu Visual C#** > i wybierz polecenie **Niestandardowe**. W polu **Nazwa** u dołu okna zmień nazwę pliku polecenia na *ReusableCommand.cs*.

3. W pliku *vsct* przejdź do sekcji Symbole i znajdź element GuidSymbol zawierający grupy i polecenia dla projektu. Powinien być nazwany guidReusableCommandPackageCmdSet.

4. Dodaj IDSymbol dla każdego przycisku, który zostanie dodany do grupy, jak w poniższym przykładzie.

    ```xml
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">
        <IDSymbol name="MyMenuGroup" value="0x1020" />
        <IDSymbol name="ReusableCommandId" value="0x0100" />
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />
    </GuidSymbol>
    ```

     Domyślnie szablon elementu polecenia tworzy grupę o nazwie **MyMenuGroup** i przycisk, który ma podaną nazwę, wraz z wpisem IDSymbol dla każdego.

5. W sekcji Grupy utwórz element Grupy, który ma takie same atrybuty GUID i ID, jak te podane w sekcji Symbole. Można również użyć istniejącej grupy lub użyć wpisu, który jest dostarczany przez szablon polecenia, jak w poniższym przykładzie. Ta grupa pojawi się w menu **Narzędzia**

    ```xml
    <Groups>
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>
        </Group>
    </Groups>
    ```

## <a name="to-create-a-group-of-buttons-for-reuse"></a>Aby utworzyć grupę przycisków do ponownego użycia

1. Można umieścić polecenie lub menu w grupie za pomocą grupy jako element nadrzędny w definicji polecenia lub menu lub umieszczając polecenie lub menu w grupie za pomocą commandPlacements sekcji.

     W sekcji Przyciski zdefiniuj przycisk, który ma grupę jako element nadrzędny, lub użyj przycisku dostarczonego przez szablon pakietu, jak pokazano w poniższym przykładzie.

    ```xml
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ReusableCommand</ButtonText>
        </Strings>
    </Button>
    ```

2. Jeśli przycisk musi pojawić się w więcej niż jednej grupie, utwórz dla niego wpis w sekcji CommandPlacements, który musi zostać umieszczony po sekcji Polecenia. Ustaw atrybuty identyfikatora GUID i identyfikatora elementu CommandPlacement, aby były zgodne z atrybutami przycisku, który chcesz umieścić, a następnie ustaw identyfikator GUID i identyfikator jego elementu nadrzędnego na atrybuty grupy docelowej, jak pokazano w poniższym przykładzie.

    ```xml
    <CommandPlacements>
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />
        </CommandPlacement>
    </CommandPlacements>
    ```

    > [!NOTE]
    > Wartość pola Priorytet określa położenie polecenia w nowej grupie poleceń. Priorytety ustawione w elemencie CommandPlacement zastępują te ustawione w definicji elementu. Polecenia o niższym priorytecie są wyświetlane przed poleceniami o wyższym priorytecie. Zduplikowane wartości priorytetu są dozwolone, ale względne położenie poleceń, które mają taką samą wartość priorytetu, nie może być zagwarantowane, ponieważ kolejność, w jakiej polecenie **devenv /setup** tworzy końcowy interfejs z rejestru, może nie być spójna.

## <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>Aby umieścić grupę przycisków wielokrotnegoużytnia w menu

1. Utwórz wpis `CommandPlacements` w sekcji. Ustaw identyfikator GUID i `CommandPlacement` identyfikator elementu na identyfikator grupy i ustaw nadrzędny identyfikator GUID i identyfikator na identyfikator lokalizacji docelowej.

    Sekcja CommandPlacements powinna być umieszczona tuż po sekcji Polecenia:

   ```xml
   <CommandTable>
   ...
     <Commands>... </Commands>
     <CommandPlacements>... </CommandPlacements>
   ...
   </CommandTable>
   ```

    Grupa poleceń może być uwzględniona w więcej niż jednym menu. Menu nadrzędne może być jednym, który został [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utworzony, który jest dostarczany przez (zgodnie z opisem w *ShellCmdDef.vsct* lub *SharedCmdDef.vsct),* lub taki, który jest zdefiniowany w innym VSPackage. Liczba warstw nadrzędnych jest nieograniczona, o ile menu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nadrzędne jest ostatecznie połączone z lub z menu skrótów, które jest wyświetlane przez vspackage.

    Poniższy przykład umieszcza grupę na pasku narzędzi **Eksploratora rozwiązań,** po prawej stronie innych przycisków.

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
