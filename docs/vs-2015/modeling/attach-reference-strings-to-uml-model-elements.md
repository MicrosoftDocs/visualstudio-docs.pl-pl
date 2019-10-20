---
title: Dołączanie ciągów odwołania do elementów modelu UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- UML - extending, reference strings
ms.assetid: 15dbed99-efce-42fe-a768-714a5804e7d1
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7726379258ef474b57f1ca4a924413cd93cf80bb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672791"
---
# <a name="attach-reference-strings-to-uml-model-elements"></a>Dołączanie ciągów odwołania do elementów modelu UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można napisać kod, aby dołączyć dowolne ciągi do elementów modelu. Ciąg może być na przykład identyfikatorem URI, buforowanym wynikiem obliczeń lub odwołaniem ModelBus do elementu w innym modelu. Każdy ciąg jest zawarty w obiekcie IReference. Dowolna liczba obiektów IReference może być dołączona do każdego elementu modelu.

 Każdy obiekt IReference ma nazwę. Tej nazwy można użyć, aby wskazać, w jaki sposób należy interpretować wartość referencyjną. Na przykład można ustawić nazwę na "URI", aby wskazać, że wartość powinna być interpretowana jako identyfikator URI. Istnieją pewne wstępnie zdefiniowane wartości nazw referencyjnych używanych przez narzędzia modelowania.

## <a name="attaching-a-reference-to-an-ielement"></a>Dołączanie odwołania do elementu IElement
 Aby skorzystać z następujących metod, należy dodać odwołanie do:

 Microsoft. VisualStudio. ArchitectureTools. rozszerzalność. dll

 Tę dyrektywę należy wstawić w kodzie:

 `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`

|Wywołanie metody|Opis|
|-----------------|-----------------|
|`element.AddReference (nameString, valueString, duplicatesAllowed)`|Tworzy `IReference` z podaną nazwą i ciągami wartości, a następnie łączy je z `element`. Zwraca `IReference`.<br /><br /> Zgłasza wyjątek, jeśli `duplicatesAllowed` ma wartość false i istnieje już `IReference` o tej samej nazwie dołączonej do `element`.|
|`element.GetReferences(name)`|Zwraca wszystkie obiekty `IReference` połączone z `element`, które mają daną `name`.|
|`element.DeleteAllReferences(name)`|Usuwa wszystkie obiekty `IReference` połączone z elementem, który ma daną nazwę.|
|`reference.Delete()`|Usuwa ten `IReference`.|
|`ReferenceConstants.WorkItem`|Wartość służąca do nazwy odwołań do elementów roboczych.|

## <a name="see-also"></a>Zobacz też
 [Definiowanie obsługi łączy elementów roboczych](../modeling/define-a-work-item-link-handler.md) [Definiowanie i Instalowanie programowania rozszerzeń modelowania](../modeling/define-and-install-a-modeling-extension.md) [przy użyciu interfejsu API UML](../modeling/programming-with-the-uml-api.md)
