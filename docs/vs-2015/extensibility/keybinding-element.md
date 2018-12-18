---
title: KeyBinding, Element | Dokumentacja firmy Microsoft
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
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 32dafc1b16282657db40531e34d1eccb02841481
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51780935"
---
# <a name="keybinding-element"></a>KeyBinding, element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

KeyBinding, element określa skróty klawiaturowe dla poleceń.  
  
 Polecenia może mieć zarówno pojedynczych, jak i podwójną klawiszy skojarzonych z nimi. Przykładem pojedynczego powiązania kluczy jest CTRL + S, aby uzyskać **Zapisz** polecenia. Podwójna klawiszy wymaga dwóch kolejnych kombinacje klawiszy, aby wyzwolić poleceniu. Przykład podwójnego powiązanie klucza jest CTRL + K, CTRL + K, aby ustawić zakładki.  
  
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
|klucz1|Wymagana. Prawidłowe wartości to wszystkie typable znaków alfanumerycznych, a także dwucyfrowych wartości szesnastkowych, poprzedzony 0 x i VK_constants.|  
|mod1|Opcjonalna. Dowolna kombinacja CTRL, ALT i SHIFT, rozdzielone spacjami.|  
|klucz2|Opcjonalna. Prawidłowe wartości to wszystkie typable znaków alfanumerycznych, a także dwucyfrowych wartości szesnastkowych, poprzedzony 0 x i VK_constants.|  
|mod2|Opcjonalna. Dowolna kombinacja CTRL, ALT i SHIFT, rozdzielone spacjami.|  
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
  
## <a name="see-also"></a>Zobacz też  
 [KeyBindings, Element](../extensibility/keybindings-element.md)   
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

