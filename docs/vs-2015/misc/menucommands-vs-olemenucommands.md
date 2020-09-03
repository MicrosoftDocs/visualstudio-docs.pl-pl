---
title: MenuCommands a OleMenuCommands | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- commands, creating in VSPackages
- command buttons, creating and placing
- menus, creating commands
ms.assetid: 553d5e07-3e19-4aba-b490-6c7dd05fd82e
caps.latest.revision: 46
manager: jillfra
ms.openlocfilehash: 42c471ca924bfded62db32a956a26c07240459eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "67624457"
---
# <a name="menucommands-vs-olemenucommands"></a>MenuCommands a OleMenuCommands
Polecenia menu można tworzyć poprzez wyprowadzanie z <xref:System.ComponentModel.Design.MenuCommand> lub z <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> obiektu oraz implementowanie odpowiednich programów obsługi zdarzeń. W większości przypadków, których można użyć <xref:System.ComponentModel.Design.MenuCommand> , jako szablonu projektu pakietu VSPackage, ale czasami może być konieczne użycie <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> .  
  
 Polecenia, które pakietu VSPackage udostępnia IDE, muszą być widoczne i włączone, zanim użytkownik będzie mógł z nich korzystać. Gdy polecenia są tworzone w pliku. vsct za pomocą szablonu projektu pakietu programu Visual Studio, są one widoczne i domyślnie włączone. Ustawienie niektórych flag poleceń, takich jak `DynamicItemStart` , może zmienić zachowanie domyślne. Widoczność, stan włączony i inne właściwości polecenia można także zmienić w kodzie w czasie wykonywania, uzyskując dostęp do <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> obiektu, który jest skojarzony z poleceniem.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby wykonać czynności opisane w tym przewodniku, należy zainstalować Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="template-locations-for-the-visual-studio-package-template"></a>Lokalizacje szablonów dla szablonu pakietu programu Visual Studio  
 Szablon pakietu programu Visual Studio można znaleźć w oknie dialogowym **Nowy projekt** w obszarze **Visual Basic/rozszerzalność**, **C#/rozszerzalność**lub **Inne typy projektów/rozszerzalność**.  
  
## <a name="creating-a-command"></a>Tworzenie polecenia  
 Wszystkie polecenia, grupy poleceń, menu, paski narzędzi i okna narzędzi są zdefiniowane w pliku vsct. Aby uzyskać więcej informacji, zobacz [tabela poleceń programu Visual Studio (. Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Jeśli tworzysz pakietu VSPackage za pomocą szablonu pakietu, wybierz **polecenie menu** , aby utworzyć plik. vsct i zdefiniować domyślne polecenie menu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozszerzenia za pomocą polecenia menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
#### <a name="to-add-a-command-to-the-ide"></a>Aby dodać polecenie do środowiska IDE  
  
1. Otwórz plik. vsct.  
  
2. W `Symbols` sekcji Znajdź element [GuidSymbol](../extensibility/guidsymbol-element.md) , który zawiera grupy i polecenia.  
  
3. Utwórz element [IDSymbol](../extensibility/idsymbol-element.md) dla każdego menu, grupy lub polecenia, które chcesz dodać, jak pokazano w poniższym przykładzie.  
  
   ```xml
   <GuidSymbol name="guidButtonGroupCmdSet" value="{f69209e9-975a-4543-821d-1f4a2c52d737}">
     <IDSymbol name="MyMenuGroup" value="0x1020" />
     <IDSymbol name="cmdidMyCommand" value="0x0100" />
   </GuidSymbol>
   ```
      
    `name`Atrybuty `GuidSymbol` `IDSymbol` elementów i zapewniają pary GUID: ID dla każdego nowego menu, grupy lub polecenia. `guid`Reprezentuje zestaw poleceń, który jest zdefiniowany dla pakietu VSPackage. Można zdefiniować wiele zestawów poleceń. Każdy identyfikator GUID: para musi być unikatowy.  
  
4. W sekcji [przyciski](../extensibility/buttons-element.md) Utwórz element [Button](../extensibility/button-element.md) , aby zdefiniować polecenie, jak pokazano w poniższym przykładzie.  
  
   ```xml
   <Button guid="guidButtonGroupCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
     <Parent guid="guidButtonGroupCmdSet" id="MyMenuGroup" />
     <Icon guid="guidImages" id="bmpPic1" />
     <Strings>
       <CommandName>cmdidMyCommand</CommandName>
       <ButtonText>My Command name</ButtonText>
     </Strings>
   </Button>
   ``` 
     
   1. Ustaw `guid` pola i tak, `id` aby odpowiadały identyfikatorowi GUID: Identyfikator nowego polecenia.  
  
   2. Ustaw `priority` atrybut.  
  
        Ten `priority` atrybut jest używany przez. vsct do określenia lokalizacji przycisku wśród innych obiektów w jego grupie nadrzędnej.  
  
        Polecenia o niższych wartościach priorytetów są wyświetlane powyżej lub z lewej strony poleceń, które mają wyższe wartości priorytetu. Wartości zduplikowanych priorytetów są dozwolone, ale względne położenie poleceń o równym priorytecie jest określane przez kolejność, w jakiej pakietów VSPackage są przetwarzane w czasie wykonywania, i nie można wstępnie określić kolejności.  
  
        Pominięcie `priority` atrybutu ustawia jego wartość na 0.  
  
   3. Ustaw `type` atrybut. W większości przypadków jego wartość to `"Button"` . Aby uzyskać opisy innych prawidłowych typów przycisków, zobacz [element Button](../extensibility/button-element.md).  
  
5. W definicji przycisku Utwórz element [Strings](../extensibility/strings-element.md) , który zawiera element [ButtonText](../extensibility/buttontext-element.md) , który zawiera nazwę menu, jak pojawia się w IDE, a element [CommandName](../extensibility/commandname-element.md) , aby zawierał nazwę polecenia, które jest używane do uzyskiwania dostępu do menu w oknie **poleceń** .  
  
    Jeśli ciąg tekstowy przycisku zawiera znak "&", użytkownik może otworzyć menu przez naciśnięcie klawisza ALT i znaku, który bezpośrednio następuje po "&".  
  
    Dodanie `Tooltip` elementu spowoduje, że zawarty tekst będzie wyświetlany, gdy użytkownik umieści wskaźnik myszy nad przyciskiem.  
  
6. Dodaj element [Icon](../extensibility/icon-element.md) , aby określić ikonę, jeśli ma być wyświetlana za pomocą polecenia. Ikony są wymagane dla przycisków na paskach narzędzi, ale nie dla elementów menu. `guid`I `id` `Icon` elementu muszą być zgodne z elementami [mapy bitowej](../extensibility/bitmap-element.md) zdefiniowanymi w `Bitmaps` sekcji.  
  
7. Dodaj flagi poleceń stosownie do potrzeb, aby zmienić wygląd i zachowanie przycisku. Aby to zrobić, Dodaj element [CommandFlag](../extensibility/command-flag-element.md) w definicji menu.  
  
8. Ustaw grupę nadrzędną polecenia. Grupa nadrzędna może być grupą, którą tworzysz, grupą z innego pakietu lub grupą ze środowiska IDE. Na przykład, aby dodać polecenie do paska narzędzi do edycji programu Visual Studio, obok przycisków **komentarz** i **Usuń komentarz** Ustaw element nadrzędny na guidStdEditor: IDG_VS_EDITTOOLBAR_COMMENT. Jeśli nadrzędny jest grupą zdefiniowaną przez użytkownika, musi być elementem podrzędnym menu, paska narzędzi lub okna narzędzi, które pojawia się w IDE.  
  
    Można to zrobić na jeden z dwóch sposobów, w zależności od projektu:  
  
   - W `Button` elemencie, Utwórz element [nadrzędny](../extensibility/parent-element.md) i ustaw jego `guid` `id` pola oraz identyfikator GUID i ID grupy, która będzie hostować polecenie, nazywane również *podstawową grupą nadrzędną*.  
  
        W poniższym przykładzie zdefiniowano polecenie, które zostanie wyświetlone w menu zdefiniowanym przez użytkownika.  
  
       ```xml
       <Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">
         <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />
         <Icon guid="guidImages" id="bmpPic1" />
         <Strings>
           <CommandName>cmdidTestCommand</CommandName>
           <ButtonText>Test Command</ButtonText>
             </Strings>
       </Button>
       ```
      
   - Możesz pominąć element, `Parent` Jeśli polecenie ma zostać umieszczone przy użyciu polecenia umieszczania. Utwórz element [CommandPlacements](../extensibility/commandplacements-element.md) przed `Symbols` sekcją i Dodaj element [CommandPlacement](../extensibility/commandplacement-element.md) , który ma `guid` i `id` polecenia, a `priority` i elementu nadrzędnego, jak pokazano w poniższym przykładzie.  
  
   ```xml
   <CommandPlacements>
     <CommandPlacement guid="guidButtonGroupCmdSet" id="cmdidMyCommand" priority="0x105">
       <Parent guid="guidButtonGroupCmdSet" id="MyMenuGroup" />
     </CommandPlacement>
   </CommandPlacements>
   ```
      
      Tworzenie wielu miejsc poleceń, które mają ten sam identyfikator GUID: ID i różne elementy nadrzędne powodują, że menu pojawia się w wielu lokalizacjach. Aby uzyskać więcej informacji, zobacz [CommandPlacements](../extensibility/commandplacements-element.md) element.  
  
    Aby uzyskać więcej informacji na temat grup poleceń i elementów nadrzędnych, zobacz [Tworzenie grup przycisków do wielokrotnego użytku](../extensibility/creating-reusable-groups-of-buttons.md).  
  
   W tym momencie polecenie będzie widoczne w środowisku IDE, ale nie będzie działać. Jeśli polecenie zostało utworzone przy użyciu szablonu pakietu, domyślnie będzie miało obsługę kliknięcia, która wyświetla komunikat.  
  
## <a name="handling-the-new-command"></a>Obsługa nowego polecenia  
 Większość poleceń w kodzie zarządzanym można obsłużyć przez strukturę zarządzanego pakietu (MPF), kojarząc polecenie z <xref:System.ComponentModel.Design.MenuCommand> obiektem lub <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> obiektem i implementując jego obsługę zdarzeń.  
  
 W przypadku kodu, który korzysta z <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu bezpośrednio dla obsługi poleceń, należy zaimplementować <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs i jego metody. Dwie najważniejsze metody to <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> i <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> .  
  
1. Pobierz <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> wystąpienie, jak pokazano w poniższym przykładzie.  
  
     [!code-csharp[ButtonGroup#21](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#21)]  
  
2. Utwórz <xref:System.ComponentModel.Design.CommandID> obiekt, który ma jako parametry identyfikator GUID i identyfikator polecenia do obsłużenia, jak pokazano w poniższym przykładzie.  
  
     [!code-csharp[ButtonGroup#22](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#22)]  
  
     Szablon pakietu programu Visual Studio zawiera dwie kolekcje `GuidList` i `PkgCmdIDList` , w celu przechowywania identyfikatorów GUID i identyfikatory poleceń. Są one wypełniane automatycznie dla poleceń, które są dodawane przez szablon, ale dla poleceń dodawanych ręcznie, należy również dodać wpis identyfikatora do `PkgCmdIdList` klasy.  
  
     Alternatywnie można wypełnić <xref:System.ComponentModel.Design.CommandID> Obiekt przy użyciu nieprzetworzonej wartości ciągu identyfikatora GUID i wartości całkowitej identyfikatora.  
  
3. Utwórz wystąpienie <xref:System.ComponentModel.Design.MenuCommand> obiektu lub, <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> który określa metodę, która obsługuje polecenie razem z <xref:System.ComponentModel.Design.CommandID> , jak pokazano w poniższym przykładzie.  
  
     [!code-csharp[ButtonGroup#23](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#23)]  
  
     <xref:System.ComponentModel.Design.MenuCommand>Jest to odpowiednie dla poleceń statycznych. Dynamiczny element menu zawiera wymagania obsługi zdarzeń QueryStatus. <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>Dodaje <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> zdarzenie, które występuje po otwarciu menu hosta polecenia i innych właściwości, takich jak <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A> .  
  
     Polecenia utworzone przez szablon pakietu są domyślnie przesyłane do <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> obiektu w `Initialize()` metodzie klasy pakietu.  
  
4. <xref:System.ComponentModel.Design.MenuCommand>Jest to odpowiednie dla poleceń statycznych. Dynamiczny element menu zawiera wymagania obsługi zdarzeń QueryStatus. <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>Dodaje <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> zdarzenie, które występuje po otwarciu menu hosta polecenia i innych właściwości, takich jak <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A> .  
  
     Polecenia utworzone przez szablon pakietu są domyślnie przesyłane do <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> obiektu w `Initialize()` metodzie klasy pakietu. Kreator programu Visual Studio implementuje `Initialize` metodę za pomocą polecenia `MenuCommand` . W przypadku wyświetlania dynamicznego elementu menu należy zmienić to `OleMenuCommand` , tak jak pokazano w następnym kroku. Ponadto aby zmienić tekst elementu menu, należy dodać flagę polecenia textchangs do przycisku polecenia menu w pliku vsct, jak pokazano w poniższym przykładzie.  
  
    ```xml
    <Button guid="guidMenuTextCmdSet" id="cmdidMyCommand" priority="0x0100" type="Button">
      <Parent guid="guidMenuTextCmdSet" id="MyMenuGroup" />
      <Icon guid="guidImages" id="bmpPic1" />
      <CommandFlag>TextChanges</CommandFlag>
      <Strings>
        <CommandName>cmdidMyCommand</CommandName>
        <ButtonText>My Command name</ButtonText>
      </Strings>
    </Button>
    ```
      
5. Przekaż nowe polecenie menu do <xref:System.ComponentModel.Design.IMenuCommandService.AddCommand%2A> metody w <xref:System.ComponentModel.Design.IMenuCommandService> interfejsie. Jest to realizowane domyślnie dla poleceń tworzonych przez szablon pakietu, jak pokazano w poniższym przykładzie.  
  
     [!code-csharp[ButtonGroup#24](../snippets/csharp/VS_Snippets_VSSDK/buttongroup/cs/buttongrouppackage.cs#24)]  
  
6. Zaimplementuj metodę, która obsługuje polecenie.  
  
#### <a name="to-implement-querystatus"></a>Aby zaimplementować QueryStatus  
  
1. Zdarzenie QueryStatus występuje przed wyświetleniem polecenia. Umożliwia to ustawienie właściwości tego polecenia w programie obsługi zdarzeń przed jego przekazaniem do użytkownika. <xref:Microsoft.VisualStudio.Shell.OleMenuCommand>Do tej metody można uzyskać dostęp tylko do poleceń, które są dodawane jako obiekty.  
  
    Dodaj `EventHandler` obiekt do <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> zdarzenia w <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> obiekcie, który został utworzony, aby obsłużyć polecenie, jak pokazano w poniższym przykładzie ( `menuItem` to jest <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> wystąpienie).  
  
    [!code-csharp[MenuText#14](../snippets/csharp/VS_Snippets_VSSDK/menutext/cs/menutextpackage.cs#14)]
    [!code-vb[MenuText#14](../snippets/visualbasic/VS_Snippets_VSSDK/menutext/vb/menutextpackage.vb#14)]  
  
    `EventHandler`Obiekt otrzymuje nazwę metody, która jest wywoływana, gdy zostanie wysłane zapytanie o stan polecenia menu.  
  
2. Zaimplementuj metodę procedury obsługi stanu zapytania dla polecenia. `object` `sender` Parametr może być rzutowany do <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> obiektu, który jest używany do ustawiania różnych atrybutów polecenia menu, łącznie z tekstem. W poniższej tabeli przedstawiono właściwości <xref:System.ComponentModel.Design.MenuCommand> klasy (której klasa MPF <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> dziedziczy z), które odpowiadają <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> flagom.  
  
   |Właściwość MenuCommand|Flaga OLECMDF|  
   |--------------------------|------------------|  
   |<xref:System.ComponentModel.Design.MenuCommand.Checked%2A> = `true`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
   |<xref:System.ComponentModel.Design.MenuCommand.Visible%2A> = `false`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
   |<xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> = `true`|<xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF>|  
  
    Aby zmienić tekst polecenia menu, użyj <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.Text%2A> właściwości <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> obiektu, jak pokazano w poniższym przykładzie.  
  
    [!code-csharp[MenuText#11](../snippets/csharp/VS_Snippets_VSSDK/menutext/cs/menutextpackage.cs#11)]
    [!code-vb[MenuText#11](../snippets/visualbasic/VS_Snippets_VSSDK/menutext/vb/menutextpackage.vb#11)]  
  
   MPF automatycznie obsługuje przypadek dla nieobsługiwanych lub nieznanych grup. Jeśli polecenie nie zostało dodane do programu <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> przy użyciu <xref:System.ComponentModel.Design.IMenuCommandService.AddCommand%2A> metody, polecenie nie jest obsługiwane.  
  
### <a name="handling-commands-by-using-the-iolecommandtarget-interface"></a>Obsługa poleceń przy użyciu interfejsu IOleCommandTarget  
 W przypadku kodu, który używa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu bezpośrednio, pakietu VSPackage musi implementować obie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody i <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu. Jeśli pakietu VSPackage implementuje hierarchię projektu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> zamiast tego należy zaimplementować metody i interfejsu.  
  
 Obie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody i <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> są przeznaczone do odbierania jednego zestawu poleceń `GUID` i tablicy identyfikatorów poleceń jako dane wejściowe. Zalecamy, aby pakietów VSPackage w pełni obsługiwać te koncepcje wielu identyfikatorów w jednym wywołaniu. Jednak tak długo, jak pakietu VSPackage nie jest wywoływana z innych pakietów VSPackage, można założyć, że tablica poleceń zawiera tylko jeden identyfikator polecenia, ponieważ <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody i są wykonywane w dobrze zdefiniowanej kolejności. Aby uzyskać więcej informacji na temat routingu, zobacz [routing poleceń w pakietów VSPackage](../extensibility/internals/command-routing-in-vspackages.md).  
  
 W przypadku kodu, który korzysta z <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu bezpośrednio dla obsługi poleceń, należy zaimplementować <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodę w pakietu VSPackage w następujący sposób, aby obsługiwać polecenia.  
  
##### <a name="to-implement-the-querystatus-method"></a>Aby zaimplementować metodę QueryStatus  
  
1. Zwróć <xref:Microsoft.VisualStudio.VSConstants.S_OK> dla prawidłowych poleceń.  
  
2. Ustaw `cmdf` element `prgCmds` parametru.  
  
    Wartość `cmdf` elementu jest logicznym związkiem wartości z <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> wyliczenia, połączone za pomocą operatora logicznego OR ( `|` ).  
  
    Użyj odpowiedniego wyliczenia na podstawie stanu polecenia:  
  
   - Jeśli polecenie jest obsługiwane:  
  
      `prgCmds[0].cmdf = OLECMDF_SUPPORTED;`  
  
   - Jeśli polecenie powinno być niewidoczne w tej chwili:  
  
      `prgCmds[0].cmdf |= OLECMDF_INVISIBLE;`  
  
   - Jeśli polecenie jest włączone i pojawia się, gdy kliknięto:  
  
      `prgCmds[0].cmdf |= OLECMDF_LATCHED;`  
  
      W przypadku poleceń przetwarzania, które są hostowane w menu typu `MenuControllerLatched` , pierwsze polecenie oznaczone przez `OLECMDF_LATCHED` flagę jest domyślnym poleceniem wyświetlanym w menu podczas uruchamiania. Aby uzyskać więcej informacji na temat `MenuController` typów menu, zobacz [element menu](../extensibility/menu-element.md).  
  
   - Jeśli polecenie jest obecnie włączone:  
  
      `prgCmds[0].cmdf |= OLECMDF_ENABLED;`  
  
   - Jeśli polecenie jest częścią menu skrótów i jest domyślnie ukryte:  
  
      `prgCmds[0] cmdf |= OLECMDF_DEFHIDEONCTXMENU`  
  
   - Jeśli polecenie używa `TEXTCHANGES` flagi, należy ustawić `rgwz` element `pCmdText` parametru na nowy tekst polecenia i ustawić `cwActual` element `pCmdText` parametru na rozmiar ciągu polecenia programu.  
  
     W przypadku warunków błędów <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Metoda musi obsłużyć następujące przypadki błędów:  
  
   - Jeśli identyfikator GUID jest nieznany lub nie jest obsługiwany, Return `OLECMDERR_E_UNKNOWNGROUP` .  
  
   - Jeśli identyfikator GUID jest znany, ale identyfikator polecenia jest nieznany lub nie jest obsługiwany, Return `OLECMDERR_E_NOTSUPPORTED` .  
  
   Implementacja pakietu VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metody musi również zwracać określone kody błędów w zależności od tego, czy polecenie jest obsługiwane i czy polecenie zostało obsłużone pomyślnie.  
  
##### <a name="to-implement-the-exec-method"></a>Aby zaimplementować metodę exec  
  
- Jeśli polecenie `GUID` jest nieznane, zwraca `OLECMDERR_E_UNKNOWNGROUP` .  
  
- Jeśli `GUID` jest znany, ale identyfikator polecenia jest nieznany, Return `OLECMDERR_E_NOTSUPPORTED` .  
  
- Jeśli `GUID` identyfikatory poleceń i pasują do pary GUID: ID, która jest używana przez polecenie w pliku. vsct, wykonaj kod skojarzony z poleceniem i Return <xref:Microsoft.VisualStudio.VSConstants.S_OK> .  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja schematu XML VSCT](../extensibility/vsct-xml-schema-reference.md)   
 [Rozszerzanie menu i poleceń](../extensibility/extending-menus-and-commands.md)
