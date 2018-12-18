---
title: Combo, Element | Dokumentacja firmy Microsoft
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
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0ab350133813f32b87570ea17df50060f93bc300
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788939"
---
# <a name="combo-element"></a>Combo, element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Określa polecenia, które są wyświetlane w polu kombi. Istnieją cztery rodzaje pola kombi w następujący sposób: typu pole kombi, DynamicCombo, IndexCombo i MRUCombo.  
  
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
|Identyfikator GUID|Wymagana. Identyfikator GUID identyfikatora polecenia identyfikator GUID/ID.|  
|identyfikator|Wymagana. Identyfikator GUID/ID identyfikator polecenia.|  
|defaultWidth|Wymagana. Liczba całkowita, która określa szerokość pikseli dla pola kombi.|  
|idCommandList|Wymagana. Identyfikator, którego są wysyłane do obiektu docelowego active polecenia narzędzia do pobrania listy elementów, które mają być wyświetlane w polu kombi. Identyfikator jest w tym samym zakresie identyfikatora GUID jako formant.|  
|priorytet|Opcjonalna. Wartość liczbowa określająca priorytet.|  
|— typ|Opcjonalna. Wartość wyliczana, który określa typ przycisku.<br /><br /> Jeśli nie zostanie podana, używa przycisku.<br /><br /> Typu pole kombi<br /> Pakietu VSPackage jest odpowiedzialny za wypełnianie zawartość dla tego pola kombi. Użytkownik nie może wpisać cokolwiek w polu tekstowym w tym listy rozwijanej.<br /><br /> DynamicCombo<br /> Pakietu VSPackage jest odpowiedzialny za wypełnianie zawartość tego pola kombi. Użytkownik może edytować ten kombi i również wybrać elementy w nim.<br /><br /> IndexCombo<br /> Taka sama jak DynamicCombo, z wyjątkiem że zgłasza indeks elementu, a nie jego tekstu.<br /><br /> MRUCombo<br /> Wypełnione przez zintegrowanego środowiska programistycznego (IDE) w imieniu pakietu VSPackage.  Użytkownik może edytować w tym polu kombi. IDE zapamiętuje maksymalnie 16 ostatnich wpisów na pola kombi.<br /><br /> Gdy użytkownik wybierze element w polu kombi lub wprowadza coś nowego, IDE powiadamia odpowiednie pakietu VSPackage.|  
|Warunek|Opcjonalna. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Nadrzędny|Opcjonalna. Elementu nadrzędnego przycisku.|  
|CommandFlag|Wymagana. Zobacz [Command Flag, Element](../extensibility/command-flag-element.md). Prawidłowe wartości CommandFlag dla przycisku, to w następujący sposób.<br /><br /> -CaseSensitive<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DynamicVisibility<br /><br /> -KlawiszeFiltru<br /><br /> -IconAndText<br /><br /> -NoAutoComplete<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -StretchHorizontally|  
|Ciągi|Wymagana. Zobacz [ciągi elementu](../extensibility/strings-element.md). ButtonText, element podrzędny musi być zdefiniowany.|  
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

