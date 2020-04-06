---
title: Wizualizator typu i przeglądarka niestandardowa | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b8def9d28279f601ff488fca457982806629c0b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712464"
---
# <a name="type-visualizer-and-custom-viewer"></a>Wizualizator typu i przeglądarka niestandardowa
Wizualizator typu jest składnikiem, który wyświetla fragment danych w określonym formacie. Format zależy wyłącznie od tego, kto implementuje wizualizator, czy to użytkownika końcowego, czy zewnętrznego dostawcy wizualizatorów.

 Przeglądarka niestandardowa jest częścią ewaluatora wyrażeń niestandardowych, która wyświetla fragment danych w określonym formacie. Ten format jest całkowicie do implementatora przeglądarki niestandardowej, co oznacza, że format jest do implementatora oceniającego wyrażenie (EE).

## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Obsługa wizualizatorów typów w oceniający wyrażenie
 EE obsługuje wizualizatory typów, obsługując zestaw interfejsów dostępnych dla wizualizatorów: interfejsy, takie jak [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) i [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). EE nie jest jednak odpowiedzialny za implementowanie samego wizualizatora typu: EE umożliwia jedynie zewnętrznym wizualizatorom dostęp do informacji o typie. Takie wizualizatory mogą być wysyłane wraz z EE i zainstalowane w odpowiednim miejscu w programie Visual Studio, dostarczone przez innego dostawcę innej firmy lub nawet przez użytkownika końcowego.

## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Obsługa niestandardowych widzów w oceniający wyrażenie
 EE może również obsługiwać niestandardowe przeglądarki, w których ee sam dostarcza kod do wyświetlania typu danych. Przeglądarka niestandardowa implementuje interfejs [IDebugCustomViewer,](../../extensibility/debugger/reference/idebugcustomviewer.md) który obsługuje wszystkie obowiązki wyświetlania danych w dowolnym formacie; przeglądarka ma pełną kontrolę nad wyświetlaczem, a nawet może pozwolić na modyfikację danych. Wszystkie niestandardowe przeglądarki dostarczane przez EE pochodzą z EE, gdy produkt jest dostarczany.

## <a name="see-also"></a>Zobacz też
- [Składniki debugera](../../extensibility/debugger/debugger-components.md)
- [Wyrażenie](../../extensibility/debugger/expression-evaluator.md)
- [Aparat debugowania](../../extensibility/debugger/debug-engine.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
