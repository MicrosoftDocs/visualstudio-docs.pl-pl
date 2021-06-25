---
title: KeyBinding, element | Microsoft Docs
description: Element KeyBinding określa skróty klawiaturowe dla poleceń. Z poleceniami mogą być skojarzone zarówno pojedyncze, jak i podwójne powiązania kluczy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6afd0a9658f088b66f2c18c632ffcd7b9a09f555
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898864"
---
# <a name="keybinding-element"></a>KeyBinding, element
Element KeyBinding określa skróty klawiaturowe dla poleceń.

 Z poleceniami mogą być skojarzone zarówno pojedyncze, jak i podwójne powiązania kluczy. Przykładem powiązania pojedynczego klawisza jest **Ctrl** + **S** dla **polecenia Save.** Podwójne powiązania klawiszy wymagają dwóch kolejnych kombinacji klawiszy w celu wyzwolenia polecenia. Przykładem podwójnego powiązania klawiszy jest <strong>Ctrl *+</strong> <strong>K,</strong>Ctrl <strong>+</strong> K**, aby ustawić zakładkę.

## <a name="syntax"></a>Składnia

```
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|guid|Wymagane.|
|identyfikator|Wymagane.|
|edytor|Wymagane. Identyfikator GUID edytora wskazuje kontekst edycji, dla którego ten skrót klawiaturowy będzie aktywny. Wartość zakresu powiązania globalnego to "guidVSStd97".|
|key1|Wymagane. Prawidłowe wartości obejmują wszystkie typowalne wartości alfanumeryczne, a także dwucyfrowe wartości szesnastowe poprzedzone cyframi 0x i [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|
|mod1|Opcjonalny. Dowolna kombinacja **klawiszy Ctrl,** **Alt** i **Shift** oddzielona spacjami.|
|key2|Opcjonalny. Prawidłowe wartości obejmują wszystkie typowalne wartości alfanumeryczne, a także dwucyfrowe wartości szesnastowe poprzedzone cyframi 0x i [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|
|mod2|Opcjonalny. Dowolna kombinacja **klawiszy Ctrl,** **Alt** i **Shift** oddzielona spacjami.|
|emulator|Opcjonalny.|
|Warunek|Opcjonalny. Zobacz [Atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|Nadrzędny||
|Adnotacja||

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[KeyBindings, element](../extensibility/keybindings-element.md)|Grupuje elementy keybinding i inne grupowania keybindings.|

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
- [KeyBindings, element](../extensibility/keybindings-element.md)
- [Visual Studio plików tabeli poleceń (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
