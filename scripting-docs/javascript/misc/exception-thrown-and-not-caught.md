---
title: Zgłoszono wyjątek i nie przechwycono | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5022
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a0e3eb6d1275e5598ad44ea553e22f0b53eeb45
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862763"
---
# <a name="exception-thrown-and-not-caught"></a>Wyjątek zgłoszony i nieprzechwycony
Dołączono `throw` instrukcję w kodzie, ale nie została ona zawarta w bloku **try** lub nie ma żadnego skojarzonego bloku **catch** w celu zalewki błędu. Wyjątki są zgłaszane z wewnątrz bloku **try** przy użyciu instrukcji **throw** i przechwytywane poza blokiem **try** przy użyciu instrukcji **catch** .  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Ujmij kod, który może zgłosić wyjątek w bloku **try** i upewnić się, że istnieje odpowiedni blok **catch** .  
  
- Upewnij się, że instrukcja catch oczekuje poprawnej formy wyjątku.  
  
- Jeśli wyjątek jest ponownie zgłaszany, upewnij się, że istnieje inna odpowiadająca instrukcja catch.  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekt Error](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Error)   
 [throw — instrukcja](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/throw)   
 [Spróbuj... catch... finally — instrukcja](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/try...catch)