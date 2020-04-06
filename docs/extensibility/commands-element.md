---
title: Element poleceń | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3ea2400cca19a02475caecec3d022e0b78794ae4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739686"
---
# <a name="commands-element"></a>Element Polecenia
Reprezentuje kolekcję poleceń na pasku narzędzi VSPackage. Kolekcja może mieć maksymalnie pięć podsekcji, w następujący sposób: menu, grupy, przyciski, kombinacje i mapy bitowe.

 Każdy element podrzędny podsekcji, na przykład \<Menu>, jest identyfikowany za pomocą unikatowego identyfikatora polecenia, który jest parą identyfikatorów GUID i numerycznych. Identyfikator GUID identyfikuje "zestaw poleceń" i jest używany do grupowanie logicznie powiązanych poleceń. VSPackage należy zdefiniować własny zestaw poleceń, aby uniknąć kolizji z identyfikatorów poleceń, które są zdefiniowane przez inne VSPackages.

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
|Pakiet|Identyfikator GUID, który identyfikuje VSPackage, który udostępnia polecenia.<br /><br /> Na przykład package="guidVsPackage1Pkg".|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Element Menu](../extensibility/menus-element.md)|Definiuje wszystkie menu, które implementuje VSPackage.|
|[Element Grupy](../extensibility/groups-element.md)|Zawiera wpisy definiujące grupy poleceń w pakiecie VSPackage.|
|[Element przycisków](../extensibility/buttons-element.md)|Elementy przycisku Grupy.|
|[Element Mapy bitowe](../extensibility/bitmaps-element.md)|Grupy Elementy mapy bitowej.|
|[Element combo](../extensibility/combos-element.md)|Grupy elementów kombi.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element CommandTable](../extensibility/commandtable-element.md)|Definiuje wszystkie elementy, które reprezentują polecenia, które VSPackage zapewnia IDE. Możliwe elementy to elementy menu, menu, paski narzędzi i pola kombi.|

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
- [Jak vspackages dodać elementy interfejsu użytkownika](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)
