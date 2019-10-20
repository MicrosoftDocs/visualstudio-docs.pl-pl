---
title: Okno dialogowe Edytor kolekcji typów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dae99166b8b811df75f2e2777d176e6778b60c7d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670149"
---
# <a name="type-collection-editor-dialog-box"></a>Edytor kolekcji typów, okno dialogowe
Okno dialogowe **Edytor kolekcji typów** służy do dodawania znanych typów do działań **wysyłania** i **odbierania** . To okno dialogowe służy również do dodawania argumentów typu ogólnego do działania **InvokeMethod** . W przypadku użycia dla działań **wysyłania** i **odbierania** do dodawania znanych typów okno dialogowe **Edytor kolekcji typów** wymaga, aby dodatki typu były unikatowe. Jeśli zostanie dodany zduplikowany typ, a zmiana zostanie zatwierdzona przez kliknięcie przycisku **OK**, zostanie zwrócony komunikat o błędzie. Gdy jest używane dla działania **InvokeMethod** do dodawania argumentów typu generycznego, okno dialogowe **Edytor kolekcji typów** umożliwia dodanie zduplikowanych typów.

> [!NOTE]
> [!INCLUDE[crabout](../includes/crabout-md.md)] znanych typów, zobacz [znane typy kontraktu danych](https://msdn.microsoft.com/library/1a0baea1-27b7-470d-9136-5bbad86c4337).

 W poniższej tabeli opisano elementy interfejsu użytkownika (UI) okna dialogowego **kolekcji typów** .

|Element interfejsu użytkownika|Opis|
|----------------|-----------------|
|**Lista typów**|Lista typów, które zostały dodane lub usunięte.|

## <a name="to-bring-up-the-type-collection-editor"></a>Aby wyświetlić Edytor kolekcji typów

#### <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Aby wyświetlić Edytor kolekcji typów dla działań wysyłania i odbierania

1. Wybierz działanie **Wyślij** lub **Odbierz** w widoku projektu.

2. Naciśnij klawisz **F4** , aby wyświetlić okno **Właściwości** .

3. W oknie **Właściwości** kliknij przycisk wielokropka obok właściwości **KnownTypes** .

#### <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>Aby wyświetlić Edytor kolekcji typów dla działania InvokeMethod

1. Wybierz działanie **InvokeMethod** w widoku projektu.

2. Naciśnij klawisz **F4** , aby wyświetlić okno **Właściwości** .

3. W oknie **Właściwości** kliknij przycisk wielokropka obok właściwości **GenericTypeArguments** .