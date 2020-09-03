---
title: Powiązanie klawiszy — element | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 75d96098e8444aac9a4fc6f895099435b54f640b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180327"
---
# <a name="keybinding-element"></a>KeyBinding, element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Element powiązanie klawiszy określa skróty klawiaturowe dla poleceń.  
  
 Polecenia mogą zawierać skojarzone z nimi powiązania z pojedynczym i podwójnym kluczem. Przykładem pojedynczego powiązania klucza jest CTRL + S dla polecenia **Zapisz** . Podwójne powiązania klawiszy wymagają dwóch kolejnych kombinacji klawiszy, aby wyzwolić polecenie. Przykładem podwójnego powiązania klawiszy jest CTRL + K, CTRL + K, aby ustawić zakładkę.  
  
## <a name="syntax"></a>Składnia  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|guid|Wymagany.|  
|identyfikator|Wymagany.|  
|edytor|Wymagany. Identyfikator GUID edytora wskazuje kontekst edycji, dla którego będzie aktywny ten skrót klawiaturowy. Globalna wartość zakresu powiązania to "guidVSStd97".|  
|key1|Wymagany. Prawidłowe wartości to wszystkie typable alfanumeryczne, a także dwucyfrowe wartości szesnastkowe poprzedzone 0x i VK_constants.|  
|mod1|Opcjonalny. Dowolna kombinacja kombinacji klawiszy CTRL, ALT i SHIFT oddzielona spacją.|  
|key2|Opcjonalny. Prawidłowe wartości to wszystkie typable alfanumeryczne, a także dwucyfrowe wartości szesnastkowe poprzedzone 0x i VK_constants.|  
|mod2|Opcjonalny. Dowolna kombinacja kombinacji klawiszy CTRL, ALT i SHIFT oddzielona spacją.|  
|emulator|Opcjonalny.|  
|Warunek|Opcjonalny. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Nadrzędny||  
|Adnotacja||  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[KeyBindings, element](../extensibility/keybindings-element.md)|Grupuje elementy powiązanie klawiszy i inne grupowania powiązań klawiszy.|  
  
## <a name="example"></a>Przykład  
  
```  
<KeyBindings>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"   
    editor="guidWidgetEditor" key1="VK_F5"/>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"   
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>  
</KeyBindings>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Element powiązań klawiszy](../extensibility/keybindings-element.md)   
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
