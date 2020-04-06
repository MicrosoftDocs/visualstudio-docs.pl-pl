---
title: Atrybuty warunkowe schematu VSCT XML | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f2b1fb3ee1b2cd396f25ec5591a585f8d87648d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697947"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Atrybuty warunkowe schematu XML VSCT
Atrybuty warunkowe można zastosować do wszystkich list i elementów. Operatory logiczne i wyrażenia rozszerzające symbol oceniają wartość true lub false. Jeśli true, skojarzonej listy lub elementu jest uwzględniony w wynikowywyjąć.

 Można przetestować rozszerzenia tokenu względem innych rozszerzeń tokenu lub stałych. Funkcja `Defined()` sprawdza, czy określona nazwa została zdefiniowana, nawet jeśli nie ma wartości.

 Gdy Condition atrybut jest stosowany do listy, warunek jest stosowany do każdego elementu podrzędnego na liście. Jeśli element podrzędny sam zawiera Condition atrybut, a następnie jego warunek jest łączony z wyrażeniem nadrzędnym przez operację AND.

 Wartości 1, "1" i "true" są oceniane jako prawdziwe, a 0, "0" i "false" są oceniane jako false.

## <a name="operators"></a>Operatory
 Następujące operatory służy do oceny wyrażeń warunkowych.

|Operator|Definicja|
|--------------|----------------|
|(,)|Grupowanie|
|!|Logiczne NOT|
|\<, >, \<=, >=, ==, !=|Relacja i równość|
|i|Wartość logiczna|
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
- [Tabela poleceń programu Visual Studio (. Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
