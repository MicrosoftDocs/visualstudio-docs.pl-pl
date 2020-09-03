---
title: Wizualizator typów i Podgląd niestandardowy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a85be2978abe35e91096b55fba5ec5281be25fbe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185310"
---
# <a name="type-visualizer-and-custom-viewer"></a>Wizualizator typów i przeglądarka niestandardowa
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wizualizator typu jest składnikiem, który wyświetla dane w bardzo specyficznym formacie. Ten format jest całkowicie do realizatora wizualizatora, może być użytkownikiem końcowym lub dostawcą wizualizatorów innych firm.  
  
 Przeglądarka niestandardowa jest częścią niestandardowej ewaluatora wyrażeń, która wyświetla dane w bardzo określonym formacie. Ten format jest całkowicie do realizatora niestandardowej przeglądarki, co oznacza, że format jest do realizatora ewaluatora wyrażeń (EE).  
  
## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Obsługa wizualizatorów typów w ewaluatora wyrażeń  
 Program EE może obsługiwać Wizualizatory typów poprzez obsługę zestawu interfejsów dostępnych dla wizualizatorów: interfejsów, takich jak [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) i [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). Należy jednak zauważyć, że EE nie odpowiada za implementację wizualizatora typu: EE tylko umożliwia zewnętrznym wizualizatorom dostęp do informacji o typie. Takie Wizualizatory mogą być dostarczane wraz z EE i instalowane w odpowiednim miejscu w programie Visual Studio, dostarczane przez innego dostawcę innych firm, a nawet przez użytkownika końcowego.  
  
## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Obsługa niestandardowych podglądów w ewaluatora wyrażeń  
 W przypadku usługi EE można także obsługiwać niestandardowe osoby przeglądające, w których sama EE dostarczają kod służący do wyświetlania typu danych. Niestandardowa przeglądarka implementuje interfejs [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) , który obsługuje wszystkie zadania pokazywania danych w dowolnym formacie. Podgląd ma pełną kontrolę nad wyświetlaniem i może nawet zezwolić na modyfikowanie danych. Wszystkie niestandardowe osoby przeglądające dostarczane przez program EE są dostarczane z EE, gdy produkt jest dostarczany.  
  
## <a name="see-also"></a>Zobacz też  
 [Składniki debugera](../../extensibility/debugger/debugger-components.md)   
 [Ewaluatora wyrażeń](../../extensibility/debugger/expression-evaluator.md)   
 [Aparat debugowania](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
