---
title: Struktury Visual C++ w Projektant klas | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646766"
---
# <a name="visual-c-structures-in-class-designer"></a>Struktury Visual C++ w Projektancie klas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projektant klas obsługuje struktury języka C++, które są zadeklarowane za pomocą słowa kluczowego `struct` . Oto przykład:

```
struct MyStructure
{
   char a;
   int i;
   long j;
};
```

 Aby uzyskać więcej informacji na temat korzystania z `struct` typu, zobacz [Struktura](https://msdn.microsoft.com/library/3c6ba273-e248-4ff1-8c69-d2abcf1263c6).

 Kształt struktury C++ na diagramie klas wygląda i działa jak kształt klasy, z tą różnicą, że etykieta odczytuje **strukturę** i ma kwadratowe rogi zamiast zaokrąglonych rogów.

|Element Code|Widok Projektant klas|
|------------------|-------------------------|
|`struct StructureName {};`|**StructureName**<br /><br /> Struktura|

## <a name="see-also"></a>Zobacz też
 [Praca z klasami kodu Visual C++ (Projektant klas)](../ide/working-with-visual-cpp-code-class-designer.md) [i](https://msdn.microsoft.com/library/516dd496-13fb-4f17-845a-e9ca45437873) [strukturą](https://msdn.microsoft.com/library/3c6ba273-e248-4ff1-8c69-d2abcf1263c6) struktury
