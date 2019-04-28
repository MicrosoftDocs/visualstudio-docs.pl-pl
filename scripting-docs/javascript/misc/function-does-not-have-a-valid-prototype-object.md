---
title: Funkcja nie zawiera prawidłowego prototypu obiektu | Dokumentacja firmy Microsoft
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5023
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 413f73a53a6d4f698219139a87c449be4c155831
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63007506"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>Funkcja nie zawiera prawidłowego prototypu obiektu
Podjęto próbę użycia **instanceof** ustalenie, jeśli obiekt pochodzi z klasy określonej funkcji, ale zostało ponownie zdefiniowane obiektu `prototype` właściwości jako `null`, lub typu obiektu zewnętrznego (zarówno nieprawidłowy [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] obiektów). Obiekt modelu obiektu hosta (na przykład dokumentów programu Internet Explorer lub obiekt window) lub zewnętrznego obiektu COM, może być obiektu zewnętrznego.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, funkcja `prototype` właściwość odwołuje się do prawidłowego [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Function — obiekt](../../javascript/reference/function-object-javascript.md)   
 [prototype, właściwość (Object)](../../javascript/reference/prototype-property-object-javascript.md)