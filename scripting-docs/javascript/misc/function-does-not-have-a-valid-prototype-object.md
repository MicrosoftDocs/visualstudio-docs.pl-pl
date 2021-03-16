---
description: Podjęto próbę użycia InstanceOf, aby określić, czy obiekt pochodzi z określonej klasy funkcji, ale ponownie zdefiniowano Właściwość prototypu obiektu jako wartość null lub typ obiektu zewnętrznego (nieprawidłowe obiekty JavaScript).
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
ms.openlocfilehash: 0356ac9ef7c63c77c0cc0dfca623ff24d3de24af
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571418"
---
# <a name="function-does-not-have-a-valid-prototype-object"></a>Funkcja nie zawiera prawidłowego prototypu obiektu
Podjęto próbę użycia **InstanceOf** , aby określić, czy obiekt pochodzi z określonej klasy funkcji, ale właściwość obiektu została `prototype` ponownie zdefiniowana jako albo `null` Typ obiektu zewnętrznego (nie dotyczy [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] obiektów). Obiektem zewnętrznym może być obiekt z modelu obiektów hosta (na przykład dokument lub obiekt okna programu Internet Explorer) albo zewnętrzny obiekt COM.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, że `prototype` Właściwość funkcji odwołuje się do prawidłowego [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekt Function](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function)   
 [prototype, właściwość (Object)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)
