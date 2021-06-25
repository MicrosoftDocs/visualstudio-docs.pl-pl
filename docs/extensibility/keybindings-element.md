---
title: KeyBindings, element | Microsoft Docs
description: Element KeyBindings grupuje elementy KeyBinding i inne grupowania KeyBindings. Ten artykuł zawiera przykład.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- KeyBindings
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBindings element (VSCT XML schema)
ms.assetid: 26a15d5c-ddea-4977-af7f-d795ff09c7ad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 128b28ff77515ac4b567ecdb8f536851da4d33ce
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903375"
---
# <a name="keybindings-element"></a>KeyBindings, element
Element KeyBindings grupuje elementy KeyBinding i inne grupowania KeyBindings.

## <a name="syntax"></a>Składnia

```xml
<KeyBindings>
  <KeyBinding>... </KeyBinding>
  <KeyBinding>... </KeyBinding>
</KeyBindings>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|Warunek|Opcjonalny. Zobacz [Atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[KeyBinding, element](../extensibility/keybinding-element.md)|Określa skróty klawiaturowe dla poleceń.|
|[Keybindings](../extensibility/keybindings-element.md)|Grupuje elementy KeyBinding i inne grupowania keybindings.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[CommandTable, element](../extensibility/commandtable-element.md)|Definiuje wszystkie elementy, które reprezentują polecenia.|

## <a name="example"></a>Przykład

```xml
<KeyBindings>
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"
    editor="guidWidgetEditor" key1="VK_F5"/>
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>
</KeyBindings>
```

## <a name="see-also"></a>Zobacz także
- [KeyBinding, element](../extensibility/keybinding-element.md)
- [Visual Studio plików tabeli poleceń (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
