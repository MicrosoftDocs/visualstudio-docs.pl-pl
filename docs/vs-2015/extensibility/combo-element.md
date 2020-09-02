---
title: Element kombi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: daa89266d653743a743f42e5f0b8e11c954adc1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184413"
---
# <a name="combo-element"></a>Combo, element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Definiuje polecenia, które pojawiają się w polu kombi. Istnieją cztery rodzaje pól kombi w następujący sposób: DropDownCombo, DynamicCombo, IndexCombo i MRUCombo.  
  
## <a name="syntax"></a>Składnia  
  
```  
<combo guid="guidMyCommandSet" id="MyCommand" defaultWidth="20" idCommandList="MyCommandListID" priority="0x102" type="DropDownCombo">  
  <Parent>... </Parent  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</combo>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|guid|Wymagany. Identyfikator GUID identyfikatora polecenia GUID/ID.|  
|identyfikator|Wymagany. Identyfikator identyfikatora polecenia GUID/ID.|  
|defaultWidth|Wymagany. Liczba całkowita, która określa szerokość pikseli dla pola kombi.|  
|idCommandList|Wymagany. Identyfikator, który jest wysyłany do aktywnego elementu docelowego polecenie w celu pobrania listy elementów do wyświetlenia w polu kombi. Identyfikator będzie mieć ten sam zakres identyfikatorów GUID co formant.|  
|priority|Opcjonalny. Wartość liczbowa, która określa priorytet.|  
|typ|Opcjonalny. Wartość wyliczana, która określa typ przycisku.<br /><br /> Jeśli nie zostanie określona, używa przycisku.<br /><br /> DropDownCombo<br /> Pakietu VSPackage jest odpowiedzialny za wypełnienie zawartości dla tego pola kombi. Użytkownik nie może wpisać niczego w polu tekstowym tego listy rozwijanej.<br /><br /> DynamicCombo<br /> Pakietu VSPackage jest odpowiedzialny za wypełnienie zawartości tego pola kombi. Użytkownik może edytować to pole kombi, a także wybrać elementy.<br /><br /> IndexCombo<br /> Taka sama jak DynamicCombo, z tą różnicą, że wywołuje indeks elementu, a nie jego tekst.<br /><br /> MRUCombo<br /> Wypełnione przez zintegrowane środowisko programistyczne (IDE) w imieniu pakietu VSPackage.  Użytkownik może edytować w tym polu kombi. Środowisko IDE zapamiętuje do ostatnich 16 wpisów na pole kombi.<br /><br /> Gdy użytkownik wybierze coś w polu kombi lub wprowadzi coś nowego, środowisko IDE powiadamia odpowiednie pakietu VSPackage.|  
|Warunek|Opcjonalny. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Nadrzędny|Opcjonalny. Element nadrzędny przycisku.|  
|CommandFlag|Wymagany. Zobacz [element flagi polecenia](../extensibility/command-flag-element.md). Prawidłowe wartości CommandFlag dla przycisku są następujące.<br /><br /> -CaseSensitive<br /><br /> - CommandWellOnly<br /><br /> - DefaultDisabled<br /><br /> - DefaultInvisible<br /><br /> - DynamicVisibility<br /><br /> -KlawiszeFiltru<br /><br /> - IconAndText<br /><br /> -Noautouzupełnianie<br /><br /> - NoButtonCustomize<br /><br /> -Nodostosowywanie<br /><br /> - NoKeyCustomize<br /><br /> - StretchHorizontally|  
|Ciągi|Wymagany. Zobacz [element Strings](../extensibility/strings-element.md). Element podrzędny ButtonText musi być zdefiniowany.|  
|Adnotacja|Opcjonalny komentarz.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Commands, element](../extensibility/commands-element.md)|Reprezentuje kolekcję poleceń na pasku narzędzi pakietu VSPackage.|  
  
## <a name="example"></a>Przykład  
  
```  
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"  
  defaultWidth="100" idCommandList="cmdidGetInsertOptionsList">  
  <CommandFlag>DynamicVisibility</CommandFlag>  
  <Strings>  
    <ButtonText>Select Insert Options</ButtonText>  
  </Strings>  
</Combo>  
  
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"  
  priority="0x0500" type="DropDownCombo" defaultWidth="100"  
  idCommandList="cmdidGetInsertOptionsList">  
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">  
  <CommandFlag>DynamicVisibility</CommandFlag>  
  <Strings>  
    <ButtonText>Select Insert Options</ButtonText>  
  </Strings>  
</Combo>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
