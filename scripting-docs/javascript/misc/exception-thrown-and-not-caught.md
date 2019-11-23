---
title: Zgłoszono wyjątek i nie przechwycono | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 05a9e4f51d5daf7a9e1b1153acbbe8b76b539b72
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572855"
---
# <a name="exception-thrown-and-not-caught"></a>Wyjątek zgłoszony i nieprzechwycony
Dołączono instrukcję `throw` w kodzie, ale nie została ona zawarta w bloku **try** lub nie ma skojarzonego bloku **catch** w celu zalewki błędu. Wyjątki są zgłaszane z wewnątrz bloku **try** przy użyciu instrukcji **throw** i przechwytywane poza blokiem **try** przy użyciu instrukcji **catch** .  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Ujmij kod, który może zgłosić wyjątek w bloku **try** i upewnić się, że istnieje odpowiedni blok **catch** .  
  
- Upewnij się, że instrukcja catch oczekuje poprawnej formy wyjątku.  
  
- Jeśli wyjątek jest ponownie zgłaszany, upewnij się, że istnieje inna odpowiadająca instrukcja catch.  
  
## <a name="see-also"></a>Zobacz także  
 [Błąd  obiektu](../../javascript/reference/error-object-javascript.md)  
 [zgłoś  instrukcji](../../javascript/reference/throw-statement-javascript.md)  
 [Try...Catch...Finally, instrukcja](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)