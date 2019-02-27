---
title: Oczekiwano cyfry szesnastkowej | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: e5cf7d77853cb200afe568656e1055459acad7d1
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56842302"
---
# <a name="expected-hexadecimal-digit"></a>Oczekiwano liczby szestnastkowej
Nieprawidłowa sekwencja unikowa Unicode została utworzona. Sekwencje unikowe Unicode rozpoczynają się od \u, i dokładnie cztery cyfry szesnastkowe (nie ma więcej i nie mniejszy). Cyfr szesnastkowych Unicode może zawierać tylko cyfry 0-9, wielkich liter A-F i małe litery a-f. W poniższym przykładzie pokazano poprawnie sformułowany sekwencja unikowa Unicode.  
  
```JavaScript  
z = "\u1A5F";  
```  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Pamiętaj, Twoje cyfr szesnastkowych Unicode zaczynają się od \u, zawiera tylko cyfry 0-9, wielkich liter A-F, małe litery a-f; i są pogrupowane w cztery cyfry.  
  
    > [!NOTE]
    >  Jeśli chcesz użyć \u tekst dosłowny w ciągu, a następnie użyj dwa razy — (\\\u) — jeden jako znak ucieczki dla pierwszego ukośnika odwrotnego.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy danych](../../javascript/data-types-javascript.md)