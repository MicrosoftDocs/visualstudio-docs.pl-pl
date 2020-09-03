---
title: Niezakończony komentarz | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1016
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d4286315-814b-4966-b4c4-1ee19d796eff
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 16f675cb62c0c3fd5f3aba7ba6190427fe101353
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85814806"
---
# <a name="unterminated-comment"></a>Niezakończony komentarz
Rozpoczęto blok komentarza wielowierszowego, ale nie został on prawidłowo zakończony. Komentarze wielowierszowe zaczynają się od kombinacji "/*" i kończą się odwrotną \* kombinacją "/". Poniżej przedstawiono przykład:  
  
```JavaScript  
/* This is a comment  
This is another part of the same comment.*/  
```  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Pamiętaj, aby zakończyć Komentarze wielowierszowe za pomocą znaku "*/".  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje komentarzy](../../javascript/reference/comment-statements-javascript.md)