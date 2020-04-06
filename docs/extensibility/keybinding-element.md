---
title: Element wiązania klawiszy | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b458e70a9a85c11707c50da2e16e3aa73f51bc12
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703142"
---
# <a name="keybinding-element"></a>Element wiązania klawiszy
Element KeyBinding określa skróty klawiaturowe dla poleceń.

 Polecenia mogą mieć skojarzone z nimi powiązania pojedyncze i podwójne klucze. Przykładem powiązania pojedynczego klucza jest **Ctrl**+**S** dla polecenia **Zapisz.** Podwójne powiązania klawiszy wymagają dwóch kolejnych kombinacji klawiszy, aby wyzwolić polecenie. Przykładem wiązania z dwoma klawiszami jest <strong>Ctrl*+</strong>K<strong>,</strong>Ctrl<strong>+</strong>K**, aby ustawić zakładkę.

## <a name="syntax"></a>Składnia

```
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|Identyfikator GUID|Wymagany.|
|id|Wymagany.|
|edytor|Wymagany. Identyfikator GUID edytora wskazuje kontekst edycji, dla którego ten skrót klawiaturowy będzie aktywny. Wartość globalnego zakresu wiązania to "guidVSStd97".|
|key1|Wymagany. Prawidłowe wartości obejmują wszystkie typowalne wartości alfanumeryczne, a także dwucyfrowe wartości szesnastkowe poprzedzone 0x i [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|
|mod1|Element opcjonalny. Dowolna kombinacja **klawiszy Ctrl**, **Alt**i **Shift** oddzielona spacją.|
|key2|Element opcjonalny. Prawidłowe wartości obejmują wszystkie typowalne wartości alfanumeryczne, a także dwucyfrowe wartości szesnastkowe poprzedzone 0x i [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|
|mod2|Element opcjonalny. Dowolna kombinacja **klawiszy Ctrl**, **Alt**i **Shift** oddzielona spacją.|
|emulator|Element opcjonalny.|
|Warunek|Element opcjonalny. Zobacz [Atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|Nadrzędny||
|Adnotacja||

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element KeyBindings](../extensibility/keybindings-element.md)|Grupy KeyBinding elementów i innych grup keybindings.|

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
- [Element KeyBindings](../extensibility/keybindings-element.md)
- [Pliki tabeli poleceń programu Visual Studio (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
