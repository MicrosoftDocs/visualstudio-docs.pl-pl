---
title: Jak pakietów VSPackage dodawać elementy interfejsu użytkownika | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
caps.latest.revision: 61
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 553c502c100cbb6ed4ae249096af408af14423b4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64833457"
---
# <a name="how-vspackages-add-user-interface-elements"></a>Dodawanie elementów interfejsu użytkownika przy użyciu pakietów VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pakietu VSPackage może dodawać elementy interfejsu użytkownika, na przykład menu, paski narzędzi i okna narzędzi, do programu Visual Studio za pomocą pliku. vsct.  
  
 Wskazówki dotyczące projektowania elementów interfejsu użytkownika można znaleźć w [wytycznych dotyczących środowiska użytkownika programu Visual Studio](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## <a name="the-visual-studio-command-table-architecture"></a>Architektura tabeli poleceń programu Visual Studio  
 Jak wspomniano, architektura tabeli poleceń obsługuje powyższe zasady architektury. Założenia za abstrakcją, strukturami danych i narzędziami architektury tabeli poleceń są następujące:  
  
- Istnieją trzy podstawowe rodzaje elementów: menu, polecenia i grupy. Menu może być uwidocznione w interfejsie użytkownika jako menu, podmenu, paski narzędzi lub okna narzędzi. Polecenia są procedurami, które użytkownik może wykonywać w IDE i mogą być udostępniane jako elementy menu, przyciski, pola listy lub inne kontrolki. Grupy są kontenerami dla menu i poleceń.  
  
- Każdy element jest określony przez definicję opisującą element, jego priorytet względem innych elementów oraz flagi modyfikujące jego zachowanie.  
  
- Każdy element ma rozmieszczenie, które opisuje element nadrzędny elementu. Element może mieć wiele elementów nadrzędnych, tak aby mógł znajdować się w wielu lokalizacjach w interfejsie użytkownika.  
  
     Każde polecenie musi mieć grupę jako nadrzędną, nawet jeśli jest jedynym elementem podrzędnym w tej grupie. Każde menu standardowe musi mieć również grupę nadrzędną. Paski narzędzi i okna narzędzi działają jako własne elementy nadrzędne. Grupa może mieć jako nadrzędną główną pasek menu programu Visual Studio lub dowolne menu, paski narzędzi lub okno narzędzi.  
  
### <a name="how-items-are-defined"></a>Jak są definiowane elementy  
 . Pliki VSCT są sformatowane w formacie XML. Plik. vsct definiuje elementy interfejsu użytkownika dla pakietu i określa, gdzie te elementy są widoczne w IDE. Każde menu, grupę lub polecenie w pakiecie otrzymuje najpierw identyfikator GUID i identyfikator w `Symbols` sekcji. W pozostałej części pliku. vsct wszystkie menu, polecenia i grupy są identyfikowane przez jego identyfikator GUID i identyfikator. W poniższym przykładzie przedstawiono typową `Symbols` sekcję wygenerowaną przez szablon pakietu programu Visual Studio, gdy w szablonie jest wybrane **polecenie menu** .  
  
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
  
 Element najwyższego poziomu `Symbols` sekcji to [element GuidSymbol](../../extensibility/guidsymbol-element.md). `GuidSymbol` elementy mapują nazwy na identyfikatory GUID, które są używane przez środowisko IDE do identyfikowania pakietów i ich części składników.  
  
> [!NOTE]
> Identyfikatory GUID są generowane automatycznie przez szablon pakietu programu Visual Studio. Możesz również utworzyć unikatowy identyfikator GUID, klikając polecenie **Utwórz identyfikator GUID** w menu **Narzędzia** .  
  
 Pierwszy `GuidSymbol` element "GUID [PackageName] pkg" jest identyfikatorem GUID samego pakietu. Jest to identyfikator GUID używany przez program Visual Studio do załadowania pakietu. Zazwyczaj nie ma elementów podrzędnych.  
  
 Według Konwencji menu i polecenia są pogrupowane pod drugim `GuidSymbol` elementem, "GUID [PackageName] CmdSet", a mapy bitowe znajdują się w trzecim `GuidSymbol` elemencie "guidImages". Nie trzeba stosować tej Konwencji, ale każde menu, grupowanie, polecenie i mapa bitowa musi być elementem podrzędnym `GuidSymbol` elementu.  
  
 W drugim `GuidSymbol` elemencie, który reprezentuje zestaw poleceń pakietu, jest kilka `IDSymbol` elementów. Każdy [element IDSymbol](../../extensibility/idsymbol-element.md) mapuje nazwę na wartość liczbową i może reprezentować menu, grupę lub polecenie, które jest częścią zestawu poleceń. `IDSymbol`Elementy w trzecim `GuidSymbol` elemencie reprezentują mapy bitowe, które mogą być używane jako ikony poleceń. Ponieważ pary GUID/ID muszą być unikatowe w aplikacji, żadne dwa elementy podrzędne tego samego `GuidSymbol` elementu nie mogą mieć tej samej wartości.  
  
### <a name="menus-groups-and-commands"></a>Menu, grupy i polecenia  
 Gdy menu, grupy lub polecenia ma identyfikator GUID i ID, można dodać go do IDE. Każdy element interfejsu użytkownika musi mieć następujące elementy:  
  
- `guid`Atrybut, który jest zgodny z nazwą `GuidSymbol` elementu, w którym jest zdefiniowany element interfejsu użytkownika.  
  
- `id`Atrybut, który jest zgodny z nazwą skojarzonego `IDSymbol` elementu.  
  
     Razem `guid` `id` atrybuty i tworzą *podpis* elementu interfejsu użytkownika.  
  
- `priority`Atrybut, który określa położenie elementu interfejsu użytkownika w jego menu nadrzędnym lub grupie.  
  
- [Element nadrzędny](../../extensibility/parent-element.md) , który zawiera `guid` `id` atrybuty, które określają podpis menu lub grupy nadrzędnej.  
  
#### <a name="menus"></a>Menu  
 Każde menu jest zdefiniowane jako [element menu](../../extensibility/menu-element.md) w `Menus` sekcji. Menu muszą mieć `guid` `id` atrybuty,, i `priority` i elementy `Parent` , a także następujące dodatkowe atrybuty i elementy podrzędne:  
  
- `type`Atrybut, który określa, czy menu ma być wyświetlane w środowisku IDE jako rodzaj menu, czy jako pasek narzędzi.  
  
- [Element Strings](../../extensibility/strings-element.md) , który zawiera [element ButtonText](../../extensibility/buttontext-element.md), który określa tytuł menu w IDE oraz [element CommandName](../../extensibility/commandname-element.md), który określa nazwę, która jest używana w oknie **polecenia** , aby uzyskać dostęp do menu.  
  
- Opcjonalne flagi. [Element flagi polecenia](../../extensibility/command-flag-element.md) może pojawić się w definicji menu, aby zmienić jego wygląd lub zachowanie w środowisku IDE.  
  
  Każdy `Menu` element musi mieć grupę jako element nadrzędny, chyba że jest to element było dokować, taki jak pasek narzędzi. Menu było dokować jest własnym obiektem nadrzędnym. Aby uzyskać więcej informacji na temat menu i wartości dla `type` atrybutu, zobacz dokumentację [elementu menu](../../extensibility/menu-element.md) .  
  
  Poniższy przykład pokazuje menu, które pojawia się na pasku menu programu Visual Studio obok menu **Narzędzia** .  
  
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
 Grupa to element, który jest zdefiniowany w `Groups` sekcji pliku. vsct. Grupy są tylko kontenerami. Nie są one wyświetlane w środowisku IDE, z wyjątkiem linii podziału w menu. W związku z tym [element grupy](../../extensibility/group-element.md) jest definiowany tylko za pomocą jego podpisu, priorytetu i elementu nadrzędnego.  
  
 Grupa może mieć menu, inną grupę lub samą siebie jako element nadrzędny. Jednak element nadrzędny jest zazwyczaj menu lub paskiem narzędzi. Menu w poprzednim przykładzie jest elementem podrzędnym `IDG_VS_MM_TOOLSADDINS` grupy, a grupa jest elementem podrzędnym paska menu programu Visual Studio. Grupa w poniższym przykładzie jest elementem podrzędnym menu w poprzednim przykładzie.  
  
```  
 <Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"  
priority="0x0600">  
   <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>  
 </Group>  
```  
  
 Ponieważ jest częścią menu, ta grupa zwykle zawiera polecenia. Może to jednak również zawierać inne menu. Jest to sposób definiowania podmenu, jak pokazano w poniższym przykładzie.  
  
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
 Polecenie, które jest dostarczane do IDE jest zdefiniowane jako [element Button](../../extensibility/button-element.md) lub [kombi](../../extensibility/combo-element.md). Aby pojawił się w menu lub pasku narzędzi, polecenie musi mieć grupę jako element nadrzędny.  
  
##### <a name="buttons"></a>Przyciski  
 Przyciski są zdefiniowane w `Buttons` sekcji. Każdy element menu, przycisk lub inny element, który użytkownik klika, aby wykonać pojedyncze polecenie, jest traktowany jako przycisk. Niektóre typy przycisków mogą również zawierać funkcje listy. Przyciski mają takie same atrybuty wymagane i opcjonalne, które są dostępne dla menu, i mogą także mieć [element ikon](../../extensibility/icon-element.md) , który określa identyfikator GUID i identyfikator mapy bitowej, która reprezentuje przycisk w IDE. Aby uzyskać więcej informacji na temat przycisków i ich atrybutów, zobacz sekcję dotyczącą [elementów Button](../../extensibility/buttons-element.md) .  
  
 Przycisk w poniższym przykładzie jest elementem podrzędnym grupy w poprzednim przykładzie i pojawi się w IDE jako element menu w menu nadrzędnym tej grupy.  
  
```  
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">  
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />  
  <Icon guid="guidImages" id="bmpPic1" />  
  <Strings>  
    <CommandName>cmdidTestCommand</CommandName>  
    <ButtonText>Test Command</ButtonText>  
  </Strings>  
</Button>  
```  
  
##### <a name="combos"></a>Pola kombi  
 Pola kombi są zdefiniowane w `Combos` sekcji. Każdy `Combo` element reprezentuje pole listy rozwijanej w środowisku IDE. Pole listy może lub nie może być zapisywalne przez użytkowników, w zależności od wartości `type` atrybutu kombi. Pola kombi mają takie same elementy i zachowanie, które są dostępne na przyciskach, a także mogą mieć następujące dodatkowe atrybuty:  
  
- `defaultWidth`Atrybut, który określa szerokość pikseli.  
  
- `idCommandList`Atrybut, który określa listę zawierającą elementy, które są wyświetlane w polu listy. Lista poleceń musi być zadeklarowana w tym samym `GuidSymbol` węźle, który zawiera pole kombi.  
  
  W poniższym przykładzie zdefiniowano element kombi.  
  
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
 Polecenia, które będą wyświetlane razem z ikoną, muszą zawierać `Icon` element, który odwołuje się do mapy bitowej przy użyciu identyfikatora GUID i identyfikatora. Każda mapa bitowa jest definiowana jako [element bitmapy](../../extensibility/bitmap-element.md) w `Bitmaps` sekcji. Jedynymi wymaganymi atrybutami `Bitmap` definicji są `guid` i `href` , które wskazują plik źródłowy. Jeśli plik źródłowy jest paskiem zasobów, wymagany jest również atrybut **usedList** , aby wyświetlić listę dostępnych obrazów na pasku. Aby uzyskać więcej informacji, zobacz dokumentację [elementu mapy bitowej](../../extensibility/bitmap-element.md) .  
  
### <a name="parenting"></a>Elementy nadrzędne  
 Poniższe reguły określają, jak element może wywoływać inny element jako element nadrzędny.  
  
|Element|Zdefiniowane w tej sekcji tabeli poleceń|Może być zawarta (jako element nadrzędny lub przez umieszczenie w `CommandPlacements` sekcji lub obie)|Może zawierać (określany jako element nadrzędny)|  
|-------------|--------------------------------------------------|---------------------------------------------------------------------------------------------------|---------------------------------------------|  
|Group (Grupa)|[Grupy, element](../../extensibility/groups-element.md)IDE, inne pakietów VSPackage|Menu, grupy, samego elementu|Menu, grupy i polecenia|  
|Menu|[Element menu](../../extensibility/menus-element.md), IDE, inne pakietów VSPackage|od 1 do *n* grup|od 0 do *n* grup|  
|Pasek narzędzi|[Element menu](../../extensibility/menus-element.md), IDE, inne pakietów VSPackage|Sam element|od 0 do *n* grup|  
|Element menu|[Button — element](../../extensibility/buttons-element.md), IDE, inne pakietów VSPackage|1 do *n* grup, sam element|-0 do *n* grup|  
|Przycisk|[Button — element](../../extensibility/buttons-element.md), IDE, inne pakietów VSPackage|1 do *n* grup, sam element||  
|Kombi|[Elementy kombi](../../extensibility/combos-element.md), IDE, inne pakietów VSPackage|1 do *n* grup, sam element||  
  
### <a name="menu-command-and-group-placement"></a>Położenie menu, polecenia i grupy  
 Menu, grupę lub polecenie może pojawić się w więcej niż jednej lokalizacji w IDE. Aby element pojawił się w wielu lokalizacjach, należy dodać go do `CommandPlacements` sekcji jako [element CommandPlacement](../../extensibility/commandplacement-element.md). Dowolne menu, grupy lub polecenia można dodać jako umieszczania polecenia. Nie można jednak umieścić pasków narzędzi w ten sposób, ponieważ nie mogą one występować w wielu lokalizacjach zależnych od kontekstu.  
  
 Umieszczenie poleceń ma `guid` atrybuty, `id` i `priority` . Identyfikatory GUID i ID muszą być zgodne z elementami, które są pozycjonowane. Ten `priority` atrybut reguluje rozmieszczenie elementu w odniesieniu do innych elementów. Gdy IDE Scala dwa lub więcej elementów o takim samym priorytecie, ich rozmieszczenia nie są zdefiniowane, ponieważ IDE nie gwarantuje, że zasoby pakietu są odczytywane w tej samej kolejności za każdym razem, gdy pakiet został skompilowany.  
  
 Jeśli menu lub grupa pojawia się w wielu lokalizacjach, wszystkie elementy podrzędne tego menu lub grupy będą wyświetlane w każdym wystąpieniu.  
  
## <a name="command-visibility-and-context"></a>Widoczność i kontekst polecenia  
 Gdy jest zainstalowanych wiele pakietów VSPackage, profuzja menu, elementów menu i pasków narzędzi może zasłaniać środowisko IDE. Aby uniknąć tego problemu, można kontrolować widoczność poszczególnych elementów interfejsu użytkownika przy użyciu *ograniczeń widoczności* i flag poleceń.  
  
##### <a name="visibility-constraints"></a>Ograniczenia widoczności  
 Ograniczenie widoczności jest ustawiane jako [element VisibilityItem](../../extensibility/visibilityitem-element.md) w `VisibilityConstraints` sekcji. Ograniczenie widoczności definiuje określone konteksty interfejsu użytkownika, w których element docelowy jest widoczny. Menu lub polecenie znajdujące się w tej sekcji jest widoczne tylko wtedy, gdy jeden z określonych kontekstów jest aktywny. Jeśli do menu lub polecenia nie odwołuje się w tej sekcji, jest on zawsze widoczny domyślnie. Ta sekcja nie ma zastosowania do grup.  
  
 `VisibilityItem` elementy muszą mieć trzy atrybuty, w następujący sposób: `guid` i `id` elementu docelowego interfejsu użytkownika i `context` . `context`Atrybut określa, kiedy element docelowy będzie widoczny, i przyjmuje prawidłowy kontekst interfejsu użytkownika jako jego wartość. Stałe kontekstu interfejsu użytkownika dla programu Visual Studio są elementami członkowskimi <xref:Microsoft.VisualStudio.VSConstants> klasy. Każdy `VisibilityItem` element może przyjmować tylko jedną wartość kontekstu. Aby zastosować drugi kontekst, utwórz drugi element, `VisibilityItem` który wskazuje na ten sam element, jak pokazano w poniższym przykładzie.  
  
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
  
##### <a name="command-flags"></a>Flagi poleceń  
 Poniższe flagi poleceń mogą wpływać na widoczność menu i poleceń, do których mają zastosowanie.  
  
 AlwaysCreate  
 Zostanie utworzone menu, nawet jeśli nie ma żadnych grup lub przycisków.  
  
 Prawidłowy dla: `Menu`  
  
 CommandWellOnly  
 Zastosuj tę flagę, jeśli polecenie nie pojawia się w menu najwyższego poziomu i chcesz udostępnić je do dodatkowego dostosowania powłoki, na przykład powiązania z kluczem. Po zainstalowaniu pakietu VSPackage użytkownik może dostosować te polecenia, otwierając okno dialogowe **Opcje** , a następnie edytując rozmieszczenie poleceń w kategorii **środowisko klawiatury** . Nie ma wpływu na umieszczanie w menu skrótów, paskach narzędzi, na kontrolerach menu lub podmenu.  
  
 Prawidłowy dla: `Button` , `Combo`  
  
 DefaultDisabled  
 Domyślnie polecenie jest wyłączone, jeśli pakietu VSPackage implementujące polecenie nie zostało załadowane lub metoda QueryStatus nie została wywołana.  
  
 Prawidłowy dla: `Button` , `Combo`  
  
 DefaultInvisible  
 Domyślnie polecenie jest niewidoczne, jeśli pakietu VSPackage implementujące polecenie nie zostało załadowane lub metoda QueryStatus nie została wywołana.  
  
 Powinien być połączony z `DynamicVisibility` flagą.  
  
 Prawidłowy dla: `Button` , `Combo` , `Menu`  
  
 DynamicVisibility  
 Widoczność polecenia można zmienić za pomocą metody QueryStatus lub identyfikatora GUID kontekstu, który znajduje się w `VisibilityConstraints` sekcji.  
  
 Dotyczy poleceń, które pojawiają się w menu, a nie na paskach narzędzi. Elementy paska narzędzi najwyższego poziomu można wyłączyć, ale nie ukryte, gdy flaga OLECMDF_INVISIBLE jest zwracana z metody QueryStatus.  
  
 W menu ta flaga wskazuje również, że powinna być automatycznie ukryta, gdy jej elementy członkowskie są ukryte. Ta flaga jest zwykle przypisana do podmenu, ponieważ menu najwyższego poziomu ma już takie zachowanie.  
  
 Powinien być połączony z `DefaultInvisible` flagą.  
  
 Prawidłowy dla: `Button` , `Combo` , `Menu`  
  
 NoShowOnMenuController  
 Jeśli polecenie, które ma tę flagę, znajduje się na kontrolerze menu, polecenie nie pojawia się na liście rozwijanej.  
  
 Prawidłowy dla: `Button`  
  
 Aby uzyskać więcej informacji na temat flag poleceń, zobacz dokumentację [elementu flagi polecenia](../../extensibility/command-flag-element.md) .  
  
##### <a name="general-requirements"></a>Wymagania ogólne  
 Aby można było wyświetlić i włączyć polecenie, musisz przekazać poniższą serię testów:  
  
- Polecenie zostało prawidłowo umieszczone.  
  
- `DefaultInvisible`Flaga nie jest ustawiona.  
  
- Menu nadrzędne lub pasek narzędzi jest widoczny.  
  
- Polecenie nie jest niewidoczne ze względu na wpis kontekstu w sekcji [VisibilityConstraints elementu](../../extensibility/visibilityconstraints-element.md) .  
  
- Kod pakietu VSPackage, który implementuje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejs Wyświetla i włącza polecenie. Kod interfejsu nie został przechwycony i działa na nim.  
  
- Gdy użytkownik kliknie polecenie, podlega procedurze opisanej w [algorytmie routingu](../../extensibility/internals/command-routing-algorithm.md).  
  
## <a name="calling-pre-defined-commands"></a>Wywoływanie wstępnie zdefiniowanych poleceń  
 [Element UsedCommands](../../extensibility/usedcommands-element.md) umożliwia pakietów VSPackage dostęp do poleceń, które są dostarczane przez inne pakietów VSPackage lub przez IDE. W tym celu Utwórz [element UsedCommand](../../extensibility/usedcommand-element.md) , który ma identyfikator GUID i identyfikator polecenia do użycia. Dzięki temu polecenie zostanie załadowane przez program Visual Studio, nawet jeśli nie jest on częścią bieżącej konfiguracji programu Visual Studio. Aby uzyskać więcej informacji, zobacz [UsedCommand element](../../extensibility/usedcommand-element.md).  
  
## <a name="interface-element-appearance"></a>Wygląd elementu interfejsu  
 Zagadnienia dotyczące wybierania i pozycjonowania elementów poleceń są następujące:  
  
- [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] oferuje wiele elementów interfejsu użytkownika, które są wyświetlane inaczej w zależności od położenia.  
  
- Element interfejsu użytkownika, który jest zdefiniowany przy użyciu `DefaultInvisible` flagi, nie będzie wyświetlany w środowisku IDE, chyba że jest on wyświetlany przez implementację pakietu VSPackage <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> metody lub skojarzoną z określonym KONTEKSTEM interfejsu użytkownika w `VisibilityConstraints` sekcji.  
  
- Nawet pomyślnie pozycjonowane polecenie może nie być wyświetlane. Dzieje się tak, ponieważ środowisko IDE automatycznie ukrywa lub wyświetla niektóre polecenia, w zależności od interfejsów, które pakietu VSPackage (lub nie zostały zaimplementowane). Na przykład implementacja pakietu VSPackage niektórych interfejsów kompilacji powoduje automatyczne wyświetlanie elementów menu związanych z kompilacją.  
  
- Zastosowanie `CommandWellOnly` flagi w definicji elementu interfejsu użytkownika oznacza, że polecenie można dodać tylko przez dostosowanie.  
  
- Polecenia mogą być dostępne tylko w niektórych kontekstach interfejsu użytkownika, na przykład, gdy okno dialogowe jest wyświetlane, gdy IDE jest w widoku projektu.  
  
- Aby spowodować, że niektóre elementy interfejsu użytkownika mają być wyświetlane w IDE, należy zaimplementować jeden lub więcej interfejsów lub napisać kod.  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md)
