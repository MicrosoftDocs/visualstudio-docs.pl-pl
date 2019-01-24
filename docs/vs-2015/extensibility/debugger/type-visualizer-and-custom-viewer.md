---
title: Typ wizualizatora i Przeglądarka niestandardowa | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54789430"
---
# <a name="type-visualizer-and-custom-viewer"></a>Wizualizator typów i przeglądarka niestandardowa
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wizualizator typów jest składnikiem, który wyświetla część danych w bardzo specyficznym formacie. Ten format jest całkowicie maksymalnie implementujący wizualizatora, użytkownik końcowy lub dostawcą wizualizatorów innych firm.  
  
 Przeglądarka niestandardowa jest częścią ewaluatora wyrażeń niestandardowych, które wyświetla część danych w formacie bardzo szczegółowych. Ten format jest całkowicie maksymalnie implementujący niestandardowe podglądu, co oznacza, że format jest maksymalnie implementujący programu expression evaluator (EE).  
  
## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Obsługa Wizualizatorów typu w ewaluatora wyrażeń  
 EE może obsługiwać wizualizatorów typu dzięki obsłudze zbiór interfejsów, które są dostępne do wizualizatorów: interfejsy, takie jak [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) i [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). Należy jednak pamiętać, że EE nie jest odpowiedzialne za wykonanie Wizualizator typów, sama: EE jedynie zezwala na zewnętrzne wizualizatorów dostęp do informacji o typie. Takie wizualizatorów może dostarczany wraz z EE i zainstalowane w odpowiednim miejscu w programie Visual Studio, dostarczone przez innego dostawcę innych firm lub nawet przez użytkownika końcowego.  
  
## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Obsługa przeglądarek niestandardowych w ewaluatora wyrażeń  
 EE może również obsługiwać przeglądarek niestandardowych, w których EE, sama dostarcza kod w celu wyświetlania typu danych. Przeglądarka niestandardowa implementuje [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) interfejs, który obsługuje wszystkie obowiązki wyświetlane dane w formacie, który lubisz jest pożądane; Podgląd ma pełną kontrolę nad wyświetlaniem oraz nawet umożliwić dane, które mają być modyfikowane. Wszelkie przeglądarek niestandardowych dostarczonych przez EE dołączone EE, gdy produkt jest wysyłany.  
  
## <a name="see-also"></a>Zobacz też  
 [Składniki debugera](../../extensibility/debugger/debugger-components.md)   
 [Ewaluator wyrażeń](../../extensibility/debugger/expression-evaluator.md)   
 [Aparat debugowania](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
