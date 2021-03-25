---
title: Atrybuty warunkowe schematu XML VSCT | Microsoft Docs
description: Dowiedz się, jak zastosować atrybuty warunkowe do list i elementów schematu XML VSCT. Atrybuty mają wartość PRAWDA lub FAŁSZ, kontrolując wynikowe dane wyjściowe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5bc1bcb9d80474b467e90de6262e797087589065
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062359"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Atrybuty warunkowe schematu XML VSCT
Można zastosować atrybuty warunkowe do wszystkich list i elementów. Operatory logiczne i wyrażenia rozszerzania symboli mają wartość PRAWDA lub FAŁSZ. W przypadku wartości true skojarzona lista lub element zostanie uwzględniony w wynikowym wyjściu.

 Można testować rozszerzenia tokenów względem innych rozszerzeń lub stałych tokenów. Funkcja `Defined()` sprawdza, czy określona nazwa została zdefiniowana, nawet jeśli nie ma wartości.

 Gdy atrybut Condition jest stosowany do listy, warunek jest stosowany do każdego elementu podrzędnego na liście. Jeśli element podrzędny zawiera atrybut Condition, jego warunek jest połączony z wyrażeniem nadrzędnym przez operację i.

 Wartości 1, "1" i "true" są oceniane jako prawdziwe, a 0, "0" i "false" są oceniane jako FAŁSZ.

## <a name="operators"></a>Operatory
 Aby obliczyć wyrażenia warunkowe, użyj następujących operatorów.

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
- [Tabela poleceń programu Visual Studio (. Vsct) — pliki](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
