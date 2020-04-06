---
title: Jak VSPackages Dodać elementy interfejsu użytkownika | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3b7d37bfe81c77536871248592d4a2e0734d1c62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707764"
---
# <a name="how-vspackages-add-user-interface-elements"></a>Jak vspackages dodać elementy interfejsu użytkownika
VsPackage można dodać elementy interfejsu użytkownika (UI), na przykład menu, paski narzędzi i okna narzędzi do programu Visual Studio za pomocą pliku *vsct.*

 Wskazówki dotyczące projektowania elementów interfejsu użytkownika można znaleźć w [wskazówki dotyczące środowiska użytkownika programu Visual Studio.](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)

## <a name="the-visual-studio-command-table-architecture"></a>Architektura tabeli poleceń programu Visual Studio
 Jak wspomniano, architektura tabeli poleceń obsługuje powyższe zasady architektury. Zasady za abstrakcje, struktury danych i narzędzia architektury tabeli poleceń są następujące:

- Istnieją trzy podstawowe rodzaje elementów: menu, polecenia i grupy. Menu mogą być widoczne w interfejsie użytkownika jako menu, podmenu, paski narzędzi lub okna narzędzi. Polecenia są procedury, które użytkownik może wykonać w IDE i mogą być udostępniane jako elementy menu, przyciski, pola listy lub inne formanty. Grupy są kontenerami zarówno dla menu, jak i poleceń.

- Każdy element jest określony przez definicję, która opisuje element, jego priorytet względem innych elementów i flagi, które modyfikują jego zachowanie.

- Każdy element ma miejsce docelowe, które opisuje element nadrzędny elementu. Element może mieć wiele elementów rzemiośowych, dzięki czemu może być wyświetlany w wielu lokalizacjach w interfejsie użytkownika.

     Każde polecenie musi mieć grupę jako element nadrzędny, nawet jeśli jest to jedyny element podrzędny w tej grupie. Każde standardowe menu musi mieć również grupę nadrzędną. Paski narzędzi i okna narzędzi działają jak ich rodzice. Grupa może mieć jako element nadrzędny główny pasek menu programu Visual Studio lub dowolne menu, pasek narzędzi lub okno narzędzia.

### <a name="how-items-are-defined"></a>Jak elementy są definiowane
 Plik *.vsct* jest sformatowany w formacie XML. Definiuje elementy interfejsu użytkownika dla pakietu i określa, gdzie te elementy pojawiają się w IDE. Każde menu, grupa lub polecenie w pakiecie jest najpierw przypisywane `Symbols` identyfikatorowi GUID i identyfikatorowi w sekcji. W pozostałej części pliku *vsct* każde menu, polecenie i grupa jest identyfikowane za pomocą kombinacji identyfikatorów GUID i ID. W poniższym przykładzie przedstawiono typową `Symbols` sekcję jako wygenerowaną przez szablon pakietu programu Visual Studio, gdy polecenie **menu** jest zaznaczone w szablonie.

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

 Elementem najwyższego `Symbols` poziomu sekcji jest [element GuidSymbol](../../extensibility/guidsymbol-element.md). `GuidSymbol`elementy mapują nazwy identyfikatorów GUID, które są używane przez IDE do identyfikowania pakietów i ich części składowych.

> [!NOTE]
> Identyfikatory GUID są generowane automatycznie przez szablon pakietu programu Visual Studio. Unikatowy identyfikator GUID można również utworzyć, klikając polecenie **Utwórz identyfikator GUID** w menu **Narzędzia.**

 Pierwszym `GuidSymbol` elementem `guid<PackageName>Pkg`, jest identyfikator GUID samego pakietu. Jest to identyfikator GUID, który jest używany przez program Visual Studio do załadowania pakietu. Zazwyczaj nie ma elementów podrzędnych.

 Zgodnie z konwencją menu i polecenia są `GuidSymbol` zgrupowane w drugim elemencie, `guid<PackageName>CmdSet`a mapy bitowe znajdują się pod trzecim `GuidSymbol` elementem. `guidImages` Nie trzeba przestrzegać tej konwencji, ale każde menu, grupa, polecenie i bitmapa musi być elementem podrzędnym `GuidSymbol` elementu.

 W drugim `GuidSymbol` elemencie, który reprezentuje `IDSymbol` zestaw poleceń pakietu, są kilka elementów. Każdy [element IDSymbol](../../extensibility/idsymbol-element.md) mapuje nazwę na wartość liczbową i może reprezentować menu, grupę lub polecenie, które jest częścią zestawu poleceń. Elementy `IDSymbol` w trzecim `GuidSymbol` elemencie reprezentują mapy bitowe, które mogą być używane jako ikony dla poleceń. Ponieważ pary identyfikatorów GUID/ID muszą być unikatowe w `GuidSymbol` aplikacji, nie dwa elementy podrzędne tego samego elementu może mieć taką samą wartość.

### <a name="menus-groups-and-commands"></a>Menu, grupy i polecenia
 Gdy menu, grupa lub polecenie ma identyfikator GUID i identyfikator, można je dodać do IDE. Każdy element interfejsu użytkownika musi mieć następujące rzeczy:

- Atrybut, `guid` który pasuje do `GuidSymbol` nazwy elementu, w obszarze który jest zdefiniowany element interfejsu użytkownika.

- Atrybut, `id` który pasuje do nazwy `IDSymbol` skojarzonego elementu.

     Razem `guid` i `id` atrybuty tworzą *podpis* elementu interfejsu użytkownika.

- Atrybut, `priority` który określa położenie elementu interfejsu użytkownika w menu nadrzędnym lub grupie nadrzędnej.

- Element [nadrzędny,](../../extensibility/parent-element.md) który ma `guid` i `id` atrybuty, które określają podpis menu nadrzędnego lub grupy.

#### <a name="menus"></a>Menu
 Każde menu jest zdefiniowane jako `Menus` element [menu](../../extensibility/menu-element.md) w sekcji. Menu musi `guid`mieć `id`, `priority` i atrybuty i `Parent` element, a także następujące dodatkowe atrybuty i elementy podrzędne:

- Atrybut, `type` który określa, czy menu powinno być wyświetlane w IDE jako rodzaj menu lub jako pasek narzędzi.

- A [Strings element,](../../extensibility/strings-element.md) który zawiera [ButtonText element](../../extensibility/buttontext-element.md), który określa tytuł menu w IDE i [CommandName element](../../extensibility/commandname-element.md), który określa nazwę, która jest używana w oknie **Polecenia,** aby uzyskać dostęp do menu.

- Opcjonalne flagi. A [CommandFlag element](../../extensibility/command-flag-element.md) może pojawić się w definicji menu, aby zmienić jego wygląd lub zachowanie w IDE.

  Każdy `Menu` element musi mieć grupę jako element nadrzędny, chyba że jest to element dokowany, taki jak pasek narzędzi. Menu dokowane jest jego własnym elementem nadrzędnym. Aby uzyskać więcej informacji na `type` temat menu i wartości dla atrybutu, zobacz dokumentację [elementu menu.](../../extensibility/menu-element.md)

  W poniższym przykładzie pokazano menu, które pojawia się na pasku menu programu Visual Studio, obok menu **Narzędzia.**

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
 Grupa jest elementem zdefiniowanym `Groups` w sekcji pliku *vsct.* Grupy to tylko kontenery. Nie są one wyświetlane w IDE, z wyjątkiem jako linii podziału w menu. W związku z tym [Group element](../../extensibility/group-element.md) jest zdefiniowany tylko przez jego podpis, priorytet i nadrzędny.

 Grupa może mieć menu, inną grupę lub siebie jako element nadrzędny. Jednak element nadrzędny jest zazwyczaj menu lub paska narzędzi. Menu we wcześniejszym przykładzie jest `IDG_VS_MM_TOOLSADDINS` elementem podrzędnym grupy, a ta grupa jest elementem podrzędnym paska menu programu Visual Studio. Grupa w poniższym przykładzie jest elementem podrzędnym menu we wcześniejszym przykładzie.

```xml
 <Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"
priority="0x0600">
   <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>
 </Group>
```

 Ponieważ jest częścią menu, ta grupa zazwyczaj zawiera polecenia. Jednak może również zawierać inne menu. W ten sposób zdefiniowane są podmenu, jak pokazano w poniższym przykładzie.

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
 Polecenie, które jest dostarczane do IDE jest zdefiniowany jako [Button elementu](../../extensibility/button-element.md) lub [Combo element](../../extensibility/combo-element.md). Aby można było pojawić się w menu lub na pasku narzędzi, polecenie musi mieć grupę jako element nadrzędny.

##### <a name="buttons"></a>Przyciski
 Przyciski są `Buttons` zdefiniowane w sekcji. Każdy element menu, przycisk lub inny element, który użytkownik kliknie, aby wykonać pojedyncze polecenie, jest uważany za przycisk. Niektóre typy przycisków mogą również zawierać funkcje listy. Przyciski mają te same atrybuty wymagane i opcjonalne, które mają menu, a także mogą mieć [element Icon,](../../extensibility/icon-element.md) który określa identyfikator GUID i identyfikator mapy bitowej reprezentujący przycisk w IDE. Aby uzyskać więcej informacji na temat przycisków i ich atrybutów, zobacz dokumentację [elementu Przyciski.](../../extensibility/buttons-element.md)

 Przycisk w poniższym przykładzie jest elementem podrzędnym grupy we wcześniejszym przykładzie i pojawi się w IDE jako element menu w menu nadrzędnym tej grupy.

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

##### <a name="combos"></a>Combo
 Kombinacje są zdefiniowane `Combos` w sekcji. Każdy `Combo` element reprezentuje pole listy rozwijanej w IDE. Pole listy może lub nie może być zapisywalne przez użytkowników, w zależności od wartości `type` atrybutu kombi. Kombinacje mają te same elementy i zachowanie, które mają przyciski, a także mogą mieć następujące dodatkowe atrybuty:

- Atrybut `defaultWidth` określający szerokość piksela.

- Atrybut `idCommandList` określający listę zawierającą elementy wyświetlane w polu listy. Lista poleceń musi być `GuidSymbol` zadeklarowana w tym samym węźle, który zawiera kombi.

  Poniższy przykład definiuje element kombi.

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
 Polecenia, które będą wyświetlane wraz z ikoną, muszą zawierać `Icon` element, który odwołuje się do mapy bitowej przy użyciu jego identyfikatora GUID i identyfikatora. Każda mapa bitowa jest definiowana `Bitmaps` jako [element bitmapy](../../extensibility/bitmap-element.md) w sekcji. Jedynymi wymaganymi atrybutami `Bitmap` `guid` dla `href`definicji są i , który wskazuje na plik źródłowy. Jeśli plik źródłowy jest paskiem zasobów, wymagany jest również atrybut **usedList,** aby wyświetlić listę dostępnych obrazów w pasku. Aby uzyskać więcej informacji, zobacz dokumentację [elementu bitmapy.](../../extensibility/bitmap-element.md)

### <a name="parenting"></a>Rodzicielstwo
 Poniższe reguły regulują, jak element może wywołać inny element jako jego element nadrzędny.

|Element|Zdefiniowano w tej sekcji tabeli poleceń|Mogą być zawarte (jako rodzic, lub `CommandPlacements` przez umieszczenie w sekcji, lub obu)|Może zawierać (dalej rodzica)|
|-------------| - | - | - |
|Grupa|[Element Grupy](../../extensibility/groups-element.md), IDE, inne pakiety VSPackages|Menu, grupa, sam element|Menu, grupy i polecenia|
|Menu|[Menu element](../../extensibility/menus-element.md), IDE, inne VSPackages|1 do *n* grup|0 do *n* grup|
|Pasek narzędzi|[Menu element](../../extensibility/menus-element.md), IDE, inne VSPackages|Sam element|0 do *n* grup|
|Element menu|[Button element](../../extensibility/buttons-element.md), IDE, inne VSPackages|1 do *n* grup, sam element|-0 do *n* grup|
|Button|[Button element](../../extensibility/buttons-element.md), IDE, inne VSPackages|1 do *n* grup, sam element||
|Kombi|[Element Combos](../../extensibility/combos-element.md), IDE, inne pakiety VSPackages|1 do *n* grup, sam element||

### <a name="menu-command-and-group-placement"></a>Położenie menu, polecenia i grupy
 Menu, grupa lub polecenie może pojawić się w więcej niż jednej lokalizacji w IDE. Aby element pojawiał się w wielu lokalizacjach, musi zostać dodany do `CommandPlacements` sekcji jako element [CommandPlacement](../../extensibility/commandplacement-element.md). Dowolne menu, grupę lub polecenie można dodać jako położenie polecenia. Jednak paski narzędzi nie mogą być rozmieszczone w ten sposób, ponieważ nie mogą być wyświetlane w wielu lokalizacjach kontekstowych.

 Miejsca docelowe `guid` `id`poleceń `priority` mają , i atrybuty. Identyfikator GUID i identyfikator musi być zgodny z elementem, który jest umieszczony. Atrybut `priority` reguluje rozmieszczenie elementu w odniesieniu do innych elementów. Gdy IDE scala dwa lub więcej elementów, które mają ten sam priorytet, ich miejsca docelowe są niezdefiniowane, ponieważ IDE nie gwarantuje, że zasoby pakietu są odczytywane w tej samej kolejności za każdym razem, gdy pakiet jest zbudowany.

 Jeśli menu lub grupa pojawi się w wielu lokalizacjach, wszystkie elementy podrzędne tego menu lub grupy pojawią się w każdym wystąpieniu.

## <a name="command-visibility-and-context"></a>Widoczność polecenia i kontekst
 Po zainstalowaniu wielu vspackages, mnóstwo menu, elementów menu i paski narzędzi może zaśmiecać IDE. Aby uniknąć tego problemu, można kontrolować widoczność poszczególnych elementów interfejsu użytkownika przy użyciu *ograniczeń widoczności* i flagi poleceń.

### <a name="visibility-constraints"></a>Ograniczenia widoczności
 Ograniczenie widoczności jest ustawiona jako element `VisibilityConstraints` [VisibilityItem](../../extensibility/visibilityitem-element.md) w sekcji. Ograniczenie widoczności definiuje określone konteksty interfejsu użytkownika, w których element docelowy jest widoczny. Menu lub polecenie, które znajduje się w tej sekcji jest widoczne tylko wtedy, gdy jeden ze zdefiniowanych kontekstów jest aktywny. Jeśli menu lub polecenia nie odwołuje się w tej sekcji, jest zawsze widoczne domyślnie. Ta sekcja nie dotyczy grup.

 `VisibilityItem`elementy muszą mieć trzy atrybuty, `id` w następujący sposób: `context` `guid` i docelowego elementu interfejsu użytkownika i . Atrybut `context` określa, kiedy element docelowy będzie widoczny i przyjmuje dowolny prawidłowy kontekst interfejsu użytkownika jako jego wartość. Stałe kontekstu interfejsu użytkownika dla programu <xref:Microsoft.VisualStudio.VSConstants> Visual Studio są członkami klasy. Każdy `VisibilityItem` element może mieć tylko jedną wartość kontekstu. Aby zastosować drugi kontekst, `VisibilityItem` należy utworzyć drugi element, który wskazuje na ten sam element, jak pokazano w poniższym przykładzie.

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

### <a name="command-flags"></a>Flagi poleceń
 Następujące flagi poleceń mogą mieć wpływ na widoczność menu i poleceń, do których się odnoszą.

 `AlwaysCreate`Menu jest tworzone, nawet jeśli nie ma grup ani przycisków.

 Ważne dla:`Menu`

 `CommandWellOnly`Zastosuj tę flagę, jeśli polecenie nie jest wyświetlane w menu najwyższego poziomu i chcesz udostępnić ją do dodatkowego dostosowywania powłoki, na przykład powiązanie go z kluczem. Po zainstalowaniu programu VSPackage użytkownik może dostosować te polecenia, otwierając okno dialogowe **Opcje,** a następnie edytując położenie polecenia w kategorii **Środowisko klawiatury.** Nie wpływa na położenie na menu skrótów, paskach narzędzi, kontrolerach menu ani podmenu.

 Ważne dla: `Button`,`Combo`

 `DefaultDisabled`Domyślnie polecenie jest wyłączone, jeśli vspackage, który implementuje polecenie nie jest załadowany lub QueryStatus metoda nie została wywołana.

 Ważne dla: `Button`,`Combo`

 `DefaultInvisible`Domyślnie polecenie jest niewidoczne, jeśli vspackage, który implementuje polecenie nie jest załadowany lub QueryStatus metoda nie została wywołana.

 Powinny być połączone `DynamicVisibility` z flagą.

 Ważne `Button`dla: `Combo`, ,`Menu`

 `DynamicVisibility`Widoczność polecenia można zmienić za `QueryStatus` pomocą metody lub kontekstu GUID, który znajduje się w `VisibilityConstraints` sekcji.

 Dotyczy poleceń wyświetlanych w menu, a nie na paskach narzędzi. Elementy paska narzędzi najwyższego poziomu można wyłączyć, `OLECMDF_INVISIBLE` ale nie `QueryStatus` są ukryte, gdy flaga jest zwracana z metody.

 W menu ta flaga wskazuje również, że powinna być automatycznie ukrywana, gdy jej elementy członkowskie są ukryte. Ta flaga jest zazwyczaj przypisana do podmenu, ponieważ menu najwyższego poziomu mają już to zachowanie.

 Powinny być połączone `DefaultInvisible` z flagą.

 Ważne `Button`dla: `Combo`, ,`Menu`

 `NoShowOnMenuController`Jeśli polecenie, które ma tę flagę, jest umieszczone na kontrolerze menu, polecenie nie pojawia się na liście rozwijanej.

 Ważne dla:`Button`

 Aby uzyskać więcej informacji na temat flag poleceń, zobacz [CommandFlag](../../extensibility/command-flag-element.md) dokumentacji elementu.

#### <a name="general-requirements"></a>Wymagania ogólne
 Polecenie musi przejść następującą serię testów, zanim będzie można je wyświetlić i włączyć:

- Polecenie jest prawidłowo ustawione.

- Flaga `DefaultInvisible` nie jest ustawiona.

- Menu nadrzędne lub pasek narzędzi są widoczne.

- Polecenie nie jest niewidoczne z powodu wpisu kontekstu w [sekcji elementu VisibilityConstraints.](../../extensibility/visibilityconstraints-element.md)

- VsPackage kod, który <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementuje interfejs wyświetla i włącza polecenie. Żaden kod interfejsu nie przechwycił go i działał na nim.

- Gdy użytkownik kliknie polecenie, staje się ono przedmiotem procedury opisanej w [algorytmie routingu](../../extensibility/internals/command-routing-algorithm.md).

## <a name="call-pre-defined-commands"></a>Wywoływanie wstępnie zdefiniowanych poleceń
 [UsedCommands element](../../extensibility/usedcommands-element.md) umożliwia VSPackages dostęp do poleceń, które są dostarczane przez inne VSPackages lub IDE. Aby to zrobić, należy utworzyć [UsedCommand element,](../../extensibility/usedcommand-element.md) który ma identyfikator GUID i identyfikator polecenia do użycia. Gwarantuje to, że polecenie zostanie załadowane przez program Visual Studio, nawet jeśli nie jest częścią bieżącej konfiguracji programu Visual Studio. Aby uzyskać więcej informacji, zobacz [UsedCommand element](../../extensibility/usedcommand-element.md).

## <a name="interface-element-appearance"></a>Wygląd elementu interfejsu
 Zagadnienia dotyczące wyboru i pozycjonowania elementów polecenia są następujące:

- [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]oferuje wiele elementów interfejsu użytkownika, które pojawiają się inaczej w zależności od miejsca docelowego.

- Element interfejsu użytkownika, który jest `DefaultInvisible` zdefiniowany przy użyciu flagi nie będą wyświetlane w IDE, chyba że <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> jest wyświetlany przez jego VSPackage `VisibilityConstraints` implementacji metody lub skojarzone z kontekstu określonego interfejsu użytkownika w sekcji.

- Nawet pomyślnie ustawione polecenie może nie być wyświetlane. Dzieje się tak, ponieważ IDE automatycznie ukrywa lub wyświetla niektóre polecenia, w zależności od interfejsów, które VSPackage ma (lub nie) zaimplementowane. Na przykład vsPackage implementacji niektórych interfejsów kompilacji powoduje elementy menu związane z kompilacją, które mają być wyświetlane automatycznie.

- Zastosowanie `CommandWellOnly` flagi w definicji elementu interfejsu użytkownika oznacza, że polecenie można dodać tylko przez dostosowanie.

- Polecenia mogą być dostępne tylko w niektórych kontekstach interfejsu użytkownika, na przykład tylko wtedy, gdy okno dialogowe jest wyświetlane, gdy IDE jest w widoku projektu.

- Aby spowodować, że niektóre elementy interfejsu użytkownika mają być wyświetlane w IDE, należy zaimplementować jeden lub więcej interfejsów lub napisać kod.

## <a name="see-also"></a>Zobacz też
- [Rozszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md)
