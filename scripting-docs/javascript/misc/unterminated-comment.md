---
title: Niezakończony komentarz | Dokumentacja firmy Microsoft
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 5bf7c570c832fb5db5489a2a9f9bec459f26f0a1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63005958"
---
# <a name="unterminated-comment"></a>Niezakończony komentarz
Rozpoczęto blok komentarzy wielowierszowych, ale nie prawidłowo zakończyć je. Wielowierszowe komentarze zaczynają się od "/ *" połączenie oraz kończyć się odwrotnej "\*/" kombinacji. Oto przykład:  
  
```JavaScript  
/* This is a comment  
This is another part of the same comment.*/  
```  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Pamiętaj zakończyć Komentarze wielowierszowe "* /".  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje komentarzy](../../javascript/reference/comment-statements-javascript.md)