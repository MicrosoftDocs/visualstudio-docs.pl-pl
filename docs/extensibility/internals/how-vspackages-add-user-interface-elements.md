---
title: Jak dodać elementy interfejsu użytkownika w pakietach VSPackage | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 40e3d5266b69419e719c5de7a003e642e8016614
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53962691"
---
# <a name="how-vspackages-add-user-interface-elements"></a>Jak dodać elementy interfejsu użytkownika w pakietach VSPackage
Dodać elementy interfejsu użytkownika, na przykład menu, paski narzędzi i narzędzi systemu windows, do programu Visual Studio poprzez pakietu VSPackage *vsct* pliku.  
  
 Możesz znaleźć wytyczne dotyczące projektowania dla elementów interfejsu użytkownika na [wskazówki dotyczące interfejsu użytkownika programu Visual Studio](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## <a name="the-visual-studio-command-table-architecture"></a>Architektura tabeli polecenia programu Visual Studio  
 Jak wspomniano, architektura tabeli polecenia obsługuje powyższych zasad architektonicznych. Założenia abstrakcji, struktur danych i narzędzia architektury tabeli polecenia są następujące:  
  
-   Istnieją trzy podstawowe typy elementów: menu, poleceń i grup. Menu mogą być udostępniane w interfejsie użytkownika jako menu, podmenu, paski narzędzi i okien narzędzi. Polecenia są procedury, które użytkownik może uruchomić w środowisku IDE, i które można uwidocznić jako elementy menu, przyciski, pola listy i inne kontrolki. Grupy są kontenerami dla zarówno menu i poleceń.  
  
-   Każdy element jest określona, zgodnie z definicją, opisujące element, jego priorytet względem innych elementów, a flagi, które modyfikują zachowanie.  
  
-   Każdy element ma umieszczenia, opisująca nadrzędnego elementu. Element może mieć wielu elementów nadrzędnych, dzięki czemu może występować w wielu lokalizacjach w interfejsie użytkownika.  
  
     Każde polecenie musi mieć grupę jako klasy nadrzędnej, nawet jeśli jest elementem podrzędnym tylko w tej grupie. Każdy standardowe menu musi mieć grupę nadrzędną. Paski narzędzi i okien narzędzi pełnić rolę własne elementy nadrzędne. Grupa może mieć jako jego element nadrzędny głównego pasek menu programu Visual Studio lub dowolnego menu, pasek narzędzi lub okna narzędzi.  
  
### <a name="how-items-are-defined"></a>Sposób definiowania elementów  
 A *vsct* plik jest sformatowany w języku XML. On definiuje elementy interfejsu użytkownika dla pakietu i określa, gdzie te elementy są wyświetlane w środowisku IDE. Identyfikator GUID i identyfikator w najpierw przypisano co menu, grupy lub polecenia w pakiecie `Symbols` sekcji. W pozostałej części *vsct* pliku, każdego menu, poleceń oraz grupy jest identyfikowana przez kombinację jego identyfikator GUID i identyfikator. W poniższym przykładzie przedstawiono typowe `Symbols` sekcji wygenerowanego przez szablon pakietu Visual Studio podczas **polecenia Menu** jest zaznaczona w szablonie.  
  
```xml  
<Symbols>  
  <!-- This is the package guid. -->  
  <GuidSymbol name="guidMenuTextPkg" value="{b1253bc6-d266-402b-89e7-5e3d3b22c746}" />  
  
  <!-- This is the guid used to group the menu commands together -->  
  <GuidSymbol name="guidMenuTextCmdSet" value="{a633d4e4-6c65-4436-a138-1abeba7c9a69}">  
  
    <IDSymbol name="MyMenuGroup" value="0x1020" />  
    <IDSymbol name="cmdidMyCommand" value="0x0100" />  
  </GuidSymbol>  
  
  <GuidSymbol name="guidImages" value="{53323d9a-972d-4671-bb5b-9e418480922f}" >  
    <IDSymbol name="bmpPic1" value="1" />  
    <IDSymbol name="bmpPic2" value="2" />  
    <IDSymbol name="bmpPicSearch" value="3" />  
    <IDSymbol name="bmpPicX" value="4" />  
    <IDSymbol name="bmpPicArrows" value="5" />  
  </GuidSymbol>  
</Symbols>  
```  
  
 Element najwyższego poziomu `Symbols` sekcja [GuidSymbol, element](../../extensibility/guidsymbol-element.md). `GuidSymbol` elementy nazwy są mapowane na identyfikatory GUID, które są używane przez IDE, aby zidentyfikować pakiety i ich części składowe.  
  
> [!NOTE]
>  Identyfikatory GUID są automatycznie generowane przez szablon pakietu Visual Studio. Unikatowy identyfikator GUID można również utworzyć, klikając **Utwórz GUID** na **narzędzia** menu.  
  
 Pierwszy `GuidSymbol` elementu `guid<PackageName>Pkg`, to identyfikator GUID pakietu. Jest to identyfikator GUID, który jest używany przez program Visual Studio można załadować pakietu. Zazwyczaj nie ma elementów podrzędnych.  
  
 Zgodnie z Konwencją, menu i poleceń, są zgrupowane w drugiej `GuidSymbol` elementu `guid<PackageName>CmdSet`, i mapy bitowe mają rozmiar w obszarze innego `GuidSymbol` elementu `guidImages`. Nie należy przestrzegać tej Konwencji, ale każdy menu, grupy, polecenia i mapy bitowej musi być obiektem podrzędnym obiektu `GuidSymbol` elementu.  
  
 W drugim `GuidSymbol` element, który reprezentuje zestaw poleceń pakiet, kilka `IDSymbol` elementów. Każdy [IDSymbol, element](../../extensibility/idsymbol-element.md) mapuje nazwę na wartość liczbową i może reprezentować menu, grupy lub polecenia, który jest częścią zestawu poleceń. `IDSymbol` Elementów w trzecim `GuidSymbol` mapy bitowe reprezentują element, który może być używany jako ikony poleceń. Ponieważ par identyfikator/GUID musi być unikatowa w aplikacji, żadne dwa elementy podrzędne tego samego `GuidSymbol` element może mieć taką samą wartość.  
  
### <a name="menus-groups-and-commands"></a>Menu, grupy i polecenia  
 Menu, grupy lub polecenie ma identyfikator GUID i identyfikator, może być dodany do środowiska IDE programu. Każdy element interfejsu użytkownika musi mieć następujące elementy:  
  
-   A `guid` atrybut, który jest zgodna z nazwą `GuidSymbol` element, który jest zdefiniowany element interfejsu użytkownika, w obszarze.  
  
-   `id` Atrybut, który jest zgodna z nazwą skojarzonego `IDSymbol` elementu.  
  
     Razem `guid` i `id` atrybuty tworzą *podpisu* elementu interfejsu użytkownika.  
  
-   A `priority` atrybut, który określa położenie elementu interfejsu użytkownika w menu nadrzędnej lub grupy.  
  
-   A [elementu nadrzędnego](../../extensibility/parent-element.md) zawierający `guid` i `id` atrybuty określające podpisu menu nadrzędnej lub grupy.  
  
#### <a name="menus"></a>Menu  
 Każde menu jest zdefiniowany jako [Menu element](../../extensibility/menu-element.md) w `Menus` sekcji. Menu musi mieć `guid`, `id`, i `priority` atrybutów, a `Parent` elementu, a także następujących dodatkowych atrybutów i elementy podrzędne:  
  
- A `type` atrybut, który określa, czy menu mają pojawiać się w środowisku IDE jako rodzaju menu lub paska narzędzi.  
  
- A [Strings, element](../../extensibility/strings-element.md) zawierający [ButtonText, element](../../extensibility/buttontext-element.md), która określa tytuł menu w IDE i [CommandName, element](../../extensibility/commandname-element.md), który określa nazwę, która jest używane w **polecenia** okna, aby uzyskać dostęp do menu.  
  
- Flagi opcjonalne. A [elementu CommandFlag](../../extensibility/command-flag-element.md) może występować w definicji menu, aby zmienić jego wygląd lub zachowanie w środowisku IDE.  
  
  Każdy `Menu` elementu musi mieć grupę jako klasy nadrzędnej, chyba że jest to element dokowalne, takie jak pasek narzędzi. Dokowalne menu jest jego własny element nadrzędny. Aby uzyskać więcej informacji na temat menu i wartości dla `type` atrybutów, zobacz [Menu element](../../extensibility/menu-element.md) dokumentacji.  
  
  W poniższym przykładzie pokazano menu, która pojawia się na pasku menu programu Visual Studio **narzędzia** menu.  
  
```xml  
<Menu guid="guidTopLevelMenuCmdSet"  
id="TopLevelMenu" priority="0x700" type="Menu">  
  <Parent guid="guidSHLMainMenu"  
          id="IDG_VS_MM_TOOLSADDINS" />  
  <Strings>  
    <ButtonText>TestMenu</ButtonText>  
    <CommandName>TestMenu</CommandName>  
  </Strings>  
</Menu>  
```  
  
#### <a name="groups"></a>Grupy  
 Grupa jest element, który jest zdefiniowany w `Groups` części *vsct* pliku. Grupy są po prostu kontenerami. Nie są wyświetlane w środowisku IDE, z wyjątkiem jako linię podziału, w menu. W związku z tym [element grupy](../../extensibility/group-element.md) jest definiowana tylko przez jego podpisu, priorytetu i nadrzędnej.  
  
 Grupa może zawierać menu, inną grupę lub samego jako element nadrzędny. Element nadrzędny jest jednak zazwyczaj menu lub paska narzędzi. Menu we wcześniejszym przykładzie jest elementem podrzędnym `IDG_VS_MM_TOOLSADDINS` grup oraz że jest elementem podrzędnym na pasku menu programu Visual Studio. Grupy w poniższym przykładzie jest elementem podrzędnym elementu menu we wcześniejszym przykładzie.  
  
```xml  
 <Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"  
priority="0x0600">  
   <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>  
 </Group>  
```  
  
 Ponieważ jest on częścią menu, ta grupa będzie zwykle zawierają polecenia. Jednak może również zawierać inne menu. Jest to sposób definiowania podmenu, jak pokazano w poniższym przykładzie.  
  
```xml  
<Menu guid="guidTopLevelMenuCmdSet" id="SubMenu"  
priority="0x0100" type="Menu">  
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"/>  
  <Strings>  
    <ButtonText>Sub Menu</ButtonText>  
    <CommandName>Sub Menu</CommandName>  
  </Strings>  
</Menu>  
```  
  
#### <a name="commands"></a>Polecenia  
 Polecenia, który został dostarczony do IDE jest zdefiniowany jako [Button element](../../extensibility/button-element.md) lub [Combo, element](../../extensibility/combo-element.md). Być wyświetlane w menu lub paska narzędzi, polecenia musi mieć grupę jako klasy nadrzędnej.  
  
##### <a name="buttons"></a>Przyciski  
 Przyciski są zdefiniowane w `Buttons` sekcji. Dowolny element menu, przycisk lub inny element, który użytkownik klika, aby wykonać jedno polecenie jest traktowane jako przycisk. Niektóre typy przycisku, mogą również zawierać funkcje listy. Przyciski mają takie same wymaganych i opcjonalnych atrybutów, które mają menu, a także mogą mieć [Icon, element](../../extensibility/icon-element.md) , który określa identyfikator GUID i identyfikator mapy bitowej, która reprezentuje przycisk w środowisku IDE. Aby uzyskać więcej informacji na temat przycisków i ich atrybutów, zobacz [Buttons, element](../../extensibility/buttons-element.md) dokumentacji.  
  
 W poniższym przykładzie przycisk jest elementem podrzędnym grupy we wcześniejszym przykładzie i pojawią się w środowisku IDE jako element menu w menu nadrzędnej tej grupy.  
  
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
  
##### <a name="combos"></a>Combos  
 Combos są zdefiniowane w `Combos` sekcji. Każdy `Combo` element reprezentuje pole listy rozwijanej w środowisku IDE. Pole listy mogą być lub zapis danych przez użytkowników, w zależności od wartości `type` atrybut kombi. Combos mają te same elementy i zachowanie, że przyciski ma, a także mogą mieć następujących dodatkowych atrybutów:  
  
- A `defaultWidth` atrybut, który określa szerokość w pikselach.  
  
- `idCommandList` Atrybut, który określa listę, która zawiera elementy, które są wyświetlane w polu listy. Lista poleceń musi być zadeklarowany w tym samym `GuidSymbol` węzeł, który zawiera kombi.  
  
  W poniższym przykładzie zdefiniowano combo, element.  
  
```xml  
<Combos>  
  <Combo guid="guidFirstToolWinCmdSet"  
         id="cmdidWindowsMediaFilename"  
         priority="0x0100" type="DynamicCombo"  
         idCommandList="cmdidWindowsMediaFilenameGetList"  
         defaultWidth="130">  
    <Parent guid="guidFirstToolWinCmdSet"  
            id="ToolbarGroupID" />  
    <CommandFlag>IconAndText</CommandFlag>  
    <CommandFlag>CommandWellOnly</CommandFlag>  
    <CommandFlag>StretchHorizontally</CommandFlag>  
    <Strings>  
      <CommandName>Filename</CommandName>  
      <ButtonText>Enter a Filename</ButtonText>  
    </Strings>  
  </Combo>  
</Combos>  
```  
  
##### <a name="bitmaps"></a>Mapy bitowe  
 Polecenia, które będą wyświetlane wraz z ikony musi zawierać `Icon` element, który odwołuje się do mapy bitowej przy użyciu jego identyfikator GUID i identyfikator. Każda mapa bitowa jest zdefiniowany jako [element bitmapy](../../extensibility/bitmap-element.md) w `Bitmaps` sekcji. Tylko wymaganych atrybutów dla `Bitmap` definicji są `guid` i `href`, który wskazuje plik źródłowy. Jeśli plik źródłowy znajduje się pasek zasobów **usedList** atrybucie uwzględniana jest również wymagane, aby wyświetlić listę dostępnych obrazów na pasku. Aby uzyskać więcej informacji, zobacz [element bitmapy](../../extensibility/bitmap-element.md) dokumentacji.  
  
### <a name="parenting"></a>Elementy nadrzędne  
 Następujące reguły określają, jak wywołać inny element jako jego element nadrzędny elementu.  
  
|Element|Zdefiniowane w tej sekcji tabeli poleceń|Mogą znajdować się (jako element nadrzędny lub umieszczania w `CommandPlacements` sekcji i / lub)|Może zawierać (określony jako element nadrzędny)|  
|-------------| - | - | - |  
|Grupa|[Element grupy](../../extensibility/groups-element.md), IDE, innych pakietów VSPackage|Menu, grupy, sam element|Menu, grupy i polecenia|  
|Menu|[Element menu](../../extensibility/menus-element.md), IDE, innych pakietów VSPackage|1, aby *n* grup|0, aby *n* grup|  
|Pasek narzędzi|[Element menu](../../extensibility/menus-element.md), IDE, innych pakietów VSPackage|Sam element|0, aby *n* grup|  
|Element menu|[Buttons, element](../../extensibility/buttons-element.md), IDE, innych pakietów VSPackage|1, aby *n* grup sam element|-0, aby *n* grup|  
|Przycisk|[Buttons, element](../../extensibility/buttons-element.md), IDE, innych pakietów VSPackage|1, aby *n* grup sam element||  
|Pole kombi|[Combos, element](../../extensibility/combos-element.md), IDE, innych pakietów VSPackage|1, aby *n* grup sam element||  
  
### <a name="menu-command-and-group-placement"></a>Menu, poleceń oraz grupy umieszczania  
 Menu, grupy lub polecenia może znajdować się w więcej niż jedną lokalizację w środowisku IDE. Dla elementu pojawią się w wielu lokalizacjach, należy dodać do `CommandPlacements` sekcji jako [CommandPlacement, element](../../extensibility/commandplacement-element.md). Wszelkie menu, grupy lub polecenia mogą być dodawane jako położenie polecenia. Jednak pasków narzędzi nie może znajdować się w ten sposób, ponieważ nie pojawiają się w wielu lokalizacjach kontekstowej.  
  
 Polecenie angażowania mają `guid`, `id`, i `priority` atrybutów. Identyfikator GUID i identyfikator musi zgadzać się z elementu, który jest umieszczony. `priority` Atrybut kontroluje umieszczanie elementu w odniesieniu do innych elementów. Gdy IDE scala dwa lub więcej elementów, które mają ten sam priorytet, ich rozmieszczenia są niezdefiniowane, ponieważ IDE nie gwarantuje, że zasoby pakietu są odczytywane w tej samej kolejności, ilekroć dany pakiet jest wbudowana.  
  
 Jeśli menu lub grupa pojawia się w wielu lokalizacjach, wszystkie elementy podrzędne tego menu lub tej grupy pojawi się w każdym wystąpieniu.  
  
## <a name="command-visibility-and-context"></a>Polecenie widoczności i kontekstu  
 Po zainstalowaniu wielu pakietów VSPackage nadmiaru menu, elementy menu i paski narzędzi mogą zbliżyć do siebie te środowiska IDE. Aby uniknąć tego problemu, można sterować widocznością poszczególnych elementów interfejsu użytkownika przy użyciu *ograniczeń widoczność* i flag poleceń.  
  
### <a name="visibility-constraints"></a>Ograniczeń widoczność  
 Ograniczenie widoczność jest ustawiony jako [VisibilityItem, element](../../extensibility/visibilityitem-element.md) w `VisibilityConstraints` sekcji. Ograniczenie widoczność definiuje określonych kontekstach interfejsu użytkownika, w których element docelowy jest widoczna. Menu lub polecenia, który znajduje się w tej sekcji jest widoczny tylko wtedy, gdy jeden z określonych kontekstach jest aktywny. Jeśli menu lub polecenia nie jest wywoływany w tej sekcji, zawsze jest domyślnie widoczny. Ta sekcja nie ma zastosowania do grup.  
  
 `VisibilityItem` elementy muszą mieć trzy atrybuty w następujący sposób: `guid` i `id` elementu interfejsu użytkownika docelowego i `context`. `context` Atrybut określa, kiedy element docelowy będzie widoczny i Trwa dowolnego prawidłowego kontekstu interfejsu użytkownika, jako jego wartość. Stałe kontekstu interfejsu użytkownika dla programu Visual Studio są elementami członkowskimi <xref:Microsoft.VisualStudio.VSConstants> klasy. Każdy `VisibilityItem` elementu może przyjąć wartość tylko jeden kontekst. Aby zastosować drugi kontekstu, Utwórz drugi `VisibilityItem` element, który wskazuje na ten sam element, jak pokazano w poniższym przykładzie.  
  
```xml  
<VisibilityConstraints>  
  <VisibilityItem guid="guidSolutionToolbarCmdSet"  
        id="cmdidTestCmd"  
        context="UICONTEXT_SolutionHasSingleProject" />  
  <VisibilityItem guid="guidSolutionToolbarCmdSet"  
        id="cmdidTestCmd"  
        context="UICONTEXT_SolutionHasMultipleProjects" />  
</VisibilityConstraints>  
```  
  
### <a name="command-flags"></a>Flag poleceń  
 Następujące flagi polecenia mogą wpływać na widoczność menu i poleceń, które odnoszą się do.  
  
 `AlwaysCreate`  
 Menu jest tworzony, nawet jeśli go nie ma grup lub przycisków.  
  
 Obowiązuje dla: `Menu`  
  
 `CommandWellOnly`  
 Zastosowanie tej flagi Jeśli polecenie nie jest wyświetlany w menu najwyższego poziomu i chcesz udostępnić dostosowania dodatkowe powłoki, na przykład powiązanie z kluczem. Po zainstalowaniu pakietu VSPackage, użytkownik może dostosować te polecenia, otwierając **opcje** okno dialogowe, a następnie edytując położenie polecenia w obszarze **środowiska klawiatury** kategorii. Nie ma wpływu na umieszczanie w menu skrótów, paski narzędzi, kontrolery menu i podmenu.  
  
 Prawidłowe dla: `Button`, `Combo`  
  
 `DefaultDisabled`  
 Domyślnie polecenie jest wyłączona, jeśli pakietu VSPackage, który implementuje polecenie nie jest załadowany lub nie została wywołana metoda QueryStatus.  
  
 Prawidłowe dla: `Button`, `Combo`  
  
 `DefaultInvisible`  
 Domyślnie polecenie jest niewidoczne, jeśli pakietu VSPackage, który implementuje polecenie nie jest załadowany lub nie została wywołana metoda QueryStatus.  
  
 Powinny być połączone z `DynamicVisibility` flagi.  
  
 Prawidłowe dla: `Button`, `Combo`, `Menu`  
  
 `DynamicVisibility`  
 Widoczność polecenia można zmienić za pomocą `QueryStatus` metody lub identyfikator GUID, który znajduje się w kontekście `VisibilityConstraints` sekcji.  
  
 Ma zastosowanie do poleceń, które są wyświetlane w menu, a nie na paskach narzędzi. Elementy paska narzędzi najwyższego poziomu może być wyłączona, ale nie ukryty, gdy `OLECMDF_INVISIBLE` flaga jest zwracana z `QueryStatus` metody.  
  
 W menu ta flaga wskazuje także, czy go powinny być automatycznie ukrywane podczas jej elementy członkowskie są ukryte. Ta flaga jest zazwyczaj przypisany do podmenu, ponieważ menu najwyższego poziomu już to zachowanie.  
  
 Powinny być połączone z `DefaultInvisible` flagi.  
  
 Prawidłowe dla: `Button`, `Combo`, `Menu`  
  
 `NoShowOnMenuController`  
 Polecenie, które ma ta flaga jest ustawiony na kontroler menu, polecenie nie są wyświetlane na liście rozwijanej.  
  
 Obowiązuje dla: `Button`  
  
 Aby uzyskać więcej informacji na temat flag poleceń, zobacz [elementu CommandFlag](../../extensibility/command-flag-element.md) dokumentacji.  
  
#### <a name="general-requirements"></a>Wymagania ogólne  
 Polecenie musi upłynąć poniższą sekwencję testy mogą być wyświetlane i włączone:  
  
-   Polecenie znajduje się poprawnie.  
  
-   `DefaultInvisible` Nie ustawiono flagi.  
  
-   Nadrzędny menu lub pasek narzędzi jest widoczna.  
  
-   Polecenie nie jest niewidoczne ze względu na zapis kontekstu, w [VisibilityConstraints, element](../../extensibility/visibilityconstraints-element.md) sekcji.  
  
-   Kod pakietu VSPackage, który implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu wyświetla i umożliwia swojej dyspozycji. Brak kodu interfejsu został on przechwycony i podjęło odpowiednie działania.  
  
-   Po kliknięciu polecenia staje się zgodnie z procedurą opisaną w [algorytm routingu](../../extensibility/internals/command-routing-algorithm.md).  
  
## <a name="call-pre-defined-commands"></a>Wywołanie polecenia wstępnie zdefiniowane  
 [UsedCommands, element](../../extensibility/usedcommands-element.md) umożliwia pakietów VSPackage polecenia dostępu, które są dostarczane przez inne pakietów VSPackage lub IDE. Aby to zrobić, należy utworzyć [UsedCommand, element](../../extensibility/usedcommand-element.md) ma identyfikator GUID i identyfikator polecenia do użycia. Gwarantuje to, że polecenia zostaną załadowane przez program Visual Studio, nawet jeśli nie jest częścią bieżącej konfiguracji programu Visual Studio. Aby uzyskać więcej informacji, zobacz [UsedCommand, element](../../extensibility/usedcommand-element.md).  
  
## <a name="interface-element-appearance"></a>Wygląd elementów interfejsu  
 Zagadnienia związane z wybraniu i pozycjonowanie elementów polecenia są następujące:  
  
- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] oferuje wiele elementów interfejsu użytkownika, które pojawiają się inaczej w zależności od położenia.  
  
- Element interfejsu użytkownika, która jest zdefiniowana za pomocą `DefaultInvisible` flagi nie będą wyświetlane w środowisku IDE, chyba że jest to albo wyświetlany przez jego implementacja pakietu VSPackage <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> metody lub skojarzone z określonym kontekstem interfejsu użytkownika w `VisibilityConstraints` sekcji.  
  
- Pomyślnie pozycjonowane polecenia mogą być niewidoczne. Ponieważ IDE automatycznie ukrywa lub wyświetla niektórych poleceń, w zależności od interfejsów, które pakietu VSPackage ma (lub nie) implementacja. Na przykład wdrożenie pakietu VSPackage niektórych twórz interfejsy elementy menu dotyczące kompilacji powoduje, że mają być automatycznie wyświetlane.  
  
- Stosowanie `CommandWellOnly` Flaga w definicji elementu interfejsu użytkownika oznacza, że polecenia mogą być dodawane tylko przez dostosowanie.  
  
- Polecenia mogą być dostępne tylko w określonych kontekstach interfejsu użytkownika, na przykład, tylko wtedy, gdy okno dialogowe jest wyświetlane, gdy IDE jest w widoku Projekt.  
  
- Aby spowodować, że niektóre elementy interfejsu użytkownika będzie wyświetlana w środowisku IDE, możesz zaimplementować jeden lub więcej interfejsów lub napisanie kodu.  
  
## <a name="see-also"></a>Zobacz także  
 [Rozszerzenie menu i poleceń](../../extensibility/extending-menus-and-commands.md)