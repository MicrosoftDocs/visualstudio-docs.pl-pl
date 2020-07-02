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
ms.openlocfilehash: 44f207d2e32a7ca79ee0d5851a80261c5da9743d
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85814593"
---
# <a name="exception-thrown-and-not-caught"></a>Wyjątek zgłoszony i nieprzechwycony
Dołączono `throw` instrukcję w kodzie, ale nie została ona zawarta w bloku **try** lub nie ma żadnego skojarzonego bloku **catch** w celu zalewki błędu. Wyjątki są zgłaszane z wewnątrz bloku **try** przy użyciu instrukcji **throw** i przechwytywane poza blokiem **try** przy użyciu instrukcji **catch** .  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Ujmij kod, który może zgłosić wyjątek w bloku **try** i upewnić się, że istnieje odpowiedni blok **catch** .  
  
- Upewnij się, że instrukcja catch oczekuje poprawnej formy wyjątku.  
  
- Jeśli wyjątek jest ponownie zgłaszany, upewnij się, że istnieje inna odpowiadająca instrukcja catch.  
  
## <a name="see-also"></a>Zobacz także  
 [Obiekt Error](../../javascript/reference/error-object-javascript.md)   
 [throw — instrukcja](../../javascript/reference/throw-statement-javascript.md)   
 [Spróbuj... catch... finally — instrukcja](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)