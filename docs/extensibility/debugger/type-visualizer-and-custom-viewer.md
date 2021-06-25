---
title: Wizualizator typów i przeglądarka niestandardowa | Microsoft Docs
description: Dowiedz się więcej o składnikach wizualizatora typów i niestandardowych podglądach, które wyświetlają dane w określonym formacie, oraz o różnicach między nimi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c18bb49c740362d42a4a54bf52f6998629acb0c0
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904425"
---
# <a name="type-visualizer-and-custom-viewer"></a>Wizualizator typów i przeglądarka niestandardowa
Wizualizator typu to składnik, który wyświetla fragment danych w określonym formacie. Format jest całkowicie zależy od tego, kto implementuje wizualizator, czy jest to użytkownik końcowy, czy też dostawca wizualizatorów innej firmy.

 Przeglądarka niestandardowa jest częścią ewaluatora wyrażeń niestandardowych, który wyświetla element danych w określonym formacie. Ten format jest całkowicie dostosowany do implementatora przeglądarki niestandardowej, co oznacza, że format należy do implementatora ewaluatora wyrażeń (EE).

## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Obsługa wizualizatorów typów w ewaluatorze wyrażeń
 EE obsługuje wizualizatory typów, obsługując zestaw interfejsów dostępnych dla wizualizatorów: interfejsy takie jak [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) [i IEEVisualizerDataProvider.](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) Jednak projekt EE nie jest odpowiedzialny za implementację samego wizualizatora typu: EE umożliwia jedynie zewnętrznym wizualizatorom dostęp do informacji o typie. Takie wizualizatory mogą być dostarczane wraz z EE i instalowane w odpowiednim miejscu w Visual Studio, dostarczone przez innego dostawcę lub nawet przez użytkownika końcowego.

## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Obsługa niestandardowych osób przeglądjących w ewaluatorze wyrażeń
 Aplikacja EE może również obsługiwać niestandardowe przeglądarki, w których sama aplikacja EE dostarcza kod do wyświetlania typu danych. Przeglądarka niestandardowa implementuje interfejs [IDebugCustomViewer,](../../extensibility/debugger/reference/idebugcustomviewer.md) który obsługuje wszystkie obowiązki wyświetlania danych w żądanym formacie; Przeglądarka ma pełną kontrolę nad wyświetlaniem i może nawet pozwolić na modyfikację danych. Wszystkie niestandardowe przeglądarki dostarczane przez program EE są dostarczane wraz z programem EE po wysłaniu produktu.

## <a name="see-also"></a>Zobacz też
- [Składniki debugera](../../extensibility/debugger/debugger-components.md)
- [Wyrażenie](../../extensibility/debugger/expression-evaluator.md)
- [Aparat debugowania](../../extensibility/debugger/debug-engine.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
