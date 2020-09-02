---
title: String — element | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db44db8926b523665a21c00b710dcee55749ab89
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699721"
---
# <a name="strings-element"></a>Strings, element
Element Strings musi zawierać co najmniej element podrzędny **ButtonText** . Wszystkie inne elementy podrzędne są opcjonalne. Nieprawidłowe znaki XML, takie jak "&" i "<", muszą być kodowane jako jednostki (" &amp; " i " &lt; " itd.).

 Znak "i" w ciągu tekstowym określa skrót klawiaturowy dla polecenia.

## <a name="syntax"></a>Składnia

```
<Strings>
  <ButtonText>... </ButtonText>
  <CommandName>... </CommandName>
</Strings>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|language|Opcjonalny. Language = ".".|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|ButtonText|To pole i pięć następujących pól tekstowych w definicji polecenia umożliwiają określenie tekstu wyświetlanego w różnych menu. Domyślnie `ButtonText` pole jest wyświetlane w obszarze Kontrolery menu. `ButtonText`Pole jest również domyślnie, jeśli inne pola tekstowe są puste. `ButtonText`Pole nie może być puste, nawet jeśli określono inne pola tekstowe.|
|ToolTipText|`ToolTipText`Pole określa tekst, który pojawia się w etykietce narzędzia dla elementu menu.<br /><br /> Jeśli `ToolTipText` pole jest puste, `ButtonText` pole jest używane.|
|MenuText|`MenuText`Pole określa tekst, który jest wyświetlany dla polecenia, jeśli znajduje się w menu głównym, na pasku narzędzi w menu skrótów lub w podmenu. Jeśli `MenuText` pole jest puste, zintegrowane środowisko programistyczne (IDE) używa tego `ButtonText` pola. `MenuText`Pola można także użyć do lokalizacji.<br /><br /> W przypadku menu skrótów `MenuText` pole jest nazwa, która jest wyświetlana na pasku narzędzi menu skrótów, co umożliwia dostosowywanie menu skrótów w środowisku IDE. W związku z tym należy określić, jak nazywa się menu skrótów; na przykład użyj "menu skrótów pakietu widżetu" zamiast "skrót".<br /><br /> Jeśli `MenuText` pole nie jest określone, `ButtonText` pole jest używane.|
|CommandName|`CommandName`Pole określa tekst, który pojawia się w kategorii klawiatura na karcie **polecenia** okna dialogowego **Dostosowywanie** (dostępne po kliknięciu pozycji **Dostosuj** w menu **Narzędzia** ).|
|CanonicalName|`CanonicalName`Pole w języku angielskim określa nazwę polecenia w tekocie w języku angielskim, którą można wprowadzić w oknie **polecenia** , aby wykonać element menu. IDE przykreśla wszystkie znaki, które nie są literami, cyframi, podkreśleniami lub osadzonymi kropkami. Ten tekst jest następnie łączony do pola, `ButtonText` Aby zdefiniować polecenie. Na przykład **Nowy projekt** w menu **plik** jest poleceniem File. NewProject.<br /><br /> Jeśli pole w języku angielskim `CanonicalName` nie jest określone, IDE używa `ButtonText` pola i obejmuje wszystkie z wyjątkiem litery, cyfry, podkreślenia i kropki osadzone. Na przykład tekst przycisku "&Definiuj polecenia..." zostanie DefineCommands, gdzie znak handlowego "i", spacja i wielokropek są usuwane.<br /><br /> Jeśli `TextChanges` flaga jest określona, a tekst polecenia zostanie zmieniony, odpowiednie polecenie rozpoznawane przez okno **polecenia** nie zmienia się; pozostaje to kanoniczna postać pól oryginalnych `ButtonText` lub w języku angielskim `CanonicalName` .|
|LocCanonicalName|`LocCanonicalName`Pole zachowuje się identycznie z polem w języku angielskim, `CanonicalName` ale umożliwia określenie zlokalizowanego tekstu polecenia. Można określić zarówno pola kanoniczne. Ze względu na to, że IDE analizuje tylko tekst wprowadzony w oknie **polecenia** i kojarzy je z poleceniem, zarówno tekst w języku angielskim, jak i innym niż angielski można skojarzyć z tym samym poleceniem.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Button, element](../extensibility/button-element.md)|Definiuje element, z którym użytkownik może korzystać.|
|[Menu, element](../extensibility/menu-element.md)|Definiuje pojedynczy element menu.|
|[Combo, element](../extensibility/combo-element.md)|Definiuje polecenia, które pojawiają się w polu kombi.|

## <a name="see-also"></a>Zobacz też
- [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
