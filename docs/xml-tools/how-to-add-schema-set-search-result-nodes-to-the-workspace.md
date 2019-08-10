---
title: Dodawanie węzłów wyników wyszukiwania zestawu schematu XML do obszaru roboczego
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ff33b3cc-4db9-4b4e-9378-b45ed5999b18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2718c08b36ff9ef3ca8ae06f7d511cacb8fa73c
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923656"
---
# <a name="how-to-add-schema-set-search-result-nodes-to-the-workspace"></a>Instrukcje: Dodawanie węzłów wyników wyszukiwania zestawu schematu do obszaru roboczego

W tym temacie wyjaśniono, jak dodać węzły, które są wyróżnione w **Eksploratorze schematu XML** jako wynik wyszukiwania słowa kluczowego w obszarze roboczym.

> [!NOTE]
> Do [obszaru roboczego](../xml-tools/xml-schema-designer-workspace.md)można dodawać tylko węzły globalne.

W tym przykładzie zastosowano przykładowy [schemat zamówienia zakupu](../xml-tools/sample-xsd-file-purchase-order-schema.md).

## <a name="to-add-schema-set-result-nodes"></a>Aby dodać węzły wynikowe zestawu schematów

1. Wykonaj kroki opisane w [temacie How to: Tworzenie i edytowanie pliku](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)schematu XSD.

2. Wpisz "purchaseOrder" w polu tekstowym wyszukiwania na pasku narzędzi [Eksploratora XML](../xml-tools/xml-schema-explorer.md) i kliknij przycisk wyszukiwania.

     ![Wyszukiwanie słów kluczowych w Eksploratorze schematu XML](../xml-tools/media/schemaexplorersearch.gif)

     Wyniki wyszukiwania są wyróżniane w **Eksploratorze schematu XML** i oznaczone przez znaczniki na pionowym pasku przewijania.

3. Dodaj wyniki wyszukiwania do obszaru roboczego, klikając przycisk **Dodaj wyróżnione węzły do obszaru roboczego** w okienku wyniki podsumowania.

     ![Wynik wyszukiwania Eksploratora schematu XML](../xml-tools/media/schemaexplorersearchresult.gif)

     Węzeł i węzeł są wyświetlane obok siebie na powierzchni projektowej [widoku wykresu.](../xml-tools/graph-view.md) `purchaseOrder` `PurchaseOrderType` Ponieważ dwa węzły są powiązane ( `purchaseOrder` element jest `PurchaseOrderType` typu), zostanie narysowana strzałka między nimi.