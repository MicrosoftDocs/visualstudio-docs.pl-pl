---
title: Interfejs IProvideExpressionContexts | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IProvideExpressionContexts interface
ms.assetid: e4c70f2c-7d86-4fdc-a1cb-f5a0bb8ed037
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6ec0d5e17b0d3527252352c2e789adfac4fa859
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63410045"
---
# <a name="iprovideexpressioncontexts-interface"></a>Interfejs IProvideExpressionContexts
Zapewnia sposób wyliczyć kontekstów wyrażenie znane niektórych składników. Aparaty skryptów zwykle implementują ten interfejs.  
  
 Menedżer debugowania procesów używa tego interfejsu, aby znaleźć wszystkie konteksty wyrażenia globalnego skojarzone z danym wątku.  
  
> [!NOTE]
> Ten interfejs jest wywoływana z wewnątrz wątku zainteresowania. Jest implementujący do identyfikowania bieżącego wątku i zwraca moduł wyliczający odpowiednie.  
  
## <a name="methods"></a>Metody  
 Oprócz metod odziedziczone `IUnknown`, `IProvideExpressionContexts` interfejsu udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IProvideExpressionContexts::EnumExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-enumexpressioncontexts.md)|Zwraca moduł wyliczający kontekstów wyrażenie znane przez ten składnik.|