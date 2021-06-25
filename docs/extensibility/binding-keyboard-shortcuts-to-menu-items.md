---
title: Wiązanie skrótów klawiaturowych z elementami menu | Microsoft Docs
description: Dowiedz się, jak zamapować skrót klawiaturowy w Visual Studio na niestandardowy przycisk, element menu lub polecenie paska narzędzi dla edytora domyślnego lub edytora niestandardowego.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6a9591a7412b0bcaf506483a16a6660790df5f40
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900437"
---
# <a name="bind-keyboard-shortcuts-to-menu-items"></a>Wiązanie skrótów klawiaturowych z elementami menu
Aby powiązać skrót klawiaturowy z poleceniem menu niestandardowego, wystarczy dodać wpis do pliku *vsct* pakietu. W tym temacie wyjaśniono, jak zamapować skrót klawiaturowy na niestandardowy przycisk, element menu lub polecenie paska narzędzi oraz jak zastosować mapowanie klawiatury w edytorze domyślnym lub ograniczyć je do edytora niestandardowego.

 Aby przypisać skróty klawiaturowe do istniejących Visual Studio menu, zobacz [Identyfikowanie i dostosowywanie skrótów klawiaturowych.](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)

## <a name="choose-a-key-combination"></a>Wybieranie kombinacji klawiszy
 Wiele skrótów klawiaturowych jest już używanych w Visual Studio. Nie należy przypisywać tego samego skrótu do więcej niż jednego polecenia, ponieważ zduplikowane powiązania są trudne do wykrycia i mogą również powodować nieprzewidywalne wyniki. Dlatego warto sprawdzić dostępność skrótu przed jego przypisaniem.

### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Aby sprawdzić dostępność skrótu klawiaturowego

1. W **oknie**  >  **Środowisko opcji**  >  **narzędzi** wybierz pozycję **Klawiatura.**

2. Upewnij się, **że ustawienie Użyj nowego skrótu w programie** ma wartość **Globalne.**

3. W Naciśnij **klawisze skrótów** wpisz skrót klawiaturowy, którego chcesz użyć.

    Jeśli skrót jest już używany w Visual Studio, skrót aktualnie używany **przez** pole pokaże polecenie, które skrót aktualnie wywołuje.

4. Wypróbuj różne kombinacje klawiszy, dopóki nie znajdziesz tej, która nie jest mapowana.

   > [!NOTE]
   > Skróty klawiaturowe, które używają **klawiszy Alt,** mogą otwierać menu i nie wykonywać polecenia bezpośrednio. W związku z **tym skrót aktualnie używany przez** pole może być puste po wpisaniu skrótu, który zawiera **Alt**. Możesz sprawdzić, czy skrót nie otwiera menu, zamykając **okno** dialogowe Opcje, a następnie naciskając klawisze.

   W poniższej procedurze przyjęto założenie, że masz istniejący pakiet VSPackage za pomocą polecenia menu. Jeśli potrzebujesz pomocy w tym celu, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Aby przypisać skrót klawiaturowy do polecenia

1. Otwórz *plik vsct* pakietu.

2. Utwórz `<KeyBindings>` pustą sekcję po `<Commands>` poleceniu , jeśli jeszcze jej nie ma.

   > [!WARNING]
   > Aby uzyskać więcej informacji na temat powiązań kluczy, zobacz [Powiązania klawiszy](../extensibility/keybinding-element.md).

    W `<KeyBindings>` sekcji utwórz `<KeyBinding>` wpis.

    Ustaw atrybuty `guid`  i  `id` na atrybuty polecenia, które chcesz wywołać.

    Ustaw atrybut `mod1` na **Control,** **Alt** lub **Shift**.

    Sekcja KeyBindings powinna wyglądać podobnie do tej:

   ```xml
   <KeyBindings>
       <KeyBinding guid="<name of command set>" id="<name of command id>"
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>
   </KeyBindings>

   ```

   Jeśli skrót klawiaturowy wymaga więcej niż dwóch klawiszy, ustaw `mod2` `key2` atrybuty i .

   W większości przypadków nie należy używać klawisza **Shift** bez drugiego modyfikatora, ponieważ naciśnięcie go już powoduje, że większość klawiszy alfanumerycznych wpisze wielkie litery lub symbol.

   Kody kluczy wirtualnych umożliwiają dostęp do kluczy specjalnych, które nie mają skojarzonego znaku, na przykład kluczy funkcji i **klawisza Backspace.** Aby uzyskać więcej informacji, zobacz [Virtual-key codes](/windows/desktop/inputdev/virtual-key-codes).

   Aby udostępnić polecenie w edytorze Visual Studio, ustaw `editor` atrybut na `guidVSStd97` .

   Aby udostępnić polecenie tylko w edytorze niestandardowym, ustaw atrybut na nazwę edytora niestandardowego wygenerowanego przez szablon pakietu podczas tworzenia pakietu VSPackage zawierającego edytor `editor` [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] niestandardowy. Aby znaleźć wartość nazwy, poszukaj w sekcji `<Symbols>` węzła, którego `<GuidSymbol>` atrybut kończy się na " `name` `editorfactory` ." Jest to nazwa edytora niestandardowego.

## <a name="example-1"></a>Przykład 1
 Ten przykład wiąże skrót klawiaturowy **Ctrl** + **Alt** + **C** z poleceniem o nazwie `cmdidMyCommand` w pakiecie o nazwie `MyPackage` .

```
<CommandTable>
. . .
<Commands>
. . .
</Commands>
<KeyBindings>
  <KeyBinding guid="guidMyPackageCmdSet" id="cmdidMyCommand"
      key1="C" mod1="CONTROL" mod2="ALT" editor="guidVSStd97" />
</KeyBindings>
. . .
</CommandTable>
```

## <a name="example-2"></a>Przykład 2
 Ten przykład wiąże skrót klawiaturowy **Ctrl** + **B** z poleceniem o nazwie `cmdidBold` w projekcie o nazwie `TestEditor` . Polecenie jest dostępne tylko w edytorze niestandardowym, a nie w innych edytorach.

```xml
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />
```

## <a name="see-also"></a>Zobacz też
- [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)
