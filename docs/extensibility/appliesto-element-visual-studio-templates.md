---
title: Element AppliesTo (szablony programu Visual Studio) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 8fb1334b-d78c-405f-98b4-786e9f6b58d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 39b5ee1e3cad0b4d8ddbe0fc2dfa1c2d478ec063
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740074"
---
# <a name="appliesto-element-visual-studio-templates"></a>Element AppliesTo (szablony programu Visual Studio)

Określa wyrażenie opcjonalne, aby dopasować jedną <xref:Microsoft.VisualStudio.Shell.Interop.VsProjectCapabilityExpressionMatcher>lub więcej możliwości (patrz ). Możliwości są udostępniane przez typy projektów za pośrednictwem hierarchii jako właściwość [__VSHPROPID5. VSHPROPID_ProjectCapabilities](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID5.VSHPROPID_ProjectCapabilities>). W ten sposób szablon może być współużytkowany przez wiele typów projektów, które mają wspólne odnośne funkcje.

Ten element jest opcjonalny. Plik szablonu może zawierać maksymalnie jedno jego wystąpienie. Element umożliwia jedynie potwierdzenie zgodności szablonu elementu z funkcjami aktualnie zaznaczonego aktywnego projektu. Nie można za jego pomocą ustawić niezgodności szablonu. Jeśli `AppliesTo` jest nieobecny lub wyrażenie nie `TemplateID` zobowiązuje się pomyślnie, to lub `TemplateGroupID` jest używany do tego, aby szablon miał zastosowanie, tak jak w przypadku poprzednich wersji produktu.

Wprowadzono w programie Visual Studio 2013 Aktualizacja 2. Aby odwołać się do poprawnej wersji, zobacz [Odwoływanie się do zestawów dostarczonych w aktualizacji SDK programu Visual Studio 2013 2](/previous-versions/dn632168(v=vs.120)).

```xml
<VSTemplate>
   <TemplateData>
      <AppliesTo>
```

## <a name="syntax"></a>Składnia

```xml
<AppliesTo>Capability1</AppliesTo>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

Brak.

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Nadawanie szablonowi kategorii.|

## <a name="text-value"></a>Wartość tekstowa

Wartość tekstowa jest wymagana. Tekst określa funkcje projektu.

Prawidłową składnię wyrażeń definiuje się następująco:

- Wyrażenie możliwości, takie jak "(VisualC &#124; CSharp) + (MSTest &#124; NUnit)".

- "&#124;" jest operatorem OR.

- Znaki "&" i "+" są zarówno operatorami AND.

- Znak „!” jest operatorem NIE.

- Nawiasy wymuszają kolejność pierwszeństwa w ocenie.

- Wyrażenie o wartości null lub puste jest interpretowane jako zgodność.

- Możliwości projektu mogą być dowolnym znakiem z wyjątkiem tych zastrzeżonych znaków:\\"'':;,+-*/{}!~&#124;&%$@^()= []<>? \t\b\n\r

## <a name="example"></a>Przykład

W przykładzie poniżej widać trzy różne szablony. `Template1`ma zastosowanie do wszystkich typów projektu Języka C# lub `WindowsAppContainer` innego typu projektu, który obsługuje możliwości. `Template2`dotyczy wszystkich projektów C# dowolnego rodzaju. `Template3`dotyczy projektów języka C#, `WindowsAppContainer` które nie są projektami.

```xml
<!--  Template 1 -->
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <AppliesTo>CSharp | WindowsAppContainer</AppliesTo>
    </TemplateData>
</VSTemplate>

<!--  Template 2 -->
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <AppliesTo>CSharp</AppliesTo>
    </TemplateData>
</VSTemplate>

<!--  Template 1 -->
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <AppliesTo>CSharp_Class + (!WindowsAppContainer)</AppliesTo>
    </TemplateData>
</VSTemplate>
```

## <a name="see-also"></a>Zobacz też

- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
