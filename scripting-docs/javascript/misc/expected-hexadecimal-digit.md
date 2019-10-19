---
title: Oczekiwana cyfra szesnastkowa | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 67a86df7-49f9-43cb-99c6-99b1a427827a
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6672046e0f7bf5e39c334dc0ba30f22eaff6e9a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573373"
---
# <a name="expected-hexadecimal-digit"></a>Oczekiwano liczby szestnastkowej
Utworzono nieprawidłową sekwencję ucieczki Unicode. Sekwencje ucieczki Unicode zaczynają się od \u, po których następuje dokładnie cztery cyfry szesnastkowe (nie więcej i nie mniej). Cyfry szesnastkowe Unicode mogą zawierać tylko cyfry 0-9, wielkie litery A-F i małe litery a-f. Poniższy przykład ilustruje poprawnie sformułowaną sekwencję ucieczki w formacie Unicode.  
  
```JavaScript  
z = "\u1A5F";  
```  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, że cyfry szesnastkowe Unicode zaczynają się od \u, zawierają tylko cyfry 0-9, wielkie litery A-F, małe litery a-f; i są pogrupowane w cztery cyfry.  
  
    > [!NOTE]
    > Jeśli chcesz użyć literału Text \u w ciągu, użyj dwóch ukośników odwrotnych — (\\ \u) — jeden do ucieczki pierwszego ukośnika odwrotnego.  
  
## <a name="see-also"></a>Zobacz także  
 [Typy danych](../../javascript/data-types-javascript.md)