---
title: Commands — element | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 194768a3b540511996e1d99e6450a7a9b24ebc74
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184293"
---
# <a name="commands-element"></a>Commands, element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Reprezentuje kolekcję poleceń na pasku narzędzi pakietu VSPackage. Kolekcja może zawierać maksymalnie pięć podsekcji: menu, grupy, przyciski, listy kombinowane i mapy bitowe.  
  
 Każdy podsekcja elementu podrzędnego, na przykład, \<Menu> jest identyfikowany przez unikatowy identyfikator polecenia, który jest identyfikatorem GUID i pary identyfikatorów liczbowych. Identyfikator GUID identyfikuje "zestaw poleceń" i służy do grupowania logicznie powiązanych poleceń. Pakietu VSPackage powinien definiować własny zestaw poleceń, aby uniknąć kolizji z identyfikatorami poleceń, które są zdefiniowane przez inne pakietów VSPackage.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|Package|Identyfikator GUID, który identyfikuje pakietu VSPackage, który zawiera polecenia.<br /><br /> Na przykład Package = "guidVsPackage1Pkg".|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Menus, element](../extensibility/menus-element.md)|Definiuje wszystkie menu, które implementuje pakietu VSPackage.|  
|[Groups, element](../extensibility/groups-element.md)|Zawiera wpisy, które definiują grupy poleceń w pakietu VSPackage.|  
|[Buttons, element](../extensibility/buttons-element.md)|Elementy przycisków grup.|  
|[Bitmaps, element](../extensibility/bitmaps-element.md)|Grupuje elementy mapy bitowej.|  
|[Combos, element](../extensibility/combos-element.md)|Grupuje elementy kombi.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[CommandTable, element](../extensibility/commandtable-element.md)|Definiuje wszystkie elementy, które reprezentują polecenia, które pakietu VSPackage zapewnia IDE. Możliwe elementy to elementy menu, menu, paski narzędzi i pola kombi.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać [elementu Commands](../extensibility/commands-element.md).  
  
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
 [Jak pakietów VSPackage Dodawanie elementów interfejsu użytkownika](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)
