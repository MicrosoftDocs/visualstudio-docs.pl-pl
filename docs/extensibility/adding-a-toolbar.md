---
title: Dodawanie paska narzędzi | Microsoft Docs
description: Dowiedz się, jak dodać pasek narzędzi zawierający przyciski, które są powiązane z poleceniami do zintegrowanego środowiska programistycznego (IDE) programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- toolbars [Visual Studio], adding to IDE
- IDE, adding toolbars
ms.assetid: 17302c25-6f59-4e97-8c85-54f95336a07f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 434f7470fe5fca13f217c981cc99d6a884117a86
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597954"
---
# <a name="add-a-toolbar"></a>Dodawanie paska narzędzi
W tym instruktażu pokazano, jak dodać pasek narzędzi do środowiska IDE programu Visual Studio.

 Pasek narzędzi to poziomy lub pionowy pasek zawierający przyciski, które są powiązane z poleceniami. W zależności od jego implementacji pasek narzędzi w IDE może być zmieniany, zadokowany po każdej stronie głównego okna środowiska IDE lub mieć miejsce przed innymi oknami.

 Ponadto użytkownicy mogą dodawać polecenia do paska narzędzi lub usuwać je z niego przy użyciu okna dialogowego **Dostosowywanie** . Zazwyczaj paski narzędzi w pakietów VSPackage są dostosowywane do użytkownika. Środowisko IDE obsługuje wszystkie dostosowania, a pakietu VSPackage reaguje na polecenia. Pakietu VSPackage nie musi wiedzieć, gdzie fizycznie znajduje się polecenie.

 Aby uzyskać więcej informacji na temat menu, zobacz [polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-toolbar"></a>Tworzenie rozszerzenia za pomocą paska narzędzi
 Utwórz projekt VSIX o nazwie `IDEToolbar` . Dodaj szablon elementu polecenia menu o nazwie **ToolbarTestCommand**. Aby uzyskać informacje o tym, jak to zrobić, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="create-a-toolbar-for-the-ide"></a>Utwórz pasek narzędzi dla środowiska IDE

1. W *ToolbarTestCommandPackage. vsct* poszukaj sekcji symboli. W elemencie GuidSymbol o nazwie guidToolbarTestCommandPackageCmdSet Dodaj deklaracje dla paska narzędzi i grupy pasków narzędzi w następujący sposób.

    ```xml
    <IDSymbol name="Toolbar" value="0x1000" />
    <IDSymbol name="ToolbarGroup" value="0x1050" />

    ```

2. W górnej części sekcji Commands (polecenia) utwórz sekcję menu. Dodaj element menu do sekcji menu, aby zdefiniować swój pasek narzędzi.

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

     Paski narzędzi nie mogą być zagnieżdżone jako podmenu. W związku z tym nie trzeba przypisywać grupy nadrzędnej. Ponadto nie ma konieczności ustawiania priorytetu, ponieważ użytkownik może przenosić paski narzędzi. Zwykle początkowe umieszczanie paska narzędzi jest zdefiniowane programowo, ale kolejne zmiany wprowadzane przez użytkownika są utrwalane.

3. W sekcji [grupy](../extensibility/groups-element.md) , po istniejącym wpisie grupy, zdefiniuj element [grupy](../extensibility/group-element.md) , aby zawierał polecenia dla paska narzędzi.

    ```xml
    <Group guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup"
          priority="0x0000">
      <Parent guid="guidToolbarTestCommandPackageCmdSet" id="Toolbar"/>
    </Group>
    ```

4. Ustaw przycisk na pasku narzędzi. W sekcji przyciski Zastąp blok nadrzędny w przycisku do paska narzędzi. Blok przycisku wynikający powinien wyglądać następująco:

    ```xml
    <Button guid="guidToolbarTestCommandPackageCmdSet" id="ToolbarTestCommandId" priority="0x0100" type="Button">
        <Parent guid= "guidToolbarTestCommandPackageCmdSet" id="ToolbarGroup" />
                <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>Invoke ToolbarTestCommand</ButtonText>
        </Strings>
    </Button>
    ```

     Domyślnie, jeśli pasek narzędzi nie ma poleceń, nie jest wyświetlany.

5. Skompiluj projekt i Rozpocznij debugowanie. Powinno zostać wyświetlone wystąpienie eksperymentalne.

6. Kliknij prawym przyciskiem myszy pasek menu programu Visual Studio, aby wyświetlić listę pasków narzędzi. Wybierz pozycję **pasek narzędzi testu**.

7. Pasek narzędzi powinien być teraz widoczny jako ikona z prawej strony ikony Znajdź w plikach. Po kliknięciu ikony zostanie wyświetlone okno komunikatu z informacją o **ToolbarTestCommandPackage. Wewnątrz IDEToolbar. ToolbarTestCommand. MenuItemCallback ()**.

## <a name="see-also"></a>Zobacz także
- [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)
