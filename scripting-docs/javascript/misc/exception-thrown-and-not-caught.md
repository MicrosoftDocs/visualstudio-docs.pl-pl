---
description: Dołączono instrukcję throw w kodzie, ale nie została ona zawarta w bloku try lub nie ma skojarzonego bloku catch w celu zalewki błędu.
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
ms.openlocfilehash: b8abcfced6dfe78dc18f4e31d2bd90d5e5a45a4a
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570638"
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
