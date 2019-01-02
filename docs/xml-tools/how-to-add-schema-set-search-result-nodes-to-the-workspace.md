---
title: Dodawanie węzłów wyników wyszukiwania zestawu schematu XML do obszaru roboczego
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9e9f004943474f9b1c0fb449c1aec23f70034c3a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53875037"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Instrukcje: Dodawanie węzłów wyników wyszukiwania zestawu schematu do obszaru roboczego

W tym temacie został objaśniony sposób dodawania węzłów, które zostały wyróżnione **Eksploratora schematu XML** w wyniku wyszukiwania słów kluczowych, w obszarze roboczym.

> [!NOTE]
> Tylko globalne węzły mogą być dodawane do [obszaru roboczego](../xml-tools/xml-schema-designer-workspace.md).


 W tym przykładzie użyto przykładu [schemat zamówienia zakupu](../xml-tools/sample-xsd-file-purchase-order-schema.md).

## <a name="to-add-schema-set-result-nodes"></a>Aby dodać węzłów wyników zestawu schematu

1.  Postępuj zgodnie z instrukcjami w [jak: Tworzenie i edytowanie pliku schematu XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2.  W polu tekstowym wyszukiwania wpisz "purchaseOrder" [Eksplorator XML](../xml-tools/xml-schema-explorer.md) paska narzędzi i kliknij przycisk wyszukiwania.

     ![Wyszukiwanie słów kluczowych Eksploratora schematu XML](../xml-tools/media/schemaexplorersearch.gif)

     Wyniki wyszukiwania zostaną wyróżnione w **Eksploratora schematu XML** i oznaczone przez znaczniki na pionowy pasek przewijania.

3.  Dodaj wyniki wyszukiwania do obszaru roboczego, klikając **Dodaj wyróżnione węzły do obszaru roboczego** przycisk w okienku wyników podsumowania.

     ![Wynik wyszukiwania Eksploratora schematu XML](../xml-tools/media/schemaexplorersearchresult.gif)

     `purchaseOrder` Węzła i `PurchaseOrderType` węzła wyświetlane obok siebie na powierzchni projektowania [widoku wykresu](../xml-tools/graph-view.md). Ponieważ dwa węzły są powiązane ( `purchaseOrder` element jest `PurchaseOrderType` typu), Strzałka jest rysowana między nimi.