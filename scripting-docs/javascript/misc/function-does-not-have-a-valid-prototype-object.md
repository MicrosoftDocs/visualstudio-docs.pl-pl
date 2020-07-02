---
title: Funkcja nie ma prawidłowego obiektu prototypu | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: ca6f13620bb486cf1663bd5bef9a9a93b2c8a480
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817362"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>Funkcja nie zawiera prawidłowego prototypu obiektu
Podjęto próbę użycia **InstanceOf** , aby określić, czy obiekt pochodzi z określonej klasy funkcji, ale właściwość obiektu została `prototype` ponownie zdefiniowana jako albo `null` Typ obiektu zewnętrznego (nie dotyczy [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] obiektów). Obiektem zewnętrznym może być obiekt z modelu obiektów hosta (na przykład dokument lub obiekt okna programu Internet Explorer) albo zewnętrzny obiekt COM.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, że `prototype` Właściwość funkcji odwołuje się do prawidłowego [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] obiektu.  
  
## <a name="see-also"></a>Zobacz także  
 [Obiekt Function](../../javascript/reference/function-object-javascript.md)   
 [prototype, właściwość (Object)](../../javascript/reference/prototype-property-object-javascript.md)