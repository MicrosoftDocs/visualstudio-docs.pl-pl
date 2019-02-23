---
title: Typ wizualizatora i Przeglądarka niestandardowa | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 219632bce50b6942d46e4061a3c7eaf8f70adfd5
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685966"
---
# <a name="type-visualizer-and-custom-viewer"></a>Wizualizator typów i Przeglądarka niestandardowa
Wizualizator typów jest składnikiem, który wyświetla część danych w określonym formacie. Format jest całkowicie maksymalnie visualizer, który implementuje, jest to użytkownik końcowy lub dostawcą firm wizualizatorów.

 Przeglądarka niestandardowa jest częścią ewaluatora wyrażeń niestandardowych, które wyświetla część danych w określonym formacie. Ten format jest całkowicie maksymalnie implementujący niestandardowe podglądu, co oznacza, że format jest maksymalnie implementujący programu expression evaluator (EE).

## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Obsługa wizualizatorów typu w ewaluatora wyrażeń
 EE obsługuje wizualizatorów typu dzięki obsłudze zbiór interfejsów, które są dostępne do wizualizatorów: interfejsy, takie jak [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) i [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). Jednak nie jest odpowiedzialny za realizację Wizualizator typów, sama EE: EE jedynie zezwala na zewnętrzne wizualizatorów dostęp do informacji o typie. Takie wizualizatorów może dostarczany wraz z EE i zainstalowane w odpowiednim miejscu w programie Visual Studio, dostarczone przez innego dostawcę innych firm lub nawet przez użytkownika końcowego.

## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Obsługa przeglądarek niestandardowych w ewaluatora wyrażeń
 EE może również obsługiwać przeglądarek niestandardowych, w których EE, sama dostarcza kod w celu wyświetlania typu danych. Przeglądarka niestandardowa implementuje [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) interfejs, który obsługuje wszystkie obowiązki wyświetlane dane w formacie, który lubisz jest pożądane; Podgląd ma pełną kontrolę nad wyświetlaniem oraz nawet można pozwolić, aby dane można modyfikować. Wszelkie przeglądarek niestandardowych dostarczonych przez EE dołączone EE, gdy produkt jest wysyłany.

## <a name="see-also"></a>Zobacz także
- [Składniki debugera](../../extensibility/debugger/debugger-components.md)
- [Ewaluator wyrażeń](../../extensibility/debugger/expression-evaluator.md)
- [Aparat debugowania](../../extensibility/debugger/debug-engine.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)