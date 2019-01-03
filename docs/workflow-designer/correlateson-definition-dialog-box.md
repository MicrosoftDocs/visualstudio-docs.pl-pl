---
title: Projektant przepływu pracy — Definiowanie CorrelatesOn, okno dialogowe
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- CorrelatesOnDefinition.UI
ms.assetid: 8b2b627a-f236-4479-aa09-525df65e3413
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4bdc8dd059679c0ba1407585525d30a28dfd8440
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53988287"
---
# <a name="correlateson-definition-dialog-box"></a>Definicja wyrażenia CorrelatesOn, okno dialogowe

**CorrelatesOn** okno dialogowe jest używany w Projektancie przepływu pracy do edytowania <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> właściwość <xref:System.ServiceModel.Activities.Receive> działania. Aby uzyskać więcej informacji, zobacz [wyświetlony Projektant działań](../workflow-designer/receive-activity-designer.md).

Korelacja między <xref:System.ServiceModel.Activities.Receive> działania określa, jak różne usługi operations łączyć się ze sobą w przepływie pracy.

W poniższej tabeli opisano elementy interfejsu użytkownika **CorrelatesOn** okno dialogowe.

|Element interfejsu użytkownika|Opis|
|-|-----------------|
|**CorrelatesWith**|<xref:System.ServiceModel.Activities.CorrelationHandle> Służący do rozsyłania wiadomości dla wystąpienia przepływu pracy odpowiednie.|
|**Zapytania XPath**|Parą klucz/wartość, która zawiera zapytania, używany do wyodrębniania danych korelacji z komunikatów przychodzących. Ta wartość odpowiada <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> właściwości. Zapytania XPath są zawarte w <xref:System.ServiceModel.MessageQuerySet> obiektu.|

## <a name="to-launch-the-correlateson-dialog-box"></a>Aby uruchomić okno dialogowe CorrelatesOn

**Receive** projektanta działań mogą być przeciągnięte z **przybornika** i porzucić do powierzchni projektanta przepływów pracy wszędzie tam, gdzie działań są zazwyczaj umieszczone. Projektant działań porzucenie tworzy <xref:System.ServiceModel.Activities.Receive> działanie przy użyciu domyślnego <xref:System.Activities.Activity.DisplayName%2A> Receive. Aby otworzyć **definice Vlastnosti Correlateson** okno dialogowe, wybierz opcję **Receive** działania projektanta, a następnie w siatce właściwości wybierz przycisk wielokropka obok tekstu kolekcji dla  **Definiowanie CorrelatesOn** właściwości.

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Activities.Receive>
- [Dodawanie CorrelationInitializers, okno dialogowe](../workflow-designer/add-correlationinitializers-dialog-box.md)
- [Dodaj korelacji, okno dialogowe](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)
- [Inicjowanie korelacji, okno dialogowe](../workflow-designer/initialize-correlation-dialog-box.md)