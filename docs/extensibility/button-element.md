---
title: Przycisk Element | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Buttons element (VSCT XML schema)
- VSCT XML schema elements, Buttons
ms.assetid: 96dccf51-2b00-4700-9d28-924b34c21ecd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9d4bfa27ac2a71e53418ac1be1f9a377f06aede7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53870180"
---
# <a name="button-element"></a>Button, element
Definiuje element, który użytkownik może interakcyjnie przeprowadzić. Przyciski może być różnego rodzaju: Przycisk, przycisk menu i SplitDropDown.  
  
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
|priority|Opcjonalna. Wartość liczbowa określająca priorytet.|  
|— typ|Opcjonalna. Wartość wyliczana, który określa typ przycisku.<br /><br /> Jeśli nie zostanie podana, używa przycisku.<br /><br /> Przycisk<br /> Standardowe polecenie, które pojawia się na paskach narzędzi (zwykle jako ikony przycisku), menu i menu kontekstowego.<br /><br /> Przycisk menu<br /> Element menu, który nie jest wykonywane polecenie, ale daje innym menu.<br /><br /> SplitDropDown<br /> Formanty, takie jak przyciski Cofnij i ponów na standardowym pasku narzędzi, które są dostępne w programie Microsoft Word.|  
|Warunek|Opcjonalna. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Element nadrzędny](../extensibility/parent-element.md)|Opcjonalna. Elementu nadrzędnego przycisku.|  
|[Icon, element](../extensibility/icon-element.md)|Opcjonalna. Ikona skojarzone z nim.|  
|[Command flag, element](../extensibility/command-flag-element.md)|Wymagana. Prawidłowe wartości CommandFlag dla przycisku, to w następujący sposób.<br /><br /> -AllowParams<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DontCache<br /><br /> -DynamicItemStart<br /><br /> -DynamicVisibility<br /><br /> -FixMenuController<br /><br /> -IconAndText<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -NoShowOnMenuController<br /><br /> -Pict<br /><br /> -PostExec<br /><br /> -ProfferedCmd<br /><br /> -RouteToDocs<br /><br /> -TextCascadeUseBtn<br /><br /> -TextMenuUseButton<br /><br /> -TextChanges<br /><br /> -TextChangesButton<br /><br /> -TextContextUseButton<br /><br /> -TextMenuCtrlUseMenu<br /><br /> -TextMenuUseButton<br /><br /> -TextOnly.|  
|[Strings, element](../extensibility/strings-element.md)|Wymagana. Element podrzędny [ButtonText, element](../extensibility/buttontext-element.md) musi być zdefiniowany.|  
|Adnotacja|Opcjonalny komentarz.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Buttons, element](../extensibility/buttons-element.md)|Grupuje elementy przycisku.|  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano przycisku w *vsct* pliku.  

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
 
## <a name="see-also"></a>Zobacz także  
 [Pliki tabeli (vsct) polecenia programu Visual Studio](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)