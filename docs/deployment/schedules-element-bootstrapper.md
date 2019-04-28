---
title: '&lt;Harmonogramy&gt; — Element (program inicjujący) | Dokumentacja firmy Microsoft'
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62927335"
---
# <a name="ltschedulesgt-element-bootstrapper"></a>&lt;Harmonogramy&gt; — element (program inicjujący)
`Schedules` Element zawiera `Schedule` elementów, które definiują określonych godzinach, w której polecenia zdefiniowane przez `Command` element powinien być uruchamiany.

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

## <a name="elements-and-attributes"></a>Atrybuty i elementy
 `Schedules` Element jest elementem podrzędnym `Product` elementu. Każdy `Product` element może mieć co najwyżej jeden `Schedules` elementu. `Schedules` Element nie ma żadnych atrybutów.

## <a name="schedule"></a>Harmonogram
 `Schedule` Element jest elementem podrzędnym `Schedules` elementu. A `Schedules` element musi mieć co najmniej jeden `Schedule` elementu.

 `Schedule` ma następujący atrybut.

|Atrybut|Opis|
|---------------|-----------------|
|`Name`|Wymagana. Nazwa elementu harmonogramu. Odpowiada to `ScheduleName` właściwość `Command` elementu. Gdy `Command` odwołuje się do harmonogramu o nazwie zostanie wykonana tylko o godzinie określonej przez to `Schedule` elementu. Harmonogramy, również mogą być skojarzone z `FailIf` i `BypassIf` elementów, które ograniczają tych testów warunkowych do wykonywania zgodnie z określonym harmonogramem. Aby uzyskać więcej informacji, zobacz [ \<polecenia > Element](../deployment/commands-element-bootstrapper.md).|

 Biorąc pod uwagę `Schedule` element może mieć dokładnie jeden z następujących elementów podrzędnych.

## <a name="buildlist"></a>BuildList
 `BuildList` Element Instruuje Instalatora Aby wykonać polecenie natychmiast, po uruchomieniu bootstrapping aplikacji.

## <a name="beforepackage"></a>BeforePackage
 `BeforePackage` Element Instruuje Instalatora Aby wykonać polecenie przed zainstalowaniem określonego pakietu.

## <a name="afterpackage"></a>AfterPackage
 `AfterPackage` Element Instruuje Instalatora aby wykonywanie polecenia po zainstalowaniu określonego pakietu.

## <a name="see-also"></a>Zobacz także
- [\<Produktu > element](../deployment/product-element-bootstrapper.md)
- [Odwołanie do schematu produktu i pakietu](../deployment/product-and-package-schema-reference.md)