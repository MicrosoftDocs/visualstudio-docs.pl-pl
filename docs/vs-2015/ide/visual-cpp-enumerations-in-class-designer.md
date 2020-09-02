---
title: Visual C++ wyliczenia w Projektant klas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f967420e37d6337ce6d86cc56524f2751218f56
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651664"
---
# <a name="visual-c-enumerations-in-class-designer"></a>Wyliczenia Visual C++ w Projektancie klas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projektant klas obsługuje C++ `enum` i typy z zakresem `enum class` . Oto przykład:

```
enum CardSuit {
   Diamonds = 1,
   Hearts = 2,
   Clubs = 3,
   Spades = 4
};

// or...
enum class CardSuit {
   Diamonds = 1,
   Hearts = 2,
   Clubs = 3,
   Spades = 4
};

```

 Kształt wyliczenia języka C++ na diagramie klas wygląda i działa jak kształt struktury, z tą różnicą, że etykieta odczytuje klasę **enum** lub **enum**, jest kolorem różowym zamiast niebieskim i ma kolorowe obramowanie na lewym i górnym marginesie. Zarówno kształty wyliczenia, jak i kształty struktury mają narożniki kwadratowe.

 Aby uzyskać więcej informacji na temat korzystania z `enum` typu, zobacz [wyliczenia](https://msdn.microsoft.com/library/081829db-5dca-411e-a53c-bffef315bcb3).

## <a name="see-also"></a>Zobacz też
 Praca z [wyliczeniami](https://msdn.microsoft.com/library/081829db-5dca-411e-a53c-bffef315bcb3) [kodu Visual C++ (Projektant klas)](../ide/working-with-visual-cpp-code-class-designer.md)
