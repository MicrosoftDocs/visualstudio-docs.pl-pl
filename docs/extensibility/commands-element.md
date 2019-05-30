---
title: Polecenia elementu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab8629fb3ef83277f1366a5141c400b8eeea70e3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341902"
---
# <a name="commands-element"></a>Commands, element
Reprezentuje kolekcję poleceń na pasku narzędzi pakietu VSPackage. Kolekcja może mieć podsekcje maksymalnie pięć w następujący sposób: menu, grup, przyciski, combos i map bitowych.

 Każdej podsekcji elementu podrzędnego, na przykład \<Menu >, jest identyfikowana przez identyfikator unikatowy polecenia, który jest identyfikatorem GUID i identyfikator liczbowy pary. Identyfikator GUID identyfikuje "zestawu poleceń" i służy do grupowania logicznie powiązanych poleceń. Pakietu VSPackage należy zdefiniować własne polecenia ustawione, aby uniknąć kolizji z identyfikatorów poleceń, które są definiowane przez innych pakietów VSPackage.

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
|Pakiet|Identyfikator GUID, który identyfikuje pakietu VSPackage, który udostępnia polecenia.<br /><br /> Na przykład pakiet = "guidVsPackage1Pkg".|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[Menus, element](../extensibility/menus-element.md)|Definiuje menu, które implementuje pakietu VSPackage.|
|[Element grupy](../extensibility/groups-element.md)|Zawiera wpisy, które definiują grup poleceń w VSPackage.|
|[Buttons, element](../extensibility/buttons-element.md)|Grupuje elementy przycisku.|
|[Bitmaps, element](../extensibility/bitmaps-element.md)|Grupuje elementy mapy bitowej.|
|[Combos, element](../extensibility/combos-element.md)|Grupuje elementy kombi.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[CommandTable, element](../extensibility/commandtable-element.md)|Definiuje wszystkie elementy, które stanowią polecenia, IDE przez pakietu VSPackage. Możliwe elementy są elementów menu, menu, paski narzędzi i pola kombi.|

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje, jak używać [Commands, Element](../extensibility/commands-element.md).

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

## <a name="see-also"></a>Zobacz także
- [Jak dodać elementy interfejsu użytkownika w pakietach VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)