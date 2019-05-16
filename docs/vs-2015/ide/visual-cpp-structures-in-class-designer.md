---
title: Struktury Visual C++ w Projektancie klas | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ed47509467bd8691b6f81dbd52fac47cf21c3715
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65698195"
---
# <a name="visual-c-structures-in-class-designer"></a>Struktury Visual C++ w Projektancie klas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projektant klas obsługuje C++ struktur, które są zadeklarowane za pomocą słowa kluczowego `struct`. Poniżej znajduje się przykład:  
  
```  
struct MyStructure  
{  
   char a;  
   int i;  
   long j;  
};  
```  
  
 Aby uzyskać więcej informacji o korzystaniu z `struct` typu, zobacz [struktury](https://msdn.microsoft.com/library/3c6ba273-e248-4ff1-8c69-d2abcf1263c6).  
  
 Kształt struktury języka C++ na diagramie klasy wygląda i działa jak kształt klasy, z tą różnicą, że czyta etykietę **struktury** i ma ostre rogi zamiast zaokrąglone rogi.  
  
|Element Code|Widok projektanta klas|  
|------------------|-------------------------|  
|`struct StructureName {};`|**StructureName**<br /><br /> Struct|  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z kodem Visual C++ (Projektant klas)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [Klasy i struktury](https://msdn.microsoft.com/library/516dd496-13fb-4f17-845a-e9ca45437873)   
 [struct](https://msdn.microsoft.com/library/3c6ba273-e248-4ff1-8c69-d2abcf1263c6)
