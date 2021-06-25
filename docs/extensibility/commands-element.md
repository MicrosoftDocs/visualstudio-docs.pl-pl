---
title: Commands, element | Microsoft Docs
description: 'Element Polecenia reprezentuje kolekcję poleceń na pasku narzędzi vsPackage i może mieć następujące sekcje: menu, grupy, przyciski, kombinacje i mapy bitowe.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e4c7b058acdd634079d0ca60dddb9f80e0e26ff0
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901873"
---
# <a name="commands-element"></a>Commands, element
Reprezentuje kolekcję poleceń na pasku narzędzi vspackage. Kolekcja może mieć maksymalnie pięć podsekcji w następujący sposób: menu, grupy, przyciski, kombi i mapy bitowe.

 Każdy element podrzędny podsekcji, na przykład , jest identyfikowany przez unikatowy identyfikator polecenia, który \<Menu> jest identyfikatorem GUID i parą identyfikatorów liczbowych. Identyfikator GUID identyfikuje "zestaw poleceń" i służy do grupowania logicznie powiązanych poleceń. Pakiet VSPackage powinien definiować własny zestaw poleceń, aby uniknąć kolizji z identyfikatorami poleceń, które są zdefiniowane przez inne pakiet VSPackages.

## <a name="syntax"></a>Składnia

```xml
<Commands package="GuidMyPackage" >
  <Menus>... </Menus>
  <Groups>... </Groups>
  <Buttons>... </Buttons>
  <Combos>... </Combos>
  <Bitmaps>... </Bitmaps>
</Commands>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|package|Identyfikator GUID identyfikujący pakiet VSPackage, który udostępnia polecenia.<br /><br /> Na przykład package="guidVsPackage1Pkg".|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Menus, element](../extensibility/menus-element.md)|Definiuje wszystkie menu implementowanych przez pakiet VSPackage.|
|[Groups, element](../extensibility/groups-element.md)|Zawiera wpisy, które definiują grupy poleceń w vsPackage.|
|[Buttons, element](../extensibility/buttons-element.md)|Grupuj elementy przycisku.|
|[Bitmaps, element](../extensibility/bitmaps-element.md)|Grupuje elementy mapy bitowej.|
|[Combos, element](../extensibility/combos-element.md)|Grupuje elementy kombi.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[CommandTable, element](../extensibility/commandtable-element.md)|Definiuje wszystkie elementy reprezentujące polecenia, które pakiet VSPackage dostarcza do środowiska IDE. Możliwe elementy to elementy menu, menu, paski narzędzi i pola kombi.|

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano, jak używać [elementu polecenia](../extensibility/commands-element.md).

```
<Commands package="guidMyPackage">
    <Menus>
      <Menu Condition="'%(DEBUG)' != 'true'"
        guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu"
        priority="0x0000" type="Menu">
        <Annotation>
          <Documentation>this is an annotation</Documentation>
          <AppInfo>
            <CustomData>
              <CustomSubElement>Some data</CustomSubElement>
            </CustomData>
          </AppInfo>
        </Annotation>
        <CommandFlag>AlwaysCreate</CommandFlag>
        <Strings>
          <ButtonText>MainMenu</ButtonText>
        </Strings>
      </Menu>
  </Menus>
<Commands>
```

## <a name="see-also"></a>Zobacz też
- [Jak pakiet VSPackages dodaje elementy interfejsu użytkownika](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)
