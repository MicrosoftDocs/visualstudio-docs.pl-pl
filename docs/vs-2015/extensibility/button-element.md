---
title: Przycisk Element | Dokumentacja firmy Microsoft
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
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 20673b87972c51a6cc0e3ce07553a0a721d7cca3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733312"
---
# <a name="button-element"></a>Button, element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Definiuje element, który użytkownik może interakcyjnie przeprowadzić. Przyciski mogą być różnych typów: przycisk, przycisk menu i SplitDropDown.  
  
## <a name="syntax"></a>Składnia  
  
```  
<Button guid="guidMyCommandSet" id="MyCommand" priority="0x102" type="button">  
  <Parent>... </Parent>  
  <Icon>... </Icon>  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</Button>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Identyfikator GUID|Wymagana. Identyfikator GUID identyfikatora polecenia identyfikator GUID/ID.|  
|identyfikator|Wymagana. Identyfikator GUID/ID identyfikator polecenia.|  
|priorytet|Opcjonalna. Wartość liczbowa określająca priorytet.|  
|— typ|Opcjonalna. Wartość wyliczana, który określa typ przycisku.<br /><br /> Jeśli nie zostanie podana, używa przycisku.<br /><br /> Przycisk<br /> Standardowe polecenie, które pojawia się na paskach narzędzi (zwykle jako ikony przycisku), menu i menu kontekstowego.<br /><br /> Przycisk menu<br /> Element menu, który nie jest wykonywane polecenie, ale daje innym menu.<br /><br /> SplitDropDown<br /> Formanty, takie jak przyciski Cofnij i ponów na standardowym pasku narzędzi, które są dostępne w programie Microsoft Word.|  
|Warunek|Opcjonalna. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Parent, element](../extensibility/parent-element.md)|Opcjonalna. Elementu nadrzędnego przycisku.|  
|[Icon, element](../extensibility/icon-element.md)|Opcjonalna. Ikona skojarzone z nim.|  
|[Command Flag, element](../extensibility/command-flag-element.md)|Wymagana. Prawidłowe wartości CommandFlag dla przycisku, to w następujący sposób.<br /><br /> -AllowParams<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DontCache<br /><br /> -DynamicItemStart<br /><br /> -DynamicVisibility<br /><br /> -FixMenuController<br /><br /> -IconAndText<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -NoShowOnMenuController<br /><br /> -Pict<br /><br /> -PostExec<br /><br /> -ProfferedCmd<br /><br /> -RouteToDocs<br /><br /> -TextCascadeUseBtn<br /><br /> -TextMenuUseButton<br /><br /> -TextChanges<br /><br /> -TextChangesButton<br /><br /> -TextContextUseButton<br /><br /> -TextMenuCtrlUseMenu<br /><br /> -TextMenuUseButton<br /><br /> -TextOnly.|  
|[Strings, element](../extensibility/strings-element.md)|Wymagana. Element podrzędny [ButtonText, Element](../extensibility/buttontext-element.md) musi być zdefiniowany.|  
|Adnotacja|Opcjonalny komentarz.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Buttons, element](../extensibility/buttons-element.md)|Grupuje elementy przycisku.|  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano przycisku w pliku vsct.  
   
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

## <a name="see-also"></a>Zobacz też  
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

