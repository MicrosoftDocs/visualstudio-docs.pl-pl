---
title: Powiązywanie skrótów klawiaturowych z elementami menu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e362a61c5ecab78c332eb5e077a02ee4e9e3fa9b
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295618"
---
# <a name="binding-keyboard-shortcuts-to-menu-items"></a>Wiązanie skrótów klawiaturowych z elementami menu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby powiązać skrót klawiaturowy z niestandardowym poleceniem menu, po prostu Dodaj wpis do pliku. vsct pakietu. W tym temacie opisano sposób mapowania skrótu klawiaturowego na przycisk niestandardowy, element menu lub polecenie paska narzędzi oraz sposób zastosowania mapowania klawiatury w domyślnym edytorze lub ograniczanie go do niestandardowego edytora.  
  
 Aby przypisać skróty klawiaturowe do istniejących elementów menu programu Visual Studio, zobacz [Identyfikowanie i Dostosowywanie skrótów klawiaturowych](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
## <a name="choosing-a-key-combination"></a>Wybieranie kombinacji klawiszy  
 Wiele skrótów klawiaturowych jest już używanych w programie Visual Studio. Nie należy przypisywać tego samego skrótu do więcej niż jednego polecenia, ponieważ duplikaty powiązań są trudne do wykrycia i mogą być również przyczyną nieprzewidzianych wyników. Z tego względu dobrym pomysłem jest zweryfikowanie dostępności skrótu przed przypisaniem.  
  
#### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Aby sprawdzić dostępność skrótu klawiaturowego  
  
1. W oknie **Narzędzia/Opcje/środowisko** wybierz pozycję **Klawiatura**.  
  
2. Upewnij się, że dla **opcji Użyj nowego skrótu w programie** ustawiono wartość **globalne**.  
  
3. W polu **naciśnij klawisze skrótu** wpisz skrót klawiaturowy, który ma być używany.  
  
    Jeśli skrót jest już używany w programie Visual Studio, **skrót aktualnie używany przez** pole będzie zawierać polecenie, które aktualnie wywołuje skrót.  
  
4. Wypróbuj różne kombinacje kluczy, dopóki nie zostanie ono zamapowane.  
  
   > [!NOTE]
   > Skróty klawiaturowe używające ALT mogą otworzyć menu i nie wykonywać bezpośrednio polecenia. W związku z tym **skrót aktualnie używany przez** pole może być pusty po wpisaniu skrótu, który zawiera Alt. Możesz sprawdzić, czy skrót nie otwiera menu, zamykając okno dialogowe **Opcje** , a następnie naciskając klawisze.  
  
   W poniższej procedurze przyjęto założenie, że masz istniejący pakietu VSPackage z poleceniem menu. Jeśli potrzebujesz pomocy, zapoznaj się z tematem [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
#### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Aby przypisać skrót klawiaturowy do polecenia  
  
1. Otwórz plik. vsct dla pakietu.  
  
2. Utwórz pustą sekcję `<KeyBindings>` po `<Commands>`, jeśli jeszcze jej nie ma.  
  
   > [!WARNING]
   > Aby uzyskać więcej informacji na temat powiązań kluczy, zobacz [powiązanie klawiszy](../extensibility/keybinding-element.md).  
  
    W sekcji `<KeyBindings>` Utwórz wpis `<KeyBinding>`.  
  
    Ustaw atrybuty `guid` i `id` na wartości poleceń, które chcesz wywołać.  
  
    Ustaw atrybut `mod1` na **Control**, **Alt**lub **SHIFT**.  
  
    Sekcja powiązania klawiszy powinna wyglądać następująco:  
  
   ```xml  
   <KeyBindings>  
       <KeyBinding guid="<name of command set>" id="<name of command id>"  
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>  
   </KeyBindings>  
  
   ```  
  
   Jeśli skrót klawiaturowy wymaga więcej niż dwóch kluczy, ustaw atrybuty `mod2` i `key2`.  
  
   W większości sytuacji nie należy używać **klawisza Shift** bez drugiego modyfikatora, ponieważ jego naciśnięcie już powoduje, że większość klawiszy alfanumerycznych może wpisać wielką literę lub symbol.  
  
   Kody kluczy wirtualnych umożliwiają dostęp do kluczy specjalnych, które nie mają skojarzonego z nimi znaku, na przykład klawisze funkcyjne i klawisz **Backspace** . Aby uzyskać więcej informacji, zobacz [kody kluczy wirtualnych](https://go.microsoft.com/fwlink/?LinkID=105932).  
  
   Aby polecenie było dostępne w edytorze programu Visual Studio, ustaw atrybut `editor` na `guidVSStd97`.  
  
   Aby polecenie było dostępne tylko w edytorze niestandardowym, należy ustawić atrybut `editor` na nazwę niestandardowego edytora, który został wygenerowany przez szablon pakietu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] podczas tworzenia pakietu VSPackage zawierającego Edytor niestandardowy. Aby znaleźć wartość nazwy, zapoznaj się z sekcją `<Symbols>` węzła `<GuidSymbol>`, którego atrybut `name` jest zakończony "`editorfactory`". To jest nazwa niestandardowego edytora.  
  
## <a name="example"></a>Przykład  
 Ten przykład wiąże skrót klawiaturowy CTRL + ALT + C do polecenia o nazwie `cmdidMyCommand` w pakiecie o nazwie `MyPackage`.  
  
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
 Ten przykład wiąże skrót klawiaturowy CTL + B z poleceniem o nazwie `cmdidBold` w projekcie o nazwie `TestEditor`. Polecenie jest dostępne tylko w edytorze niestandardowym, a nie w innych edytorach.  
  
```xml  
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)
