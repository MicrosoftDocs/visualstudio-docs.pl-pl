---
title: Powiązanie skrótów klawiaturowych z elementami menu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94feafbc614be61aaa4eef9e26669c0fbe901ed5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740024"
---
# <a name="bind-keyboard-shortcuts-to-menu-items"></a>Powiązuj skróty klawiaturowe z elementami menu
Aby powiązać skrót klawiaturowy z poleceniem menu niestandardowego, wystarczy dodać wpis do pliku *vsct* dla pakietu. W tym temacie wyjaśniono, jak zamapować skrót klawiaturowy na przycisk niestandardowy, element menu lub polecenie paska narzędzi oraz jak zastosować mapowanie klawiatury w edytorze domyślnym lub ograniczyć go do edytora niestandardowego.

 Aby przypisać skróty klawiaturowe do istniejących elementów menu programu Visual Studio, zobacz [Identyfikowanie i dostosowywanie skrótów klawiaturowych](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

## <a name="choose-a-key-combination"></a>Wybieranie kombinacji klawiszy
 Wiele skrótów klawiaturowych jest już używanych w programie Visual Studio. Nie należy przypisywać tego samego skrótu do więcej niż jednego polecenia, ponieważ zduplikowane powiązania są trudne do wykrycia i mogą również powodować nieprzewidywalne wyniki. W związku z tym warto sprawdzić dostępność skrótu przed jego przypisaniem.

### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Aby sprawdzić dostępność skrótu klawiaturowego

1. W oknie**Środowisko** **opcji** >  **narzędzi** > wybierz pozycję **Klawiatura**.

2. Upewnij się, że **użyj nowego skrótu jest** ustawiona na **Globalna**.

3. W polu **Naciśnij klawisze skrótów** wpisz skrót klawiaturowy, którego chcesz użyć.

    Jeśli skrót jest już używany w programie Visual Studio, **skrót aktualnie używany przez** pole pokaże polecenie, które skrót obecnie wywołuje.

4. Wypróbuj różne kombinacje klawiszy, aż znajdziesz taki, który nie jest mapowany.

   > [!NOTE]
   > Skróty klawiaturowe korzystające z **klawisza Alt** mogą otwierać menu i nie wykonywać bezpośrednio polecenia. W związku z tym **skrót aktualnie używany przez** pole może być puste po wpisaniu skrótu zawierającego **Alt**. Można sprawdzić, czy skrót nie otwiera menu, zamykając okno dialogowe **Opcje,** a następnie naciskając klawisze.

   Poniższa procedura zakłada, że masz istniejący VSPackage z poleceniem menu. Jeśli potrzebujesz pomocy w tym zakresie, spójrz na [Utwórz rozszerzenie za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).

### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Aby przypisać skrót klawiaturowy do polecenia

1. Otwórz plik *vsct* dla pakietu.

2. Utwórz `<KeyBindings>` pustą `<Commands>` sekcję po, jeśli nie jest jeszcze obecny.

   > [!WARNING]
   > Aby uzyskać więcej informacji na temat powiązań kluczy, zobacz [Keybinding](../extensibility/keybinding-element.md).

    W `<KeyBindings>` sekcji utwórz `<KeyBinding>` wpis.

    Ustaw `guid` atrybuty i `id` te polecenia, które chcesz wywołać.

    Ustaw `mod1` atrybut na **Formant,** **Alt**lub **Shift**.

    Sekcja KeyBindings powinna wyglądać mniej więcej tak:

   ```xml
   <KeyBindings>
       <KeyBinding guid="<name of command set>" id="<name of command id>"
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>
   </KeyBindings>

   ```

   Jeśli skrót klawiaturowy wymaga więcej niż `mod2` `key2` dwóch klawiszy, ustaw atrybuty i atrybuty.

   W większości sytuacji **Shift** nie powinny być używane bez drugiego modyfikatora, ponieważ naciśnięcie go powoduje już większość klawiszy alfanumeryczne, aby wpisać wielką literę lub symbol.

   Kody kluczy wirtualnych umożliwiają dostęp do kluczy specjalnych, które nie mają skojarzonego z nimi znaku, na przykład klawiszy funkcyjnych i **klawisza Backspace.** Aby uzyskać więcej informacji, zobacz [Kody klucza wirtualnego](/windows/desktop/inputdev/virtual-key-codes).

   Aby udostępnić polecenie w edytorze Visual `editor` Studio, `guidVSStd97`ustaw atrybut na .

   Aby udostępnić polecenie tylko w edytorze `editor` niestandardowym, ustaw atrybut na nazwę edytora niestandardowego, który został wygenerowany przez szablon [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pakietu podczas tworzenia programu VSPackage zawierającego edytor niestandardowy. Aby znaleźć wartość nazwy, `<Symbols>` poszukaj w sekcji węzła, `<GuidSymbol>` którego `name` atrybut kończy się na "`editorfactory`." Jest to nazwa edytora niestandardowego.

## <a name="example"></a>Przykład
 W tym przykładzie skrót klawiaturowy **Ctrl**+**Alt**+**C** z poleceniem o nazwie `cmdidMyCommand` w pakiecie o nazwie `MyPackage`.

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

## <a name="example"></a>Przykład
 W tym przykładzie skrót klawiaturowy **Ctrl**+**B** wiąże z poleceniem o nazwie `cmdidBold` `TestEditor`. Polecenie jest dostępne tylko w edytorze niestandardowym, a nie w innych edytorach.

```xml
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />
```

## <a name="see-also"></a>Zobacz też
- [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)
