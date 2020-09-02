---
title: '&lt;Schedules — &gt; element (program inicjujący) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Schedules> element [bootstrapper]
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2f6e4ae90dbd36dab4f4df7f72d5ecf57ee04b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62927335"
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;Schedules — &gt; element (program inicjujący)
`Schedules`Element zawiera `Schedule` elementy, które definiują określone czasy, w których polecenia zdefiniowane przez `Command` element powinny być uruchamiane.

## <a name="syntax"></a>Składnia

```xml
<Schedules>
    <Schedule
        Name
    >
        <BuildList />
        <BeforePackage />
        <AfterPackage />
    </Schedule>
</Schedules>
```

## <a name="elements-and-attributes"></a>Elementy i atrybuty
 `Schedules`Element jest elementem podrzędnym `Product` elementu. Każdy `Product` element może mieć co najwyżej jeden `Schedules` element. `Schedules`Element nie ma żadnych atrybutów.

## <a name="schedule"></a>Zaplanuj
 `Schedule`Element jest elementem podrzędnym `Schedules` elementu. `Schedules`Element musi zawierać co najmniej jeden `Schedule` element.

 `Schedule` ma następujący atrybut.

|Atrybut|Opis|
|---------------|-----------------|
|`Name`|Wymagany. Nazwa elementu harmonogramu. Odpowiada `ScheduleName` właściwości `Command` elementu. Gdy `Command` odwołuje się do określonego harmonogramu, zostanie on wykonany tylko w czasie wskazywanym przez ten `Schedule` element. Harmonogramy mogą również być skojarzone z `FailIf` `BypassIf` elementami i, które ograniczają te testy warunkowe do wykonania zgodnie z określonym harmonogramem. Aby uzyskać więcej informacji, zobacz [ \<Commands> element](../deployment/commands-element-bootstrapper.md).|

 Dany `Schedule` element może mieć dokładnie jeden z następujących elementów podrzędnych.

## <a name="buildlist"></a>BuildList
 `BuildList`Element instruuje Instalatora, aby wykonał polecenie natychmiast po uruchomieniu aplikacji inicjującej.

## <a name="beforepackage"></a>BeforePackage
 `BeforePackage`Element instruuje Instalatora, aby wykonał polecenie przed zainstalowaniem określonego pakietu.

## <a name="afterpackage"></a>AfterPackage
 `AfterPackage`Element instruuje Instalatora, aby wykonał polecenie po zainstalowaniu określonego pakietu.

## <a name="see-also"></a>Zobacz też
- [\<Product> postaci](../deployment/product-element-bootstrapper.md)
- [Dokumentacja schematu produktu i pakietu](../deployment/product-and-package-schema-reference.md)