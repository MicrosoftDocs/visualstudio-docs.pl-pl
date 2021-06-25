---
title: Atrybuty warunkowe schematu XML VSCT | Microsoft Docs
description: Dowiedz się, jak stosować atrybuty warunkowe do list i elementów schematu XML VSCT. Atrybuty mają wartość true lub false, kontrolując wynikowe dane wyjściowe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e91207016ed6e1baab80b323680d10a40e0331d8
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905257"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Atrybuty warunkowe schematu XML VSCT
Atrybuty warunkowe można stosować do wszystkich list i elementów. Operatory logiczne i wyrażenia rozszerzenia symboli mają wartość true lub false. W przypadku wartości true skojarzona lista lub element są uwzględniane w wynikowych danych wyjściowych.

 Rozszerzenia tokenów można testować względem innych rozszerzeń tokenów lub stałych. Funkcja `Defined()` sprawdza, czy określona nazwa została zdefiniowana, nawet jeśli nie ma żadnej wartości.

 Gdy atrybut Warunek jest stosowany do listy, warunek jest stosowany do każdego elementu podrzędnego na liście. Jeśli element podrzędny sam zawiera atrybut Warunek, jego warunek jest połączony z wyrażeniem nadrzędnym przez operację AND.

 Wartości 1, "1" i "true" są oceniane jako true, a wartości 0, "0" i "false" są oceniane jako false.

## <a name="operators"></a>Operatory
 Aby ocenić wyrażenia warunkowe, użyj następujących operatorów.

|Operator|Definicja|
|--------------|----------------|
|(,)|Grupowanie|
|!|Logiczne NOT|
|\<, >, \<=, >=, ==, !=|Relacyjne i równość|
|oraz|Wartość logiczna|
|lub|Wartość logiczna|

## <a name="examples"></a>Przykłady

```xml
<Menu Condition="Defined(DEBUG)" ...
</Menu>

<Menu Condition="%(SKU_MODE) = 'Demo'" ...
</Menu>

<Menus Condition="Defined(DEBUG)">
    <Menu ...
    </Menu>
</Menus>

<Menus Condition="Defined(DEMO_SKU)">
    <Menus Condition="!Defined(DEBUG)">
        <Menu ...
        </Menu>
    </Menus>

    <Menu ...
    </Menu>
</Menus>

<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))
and !Defined(DEBUG)">
    <Menu ...
    </Menu>
</Menus>
```

## <a name="see-also"></a>Zobacz też
- [Visual Studio tabeli poleceń (. Pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
