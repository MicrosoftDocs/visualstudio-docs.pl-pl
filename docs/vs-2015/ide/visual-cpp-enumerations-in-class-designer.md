---
title: Wyliczenia Visual C++ w Projektancie klas | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer [Visual Studio], enumerations
ms.assetid: 11e90ba1-18cd-44f8-9e26-e3746a7a19d1
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b38d36c1fdc0033115f1d7a4cf18265dc1f2a3ab
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696362"
---
# <a name="visual-c-enumerations-in-class-designer"></a>Wyliczenia Visual C++ w Projektancie klas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projektant klas obsługuje C++ `enum` i zakresami `enum class` typów. Poniżej znajduje się przykład:  
  
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
  
 Kształt wyliczenia C++ na diagramie klasy wygląda i działa jak kształt struktury, chyba że czyta etykietę **wyliczenia** lub **Enum class**, jest różowy, a nie niebieski i ma kolorowe obramowanie na lewym i górnym marginesy. Zarówno wyliczenia kształtów, jak i struktury mają ostre rogi.  
  
 Aby uzyskać więcej informacji o korzystaniu z `enum` typu, zobacz [wyliczenia](https://msdn.microsoft.com/library/081829db-5dca-411e-a53c-bffef315bcb3).  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z kodem Visual C++ (Projektant klas)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [Wyliczenia](https://msdn.microsoft.com/library/081829db-5dca-411e-a53c-bffef315bcb3)
