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
ms.openlocfilehash: 31226f972ff4714dd81207cf27d862d3449184a5
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56840766"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>Funkcja nie zawiera prawidłowego prototypu obiektu
Podjęto próbę użycia **instanceof** ustalenie, jeśli obiekt pochodzi z klasy określonej funkcji, ale zostało ponownie zdefiniowane obiektu `prototype` właściwości jako `null`, lub typu obiektu zewnętrznego (zarówno nieprawidłowy [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] obiektów). Obiekt modelu obiektu hosta (na przykład dokumentów programu Internet Explorer lub obiekt window) lub zewnętrznego obiektu COM, może być obiektu zewnętrznego.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Upewnij się, funkcja `prototype` właściwość odwołuje się do prawidłowego [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Function — obiekt](../../javascript/reference/function-object-javascript.md)   
 [prototype, właściwość (Object)](../../javascript/reference/prototype-property-object-javascript.md)