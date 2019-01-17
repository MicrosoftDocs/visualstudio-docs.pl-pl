---
title: Oczekiwano cyfry szesnastkowej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 67a86df7-49f9-43cb-99c6-99b1a427827a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9e29131c4ecf4f476a30da94ec67676d6bea347
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346049"
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