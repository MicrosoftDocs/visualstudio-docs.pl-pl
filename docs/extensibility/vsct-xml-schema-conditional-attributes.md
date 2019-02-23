---
title: Atrybuty warunkowe schematu VSCT XML | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 73e48cfb0a30ca71592879c8276ef1be76cb973f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56680299"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Atrybuty warunkowe schematu VSCT XML
Atrybuty warunkowe można zastosować do wszystkich list i elementów. Operatory logiczne i wyrażenia rozszerzenia symboli zwrócić wartość PRAWDA lub FAŁSZ. W przypadku opcji true skojarzona lista lub element znajduje się w dane wyjściowe.

 Możesz przetestować rozszerzenia tokenu względem innych rozszerzenia tokenu lub stałe. Funkcja `Defined()` sprawdza, czy została zdefiniowana określonej nazwie, nawet wtedy, gdy go nie ma wartości.

 Gdy warunek jest stosowany do listy, warunek jest stosowany do każdego elementu podrzędnego, na liście. Jeśli nie zawiera elementu podrzędnego samego zawiera atrybut warunku, jego stan jest łączony w za pomocą wyrażenia nadrzędnego przez operację i.

 Wartości 1, "1" i "prawda", są oceniane jako PRAWDA, a 0, "0" i "false", które są obliczane jako wartość false.

## <a name="operators"></a>Operatory
 Użyj następujących operatorów można obliczyć wartości wyrażenia warunkowe.

|Operator|Definicja|
|--------------|----------------|
|(,)|Grupowanie|
|!|Logiczne NOT|
|\<, >, \<=, >=, ==, !=|Relacyjne i równości|
|and|Boolean|
|lub|Boolean|

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

## <a name="see-also"></a>Zobacz także
- [Tabeli poleceń w usłudze Visual Studio (. Pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)