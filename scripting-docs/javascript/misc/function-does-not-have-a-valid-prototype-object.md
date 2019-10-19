---
title: Funkcja nie ma prawidłowego obiektu prototypu | Microsoft Docs
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
ms.openlocfilehash: cb3cffa4bffd616560aa95ace4ad82a4368ebbd5
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574601"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>Funkcja nie zawiera prawidłowego prototypu obiektu
Podjęto próbę użycia **InstanceOf** , aby określić, czy obiekt pochodzi z określonej klasy funkcji, ale ponownie zdefiniowano Właściwość `prototype` obiektu jako `null` lub typ obiektu zewnętrznego (nieprawidłowymi obiektami [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]). Obiektem zewnętrznym może być obiekt z modelu obiektów hosta (na przykład dokument lub obiekt okna programu Internet Explorer) albo zewnętrzny obiekt COM.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, że właściwość `prototype` funkcji odwołuje się do prawidłowego obiektu [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Zobacz także  
 @No__t_1 [obiektu funkcji](../../javascript/reference/function-object-javascript.md)  
 [prototype, właściwość (Object)](../../javascript/reference/prototype-property-object-javascript.md)