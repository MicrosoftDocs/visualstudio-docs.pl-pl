---
title: Tworzenie grup do ponownego użycia przycisków | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- button groups, creating in VSPackages
- VSPackages, creating reusable button groups
- buttons, creating reusable groups
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
caps.latest.revision: 45
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4978a2a8d176ecf3c270bad32a1ae9f82397a642
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60065808"
---
# <a name="creating-reusable-groups-of-buttons"></a>Tworzenie grup przycisków do wielokrotnego użytku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Grupy poleceń jest kolekcją poleceń, które są zawsze wyświetlane razem na menu lub paska narzędzi. Wszystkie grupy poleceń może być ponownie wykorzystana, przypisując go do innego elementu nadrzędnego menu w sekcji CommandPlacements pliku vsct  
  
 Polecenie grupy zwykle zawierają przyciski, ale może również zawierać inne menu lub pola kombi.  
  
### <a name="to-create-a-reusable-group-of-buttons"></a>Aby utworzyć grupę wielokrotnego użytku przycisków  
  
1. Utwórz projekt VSIX, o nazwie `ReusableButtons`. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2. Po otwarciu projektu, Dodaj polecenie niestandardowe szablon elementu o nazwie **ReusableCommand**. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Add / nowy element**. W **Dodaj nowy element** okno dialogowe, przejdź do **Visual C# / rozszerzalności** i wybierz **polecenia niestandardowego**. W **nazwa** u dołu okna, Zmień nazwę pliku polecenia, aby **ReusableCommand.cs**.  
  
3. W pliku vsct przejdź do sekcji symbole i Znajdź element GuidSymbol, który zawiera grupy i polecenia do projektu. Połączenie powinno miało guidReusableCommandPackageCmdSet.  
  
4. Dodaj IDSymbol dla każdego przycisku, który zostanie dodany do grupy, jak w poniższym przykładzie.  
  
    ```xml  
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">  
        <IDSymbol name="MyMenuGroup" value="0x1020" />  
        <IDSymbol name="ReusableCommandId" value="0x0100" />  
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />  
    </GuidSymbol>  
    ```  
  
     Domyślnie szablon elementu polecenie tworzy grupę o nazwie **mojaGrupa** i przycisk, który zawiera nazwę która została podana, wraz z IDSymbol wpis dla każdego.  
  
5. W sekcji grupy należy utworzyć element grupy, która ma takie same atrybuty identyfikator GUID i identyfikator, jak te podane w sekcji symboli. Możesz również użyć istniejącej grupy lub użyć wpis, który znajduje się w szablonie polecenia jak w poniższym przykładzie. Ta grupa pojawia się na **narzędzia** menu  
  
    ```xml  
    <Groups>  
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">  
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>  
        </Group>  
    </Groups>  
    ```  
  
### <a name="to-create-a-group-of-buttons-for-reuse"></a>Aby utworzyć grupę przycisków do ponownego wykorzystania  
  
1. Polecenie lub menu można umieścić w grupie przy użyciu grupy jako element nadrzędny w definicji polecenia lub menu lub poprzez umieszczenie polecenia lub menu w grupie za pomocą sekcji CommandPlacements.  
  
     W sekcji przyciski zdefiniowanie przycisku, który zawiera grupy jako klasy nadrzędnej, lub użyj przycisku, który jest dostarczany przez szablon pakietu, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ReusableCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
2. Jeśli przycisk musi znajdować się w więcej niż jednej grupy, Utwórz wpis dla niego w sekcji CommandPlacements, która musi być umieszczone po sekcji poleceń. Ustawianie atrybutów identyfikator GUID i identyfikator CommandPlacement, element na odpowiednie dla przycisku który ma zostać ustawiony, a następnie ustaw identyfikator GUID i identyfikator odpowiedniego elementu nadrzędnego z tymi grupy docelowej, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <CommandPlacements>  
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">  
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />  
        </CommandPlacement>  
    </CommandPlacements>  
    ```  
  
    > [!NOTE]
    >  Wartość pola Priorytet określa położenie polecenie w nowej grupie poleceń. Ustaw priorytety w CommandPlacement, element przesłaniają akcje określonych w definicji elementu. Polecenia, które mają niższe wartości priorytetu są wyświetlane przed poleceniami, które mają wyższe wartości priorytetu. Priorytet zduplikowane wartości są dozwolone, ale nie można zagwarantować względne położenie poleceń, które mają taką samą wartość priorytetu, ponieważ kolejność, w której **devenv/Setup** polecenie tworzy ostatecznego interfejsu z rejestru może nie być zgodne.  
  
### <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>Aby umieścić wielokrotnego użytku grupy przycisków w menu  
  
1. Utwórz wpis w `CommandPlacements` sekcji. Ustaw identyfikator GUID i identyfikator `CommandPlacement` elementu, aby te grupy i Ustaw element nadrzędny identyfikator GUID i identyfikator do tych lokalizacji docelowej.  
  
     W sekcji CommandPlacements należy umieścić tuż po sekcji poleceń:  
  
    ```xml  
    <CommandTable>  
    ...  
      <Commands>... </Commands>  
      <CommandPlacements>... </CommandPlacements>  
    ...   
    </CommandTable>  
    ```  
  
     Grupy poleceń, można umieścić w menu więcej niż jeden. Menu nadrzędny może być taki, który został utworzony, jedną, która jest dostarczana przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (jak opisano powyżej w ShellCmdDef.vsct lub SharedCmdDef.vsct), czy taki, który jest zdefiniowany w innym pakietu VSPackage. Liczba warstw element nadrzędny jest nieograniczona, tak długo, jak menu nadrzędnego ostatecznie jest podłączony do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] lub menu skrótów, które są wyświetlane według pakietu VSPackage.  
  
     Poniższy przykład umieszcza grupie na **Eksploratora rozwiązań** paska narzędzi po prawej stronie inne przyciski.  
  
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
