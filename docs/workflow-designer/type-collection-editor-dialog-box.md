---
title: Projektant przepływu pracy-typ okna dialogowego edytora kolekcji
description: Dowiedz się, jak za pomocą okna dialogowego Edytor kolekcji typów dodawać znane typy do działań wysyłania i odbierania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b8f194ee792f2a60df71a78af6f41e45aaac91da
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875266"
---
# <a name="type-collection-editor-dialog-box"></a>Edytor kolekcji typów, okno dialogowe

Okno dialogowe **Edytor kolekcji typów** służy do dodawania znanych typów do działań **wysyłania** i **odbierania** . To okno dialogowe służy również do dodawania argumentów typu ogólnego do działania **InvokeMethod** . W przypadku użycia dla działań **wysyłania** i **odbierania** do dodawania znanych typów okno dialogowe **Edytor kolekcji typów** wymaga, aby dodatki typu były unikatowe. Jeśli zostanie dodany zduplikowany typ, a zmiana zostanie zatwierdzona przez kliknięcie przycisku **OK**, zostanie zwrócony komunikat o błędzie. Gdy jest używane dla działania **InvokeMethod** do dodawania argumentów typu generycznego, okno dialogowe **Edytor kolekcji typów** umożliwia dodanie zduplikowanych typów.

Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](/dotnet/framework/wcf/feature-details/data-contract-known-types).

W poniższej tabeli opisano elementy interfejsu użytkownika (UI) okna dialogowego **kolekcji typów** .

|Element interfejsu użytkownika|Opis|
|-|-----------------|
|**Lista typów**|Lista typów, które zostały dodane lub usunięte.|

## <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Aby wyświetlić Edytor kolekcji typów dla działań wysyłania i odbierania

1. Wybierz działanie **Wyślij** lub **Odbierz** w widoku projektu.

2. Naciśnij klawisz **F4** , aby wyświetlić okno **Właściwości** .

3. W oknie **Właściwości** kliknij przycisk wielokropka obok właściwości **KnownTypes** .

## <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>Aby wyświetlić Edytor kolekcji typów dla działania InvokeMethod

1. Wybierz działanie **InvokeMethod** w widoku projektu.

2. Naciśnij klawisz **F4** , aby wyświetlić okno **Właściwości** .

3. W oknie **Właściwości** kliknij przycisk wielokropka obok właściwości **GenericTypeArguments** .
