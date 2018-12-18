---
title: Wiązanie skrótów klawiaturowych z elementami Menu | Dokumentacja firmy Microsoft
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
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5fd5ab9b09956c41620947ad1bcf529550db4aca
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752906"
---
# <a name="binding-keyboard-shortcuts-to-menu-items"></a>Wiązanie skrótów klawiaturowych z elementami menu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby powiązać polecenia niestandardowego menu skrótu klawiaturowego, Dodaj odpowiedni wpis do pliku vsct pakietu. W tym temacie opisano sposób mapowania skrótów klawiaturowych na niestandardowy przycisk, element menu lub paska narzędzi polecenia, a także jak zastosować Mapowanie klawiatury w edytorze domyślnej lub ograniczyć je do edytora niestandardowego.  
  
 Aby przypisać skróty klawiaturowe do istniejących elementów menu programu Visual Studio, zobacz [określenie i dostosowywanie skrótów klawiaturowych](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
## <a name="choosing-a-key-combination"></a>Wybranie kombinacji klawiszy  
 Wiele skrótów klawiaturowych są już używane w programie Visual Studio. Nie należy przypisywać ten sam skrót do więcej niż jednego polecenia, ponieważ zduplikowane powiązania są trudne do wykrycia, a także mogą powodować nieprzewidywalne skutki. Dlatego jest dobry pomysł, aby sprawdzić dostępność skrót, przed przypisaniem go.  
  
#### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Aby sprawdzić dostępność skrót klawiaturowy  
  
1. W **narzędzia / Opcje / środowisko** wybierz **klawiatury**.  
  
2. Upewnij się, że **Użyj nowego skrótu** ustawiono **Global**.  
  
3. W **naciśnij klawisze skrótu** wpisz skrót klawiaturowy, który chcesz użyć.  
  
    Jeśli skrót jest już używany w programie Visual Studio, **skrót aktualnie używany przez** zostanie wyświetlone skrót aktualnie wywołuje polecenie.  
  
4. Wypróbuj różne kombinacje klawiszy, dopóki nie znajdziesz taki, który nie jest zamapowany.  
  
   > [!NOTE]
   >  Skróty klawiaturowe, które używają ALT może otworzyć menu i nie są bezpośrednio wykonania polecenia. W związku z tym **skrót aktualnie używany przez** pole może być pusty podczas wpisywania tekstu skrót, który zawiera ALT. Możesz sprawdzić, czy skrót nie otwiera menu przez zamknięcie **opcje** okno dialogowe, a następnie naciskając klawisze.  
  
   W poniższej procedurze przyjęto, że masz istniejących pakietów VSPackage przy użyciu polecenia menu. Jeśli potrzebujesz pomocy z tą operacją, Przyjrzyj się [Tworzenie rozszerzenia za pomocą polecenia Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
#### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Aby przypisać skrót klawiaturowy do polecenia  
  
1. Otwórz plik vsct dla pakietu.  
  
2. Utwórz pustą `<KeyBindings>` sekcji po `<Commands>` Jeśli nie jest już obecny.  
  
   > [!WARNING]
   >  Aby uzyskać więcej informacji na temat powiązania klawiszy zobacz [powiązanie klawiszy](../extensibility/keybinding-element.md).  
  
    W `<KeyBindings>` sekcji, Utwórz `<KeyBinding>` wpisu.  
  
    Ustaw `guid` i `id` atrybuty do tych poleceń, aby wywołać.  
  
    Ustaw `mod1` atrybutu **kontroli**, **Alt**, lub **Shift**.  
  
    W sekcji powiązania klawiszy powinno wyglądać mniej więcej tak:  
  
   ```xml  
   <KeyBindings>  
       <KeyBinding guid="<name of command set>" id="<name of command id>"  
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>  
   </KeyBindings>  
  
   ```  
  
   Jeśli skrót klawiaturowy wymaga więcej niż dwa klucze, należy ustawić `mod2` i `key2` atrybutów.  
  
   W większości sytuacji **Shift** nie należy używać bez modyfikatora drugiej już naciśnięcie klawisza powoduje, że większość klawisze alfanumeryczne wpisać wielką literę lub symbol.  
  
   Kody klucz wirtualnej umożliwiają uzyskanie dostępu do klawisze specjalne, które nie mają skojarzonych z nimi, na przykład klawiszy funkcyjnych znak i **BACKSPACE** klucza. Aby uzyskać więcej informacji, zobacz [kody klucz wirtualnej](http://go.microsoft.com/fwlink/?LinkID=105932).  
  
   Aby udostępnić polecenie w programie Visual Studio edytor, należy ustawić `editor` atrybutu `guidVSStd97`.  
  
   Aby polecenie dostępne tylko w niestandardowy edytor, należy ustawić `editor` atrybutu Nazwa niestandardowy edytor, który został wygenerowany przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] szablonu pakietu podczas tworzenia pakietu VSPackage, który zawiera niestandardowy Edytor. Aby znaleźć wartości nazwy, Szukaj w `<Symbols>` sekcji `<GuidSymbol>` węzła którego `name` atrybut kończy się na "`editorfactory`." Jest to nazwa edytora niestandardowego.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wiąże skrótu klawiaturowego CTRL + ALT + C polecenie o nazwie `cmdidMyCommand` w pakiecie o nazwie `MyPackage`.  
  
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
 W tym przykładzie wiąże skrótu klawiaturowego CTL + B polecenie o nazwie `cmdidBold` w projekcie o nazwie `TestEditor`. Polecenie jest dostępne tylko w edytorze niestandardowym i nie znajduje się w innych edytorów.  
  
```xml  
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)

