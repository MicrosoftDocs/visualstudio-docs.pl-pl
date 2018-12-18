---
title: Atrybuty warunkowe schematu VSCT XML | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9524f1306c86f110498d71d4057378cd834d207b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817246"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Atrybuty warunkowe schematu XML VSCT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Atrybuty warunkowe mogą być stosowane do wszystkich list i elementów. Operatory logiczne i wyrażenia rozszerzenia symboli zwrócić wartość PRAWDA lub FAŁSZ. W przypadku opcji true skojarzona lista lub element znajduje się w dane wyjściowe.  
  
 Rozszerzenia tokenu można przetestować względem innych rozszerzenia tokenu lub stałe. Funkcja Defined() służy do sprawdzenia, czy została zdefiniowana określonej nazwie, nawet wtedy, gdy go nie ma wartości.  
  
 Gdy warunek jest stosowany do listy, warunek jest stosowany do każdego elementu podrzędnego, na liście. Jeśli nie zawiera elementu podrzędnego samego zawiera atrybut warunku, jego stan jest łączony w za pomocą wyrażenia nadrzędnego przez operację i.  
  
 Wartości 1, "1" i "prawda", są oceniane jako PRAWDA, a 0, "0" i "false", które są obliczane jako wartość false.  
  
## <a name="operators"></a>Operatory  
 Następujące operatory mogą służyć do oceny wyrażenia warunkowe.  
  
|Operator|Definicja|  
|--------------|----------------|  
|(,)|Grupowanie|  
|!|Logiczne NOT|  
|\<, >, \<=, >=, ==, !=|Relacyjne i równości|  
|and|Boolean|  
|lub|Boolean|  
  
## <a name="examples"></a>Przykłady  
  
```  
<Menu Condition="Defined(DEBUG)" …  
</Menu>  
  
<Menu Condition="%(SKU_MODE) = 'Demo'" …  
</Menu>  
  
<Menus Condition="Defined(DEBUG)">  
    <Menu …  
    </Menu>  
</Menus>  
  
<Menus Condition="Defined(DEMO_SKU)">  
    <Menus Condition="!Defined(DEBUG)">  
        <Menu …  
        </Menu>  
    </Menus>  
  
    <Menu …  
    </Menu>  
</Menus>  
  
<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))   
and !Defined(DEBUG)">  
    <Menu …  
    </Menu>  
</Menus>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Tabela poleceń programu Visual Studio (pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

