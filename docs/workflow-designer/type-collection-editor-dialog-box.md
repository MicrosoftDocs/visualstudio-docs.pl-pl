---
title: Projektant przepływu pracy — okno dialogowe Edytor kolekcji typów
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 191635364c445bc3959ee2f5f63c7c72c71f171d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433932"
---
# <a name="type-collection-editor-dialog-box"></a>Edytor kolekcji typów, okno dialogowe

**Editor typu Kolekce** okno dialogowe służy do dodawania znanych typów do **wysyłania** i **Receive** działań. To okno dialogowe umożliwia również dodawać argumenty typu generycznego **InvokeMethod** działania. Gdy jest używana dla **wysyłania** i **Receive** działań do dodania znane typy **Editor typu Kolekce** okno dialogowe wymaga dodatki typu, aby była unikatowa. Jeśli zduplikowany typ zostanie dodany, a zmiana jest zatwierdzona, klikając **OK**, zwracany jest komunikat o błędzie. Gdy jest używana dla **InvokeMethod** działanie, aby dodać argumenty typu generycznego **Editor typu Kolekce** okno dialogowe umożliwia dodanie typy zduplikowanych.

Aby uzyskać więcej informacji, zobacz [znane typy kontraktów danych](/dotnet/framework/wcf/feature-details/data-contract-known-types).

W poniższej tabeli opisano elementy interfejsu użytkownika **kolekcji typów** okno dialogowe.

|Element interfejsu użytkownika|Opis|
|-|-----------------|
|**Lista typów**|Lista typów, które zostały dodane lub usunięte.|

## <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Aby przełączyć się Edytor kolekcji typów do wysyłania i odbierania działań

1. Wybierz **wysyłania** lub **Receive** działania w widoku Projekt.

2. Naciśnij klawisz **F4** aby przywołać **właściwości** okna.

3. W **właściwości** , kliknij przycisk wielokropka znajdujący się obok **element KnownTypes** właściwości.

## <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>Aby wyświetlić się Edytor kolekcji typów dla działania InvokeMethod

1. Wybierz **InvokeMethod** działania w widoku Projekt.

2. Naciśnij klawisz **F4** aby przywołać **właściwości** okna.

3. W **właściwości** , kliknij przycisk wielokropka znajdujący się obok **GenericTypeArguments** właściwości.