---
title: Struktury C++ wizualizacji w Projektant klas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], structures
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc9c09c5f92c4193d3d3f58c819f4bc0fc9aaebf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646766"
---
# <a name="visual-c-structures-in-class-designer"></a>Struktury Visual C++ w Projektancie klas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projektant klas obsługuje C++ struktury, które są zadeklarowane za pomocą słowa kluczowego `struct`. Oto przykład:

```
struct MyStructure
{
   char a;
   int i;
   long j;
};
```

 Aby uzyskać więcej informacji o używaniu typu `struct`, zobacz [struct](https://msdn.microsoft.com/library/3c6ba273-e248-4ff1-8c69-d2abcf1263c6).

 Kształt C++ struktury na diagramie klas wygląda i działa jak kształt klasy, z tą różnicą, że etykieta odczytuje **strukturę** i ma kwadratowe rogi zamiast zaokrąglonych rogów.

|Element Code|Widok Projektant klas|
|------------------|-------------------------|
|`struct StructureName {};`|**StructureName**<br /><br /> Struct|

## <a name="see-also"></a>Zobacz też
 [Praca z klasami Visual C++ Code (Projektant klas)](../ide/working-with-visual-cpp-code-class-designer.md) [i](https://msdn.microsoft.com/library/516dd496-13fb-4f17-845a-e9ca45437873) [strukturą](https://msdn.microsoft.com/library/3c6ba273-e248-4ff1-8c69-d2abcf1263c6) struktury
