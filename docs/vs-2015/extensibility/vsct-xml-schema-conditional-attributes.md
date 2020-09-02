---
title: Atrybuty warunkowe schematu XML VSCT | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6294ee8027b61840149096561efc91b8a4a3c3ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62422166"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Atrybuty warunkowe schematu XML VSCT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Atrybuty warunkowe mogą być stosowane do wszystkich list i elementów. Operatory logiczne i wyrażenia rozszerzania symboli mają wartość PRAWDA lub FAŁSZ. W przypadku wartości true skojarzona lista lub element zostanie uwzględniony w wynikowym wyjściu.  
  
 Rozszerzenia tokenów można testować względem innych rozszerzeń lub stałych tokenów. Funkcja defined () służy do sprawdzania, czy określona nazwa została zdefiniowana, nawet jeśli nie ma wartości.  
  
 Gdy atrybut Condition jest stosowany do listy, warunek jest stosowany do każdego elementu podrzędnego na liście. Jeśli element podrzędny zawiera atrybut Condition, jego warunek jest połączony z wyrażeniem nadrzędnym przez operację i.  
  
 Wartości 1, "1" i "true" są oceniane jako prawdziwe, a 0, "0" i "false" są oceniane jako FAŁSZ.  
  
## <a name="operators"></a>Operatory  
 Następujące operatory mogą służyć do obliczania wyrażeń warunkowych.  
  
|Operator|Definicja|  
|--------------|----------------|  
|(,)|Grupowanie|  
|!|Logiczne NOT|  
|\<, >, \<=, >=, ==, !=|Relacyjne i równość|  
|oraz|Wartość logiczna|  
|lub|Wartość logiczna|  
  
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
