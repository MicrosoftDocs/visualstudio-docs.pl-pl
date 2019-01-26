---
title: KeyBinding, Element | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4706114f87e18ce97789e41098e13cf38917d533
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54933042"
---
# <a name="keybinding-element"></a>KeyBinding, element
KeyBinding, element określa skróty klawiaturowe dla poleceń.  
  
 Polecenia może mieć zarówno pojedynczych, jak i podwójną klawiszy skojarzonych z nimi. Na przykład jednego powiązanie klawiszy **Ctrl**+**S** dla **Zapisz** polecenia. Podwójna klawiszy wymaga dwóch kolejnych kombinacje klawiszy, aby wyzwolić poleceniu. Na przykład dwa powiązanie klawiszy <strong>Ctrl*+</strong>K<strong>,</strong>Ctrl<strong>+</strong>K** Aby ustawić zakładki.  
  
## <a name="syntax"></a>Składnia  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|Identyfikator GUID|Wymagana.|  
|identyfikator|Wymagana.|  
|edytor|Wymagana. Identyfikator GUID edytora wskazuje Kontekst edycyjny, dla którego ten skrót klawiaturowy zostanie uaktywniona. Wartość zakresu globalnego powiązania jest "guidVSStd97".|  
|key1|Wymagana. Prawidłowe wartości to wszystkie typable znaków alfanumerycznych, a także dwucyfrowych wartości szesnastkowych, poprzedzony 0 x i [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|  
|mod1|Opcjonalna. Dowolną kombinację **Ctrl**, **Alt**, i **Shift** rozdzielone spacjami.|  
|key2|Opcjonalna. Prawidłowe wartości to wszystkie typable znaków alfanumerycznych, a także dwucyfrowych wartości szesnastkowych, poprzedzony 0 x i [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|  
|mod2|Opcjonalna. Dowolną kombinację **Ctrl**, **Alt**, i **Shift** rozdzielone spacjami.|  
|Emulator|Opcjonalna.|  
|Warunek|Opcjonalna. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|Nadrzędny||  
|Adnotacja||  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[KeyBindings, element](../extensibility/keybindings-element.md)|Grupuje elementy powiązanie klawiszy i inne grupy powiązań klawiszy.|  
  
## <a name="example"></a>Przykład  
  
```  
<KeyBindings>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"   
    editor="guidWidgetEditor" key1="VK_F5"/>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"   
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>  
</KeyBindings>  
```  
  
## <a name="see-also"></a>Zobacz także  
 [KeyBindings, element](../extensibility/keybindings-element.md)   
 [Pliki tabeli (vsct) polecenia programu Visual Studio](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
