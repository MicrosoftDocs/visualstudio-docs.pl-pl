---
title: Dodawanie paska narzędzi | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
caps.latest.revision: 39
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: de74961715a82dde4e184509094d05145ad0f79c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60077722"
---
# <a name="adding-a-toolbar"></a>Dodawanie paska narzędzi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu pokazano, jak dodać pasek narzędzi środowiska IDE programu Visual Studio.  
  
 Pasek narzędzi jest poziomy lub pionowy pasek, zawierający przyciski, które są powiązane z poleceń. W zależności od jego implementacja paska narzędzi w IDE mogą być przeniesiony, zadokowany po dowolnej stronie głównego okna środowiska IDE lub wykonywane na bieżąco przed innymi oknami.  
  
 Ponadto użytkownicy mogą dodać polecenia do paska narzędzi lub usuń je z niego, używając **Dostosuj** okno dialogowe. Zazwyczaj paski narzędzi w pakietach VSPackage są dostosowywane do użytkownika. IDE obsługuje wszystkie dostosowania i pakietu VSPackage reaguje na polecenia. Pakietu VSPackage nie musi wiedzieć, gdzie fizycznie znajduje się polecenie.  
  
 Aby uzyskać więcej informacji na temat menu, zobacz [polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-an-extension-with-a-toolbar"></a>Tworzenie rozszerzenia za pomocą paska narzędzi  
 Utwórz projekt VSIX, o nazwie `IDEToolbar`. Dodaj szablon elementu polecenia menu o nazwie **ToolbarTestCommand**. Aby dowiedzieć się, jak to zrobić, zobacz [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="creating-a-toolbar-for-the-ide"></a>Tworzenia paska narzędzi dla środowiska IDE  
  
1. ToolbarTestCommandPackage.vsct poszukaj sekcji symboli. W GuidSymbol, element o nazwie guidToolbarTestCommandPackageCmdSet Dodaj następujące deklaracje dla paska narzędzi i grupę paska narzędzi.  
  
    ```xml  
    <IDSymbol name="Toolbar" value="0x1000" />  
    <IDSymbol name="ToolbarGroup" value="0x1050" />  
  
    ```  
  
2. W górnej części sekcji polecenia Utwórz sekcję menu. Dodaj Menu element do sekcji menu, aby zdefiniować paska narzędzi.  
  
    ```xml  
    <Menus>  
        <Menu guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"  
            type="Toolbar" >  
            <CommandFlag>DefaultDocked</CommandFlag>  
            <Strings>  
                <ButtonText>Test Toolbar</ButtonText>  
                <CommandName>Test Toolbar</CommandName>  
            </Strings>  
          </Menu>  
    </Menus>  
    ```  
  
     Nie można zagnieżdżać pasków narzędzi takich jak podmenu. W związku z tym nie trzeba przypisać grupę nadrzędną. Ponadto nie masz można ustawić priorytet, ponieważ użytkownik może poruszać się paski narzędzi. Zazwyczaj początkowe położenie paska narzędzi jest zdefiniowany programowo, ale kolejne zmiany przez użytkownika są zachowywane.  
  
3. W [grup](../extensibility/groups-element.md) po istniejący wpis grupy sekcji zdefiniować [grupy](../extensibility/group-element.md) elementu, aby zawierał polecenia na pasku narzędzi.  
  
    ```xml  
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"  
          priority="0x0000">  
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>  
    </Group>  
    ```  
  
4. Przyciskowi są wyświetlane na pasku narzędzi. W sekcji przyciski Zastąp nadrzędny blok przycisku na pasku narzędzi. Wynikowy blokowych przycisk powinien wyglądać następująco:  
  
    ```xml  
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">  
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />  
                <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     Domyślnie jeśli pasek narzędzi ma żadne polecenia nie ma.  
  
5. Skompiluj projekt, a następnie rozpocząć debugowanie. Wystąpienie eksperymentalne powinna zostać wyświetlona.  
  
6. Kliknij prawym przyciskiem myszy na pasku menu programu Visual Studio można pobrać listy pasków narzędzi. Wybierz **Test narzędzi**.  
  
7. Pasek narzędzi powinna zostać wyświetlona jako ikony po prawej stronie Znajdź w plikach ikonę. Po kliknięciu ikony, powinien zostać wyświetlony komunikat informujący, że **ToolbarTestCommandPackage. Inside IDEToolbar.ToolbarTestCommand.MenuItemCallback()**.  
  
## <a name="see-also"></a>Zobacz też  
 [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)
