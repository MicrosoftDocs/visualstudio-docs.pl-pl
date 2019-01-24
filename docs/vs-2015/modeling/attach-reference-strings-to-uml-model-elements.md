---
title: Dołączanie ciągów odwołania do elementów modelu UML | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- UML - extending, reference strings
ms.assetid: 15dbed99-efce-42fe-a768-714a5804e7d1
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bd5a1ae4abc2e0b5c508b7b77160bbf8da3bb45e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54764967"
---
# <a name="attach-reference-strings-to-uml-model-elements"></a>Dołączanie ciągów odwołania do elementów modelu UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można napisać kod, aby dołączyć dowolne ciągi z elementami modelu. Ciąg może być na przykład identyfikatora URI w pamięci podręcznej wyniku obliczenia lub ModelBus odwołanie do elementu w innym modelem. Każdy ciąg jest zawarty w obiekcie IReference. Dowolna liczba obiektów IReference można dołączyć do każdego elementu modelu.  
  
 Każdy obiekt IReference ma nazwę. Aby wskazać, jak interpretować wartość odniesienia, można użyć tej nazwy. Na przykład można ustawić nazwę "URI", aby wskazać, że wartość powinno być interpretowane jako identyfikator URI. Istnieją niektóre odwołanie do wstępnie zdefiniowanych wartości nazw, który jest używana przez narzędzia modelowania.  
  
## <a name="attaching-a-reference-to-an-ielement"></a>Odwołanie do IElement dołączania  
 Aby skorzystać z następujących metod, należy dodać odwołanie do:  
  
 Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll  
  
 Ta dyrektywa należy wstawić w kodzie:  
  
 `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`  
  
|Wywołanie metody|Opis|  
|-----------------|-----------------|  
|`element.AddReference (nameString, valueString, duplicatesAllowed)`|Tworzy `IReference` przy użyciu podanej nazwy i wartości ciągów i dołącza go do `element`. Zwraca `IReference`.<br /><br /> Zgłasza wyjątek, jeśli `duplicatesAllowed` ma wartość false, a istnieje już `IReference` o takiej samej nazwie, dołączone do `element`.|  
|`element.GetReferences(name)`|Zwraca wszystkie `IReference` obiekty połączone `element` , które mają dany `name`.|  
|`element.DeleteAllReferences(name)`|Usuwa wszystkie `IReference` obiekty połączone do elementu, który ma na imię.|  
|`reference.Delete()`|Spowoduje to usunięcie `IReference`.|  
|`ReferenceConstants.WorkItem`|Wartość używana do odwołania do elementu roboczego nazwy.|  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie procedury obsługi łącza elementu roboczego](../modeling/define-a-work-item-link-handler.md)   
 [Definiowanie i instalowanie rozszerzenia modelowania](../modeling/define-and-install-a-modeling-extension.md)   
 [Programowanie za pomocą interfejsu API UML](../modeling/programming-with-the-uml-api.md)
